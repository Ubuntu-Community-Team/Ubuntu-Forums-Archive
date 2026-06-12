---
title: "How to get Dvico FusuionHDTV Dual Express DVB-T card to work"
date: 2009-08-30
forum: Multimedia Software
---

### Post by Stolea on 2009-08-30
I am trying to get met brand new Dvico FusionHDTV Dual Express DVB-T Pcie card installed / working in Jaunty 9.04. (For use in Australia)
After spending the better part of  today trying to make some sense as to what I must install and what to do, and am now really no wiser than when I started.
My questions are:
1) Do I need to install firmware or not?
2) Do I need to install drivers or not?
3) What software is needed.

There seems to be so much contradictory information and very little accurate advice relating to current hardware and the current release. A lot of the info relates to earlier versions.

dmsg tells me that it has the card installed.

Where can I read up what relates to my setup, or what do I have to do?
Help!!!!

---

### Post by Stolea on 2009-08-30
Anyone, please. I can't be alone with this problem. :)

---

### Post by Stolea on 2009-09-06
I am still not getting anywhere with this card. According to [http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express]("http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express") it should by rights work.
When I go > dmsg
I get the following:
>   15.636387] cx23885 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.636569] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   16.195796] intel_rng: Firmware space is locked read-only. If you can't or
[   16.195797] intel_rng: don't want to disable this in firmware setup, and if
[   16.195798] intel_rng: you are certain that your system has a functional
[   16.195798] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   16.290826] input:  as /devices/virtual/input/input7
[   16.296047] ir-kbd-i2c:  detected at i2c-0/0-006b/ir0 [cx23885[0]]
[   16.304281] iTCO_vendor_support: vendor-support=0
[   16.305565] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   16.305669] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   16.305719] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.305772] cx23885_dvb_register() allocating 1 frontend(s)
[   16.305775] cx23885[0]: cx23885 based dvb card
[   16.426357] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.426418] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.439588] xc2028 0-0061: creating new instance
[   16.439589] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   16.439592] DVB: registering new adapter (cx23885[0])
[   16.439595] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   16.439754] cx23885_dvb_register() allocating 1 frontend(s)
[   16.439756] cx23885[0]: cx23885 based dvb card
[   16.440318] xc2028 1-0061: creating new instance
[   16.440319] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   16.440321] DVB: registering new adapter (cx23885[0])
[   16.440322] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   16.440472] cx23885_dev_checkrevision() Hardware revision = 0xa5
[   16.440478] cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xff400000
[   16.440483] cx23885 0000:04:00.0: setting latency timer to 64

I have installed me-tv but for some reason it thinks its a Zarlink ZL10353 DVB-T. It gives me the right locations for Melbourne Australia to scan, but cannot find anything.
Any help would be more than welcome as I am just about to resign myself to sticking with WinXp as my main OS. I really like Ubuntu and have been chisseling away at it for 2 years now, but some things are just too hard to do.

---

### Post by mrflashpants on 2009-10-18
I got the following from this link:

[http://ubuntuforums.org/showthread.php?t=616103&highlight=dvico+dual](http://ubuntuforums.org/showthread.php?t=616103&highlight=dvico+dual)

Please bear in mind that I set it up on Ubuntu 8.04 for compatibility reasons that are unrelated to this card.  Please read the above mentioned post b/c there are updates regarding alternate versions of the card

HOWTO: DViCO FusionHDTV DVB-T Dual

Driver Installation
(Make sure v4l and Dvb are NOT installed!)

# apt-get install mercurial build-essential linux-headers-`uname -r`

# sudo apt-get install unzip

# sudo apt-get install dvb-utils

# mkdir firmware

# cd firmware/

# wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)

# unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

# cp /usr/src/linux/Documentation/video4linux/extract_xc3028.pl

# ./extract_xc3028.pl

/* Don't copy the firmware just yet.... */

# cd ..

# hg clone [http://linuxtv.org/hg/~stoth/v4l-dvb/](http://linuxtv.org/hg/~stoth/v4l-dvb/)

# cd v4l-dvb

# sudo make && make install

# sudo cp firmware/xc3028-v27.fw /lib/firmware

# sudo reboot

...

# dmesg | grep cx23885

# ls /dev/dvb

then shut down the pc let it sit for 30 secs the boot back up.






Quick test

# apt-get install dvb-utils

# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-sydney_north_shore > channels.conf

# sudo cp channels.conf /etc && cp channels.conf ~/.tzap

# tzap -c /etc/channels.conf -r "ABC2"

leave open and from a new terminal window as a normal user type

# mplayer /dev/dvb/adapter0/dvr0

the above example assumes your in sydney you can find your conf file for your town or city in /usr/share/doc/dvb-utils/examples/scan/dvb-t

now su back to normal user by typing "exit" or "su - user"






Remote installation

type

# dmesg | grep IR

you should see somthing like this

input: IR-receiver inside an USB DVB receiver as /class/input/input6

now open /etc/udev/rules.d/60-symlinks.rules

# gksudo gedit /etc/udev/rules.d/60-symlinks.rules

or kubuntu

kdesu kate /etc/udev/rules.d/60-symlinks.rules

and add this line at the bottom

# Create /dev/input/irremote for Dvico Fusion remote
KERNEL=="event*",SYSFS{name}=="i2c IR (FusionHDTV)",SYMLINK="input/irremote" 

reboot so /dev/input/irremote is made

after reboot in terminal type

# sudo dpkg-reconfigure lirc

scroll down to linux input layer then select it

on page 2 for IR transmitter select none

on page 3 select /dev/input/irremote

download attached lirc1.tar.bz2 if you remote look like this

and download lirc2.tar.bz2 if you remote looks like this

replace lircx with lirc1 or lirc2 in terminal type

# tar xvjf lirc2.tar.bz2

# cd lirc2

# sudo cp -R lirc /etc

# mv /etc/lirc/lircrc ~/.mythtv

# ln -s ~/.mythtv/lircrc ~/.lircrc

# sudo ln -s ~/.mythtv/lircrc /etc

# sudo ln -s ~/.mythtv/lircrc /etc/lirc

now restart lircd

# sudo /etc/init.d/lirc restart

test

# irw

press keys on remote

Good luck as I have nothing else to offer :)

and Please thank oobe-feisty!

---

### Post by Stolea on 2009-10-19
> Driver Installation
(Make sure v4l and Dvb are NOT installed!)

Silly Question of the day:
How do I find that out, and if they are installed, how do I get rid of them??

---

### Post by mrflashpants on 2009-10-19
Personally, I did a search for those in Synaptic package manager, but if you manually compiled and installed either of those apps they won't show up in synaptic.  I'm sure you would know if you did or not :)

---

