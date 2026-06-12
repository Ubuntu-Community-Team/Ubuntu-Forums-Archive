---
title: "Telstra Mobile Broadband - Turbo Stick not working"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by aufty on 2011-04-07
I have an acer 532h aspire one, running ubuntu 10.04 (EasyPeasy).

I've read countless threads about this and I've done loads of "fixes". The most frustrating part is, I found a workaround, but it only worked for two uses. Basically, I bought a Telstra Turbo USB broadband stick and I've been having a bit of hell getting it to work. First I couldn't get the computer to recognize it had been plugged in at all. I downloaded the modeswitch packages to no avail. I tried a few other terminal tweaks but they didn't change anything either. I left the card in and restarted the netbook and it finally recognized the wireless card. I was able to surf the internet for an hour or so a couple times. But after stowing the computer away for a couple hours and turning it on again, I found that this work around was no longer effective. So now I'm back to the blue light never blinking and I have to tether my phone and pay ridiculous data charges because I'm in the middle of nowhere.

Sorry I'm really new at troubleshooting things that don't work right out of the box. Does anyone have any ideas/suggestions?

It's a telstra turbo prepaid wireless broadband. The stick isn't even recognized as removable media, if that helps.

lsusb returns this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 04e8:6810 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 012: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA[/COLOR]
Bus 001 Device 003: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Also this might be relevant:
aufty@aufty-laptop:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[  378.748551] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[  420.122744] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[ 2461.667408] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[ 2713.394826] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[ 3300.861452] cdc_acm 3-1:1.0: ttyACM0: USB ACM device

---

### Post by aufty on 2011-04-07
Someone with a problem almost identical to mine used sakis3g script and had success, but it didn't work for me. Says "Failed to connect", although the "switch" part appears to be working.

---

### Post by aufty on 2011-04-07
I uninstalled usb-modeswitch and the stick appears to be working on boot again. Testing plug and play... Nope.

If the modem is plugged in on boot it will connect once. If it's unplugged or disconnected, the modem can be seen by the manager but it won't connect. Either way I'm just happy it works at all. If anyone knows how to fix the reconnecting issue let me know!

---

