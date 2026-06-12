---
title: "HP UN2420 GOBI 3G Modem"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by andrewtayloruk on 2009-12-23
Hi,

I've got a HP Mini 311c 1030SA with a UK 'three-mobile' SIM in it, I'm trying to get it working under Linux using Ubuntu 9.10 (although I've tried with Slackware as well) , but I'm not having much luck.

I've read all the posts about the GOBI_LOADER but even though I've patched my qcserial with the updated device number (From lsusb: Bus 001 Device 002: ID 03f0:241d Hewlett-Packard ) the ttyUSB0 fails to be created. Obviously I need to load the firmware to the device before it can be used as a modem, but, until I get that serial-port available to the gobi_loader app, I can't do this.

I'm running the latest ubuntu kernel which from memory is 2.6.31.16, and I followed these instructions, [http://www.madox.net/blog/projects/hp-p ... reference/]("http://www.madox.net/blog/projects/hp-probook-5310m-ubuntu-reference/") which are the only ones I could find that match my hardware device ID.

I'm loving everything about the device, but, the inbuilt 3G is a must for me, I don't have long before I can return the device for a refund, so, if anyone can help me out, I'd really appreciate it.

Thanks

Andrew

---

### Post by rash.m2k on 2010-01-03
Hi,

I've also just got a brand new HP 311c, so far i've got the nvidia drivers working, set the corrent DPI got the wireless drivers working.

(Download and install broadcom-wl rpm to activate wirless)

I'm running openSUSE 11.2 kernel 2.6.31.5-0.1-desktop, here is what you are looking for:

[http://www.madox.net/blog/projects/hp-probook-5310m-ubuntu-reference/](http://www.madox.net/blog/projects/hp-probook-5310m-ubuntu-reference/)

And this here:

[http://ubuntuforums.org/showthread.php?t=1008200&page=2](http://ubuntuforums.org/showthread.php?t=1008200&page=2)

You need to recompile the kernel - I'm no expert so i'm unsure what the ramifications of compiling the kernel will be. Any help would be greatly appreciated.

---

