---
title: "Help with X10 lirc_atiusb required"
date: 2008-07-08
forum: Mythbuntu
---

### Post by Tukcedo on 2008-07-08
Ubuntu Friends,

I'm running Mythbuntu 8.04 on a Dell GX270 and most is working rather well, apart from the remote control, which I've been struggling with for days now. I've read through and followed literally scores of HowTo's, FAQ's and what have you not, but as yet to no avail. I'm writing this from memory (am not at home right now), but this is the status:

- Remote is an MCE with a USB-stick like receiver which advertises itself as an X10 according to lsusb
- Logs (messages, syslog) show that it is being recognised and initialised and both lirc_atiusb and lirc_dev are running
- In lirc/hardware.conf the driver is listed as atilubusb and lirc_atiusb and lirc_dev as modules, ati_remote is blacklisted
- /dev/lirc0 and /dev/lircd are being created although lirc0 has 660 permissions which I have to change to 666 in /etc/rc.local
- lircd.conf contains codes which I downloaded from internet and that I managed to confirm with mode2
- After running the mythbuntu script that creates the lircrc file (can't remember name exactly) I make both lirc/hardware.conf and the lircrc file contain the same remote "name": X10
- ONCE, just once, I managed to get irw to run and it showed the correct codes (mode2 always works)
- irw normally crashes lircd with a message in syslog saying that it can't assign the usb device or something along those lines, I can run lircd manually in foreground with input pointing to /dev/lirc0 and output to /dev/lircd and then it stays alive and allows irw to run

My conclusion is that the basic hardware/lirc functionality works since mode2 shows the correct results. However, at the next conceptual level it seems to go wrong, which is probably why irw doesn't normally work.

So how do I enable Mythbuntu to work with this remote, do I have to use irexec, something else perhaps??? Your suggestions are well appreciated!!!

---

### Post by sirld on 2011-11-08
Hey,

I have Ubuntu 10.04 and have a similar problem with lirc. This is the output of my dmesg when I plug the USB receiver in:

```
Nov  8 10:02:47 alexander-laptop kernel: [ 7431.984090] usb 3-2: new low speed USB device using uhci_hcd and address 4
Nov  8 10:02:47 alexander-laptop kernel: [ 7432.163336] usb 3-2: configuration #1 chosen from 1 choice
Nov  8 10:02:47 alexander-laptop kernel: [ 7432.166200] lirc_dev: lirc_register_driver: sample_rate: 0
Nov  8 10:02:47 alexander-laptop kernel: [ 7432.186067] lirc_atiusb[4]: X10 Wireless Technology Inc USB Receiver on usb3:4
```

This is, when I execute ```
mode2 -d /dev/lirc0 -r
``` and press some buttons on the remote:

```
root@alexander-laptop:/dev# mode2 -d /dev/lirc0 -r
code: 0x144d780000
code: 0x144d780000
code: 0x14cef90000
code: 0x14c5f00000
code: 0x1447720000
code: 0x14c6f10000
code: 0x14c6f10000

```

When I execute irw (lircd running), it just exits without a word or it stays open without saying anything.

When I execute irrecord:

```
root@alexander-laptop:/dev# irrecord -d /dev/lirc0 -f -H atilibusb ~/lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: couldn't claim USB interface: Device or resource busy
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

How do I debug this? Does anybody know what might go wrong here? I know that the remote works, because it did on my old gentoo...

Thanks a lot in advance!

---

