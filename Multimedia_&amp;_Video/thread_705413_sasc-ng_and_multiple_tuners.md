---
title: "sasc-ng and multiple tuners"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by Vies1 on 2008-02-23
Hi everyone,

I have sasc-ng woking in my system partly. I have three tuners in my mythtv box, currently my problem is, that I can create only one virtual adapter using sasc-ng.

sasc-ng help states that I can ad as many -j arguments that I need to sasc-ng command. Problem is, that only 0:3, 1:3 or 2:3 works, because there is no adapter4 or adapter5 virtual devices and sasc-ng wont create them.

Is there something else I should do? Any way to create those additional devices. Or do I have to just dedicate one tuner for pay-tv channels.

---

### Post by rigolo on 2008-02-24
how did you load the dvbloopback kernel modole? did you just used insmod dvbloopback?

You can supply the num_adapter=n option when you load the dvbloopback adapter where n is the number of virtual dvb adapters you want to have (max = 8 - realadaptors due to the max 8 dvb device limit of linux)

I have setup the dvbloopback adapter to autoload in ubuntu as follows:

1) add the following line to /etc/modules

              [INDENT]dvbloopback[/INDENT]

2) create the following file

              [INDENT]sudo nano /etc/modprobe.d/dvbloopback[/INDENT]

with the following contents:

              [INDENT]options dvbloopback num_adapters=4 [/INDENT]

3) place your dvbloopback.ko in the right directory based on your kernel version in /lib/modules

reboot ... and good luck

---

