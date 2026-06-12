---
title: "alcatel x080s 3g modem"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by konsta82 on 2011-02-28
I can't use this modem on my lucid. Already installed usb-modeswitch & wvdial but still nothing. I can see mede in computer,named as mmc storage device,but I can't open it. When I installed usb-modeswitch for maverick,I was able to open it and it was shown as mounted on desktop,but there was no broadband connection in network manager.
Spent hours on google but I couldn't find nothing usefull.
Any idea's ???

---

### Post by alexfish on 2011-02-28
Hi

can have a look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

if still a problem

can post back here

alexfish

---

### Post by konsta82 on 2011-02-28
I'll try to do everything from your post. Will let you know what happened soon

---

### Post by konsta82 on 2011-02-28
```
echo -e "AT+CGDCONT?\r" > /dev/ttyUSB2"
```
no results for this

Later,network is recognised and it says modem is ready

```
konsta@konsta-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[  101.668296] usb 2-4: generic converter now attached to ttyUSB0
[  101.668624] usb 2-4: generic converter now attached to ttyUSB1
[  101.668924] usb 2-4: generic converter now attached to ttyUSB2

```
this looks ok probably :
```
konsta@konsta-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1bbb:0000 T & A Mobile Phones 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by konsta82 on 2011-02-28
Managed to connect via nm-applet but after restart it can't connect again

---

### Post by konsta82 on 2011-02-28
Solved with this script [http://www.sakis3g.org/]("http://www.sakis3g.org/")

Many thanks to Alexfish

---

### Post by alexfish on 2011-02-28
hi

was any specific command used to eject the device

also did you use a specific command to load the drivers

> [FONT=monospace]konsta@konsta-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[  101.668296] usb 2-4: [COLOR=Blue]generic converter now attached[/COLOR] to ttyUSB0
[  101.668624] usb 2-4: [COLOR=Blue]generic converter now attached[/COLOR] to ttyUSB1
[  101.668924] usb 2-4: [COLOR=Blue]generic converter now attached[/COLOR] to ttyUSB2[/FONT]was the computer shut down for the reboot

or just a reboot

ADDED: LOOKS AS IF THE PROBLEM SOLVED : YOUR POST GOT THERE BEFORE MINE

alexfish

---

### Post by kkfok1 on 2011-04-10
Hi,

Thank you for creating this post and provide the solution. 

There is a small problem that if I have connected to the internet using wire/wireless network in the beginning and when this connection is not available, I plug in the usb and want to use the 3G modem connection, although the sakis3g said connected but seems that Ubuntu Lucid still trying to access using the wire/wireless connection. I have to reboot the machine and only use the usb from the beginning in order for me to get the connection.

Can someone provide some "auto-switching" solution ?

thanks

---

