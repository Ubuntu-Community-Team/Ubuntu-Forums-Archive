---
title: "Need to umount 3G modem to get it working... Any workaround?"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2011-01-09
Hello there.

I have a ZTE 3G modem that seems to be fully compatible with Ubuntu. On my desktop that runs 10.10 i can simply plug it in and the system will automatically recognize it and connect the internet.

However, on my notebook i'm running the LTS version, and when i plug the modem it detects it as an storage media and mount it as a CD, so i need to eject it every time after i plug, so that the system can detect it as a modem and connect.

Is there a way to avoid Ubuntu mounting it?

Thanks in advance.

---

### Post by alexfish on 2011-01-09
hi

can try :

[COLOR=Blue][B][COLOR=Black]ZTE DEVICES NOT SWITCHING:

to find state of device : from the terminal
[/COLOR][/B][COLOR=Black]
Code:

[COLOR=Blue]usb-devices[/COLOR]

example reply

T: Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#= 5 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=[COLOR=Blue]19d2[/COLOR] ProdID=[COLOR=Blue]2000[/COLOR] Rev=00.00
S: Manufacturer=ZTE, Incorporated
S: Product=ZTE CDMA Technologies MSM
C: #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=[COLOR=Blue]usb-storage[/COLOR]

to fix try

Code:

[COLOR=Blue]sudo gedit /etc/udev/rules.d/zte_eject.rules
[/COLOR]
add this line edit the device ID's according to the device

SYSFS{idVendor}=="[COLOR=Blue]19d2[/COLOR]", SYSFS{idProduct}=="[COLOR=Blue]2000[/COLOR]", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

save exit and reboot[/COLOR][/COLOR]

remember to change the [COLOR=Blue]ID's[/COLOR] according to the device
if this rule fails then assume latest usb_modeswitch is required for your device

also check to see if the latest usb_modeswitch  installed on the system , ubuntu 10.10 may have a version installed at default (I think says he),but may not be the latest

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

alexfish

---

### Post by Repgahroll on 2011-01-10
Thank you very much!

---

