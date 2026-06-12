---
title: "Airlink 101 USB Wireless on Ubuntu 9.10"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2010-01-27
Howdy All,

So I recently obtained a USB wifi card, an Airlink 101 USB device. When I attach it to my Ubuntu system it is recognized by the network manager and it can see my wifi network - however it is unable to connect. When I enter the passcode for my wifi it spins trying to connect and then spits it back to me telling me I need to reenter the password after a few moments - I am 100% sure the password is correct. I tried the device on two different Ubuntu systems (one 32bit and one 64bit) and achieved the same results on each.

I can confirm the wifi itself works as I am typing from my laptop connected to it as we speak...

~Jeff

---

### Post by PRC09 on 2010-01-27
Not sure if it is a solution but read here somewhere that you can try right click on the network icon and select edit connections,select wireless,select add and re-setup your wireless with the needed info, reboot and then try connecting with the new connection.

---

### Post by beastrace91 on 2010-01-27
> **PRC09 said:**
> Not sure if it is a solution but read here somewhere that you can try right click on the network icon and select edit connections,select wireless,select add and re-setup your wireless with the needed info, reboot and then try connecting with the new connection.

Tried every hat trick like this I could think of - no good.

Any other ideas? I really need this wifi card to work and trying to avoid going back to Win7 as the solution.

Regards,
~Jeff

---

### Post by beastrace91 on 2010-01-30
I think I've gained some insight into why the Wireless card does not connect properly - for some reason when I do an **lsusb** it lists the card as an atheros device even though it is a ralink chipset... Could this be causing the kernel to be using the wrong driver for the card? If so how do I go about telling my system that it is actually a different card than has been automatically recognized?

Regards,
~Jeff

---

### Post by chewearn on 2010-01-30
Try this command:
```
lshw -c network
```

This will list the network hardware information.__

---

### Post by pdc on 2010-01-30
so what does 

> lsusb

give you, Jeff?

---

### Post by beastrace91 on 2010-02-02
Sorry for the delay, output of the two suggested commands: ```
oem@mintmedia ~ $ lsusb
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 003: ID 0ecd:a100 Lite-On IT Corp. LDW-411SX DVD/CD Rewritable Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0421:01c8 Nokia Mobile Phones 
Bus 001 Device 003: ID 14b2:3c27 Atheros Communications Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
oem@mintmedia ~ $ lshw -c network
WARNING: you should run this program as super-user.
^CI (sysfs)  
oem@mintmedia ~ $ sudo lshw -c network
[sudo] password for oem: 
SCSI    
```

Ideas/suggestions? As you can see lsusb lists the card as an Atheros device, however when I install the drivers for it on Windows it installs ralink chipset drivers...

Regards,
~Jeff

---

### Post by chewearn on 2010-02-02
Perhaps if you let
```
lshw -c network
```
complete, we can see the detail product model/id.

Note:
There is no need to run it with "sudo"; just ignore the complaint.

---

### Post by pdc on 2010-02-02
if you do a google search on 

> ubuntu 14b2:3c27 Atheros Communications Inc

you get some curious things; 

[http://lists.plug.phoenix.az.us/lurker/message/20081206.054839.eeb2c01a.ja.html](http://lists.plug.phoenix.az.us/lurker/message/20081206.054839.eeb2c01a.ja.html)

perhaps explains your atheros ralink dichotomy

the post above on fedora did yum install rt2870 

then iwconfig and got

> ra0 RT2870 Wireless ESSID:"" Nickname:"RT2870STA"
Mode:Auto Frequency=2.462 GHz Access Point: 00:18:02:78:B3:F3
Bit Rate=150 Mb/s
RTS thr:off Fragment thr:off
Link Quality=70/100 Signal level:-88 dBm Noise level:-97 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

you can read the rest of his post

you may well have the rt2870 advice at your fingertips; this post seems to be recommended for those wishing to read it

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom](http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom)

---

### Post by beastrace91 on 2010-02-02
> **chewearn said:**
> Perhaps if you let
```
lshw -c network
```
complete, we can see the detail product model/id.

Sorry about that, it hung the first time so I thought it was finished. Here is the output after I let it complete: ```
oem@mintmedia ~ $ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:a1:5b:6c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:28 memory:fe02b000-fe02bfff ioport:d800(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1d:6a:47:cb:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

```

Like I said - Ubuntu can see my wireless network however it cannot actually connect to it for what ever reason :-/

@pdc Going to look into that link you posted thanks.

~Jeff

---

### Post by beastrace91 on 2010-02-02
> **pdc said:**
> you may well have the rt2870 advice at your fingertips; this post seems to be recommended for those wishing to read it

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom](http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom)

My airlink is indeed an ra2870 and blacklisting the kernel modules as described in this thread worked like a charm!

Thanks much!
~Jeff

---

### Post by pdc on 2010-02-02
delighted to hear it worked; enjoy!

---

