---
title: "Mythbuntu and LIRC"
date: 2014-04-13
forum: Mythbuntu
---

### Post by NikosF on 2014-04-13
I'm running into a problem, where in the past I had none.

I've been using Microsoft MCE remotes for a few years now (initially on Fedora and for the past few years on Ubuntu).

One of my (ION-based) frontends recently died and I built a new frontend with a Gigabyte MB and an i3 CPU. Previously LIRC worked flawlessly, and now with the new build it doesn't work at all. I'm using Mythbuntu 12.04 LTS - and used MCC to set up LIRC as I had in the past.  I'm getting the identical (similar) problem on another frontend that is a Zotac Zbox (but another Zbox has no issues with the same remote).

It doesn't respond at all to remote button pushes.

When I run irw - I get no response at all on the screen.

mode2 doesn't work - I get 
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

/dev/lirc0 is established just fine.

lsusb gives: Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 17ef:6014 Lenovo Mini Wireless Keyboard N5901
Bus 003 Device 003: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

uname -a:
Linux basement 3.8.0-38-generic #56~precise1-Ubuntu SMP Thu Mar 13 16:22:48 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

From dmesg:
[ 2.409863] IR LIRC bridge handler initialized
nikos@basement:/dev$ dmesg | grep mceusb
[ 2.399240] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input5
[ 2.409860] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[ 2.527745] mceusb 3-3:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[ 2.527748] mceusb 3-3:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
[ 2.527773] usbcore: registered new interface driver mceusb

Everything seems to be initializing just fine - just not responding.

Any hints on what to do next?

Thanks!
Nikos

---

### Post by khPWXxF on 2014-04-18
I see from the notes taken at the time that I had a problem like yours with 9.04, though with a Hauppauge remote.  It did not work because I was not prompted to say which 'event' it was using during installation.
 
Find out the ‘event’ being used with cat /proc/bus/input/devices.
 
In Mythbuntu control panel, selecting the device did not prompt for the ‘event’
I had the select it, then remove it, then re-install it.  It then asked to identify event.
 
Could this be your problem?
Phil

---

### Post by Dave_Alverson on 2014-04-18
Whats the output from ir-keytable.  Also, stop lirc and run "ir-keytable -t" and see if you get anything from pressing buttons on the remote. Whats in your hardware.conf, especially REMOTE_DRIVER, REMOTE_DEVICE and LOAD_MODULES.

---

