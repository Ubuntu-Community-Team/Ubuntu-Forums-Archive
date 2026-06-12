---
title: "Overriding NetworkManager"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by Living2007 on 2010-03-14
I have made some manual settings for my network adapter. Note: that I have upgraded to 9.10 from 8.04 LTS.

After making the changes to /etc/network/interfaces, NetworkManager will not co-operate and will set to the automatic settings.

How do I stop NM?

---

### Post by chili555 on 2010-03-14
This is an ongoing issue of research by me. I believe that NM is so tightly interwoven into our systems that manual configuration won't work, at all, unless NM is completely removed. Thank you for agreeing to be a test pilot in my further learning!

There are several tings you can try. First, you can go to System > Preferences > Startup Applications and uncheck NM. Reboot. Is the behavior improved; that is, do your manual settings in *interfaces* work?

Second, you can do:```
sudo /etc/init.d/network-manager stop
```Of course, the method that always works is to remove NM entirely. I will appreciate your observations.

---

### Post by Living2007 on 2010-03-24
Removing NM was a failure as I could no longer connect and redownload it. Since re-installing and inputing the following into "interfaces" 

```
audo wlan0
iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-essid wireless
wireless-key s:[128-bit ACSII key]

#auto eth0
iface eth0 inet dhcp
```

i'm still running on dynamic IP address with 192.168.1.6 currently being used!

Note: that I am now using 9.10 cause I thought i might be able to get my Canon iP1600 printer working, not work at all as no driver exists for 9.10...

---

### Post by kerry_s on 2010-03-24
use the network manger to set the static settings, i do it on mine.

---

### Post by dineshs on 2010-03-24
What I understand is that,If you are using network manager,any changes you make (by rightclicking on the nmapplet tray icon) will be written on /etc/NetworkManager/system-connections and not on /etc/network/interfaces.So the contents of the file /etc/network/interfaces should be```
auto lo
iface lo inet loopback
```
(comment out anything else)

---

### Post by Iowan on 2010-03-24
> **Living2007 said:**
> 

```
[COLOR="Red"]audo[/COLOR] wlan0
iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-essid wireless
wireless-key s:[128-bit ACSII key]

#auto eth0
iface eth0 inet dhcp
```

Is this (hand) transcribed from */etc/network/interfaces* - or is "auto" actually misspelled in the file?

---

