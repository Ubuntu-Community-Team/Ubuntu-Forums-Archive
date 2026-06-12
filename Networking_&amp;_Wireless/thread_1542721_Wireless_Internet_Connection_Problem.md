---
title: "Wireless Internet Connection Problem"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by shahesan on 2010-07-31
Hi all,
I am using BSNL EVDO Usb modem (HUAWEI EC325)(Locked by BSNL).It sucessfully detected in Network Manager of UBUNTU 10.04 LTS.But when i connects,It doesn't works.I tried Wvdial app and confiqured but showing MODEM NOT RESPONDING.. i don't know what to do.. Anyone have any idea ? Me new to Ubuntu,So i lack some Knowledge on it.But i am trying to understand.Please Help me to fix this.

---

### Post by dineshs on 2010-07-31
May be your wvdial.conf has a wrong entry regarding the modem port.Pl try this
```
gksudo gedit /etc/wvdial.conf
```
there is a line similar to```
Modem = /dev/ttyS1
```Edit the line ```
Modem = /dev/ttyUSB0
```save and close file
Now run wvdial and see
(You can also try ttyUSB1 ttyUSB2 ttyUSB3 if USB0 doesnt work)
If you still have difficulties please post the output of
```
dmesg | grep -e "modem" -e "tty" 
```and
```
lsusb
```

---

### Post by shahesan on 2010-08-01
My Usb Modem is connected now using GNOME PPP Dialer But Sometimes Internet speed Becomes DamN Slow.. Network manager too detects mOdem and After confiquration,It still shows OFFLINE.PPP Dailer works but Speed.. Any suggestions ??

@dineshs : i think you are from Kerala Like Mine,I am Using BSNL NIC EVDO Datacard.

---

### Post by dineshs on 2010-08-01
Pl post the contents of
```
cat /etc/resolv.conf
```

---

