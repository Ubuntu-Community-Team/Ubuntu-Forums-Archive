---
title: "Hauppauge Nova-T Stick + Lirc"
date: 2011-08-22
forum: Multimedia Software
---

### Post by welshboy11 on 2011-08-22
Hi.  I've recently install Ubuntu 11.04 onto my HTPC/Server for use with  xbmc and tvheadend. Everything is set up how I wish and works perfectly.


My  only problem is that I have a Hauppauge Nova-t Stick (dvb-t tuner for  freeview in the UK) and it doesn't get picked up by lirc, irw, evtest or  irrecord...


When i run cat /proc/bus/input/devices Here is my output.

> 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=2040 Product=7070 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:03.3-3/ir0
S: Sysfs=/devices/pci0000:00/0000:00:03.3/usb1/1-3/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=100013
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffc
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA SIS966 Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:0f.0/sound/card1/input5
U: Uniq=
H: Handlers=event5 
B: PROP=0
B: EV=21
B: SW=4
This clearly show that the ir receiver is working and that it is detected.

When i run sudo evtest /dev/input/event4
Here is what I get
> 
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x2040 product 0x7070 version 0x100
Input device name: "IR-receiver inside an USB DVB receiver"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 2 (1)
    Event code 3 (2)
    Event code 4 (3)
    Event code 5 (4)
    Event code 6 (5)
    Event code 7 (6)
    Event code 8 (7)
    Event code 9 (8)
    Event code 10 (9)
    Event code 11 (0)
    Event code 41 (Grave)
    Event code 52 (Dot)
    Event code 55 (KPAsterisk)
    Event code 102 (Home)
    Event code 103 (Up)
    Event code 105 (Left)
    Event code 106 (Right)
    Event code 108 (Down)
    Event code 111 (Delete)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 119 (Pause)
    Event code 128 (Stop)
    Event code 139 (Menu)
    Event code 158 (Back)
    Event code 164 (PlayPause)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 173 (Refresh)
    Event code 207 (Play)
    Event code 208 (Fast Forward)
    Event code 210 (Print)
    Event code 223 (Cancel)
    Event code 226 (Media)
    Event code 352 (Ok)
    Event code 354 (Goto)
    Event code 355 (Clear)
    Event code 358 (Info)
    Event code 363 (Channel)
    Event code 365 (EPG)
    Event code 370 (Subtitle)
    Event code 375 (Screen)
    Event code 377 (TV)
    Event code 385 (Radio)
    Event code 386 (Tuner)
    Event code 388 (Text)
    Event code 389 (DVD)
    Event code 392 (Audio)
    Event code 393 (Video)
    Event code 398 (Red)
    Event code 399 (Green)
    Event code 400 (Yellow)
    Event code 401 (Blue)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 405 (Last)
    Event code 407 (Next)
    Event code 410 (Shuffle)
    Event code 412 (Previous)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)
 But I receive no feedback when pressing any buttons.

sudo irrecord REMOTE_NAME
Gives me this
> 
irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: initializing '/dev/input/event0'
This program will record the signals from your remote control
and create a config file for lircd.


Usually it's not necessary to create a new config file for devinput
devices. A generic config file can be found at:
[http://www.lirc.org/remotes/devinput/](http://www.lirc.org/remotes/devinput/)
You should try this config file before creating your own config file.

A proper config file for lircd is maybe the most vital part of this
package, so you should invest some time to create a working config
file. Although I put a good deal of effort in this program it is often
not possible to automatically recognize all features of a remote
control. Often short-comings of the receiver hardware make it nearly
impossible. If you have problems to create a config file READ THE
DOCUMENTATION of this package, especially section "Adding new remote
controls" for how to get help.

If there already is a remote control of the same brand available at
[http://www.lirc.org/remotes/](http://www.lirc.org/remotes/) you might also want to try using such a
remote as a template. The config files already contain all
parameters of the protocol used by remotes of a certain brand and
knowing these parameters makes the job of this program much
easier. There are also template files for the most common protocols
available in the remotes/generic/ directory of the source
distribution of this package. You can use a template files by
providing the path of the file as command line parameter.

Please send the finished config files to <lirc@bartelmus.de> so that I
can make them available to others. Don't forget to put all information
that you can get about the remote control in the header of the file.

Press RETURN to continue.


Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event0'
 None of these show up any trace of activity. I have tried installing lirc through apt0get install lirc and also downloading the archive from lirc.org and compiling it and installing it myself. I have downloaded numerous files which are meant to be for my receiver, such as hardware.conf lircd.conf.

I have attached both files below.

Any help would be appreciated as I don't want to control my HTPC via keyboard which is 20 feet away from my sofa!

Thanks

---

### Post by welshboy11 on 2011-08-29
Come on? Anyone please? I still haven't figure this one out! I've even tried getting Eventghost to run because the receiver worked fine with that under windows on the same machine.

---

### Post by BicyclerBoy on 2011-08-29
Quote from MythTV site..could be out-of-date.

As of 2.6.36, some infrared receiver drivers have been removed from  LIRC and into the kernel.  The following drivers are no longer available  in lirc: 
 
[LIST]
[*] mceusb
[*] streamzap
[*] it8x
[*] ene0100
[/LIST]
 Other LIRC drivers have been moved to staging. For example, the lirc_i2c driver is in this part of the kernel now. 

EOQ.

So lirc may not be needed & actually be the case of the problem..

There is a third party projects/mythbuntu section here on Ubuntu Forums..

---

### Post by welshboy11 on 2011-08-29
Thanks for the reply but I fixed this problem earlier.

Here's what I did for anyone who has the same problem...

1. Opened synaptic package managed searched for LIRC fully removed anything that was installed. 

2. Opened the Extra drivers installer and installed the tuner driver that was reccomended.

3. Rebooted the pc and then run evtest /cat/... etc... and I was finally having input!

4. Re-installed LIRC tried the irw command and my remote was working fine.

Then I just went on to configure it to work with XBMC and now everything is right in the world again:p

---

### Post by BicyclerBoy on 2011-08-30
Sounds like you did not have the non-free firmware package.

running this from terminal
dmesg
and searching for messages about the device would have revealed this..

---

### Post by welshboy11 on 2011-08-30
every time i ran dmesg it showed that the device had been initialized correctly and everything was working fine...

---

