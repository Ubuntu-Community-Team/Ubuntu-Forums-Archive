---
title: "GPRS via Bluetooth problem"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by Suolx on 2005-03-15
Hoary release, newest updates, 2.6.10-4-686 kernel

Fujitsu Siemens Amilo Pro V2000 centrino laptop
Mitsumi usb dongle
Sony Ericsson T68i phone

I have managed to get connection between laptop and phone work to a point.
Pairing can be done by phone if I type PIN key found in /etc/bluetooth/pin
i can ping my phone with the laptop
gnome-manager and hcitool finds the phone but can't do nothing to it. 


GPRS is the thing I want to get working and rfcomm is configured propably right. 

"rfcomm" says:
rfcomm0: 00:0A:D9:2E:BA:AC channel 0 clean

"rfcomm connect /dev/rfcomm0 00:0A:D9:2E:BA:AC"  says:
Can't connect RFCOMM socket: Host is down

if i try to use /dev/rfcomm0 as modem, any PPP connection software etc says that it can't connect.

Any ideas?

---

### Post by Suolx on 2005-03-22
Got it working, tho whines about login/password...grr =)

---

### Post by magicrobotmonkey on 2006-05-05
how'd you make it use rfcomm0 as a modem? I cant figure out how to do that

---

