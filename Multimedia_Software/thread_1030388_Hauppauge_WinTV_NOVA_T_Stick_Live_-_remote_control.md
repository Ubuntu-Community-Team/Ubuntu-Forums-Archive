---
title: "Hauppauge WinTV NOVA T Stick Live - remote control"
date: 2009-01-04
forum: Multimedia Software
---

### Post by hitesh on 2009-01-04
Hi,

First the good news, I bought Hauppauge WinTV NOVA T Stick Live, Model 353 and it worked immediately and I am able to watch TV using gxine and totem.

Now the bad :(, After searching high and low and spending the whole day on trying to get the remote to work, I have given up.
The remote is a 35 key remote with Model no. DSR 0112.

What I have tried:
mythbuntu-control-centre
gnome-lirc-properties
and direct edits of the hardware.conf and lircd.conf

I have tried several config files found on the net for Hauppauge but none work.

First the output from cat /proc/bus/input/devices

```

I: Bus=0003 Vendor=2040 Product=7070 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:02.1-6/ir0
S: Sysfs=/devices/pci0000:00/0000:00:02.1/usb1/1-6/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd

```

i am on ubuntu 8.10, output of uname -a 
```

Linux dextop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```

lircd starts up and when I run irw it connects OK, but never registers any button press.

In the syslog I see 1 or 2 lines like below every time I press a button.

```
Jan  4 17:22:44 dextop kernel: [ 1543.552409] dib0700: Unknown remote controller key: 1D 1C  1  0
Jan  4 17:22:44 dextop kernel: [ 1543.856386] dib0700: Unknown remote controller key: 1D 1F  0  0
```

This makes me believe I have a wrong lirc.conf file, so I tries to generate one from scratch using irrecord, it it fails too with this error

```

sudo irrecord -H dev/input  -d /dev/input/event7 ./lircd.conf 
irrecord -  application for recording IR-codes for usage with lirc
-snip-
Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event7'

```

Although I press and hold a button and can see it triggering a syslog entry irrecord catches nothing.

doing evtest also yield no result 
```

sudo evtest /dev/input/event7
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x2040 product 0x7070 version 0x100
Input device name: "IR-receiver inside an USB DVB receiver"
...

```
and then when I press buttons nothing happens, except for the entry in syslog.

Totally clueless on what to do next, please help, Thanks.

---

### Post by hitesh on 2009-01-06
bump up.. somebody please help

---

### Post by acid68 on 2010-02-01
Hi there !
Still got an issue ? 
I saw your post and used it to get to the same point regarding the gap detection. 

I found that if you keep holding down a button ( any ) it completes the gap setting and then you can create your file. 

I'm still working on mine ( just started this evening, its making my head hurt already ), got the map file generated, just going to test it in a mo.

How have you got on with yours ?

---

### Post by acid68 on 2010-02-02
In case anyones interested.

I have a Hauppauge Nova-T Stick USB DVB-T ( thats a single tuner device, half a NOVA-T 500 ? ) and I do now have a working Lirc setup with double key press corrections added.

Here are the three config files. hardware.conf lircd.conf and lircrc from my setup.

The was tested on a mythbuntu rig 2.6.31-16 upgraded to 2.6.31-17 kernel with v 1.20 firmware loaded for the usb tv device

I had to add the .txt extension to upload, so remove this before use.

[ATTACH]145782[/ATTACH]

[ATTACH]145783[/ATTACH]

[ATTACH]145784[/ATTACH]

---

### Post by ice cold on 2010-05-25
Hi acid68, I've got a nova-t stick but apparently it can come with one of two remotes, a small, thin credit card sized one or a full media centre one.  Mine is the former, is this the one you have too?

---

