---
title: "problem with AVM Fritz WLAN USB Stick"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by wkt on 2010-07-04
I have a problem with my AVM Fritz WLAN USB Stick which I get not activated.

I installed the nice ndisgtk program und could install the AVM Linux driver for the stick. ( ndiswrapper directory correctly filled )

But if I run the wpa-supplcant command I get errors. The history of the commands I ran and output I got follows here : can you have a look and make a suggestion what might be wrong with my wpa-supplicant configuration file ? Or is the driver not working ?
My network is WPA2.

# iwconfig output

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# output of : iwlist wlan0 scan 

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:3F:47:10:44
                    ESSID:"FRITZ!Box Fon WLAN 7113"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

# wpa2 supplicant file

network={ 
    ssid="FRITZ!Box Fon WLAN 7113" 
    key_mgmt=WPA-PSK 
    proto=WPA2 
    pairwise=CCMP  
    group=CCMP 
    psk="hier habe ich meinen geheimen Schlüssel eingetragen" 
}

# Protokol of output of wpa_supplicant command under Ubuntu
  sudo wpa_supplicant -Dwext -i wlan0 -c config-wpa2 -dd

Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 304 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1f:3f:47:10:44 ssid='FRITZ!Box Fon WLAN 7113' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   **skip RSN IE - GTK cipher mismatch**
Try to find non-WPA AP
0: 00:1f:3f:47:10:44 ssid='FRITZ!Box Fon WLAN 7113' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   **skip - non-WPA network not allowed**
No suitable AP found.

---

### Post by flash63 on 2010-07-04
Hallo,
die FB verwendet gemischte Verschlüsselung. Das passt nicht zur angelegten Konfiguration. Zeigt ja auch direkt die Fehlermeldung:
> skip RSN IE - GTK cipher mismatch

Ändere die SSID von Werkseinstellung "FRITZ!Box Fon WLAN 7113" auf etwas anderes und verwende rein WPA2-CCMP (AES). Der Network-Manager funktioniert aber auch mit dem Stick und eine manuelle Konfiguration ist normalerweise nicht erforderlich.

---

### Post by wkt on 2010-07-04
Die Werkseinstellung der SSID kann ich nicht ändern, da ich einen Rechner mit Windows CE habe, der diese Einstellung unveränderbar braucht.

Ist der Netzwerkmanager ein besonders zu installierendes Programm oder ist der gemeint der schon im System vorhanden ist. Der zeigt aber die WLAN Verbindung nicht an und ich weiß nicht was/ob ich da was HINZUFÜGEN muß/soll.
Bräuchte eine Anleitung wie ich den bedienen soll.

Danke für die Antwort. Ich habe im Router auf WPA2 (CCMP) umgestellt, das hatte aber keine positive Wirkung. Muß ich statt WPA2 dieses RSN in der config Datei angeben. Bin ziemlich ratlos !

---

### Post by flash63 on 2010-07-04
Hallo,
> Die Werkseinstellung der SSID kann ich nicht ändern, da ich einen Rechner mit Windows CE habe, der diese Einstellung unveränderbar braucht.
das verstehe ich jetzt zwar nicht, da die SSID ja automatisch übernommen wird. Aber ok, ist nicht zwingend erforderlich.

Der Mangaer ist das kleine Symbol rechts im oberen Panel links neben dem Lautstärkeregler.
> Muß ich statt WPA2 dieses RSN in der config Datei angeben. Bin ziemlich ratlos !
Das ist egal, beides ist möglich.

Für eine genauere Diagnose benötige ich weitere Angaben zu System und verwendetem Treiber mit angeschlossenen Fritz-Stick
```

cat /etc/lsb-release
uname -a
lsusb
ndiswrapper -l
dmesg | grep ndis
iwconfig

```

---

### Post by wkt on 2010-07-05
> **flash63 said:**
>  Der Mangaer ist das kleine Symbol rechts im oberen Panel links neben dem Lautstärkeregler.

Vielen Dank ! Das war der entscheidende Hinweis. Mit dem Network-Manager-Applet hat die Verbindung sofort geklappt !!! Nur dieser wpa-supplicant-Befehl hatte immer wieder Probleme. 

Sollten Sie noch an den Informatione zum System und der Ausgabe von wpa-supplicant interessiert sein kann ich die jederzeit nachreichen.

---

