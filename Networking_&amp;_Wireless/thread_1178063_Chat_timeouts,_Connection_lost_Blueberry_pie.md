---
title: "Chat timeouts, Connection lost? Blueberry pie?"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by Collinux on 2009-06-04
[SIZE=2]Hello, I'm new around here, and I'm having some trouble with my wireless.

I have a Compaq C300 laptop. With this model, wireless works right out of the box with ubuntu, but I'm having a bit of an issue with my connection being choppy. I don't notice it with normal browsing, and I'm not given any signal that the connection was lost.. except in two places - Chat programs (I've tried pidgin, amsn, even ebuddy - happens all across the board) and while watching Youtube videos. A lot of times, a video will load about 1/8th of the way, then lose the connection, then regain it.

The message I get in most chat programs is "The connection was lost" with the option to reconnect. In the Debug window of Pidgin, it shows tens of times a minute "[/SIZE][COLOR=#000000][SIZE=3][SIZE=2]**proxy:** No environment settings found, not using a proxy". 

So I went to my Network Proxy settings and changed from Direction Connection to a proxy site. Didn't fix the problem.. My boyfriend thinks that it's a router issue - I have a D-Link dir-625 (just in case it's relevant info, might as well say).

Would it be worth my time to call D-Link? Is there anything else I should try to fix this problem? The connecting and reconnecting is really annoying and makes communicating impossible. Sorry for being wordy, but it's better than being vague and leaving tons of questions for you guys to ask.

Thanks,
Colleen
[/SIZE][/SIZE][/COLOR]

---

### Post by Collinux on 2009-06-04
[SIZE=2]Oh, more info, sorry. This is what I get from Terminal, using the commands in the "how to post a wireless issue" thing:[/SIZE]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

[SIZE=2]With the command "lsusb":[/SIZE]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[SIZE=3]Maybe this is some help. [/SIZE]:KS

---

### Post by pastalavista on 2009-06-04
[This post]("http://ubuntuforums.org/showthread.php?t=87798") may be the fix you need.. maybe.

or maybe [this one]("http://ubuntuforums.org/showthread.php?t=6841")

---

### Post by Collinux on 2009-06-04
Pidgin hasn't timed out yet - Thank you, Pasta la vista! The messages are still there in the Debug window, but I don't care, as long as the program does its job. Your name is making me hungry.. but anyway, thanks.

Hasta la pasta!

---

