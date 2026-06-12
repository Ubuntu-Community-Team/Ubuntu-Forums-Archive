---
title: "WLAN ThinkPad Edge E520 einrichtung geht nicht inkl. collectNWData"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by SyTeX on 2011-10-19
Hallo liebe Community =)
 

 Das ist mein erster Thread hier im LinuxBoard und leider komm ich gleich mit einem Problem :(
 

 Nach langer suche im Internet und vielen gefunden Threads zu diesem Thema schaff ich es leider dennoch nicht mein WLAN auf meinem Xubuntu 11.10 System (ThinkPad Edge E520) zum laufen zu bringen.
 

 Nach einer frischen Installation hatte ich mit iwconfig versucht zu schauen ob WLAN erkannt wurde...leider mit diesem Resultat:
 

```
lo        no wireless extensions.
 

 eth0      no wireless extensions.
 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off
           Power Management:on
 
``` Im Ubuntu WLAN wiki ([http://wiki.ubuntuusers.de/WLAN](http://wiki.ubuntuusers.de/WLAN)) hab ich versucht den Anweisungen zu folgen,
 was mich dazu bewegt hatte den ndiswrapper zu installieren.
 Da ich noch ein WIN7 OS parallel laufen habe, konnte ich nachschauen welchen Treiber ich dafür benötige und habe diesen auch auf der Lenovo-Homepage geladen und im ndiswrapper
 auch aufgerufen.
 Im gui vom ndiswrapper wird mir auch gezeigt das der Treiber netwns64 kompatibel ist,
 da dort „Hardware verfügbar: Ja“ steht.
 Consolen ausgabe:
```
netwns64 : driver installed 
     device (8086:0084) present (alternate driver: iwlagn)

``` Jedoch gibt iwconfig immer noch das selbe aus und ich kann keine WLAN Netze erkennen.
 

 Ich habe auf meinem Lenovo auch kein Hardware Switch mit dem ich das WLAN Ein- bzw. Ausschalten kann.
 Im NetzwerkManager ist unter dem Button Netzwerk aktivieren auch ein
 Funknetzwerk aktivieren, jedoch passiert nichts wenn ich diesen betätige.
 

 Auf verschiedenen Homepages habe ich gelesen das es auch mit den Broadcom und den STA
 Treibern laufen könnte. Über den SoftwareManager habe ich die Treiber installiert (immer nur 1 zur gleichen Zeit natürlich) und auch nach mehreren neustarts war das Ergebnis das gleiche.
 

 Zurzeit hab ich den ndiswrapper mit dem Windows Treiber aktiv und hab damit das ShellScript laufen lassen das die Netzwerke Prüft: collectNWData.sh
 

 Hier ist die ausgabe die ich bekommen habe:
 [http://pastehtml.com/view/bb4egledl.txt](http://pastehtml.com/view/bb4egledl.txt)
 

 Ich möchte im Endeffekt eine Verbindung zum Router aufbauen können und damit ins Internet oder einem LAN Netzwerk beitreten.
 

 Ich hoffe das mir irgendwer helfen könnte, da ich lieber wieder mit meinem Linux System arbeiten möchte.
 

 LG Sy

---

