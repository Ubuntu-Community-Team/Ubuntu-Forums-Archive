---
title: "O2 dongle not appearing in Ubuntu"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by merrymoll on 2010-04-06
Yes, it me begging for help *again. :p*
 
I've got an O2 dongle 3g, and want to use it on my Eeepc 2G surf, which has Eeebuntu base (equivalent to Ubuntu 9.10).  
 
Now, I see that the dongle is supposed to be recognised by the system, but that's not happening here.  I plug it in but nothing happens, it doesn't come up on the desktop or in the files menu.  It's as if there's nothing plugged in.  The dongle does work - tested it on a windows PC, and I've filled in all the correct info on the network settings in ubuntu.
 
Anyone know what's going on, and how I can fix this?

---

### Post by alexfish on 2010-04-06
hi

try to find if the dongle is been recognised by the system , enter these commands from the terminal and post the results

Code:

lsusb

Code:

dmesg | grep -e "modem" -e "tty" 

from a separate terminal

Code:

tail -f /var/log/syslog   ; enter this before the dongle is plugged in


also by which dialup method or version of software are you configuring the device

thanks in advance

alexfish

---

### Post by merrymoll on 2010-04-06
> **alexfish said:**
> hi

try to find if the dongle is been recognised by the system , enter these commands from the terminal and post the results

Code:

lsusb

Code:

dmesg | grep -e "modem" -e "tty" 

from a separate terminal

Code:

tail -f /var/log/syslog   ; enter this before the dongle is plugged in


also by which dialup method or version of software are you configuring the device

thanks in advance

alexfish

Right, here's what I got:

moll@eccles:~$ lsusb
Bus 001 Device 007: ID 19d2:2000  
Bus 001 Device 003: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
moll@eccles:~$ dmesg | grep -e "modem" -e "tty" 
[    0.004000] console [tty0] enabled
moll@eccles:~$ dmesg | grep -e "modem" -e "tty" 
[    0.004000] console [tty0] enabled

and:

moll@eccles:~$ tail -f /var/log/syslog
Apr  6 20:08:41 eccles anacron[4639]: Updated timestamp for job `cron.daily' to 2010-04-06
Apr  6 20:09:26 eccles anacron[4848]: Anacron 2.3 started on 2010-04-06
Apr  6 20:09:26 eccles anacron[4848]: Will run job `cron.weekly' in 10 min.
Apr  6 20:09:26 eccles anacron[4848]: Will run job `cron.monthly' in 15 min.
Apr  6 20:09:26 eccles anacron[4848]: Jobs will be executed sequentially
Apr  6 20:09:29 eccles kernel: [  541.052142] usb 1-2: new high speed USB device using ehci_hcd and address 7
Apr  6 20:09:29 eccles kernel: [  541.234275] usb 1-2: configuration #1 chosen from 1 choice
Apr  6 20:09:29 eccles kernel: [  541.271601] usb-storage: device ignored
Apr  6 20:10:01 eccles /USR/SBIN/CRON[5009]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  6 20:10:16 eccles kernel: [  588.152461] usb 1-2: USB disconnect, address 7
Apr  6 20:11:30 eccles kernel: [  662.460100] usb 1-2: new high speed USB device using ehci_hcd and address 8
Apr  6 20:11:30 eccles kernel: [  662.654092] usb 1-2: configuration #1 chosen from 1 choice
Apr  6 20:11:30 eccles kernel: [  662.681797] usb-storage: device ignored
Apr  6 20:17:01 eccles /USR/SBIN/CRON[5284]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


As for what I'm using to configure, it's just the network connection manager that came with Ubuntu - the OS is 9.10, if that's any help.  What further info do you need, and how can I get it for you?

Thanks!:)

---

### Post by alexfish on 2010-04-06
hi

from the info above it looks as if the device is of the zte family, and this one is only been seen as the cd, and not recognised by the kernel , although a few of them do work out of the box, and some may require the usb modeswitch

 a little twist  these modems.Sometimes the usb modeswitch will reset the device,so if you have the usb modeswitch installed the try to remove it, then see if it is recognised by the system

if not

can you have a look to see which model it is, have a look at the case and supply all info on it

then try the latest usb modeswitch from debian



[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]

 regards

alexfish

---

### Post by pdc on 2010-04-06
Hi merrymoll;

so you need to "unmask" the modem in your device;

alex quite rightly describes one way;

another way to try quickly before installing usb_modeswitch is if you get an icon on your desktop; right-click on it, and select "eject" from the drop down menu;

you can try that before installing usb_modeswitch;

if you get the icon, and it disappears, if you type

> lsusb

you will likely see a different number now for your device now

.. for example ..

> 19d2:0031  or 19d2:0063 or something ... that's good !!

you then configure from the network manager; are you happy with that bit?

if "eject" works, we can tell you a simple way

---

