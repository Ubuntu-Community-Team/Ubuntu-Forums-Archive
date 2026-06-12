---
title: "Problem:SetUp ZTE CDMA 2000 IX EVDO bsnl wireless terminal"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by JJWGOURAV on 2010-05-11
[FONT=&quot][/FONT]Hi,everyone!!! I started using linux ubuntu version9.04 2 days ago...And I am facing difficulties in configuring or using my bsnl ZTE CDMA 2000 IX EV-DO wireless data terminal in ubuntu... I can't install gnome-ppp on my system... Please help me in installing it in offline mode...

Also,I tried the following commands:
   [FONT=&quot]$ sudo aptitude update[/FONT][FONT=&quot]
[/FONT][FONT=&quot]$ sudo aptitude install wvdial gnome-ppp[/FONT][FONT=&quot][/FONT]
    [FONT=&quot]# lsusb
[/FONT]  [FONT=&quot]#modprobe usbserial vendor=0x19d2 product=0xfffe[/FONT]    [FONT=&quot]$ sudo nano -w /etc/wvdial.conf[/FONT]
I made the following changes in my wvdial.conf file,
  [FONT=&quot][Dialer Defaults][/FONT][FONT=&quot]
[/FONT][FONT=&quot]Init1 = ATZ[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Stupid Mode = 1[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Modem Type = USB Modem[/FONT][FONT=&quot]
[/FONT][FONT=&quot]ISDN = 0[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Phone = #777[/FONT][FONT=&quot]
[/FONT][FONT=&quot]New PPPD = yes[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Modem = /dev/ttyUSB0[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Username = *Your BSNL username here*[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Password = *Your BSNL Password*[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Baud = 460800[/FONT][FONT=&quot]
  I now saved the file and ran the following command:

[/FONT]  [FONT=&quot]$ sudo wvdial[/FONT]

I am getting an error message as:

Wvdial configuration 1.60
/dev/modem: command not found
/dev/modem: command not found
/dev/modem: command not found


Someone please suggest me on how can I getmy data card up and working in ubuntu...:)
Thanx in advance..

---

### Post by dineshs on 2010-05-11
Pl post the output of
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty" 
```
```
sudo wvdialconf
```

---

