---
title: "Sprint Sierra 250U 3G only"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by n.brenner on 2010-09-25
1  In terminal...App > Acc > terminal

sudo gedit /etc/modules

under lp, add the word: option

make no other changes

file > save >quit

2  sudo gedit /etc/rc.local

under #By default.....

add: echo "1199 0301" > /sys/bus/usb-serial/drivers/option1/new_id

make no other changes

file > save > quit

you are set up for 3G.  4G will probably be set up in Meerkat

restart

---

### Post by ScarEye on 2011-01-19
Hi,  This work with KPPP or something I am guessing?  Correct?

---

### Post by SaintDanBert on 2011-03-09
This thread says **SOLVED** but I continue to be stumped getting my 250U to work at all with Ubuntu Lucid.  Clear Mobile 4G provides the broadband service.

NOTE -- I have a shell script, **logStamp.sh** that puts its arguments into **/var/log/messages**. I use these as sign posts along the way to reporting troubles and watching what is happening.

On connection I get the following in **/var/log/messages**
```

Mar  9 10:16:47 mumbles GRILLON: *****=====***** Connect Sierra 250U 4G dongle *****=====*****
Mar  9 10:16:48 mumbles GRILLON: *****=====***** Connect Sierra 250U 4G dongle *****=====*****
Mar  9 10:16:59 mumbles kernel: [94272.689129] usb 1-3: new high speed USB device using ehci_hcd and address 13
Mar  9 10:16:59 mumbles kernel: [94272.820772] usb 1-3: configuration #1 chosen from 1 choice
Mar  9 10:16:59 mumbles kernel: [94272.820992] hub 1-3:1.0: USB hub found
Mar  9 10:16:59 mumbles kernel: [94272.821183] hub 1-3:1.0: 2 ports detected
Mar  9 10:17:02 mumbles kernel: [94275.576208] usb 1-3.2: new full speed USB device using ehci_hcd and address 15
Mar  9 10:17:02 mumbles kernel: [94275.674014] usb 1-3.2: configuration #1 chosen from 1 choice
Mar  9 10:17:02 mumbles kernel: [94275.674749] sierra 1-3.2:1.0: Sierra USB modem converter detected
Mar  9 10:17:02 mumbles kernel: [94275.675047] usb 1-3.2: Sierra USB modem converter now attached to ttyUSB0
Mar  9 10:17:02 mumbles kernel: [94275.675158] usb 1-3.2: Sierra USB modem converter now attached to ttyUSB1
Mar  9 10:17:02 mumbles kernel: [94275.675266] usb 1-3.2: Sierra USB modem converter now attached to ttyUSB2
Mar  9 10:17:02 mumbles kernel: [94275.675370] usb 1-3.2: Sierra USB modem converter now attached to ttyUSB3
Mar  9 10:17:03 mumbles kernel: [94277.108200] usb 1-3.1: new high speed USB device using ehci_hcd and address 16
Mar  9 10:17:04 mumbles kernel: [94277.201179] usb 1-3.1: configuration #1 chosen from 1 choice

```

I don't get anything in the way of a new network interface after connection of the dongle. [highlight]Isn't that supposed to happen with **ehci_hcd** detection?[/highlight] It appears to want handshakes similar to dial-up or PPP or PPPOE. This is not the case with win-dose (see below).

When I unplug the device, I get the following:
```

Mar  9 10:17:34 mumbles GRILLON: *****=====***** Remove Sierra 250U 4G dongle *****=====*****
Mar  9 10:17:36 mumbles GRILLON: *****=====***** Remove Sierra 250U 4G dongle *****=====*****
Mar  9 10:17:39 mumbles kernel: [94313.108725] usb 1-3: USB disconnect, address 13
Mar  9 10:17:39 mumbles kernel: [94313.108734] usb 1-3.1: USB disconnect, address 16
Mar  9 10:17:39 mumbles kernel: [94313.109351] usb 1-3.2: USB disconnect, address 15
Mar  9 10:17:39 mumbles kernel: [94313.109863] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
Mar  9 10:17:39 mumbles kernel: [94313.110026] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
Mar  9 10:17:39 mumbles kernel: [94313.110185] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
Mar  9 10:17:39 mumbles kernel: [94313.110350] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
Mar  9 10:17:39 mumbles kernel: [94313.110399] sierra 1-3.2:1.0: device disconnected

```


Win-dose Behavior
================
Under win-dose, there is a "connection manager" application. I don't provide, nor do I know, any login or other session credentials. The support desk told me that the hardware has its ID details -- like a mobile phone.

When I connect the dongle, win-dose sees the hardware and the application appears on the desktop. After a short processing delay, the connection is awake and available.

---

### Post by rrubr on 2011-03-19
I have a Dell Mini10 (1010) netbook running Ubuntu netbook edition 10.10 with the gnome desktop (the poulsbo problem), and after doing the 2 edits, my 250U says it connects with Time Warner broadband (3G), but I can't do anything with the connection.  My Wifi connection stays active, and if I manually disconnect it, I have no internet access, although the connection manager says the BB is still connected.  Any ideas?

---

