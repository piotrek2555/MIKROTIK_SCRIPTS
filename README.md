# MIKROTIK_SCRIPT
///////
Switch LEDS- Przełączanie ledów.
///////
Script wlan-off-on-time - W określonych godzinach wlącza i wylącza wifi.
///////
<b>Arp-dynamic-mac-qos</b> / Zmiana dynamiczna kolejki qos w routerze MIkrotik, na podstawie adresu mac wyciągniętego z tablicy ARP.

Przydatne do qos po mac adresie.
Nawet jak host zmieni adres ip to i tak nie obejdzie limitu prędkości.

Można dodać arp-reply, by zablokować cały internet po zmianie adresu IP L3. /

/////////

WAN RESTART  -Restart wan na 10s, czyli zmiana ip dynamicznego. Wykrywanie interfejsu za pomocą ~ regexp . Działa z jednym interfejsem wan 

////////
EMAIL-BCK / #ustawienia tutaj pomiędzy "" wpisać swoje dane.

:local username "username"
:local email "email"
:local haslo "haslo"

Zmienić w skrypcie na własne.
Można dopisać, aby zmieniało model i jest skrypt uniwersalny
Działa z gmail backup
Wkleić w scripts i scheduler na tydzień.
Dodana zmienna dev określająca board-name z routerboard.
Działa tylko z mikrotik roterboard i ccr. Wersja sprawdzana 6.46.7
Wysyła także wersje systemu w e-mailu /


////////////////////////////////////


//////
wlan-off-on:


Poprawiony, interjes wylączania nie jako nazwa ale zmienna.

Sprawdza int 2.4 jeżeli jest wyłączony do go wlącza, ale interfejs 5Ghz także włącza, get 0 disable. Na podstawie pierwszego interfejsu 2.4 włącza drugi 5.

Jeżeli jest włączony interfejs 2.4 to go wyłącza, ale także wyłącza 5ghz 


/////////////


ddns.TXT ver.1: - Skrypt DDNS no-ip
Działa z wersją ROS 6.44.3
DDNS-NO.IP
Działa z usługą VPN IPSEC, IKEv2 


//////////////////////////
QOS-QUOTA -Skrypt działa w wersji ROS. 6.x //

Skrypt limituje prędkość po przekroczeniu 10 mb na kolejcie test do 256k około. Więcej w dokumentacji w środku skryptu.

typ kolejki ustaw default w obu przypadkach

można dostosować wartości do swoich prędkości na interfejsie

dodaj scheduler 5 min do odpalania skryptu:

w on event wpisać :

/system script run [find name="Limit-test"] /////////


/////////////
tx-power : Skrypt zmiejszający moc tx-power karty WLAN w godzinach od 22 do 07 na 3 dbi a potem zwiększający na 30 dbi

Karta Wlan nazwa: wlan0-main
Należy ustawić wartość mode tx-power na: all rates fixed, nie na default, bo skrypt nie zadziała.

Automatycznie dodaje się do harmonogramu z
ustawienie 55 minut sprawdzania

Skrypt:WLAN

Wkleić do termianala w WINBOX /////

DDNS ver.2  NOIP.com ///


Zmienia tylko WTEDY go ip w DDNS 
:if ($newIP =! $CurrentIP ) do={...} else={...} / Zapisuje w logach INFO.

Działa z  VPN  
