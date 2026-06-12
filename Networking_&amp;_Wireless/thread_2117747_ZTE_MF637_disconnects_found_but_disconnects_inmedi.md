---
title: "ZTE MF637 disconnects found but disconnects inmediatly"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by cabuyano on 2013-02-19
I just bought a ZTE MF637 ( lsusb reports vendor 0x19d2 product 0x0121)broadband dongle from Orange for my Ubuntu 12.04 box. I've done everything adviced in this forum to make it work but it's been useless so far. I have search this forum many many time and tested every solution but nothing solves my connection problem.
Ubuntu detects the modem and I have created the corresponding connection but when I try to connect the modem disconnects inmediatly.

I need help....better...I need a solution because I dont want to go back to Windows. :KS

Repeat: I've followed every suggestion found in this forum but no luck so fat.
I Need You Help.

---

### Post by cabuyano on 2013-02-19
I forgot to mention that if I run Live CD, the modem is recognized and I can connect to internet.

Hope this help

---

### Post by zearendil on 2013-03-23
I have the same issue. Did not try the Live CD. But tried on different machines, all under kubuntu 12.04 LTS, some updated lately, some did not updated for months, same result. Windows XP works with the drivers provided from the device.

It was working fine, at some point (maybe a month ago) just stopped working as described above. This is what I see in the /var/log/syslog:
> 
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) starting connection 'GloBul'
Mar 23 16:39:59 trader NetworkManager[1209]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Mar 23 16:39:59 trader NetworkManager[1209]: <info> (ttyUSB2): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Mar 23 16:39:59 trader NetworkManager[1209]: <info> (ttyUSB2): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 23 16:39:59 trader NetworkManager[1209]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Mar 23 16:39:59 trader modem-manager[1137]: <info>  (ttyUSB2) opening serial port...
Mar 23 16:39:59 trader modem-manager[1137]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (disabled -> enabling)
Mar 23 16:40:00 trader modem-manager[1137]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (enabling -> disabled)
Mar 23 16:40:00 trader modem-manager[1137]: <info>  (ttyUSB2) closing serial port...
Mar 23 16:40:00 trader modem-manager[1137]: <info>  (ttyUSB2) serial port closed
Mar 23 16:40:00 trader NetworkManager[1209]: <warn> GSM modem enable failed: (32) Unknown error
Mar 23 16:40:00 trader NetworkManager[1209]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'modem-init-failed') [40 120 28]
Mar 23 16:40:00 trader NetworkManager[1209]: <warn> Activation (ttyUSB2) failed.
Mar 23 16:40:00 trader NetworkManager[1209]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 23 16:40:00 trader NetworkManager[1209]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Mar 23 16:40:00 trader NetworkManager[1209]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Mar 23 16:40:00 trader NetworkManager[1209]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed


---

### Post by alexfish on 2013-03-23
have you tried ppp direct

to configure a ppp connection

```
sudo pppconfig
```

take your time with the details , the Number is usually *99#

ensure to set permisions

to call from the terminal

```
pon <your conecction>
```
 to disconect
```
 poff
```

BR

Alex

---

### Post by zearendil on 2013-03-24
> **alexfish said:**
> have you tried ppp direct

to configure a ppp connection

```
sudo pppconfig
```

take your time with the details , the Number is usually *99#


Thanks for the advice. But I could not deal with this. Tried different options, it did not ask me for the PIN for example. Can you recommend any tutorial on this? I saw few on the Internet, but looks like I do not have enough understanding to apply them.

---

### Post by zearendil on 2013-03-24
I noticed when I provide wrong parameters, like wrong dial number, it returns the same error 32. So most probably the provider changed some parameter, but the tech support was not aware of this.

---

### Post by alexfish on 2013-03-24
Can Ty Network manager with just the Phone Number this is generally pick out of the registers on the device
*99# is default ,

can look at this old thread , may be useful ,or may be not

[h=1][SIZE=2][How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")[/SIZE][/h]
Alex

---

### Post by zearendil on 2013-03-24
Once I realized the problem could be in the parameters, but not in the software, I tried different passwords, APNs, etc. Finally I found the right combination. Looks like the ISP changed the password (and/or APN), but because 'they support only windows' with a stupid software that masks the parameters, even the tech support guys did not know about this.

So I kind of lost your time, I am sorry about this :(. But at least it works now :guitar:

Thanks for the help!

---

### Post by alexfish on 2013-03-24
No problem

User names and passwords are mentioned in first post of the "How To"

> [FONT=Verdana][SIZE=2]Importance of User names and passwords .[/SIZE][/FONT]

BR

Alex

---

