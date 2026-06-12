---
title: "sony eriscson MD 300"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by ottomane on 2009-12-14
i have : 

----> 3G sony eriscson MD 300

----> OS : Ubuntu 9.10 - le Koala Karmique 

sudo gedit /etc/udev/rules.d/50-md300modem.rules

ACTION!="add", GOTO="3G_End" 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="d0cf", ATTRS{idVendor}=="0fce", RUN+="/bin/sh -c 'echo 2 > /sys/%p/bConfigurationValue'"
#SUBSYSTEMS=="usb", ATTRS{idProduct}=="d0cf", ATTRS{idVendor}=="0fce", NAME="%k", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'"
#BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", NAME="modem", PROGRAM="/bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'", RUN+="/usr/local/bin/md300-ethernet"
#SUBSYSTEMS=="usb", ATTRS{idProduct}=="d0cf", ATTRS{idVendor}=="0fce", RUN+="/usr/sbin/usb_modeswitch --default-vendor 0x0fce --default-product 0xd0cf" 
#BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", NAME="modem", PROGRAM="/bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'", RUN+="/usr/local/bin/md300-ethernet"
LABEL="3G_End"

gedit /etc/wvdial.conf

[Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","www.internet1.meditel.ma"
Phone = *99#
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = MEDINET
Username = MEDINET
Auto Reconnect = off
#Abort on Busy = on
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = 1


sudo wvdial :

Dec 14 14:22:00 othmane-laptop pppd[3256]: pppd 2.4.5 started by root, uid 0
Dec 14 14:22:00 othmane-laptop pppd[3256]: Using interface ppp0
Dec 14 14:22:00 othmane-laptop pppd[3256]: Connect: ppp0 <--> /dev/ttyACM0
Dec 14 14:22:00 othmane-laptop pppd[3256]: CHAP authentication succeeded: Congratulations!
Dec 14 14:22:00 othmane-laptop pppd[3256]: CHAP authentication succeeded
Dec 14 14:22:02 othmane-laptop pppd[3256]: LCP terminated by peer
Dec 14 14:22:02 othmane-laptop pppd[3256]: Modem hangup
Dec 14 14:22:02 othmane-laptop pppd[3256]: Connection terminated.
Dec 14 14:22:02 othmane-laptop pppd[3256]: Exit.

have you a solution?

---

### Post by puppywhacker on 2009-12-14
The modem connects and the operator drops the LCP link, the negotiation fails so you have to identify the option that fails. Wireshark or tcpdump may help or the wvdial dialup logs

---

### Post by GeorgeVita on 2009-12-14
Hi **ottomane**,
possibly your APN setting at Init4 line is wrong.

Ask your provider or try without 'www.' in front as:
```
Init4 = AT+CGDCONT=1,"IP","internet1.meditel.ma"
```

Regards,
George

---

### Post by ottomane on 2009-12-15
it works thx a lot [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001")

---

