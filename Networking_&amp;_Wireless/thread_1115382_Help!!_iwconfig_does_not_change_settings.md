---
title: "Help!! iwconfig does not change settings"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by i_8_tacos on 2009-04-03
hi im a linux newbie and i have been having trouble getting my wireless to work.

it all started when network manager just quit connecting. so after hours of reading i figured out how to use sudo iwconfig and dhclient to make my wireless work. It was working great but it would drop the connection sometimes so i tried installing WICD. for some odd reason i could not get it to connect with wicd. so i removed it and now i can't use the internet

i try doing :
sudo iwconfig wlan1 essid "2WIRE317"
 but then when i iwconfig with no paramaters it still says essid: off/any. its almost as if wicd or network manager is still running but i removed those packages already.

Btw .... rebooting does not help.
any help is much apreciated.

---

### Post by x22 on 2009-04-03
welcome to the forum

here's what I use to fire up the wireless:

ifconfig wlan0 up
iwconfig wlan0 essid home
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 12345abcde
iwconfig wlan0 key open
dhclient wlan0 

modify to suit

---

### Post by i_8_tacos on 2009-04-04
well thanks almost exactly what i do to get mine to work excep that right now it does not save the settings i type in

example:
i8tacos@i8tacos:~$ sudo iwconfig wlan1 essid "2WIRE317"

i8tacos@i8tacos:~$ sudo iwconfig

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"off/any"  
          Mode:Managed  Frequency:2.462 GHz  Access Point:
          Bit Rate=   Tx-Power:   Sensitivity= 
          RTS thr:   Fragment thr:
          Power Management:
          Link Quality:0/100  Signal level:  Noise level:
          Rx invalid nwid:  Rx invalid crypt:  Rx invalid frag:
          Tx excessive retries:  Invalid misc:   Missed beacon:

---

