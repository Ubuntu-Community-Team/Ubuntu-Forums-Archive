---
title: "Bluetooth audio earpiece not wkg"
date: 2008-08-21
forum: Multimedia Software
---

### Post by digimark on 2008-08-21
Hi All....

OK I've seem to have tried everything to no avail here. Bluetooth seems partiularly painful.

OK so I have loaded all the alsa stuff, tried the bluez apps even tried command line. Audio hardware is as follows:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

the Bluetooth app is running and can see my earpiece from the gui. but NOT from the command line. Skype can see the device but just tells me that theres a problem withthe sound output! Skype works fine with the inbuilt speakers and mike.......

i have tried to restart alsa and force a reload (which killed all sound!)

alsa conf doesnt work although I think I have alsa-utils have tried to load it via sudo apt-get install alsa-utils but it tells me its installed.....

tried btsco to no avail also......

It seems to me that the apps can see the bluetooth devices but the OS cannot?

HCITOOL scan sees the bluetooth dongle (Dlink) but NOT the earpiece?!

hcitool dev
Devices:
	hci0	00:19:5B:10:C9:9C


also

sudo hidd --connect 00:0D:3C:62:BD:AC
Can't get device information: Success

nothing but the bluetooth preferences app shows the earpiece as connected!!

However 

 hcitool con
Connections:
	> ACL 00:0D:3C:62:BD:AC handle 11 state 1 lm MASTER AUTH ENCRYPT SECURE

it IS there!!!! ARGH!!!!

I am at a loss as to what to try next!

Any help much appreciated!

/Mark

---

### Post by rpcutts on 2008-08-21
It would appear I have this exact problem.
It's driving me mad. Not to mention the £30 I've wasted on hardware.

---

