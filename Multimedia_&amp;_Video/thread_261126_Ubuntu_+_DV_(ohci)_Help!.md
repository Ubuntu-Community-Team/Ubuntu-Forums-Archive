---
title: "Ubuntu + DV (ohci) Help!"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by endura29 on 2006-09-19
Hello,
well after a few weeks of stubborness, I'm posting.

So I have a Panasonic GS-180 Camera which works well in Windows on my Dell Inspiron 5150. I've proven that firewire works/is loaded in module by plugging in both an ipod and external hard drive via the 1394 port.

First thing I tried was Kino. I'm given options for raw1394 and dv1394 drivers. I've tried all sorts of variations (and running it from root) but not getting anywhere as far as capture.

So I ran gscanbus which is amazingly slow when I plug in my camera, but quite fast with the external hard drive. I'm noticing is gscanbus says I'm using the OHCI1394 driver. This is confirmed by dmesg and my logs.

Then, I do a dmesg | grep 1394
```

<17179577.476000> ieee1394: Initialized config rom entry `ip1394'
<17179577.840000> ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
<17179577.888000> ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=<169> MMIO= Max Packet=<2048>
<17179579.160000> ieee1394: Host added: ID:BUS<0-00:1023> GUID<394fc0002d8420a1>
<17179597.608000> ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
<17179597.608000> ieee1394: sbp2: Try serialize_io=0 for better performance
<17179598.900000> ieee1394: raw1394: /dev/raw1394 device initialized
<17179598.924000> video1394: Installed video1394 module

```
So it points out that I *should* have Kino run using the dv1394 driver and using the following option: /dev/video1394-0/host0/PAL/in
But that gives me the dreaded error regarding read/write permissions to /dev/raw1394 or is it in the kernel. I assume it is because I can use the damned ipod. And as I've said, I run Kino as root and its the same thing.

I've also tried variations /dev/video1394-0 etc. and half the time it lets me try to capture but then says capture failed.

Running dvgrab gives the following:
```

root@caduceus:/dev# dvgrab
Error: no camera exists

```
Now, I've also found various other interesting messages by doing the whole:
tail /var/log/messages | grep 1394 which gives:
```

Sep 19 12:48:25 localhost kernel: <17197339.116000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:27 localhost kernel: <17197341.004000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:29 localhost kernel: <17197342.892000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:35 localhost kernel: <17197348.728000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:36 localhost kernel: <17197350.632000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:42 localhost kernel: <17197356.464000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:45 localhost kernel: <17197359.000000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:53 localhost kernel: <17197367.376000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:55 localhost kernel: <17197369.380000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Sep 19 12:48:56 localhost kernel: <17197370.196000> ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission

```
Now I've tried searching that one, etc. but quite honestly I'm a bit stumped up till here.

I do the same thing with the ipod and I get:
```

Sep 19 13:22:43 localhost kernel: <17199396.640000> ieee1394: sbp2: Logged into SBP-2 device

```
To be honest, I haven't done too much with hardware tweakings in Linux and am unsure as far as ctx-0 so I'd love a little bit of help.

Anyone have any ideas?

---

### Post by ddennedy on 2006-09-20
The bus resets are causing your problems when configuration is not. You need to sort it out. Most often, the problem is something hardware related including cable and camera. Maybe check the cable and camera on another computer.

As for configuration in Kino, you need to set the device file in preferences to /dev/dv1394-0 unless you have more than one /dev/dv1394-N file, in which case, you have to try them all in turn. (You get one of these device files per firewire, and multiple is not too uncommon on desktop systems). Then, run it with sudo to avoid any permissions issues while you are testing the configuration. First, see if you can enable the AV/C button in Capture and test VCR control before trying capture.

---

### Post by endura29 on 2006-09-21
ddennedy-
thanks for the advice. I'm unsure how it could be a hardware bug as the camera works fine if I am to boot into Windows on this same machine with same cable.

I'll try another and see if that differs at all and also will connect it to my desktop tomorrow morning (its 3am!), run the same tests and see what happens there.

---

### Post by endura29 on 2006-09-21
Bah!

So I noticed that my external hard drive didn't work with the cable I was using. Anyways I picked up a $30 belkin (will return after my newegg cables come) and the Camera/recording works awesome with Kino!

Guess the lesson is to keep extra firewire cables around hehe.

Thanks!

---

### Post by Sabot on 2006-09-24
I was trying to get my camcorder to work with Kino and I tried every type of module and so forth.  What I found out is I have to have an external Firewire HD attached to get Ubuntu to recognize my DV camcorder.

This is what I did to get my camcorder working.

1. Added raw1394 and dv1394 to modules file.
```
Sudo gedit /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
raw1394
dv1394

```
2. I then restarted my machine.

I had to make sure I had my camcorder off on restart.  If I did not, my external Firewire HD would not mount. 

This is the error that came up when I ran dmesg.

```
dmesg | grep 1394

[17181518.924000] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0

```

3. Turned on Firewire HD.
4. Turned on camcorder
5. Ran Kino
```
sudo kino
```

Kino would now find my camcorder and it would allow me to caputure video. 

This is really wierd, but it was the only way I could get Kino to find my camcorder.

---

### Post by ramadhian on 2007-07-14
This tips not work with me

I have JVC-D73AG here and i'm using Ubuntu 7.04

kenzo@ramadhian:~$ dmesg | grep 1394
[   33.710023] ieee1394: Initialized config rom entry `ip1394'
[   34.227586] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feafe000-feafe7ff]  Max Packet=[65536]  IR/IT contexts=[4/4]
[   34.234564] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[   35.501679] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[ffffffffffffffff]
[   50.575637] ieee1394: raw1394: /dev/raw1394 device initialized
[   50.599727] WARNING: The dv1394 driver is unsupported and will be removed from Linux soon. Use raw1394 instead.
[  402.046170] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[  402.046232] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 1240.318317] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1240.589901] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 1240.589952] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080880304f88088]

I have kino 1.0.0 compiled with "--with-dv1394" --enabled-quicktime --enable-local-ffmpeg

kenzo@ramadhian:~$ uname -mrs
Linux 2.6.20-16-generic i686

kenzo@ramadhian:~$ lsmod | grep 1394
dv1394                 20696  0 
raw1394                30328  0 
ohci1394               36528  1 dv1394
ieee1394              299448  4 dv1394,raw1394,sbp2,ohci1394

kenzo@ramadhian:~$ ls -lh /dev/raw1394 
crw-rw---- 1 root video 171, 0 2007-07-15 03:20 /dev/raw1394

kenzo@ramadhian:~$ ls -lh /dev/dv1394/0 
crw-rw---- 1 root root 171, 32 2007-07-15 03:20 /dev/dv1394/0

kenzo@ramadhian:~$ cat /etc/udev/rules.d/40-permissions.rules | grep 1394
SUBSYSTEMS=="ieee1394",                 GROUP="plugdev"
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
KERNEL=="raw1394",                 GROUP="video", MODE="0660"
KERNEL=="dv1394*",                 GROUP="video", MODE="0660"
KERNEL=="video1394*",              GROUP="video", MODE="0660"

kenzo@ramadhian:~$ groups
kenzo adm dialout fax cdrom floppy tape audio dip video plugdev scanner netdev lpadmin powerdev admin fuse avg vboxusers


AV/C Device show nothing

dv1394 device = /dev/dv1394-0

I've ones success to capture DV right after I install Ubuntu 7.04 at the first time.

I think its begin not working after I upgrade my kernel version to Linux 2.6.20-16-generic i686

Any solution for this ???

---

