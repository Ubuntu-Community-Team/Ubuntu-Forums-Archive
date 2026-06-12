---
title: "MAC Address won't clone?"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by tez1982 on 2011-04-07
Bit of a strange one, to get internet I have to clone my MAC address on eth0.

I'm using Ubuntu 10.10 64bit and have had a couple of strange problems.

1. If I run macchanger after login and set the mac to the correct one everything works perfectly. But as soon as I reboot it reverts back to the old mac.

2. If I use the network settings (ie. the tray icon in the top right) to spoof the mac, then I get no connection. Eventually it does connect (I'm talking about a 10 minute wait) then I get kicked off after a few minutes.

3. If I edit the /etc/network/interfaces files there is no setting for et0. All that is in the file is:
auto lo
iface lo inet loopback
If I add the settings for et0 then I get the same problems as in 2. The settings I've been adding are.
auto eth0
iface eth0 inet dhcp
hwaddress ether 01:02:03:04:05:06 (obviously with a different MAC)


Can anyone point me in the right direction?

Thanks

Tez

---

### Post by tez1982 on 2011-04-07
Update:

My university turn off any plug for several minutes if they detect more than 1 MAC address of the same plug within a few seconds of each other. I assume this is what is causing the problems in 1 and 2?

---

### Post by tez1982 on 2011-04-07
Narrowed it right down now:

Contents of /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#pre-up ifconfig eth0 hw ether 00:01:02:03:04:05
hwaddress ether 00:24:8D:C3:5F:0B
#pre-up ifconfig eth0 hw ether 00:01:02:03:04:05

Whatever I do, when my laptop starts up the Mac Address has defaulted back? If I /etc/init.d/networking restart then the MAC address changes to what it should be???

---

