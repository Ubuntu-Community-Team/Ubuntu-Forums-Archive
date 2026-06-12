---
title: "Skype disables webcam until reboot (used to work)"
date: 2011-12-25
forum: Multimedia Software
---

### Post by Paddy Landau on 2011-12-25
The last time I tested my webcam on both Cheese and Skype was a few weeks ago, and it worked perfectly.

However, now I've found that Skype disables the webcam.

[LIST]
[*]If I start Cheese, the little blue light comes on and the webcam works.
[*]However, if I start Skype, the little blue light remains unlit and I get a black screen. Thereafter, the webcam won't work even if I close Skype and start Cheese, until I reboot.
[/LIST]
More information:

[LIST]
[*]I have tried all of:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
XLIB_SKIP_ARGB_VISUALS=1 skype
```
[*]I am using Natty 11.04 64-bit, fully updated.
[*]Both Cheese and Skype report the device as CNFA257 (/dev/video0). The webcam is built into the computer.
[*]```
[COLOR=Navy]*lsmod | grep -F videodev*[/COLOR]
videodev               82052  2 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
```
[*]```
[COLOR=Navy]*lsusb*[/COLOR]
Bus 002 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0408:3003 Quanta Computer, Inc. 
Bus 001 Device 003: ID 04f2:b28b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
[/LIST]
Please help me get the webcam working on Skype again!

---

### Post by Paddy Landau on 2011-12-26
Bump!

---

### Post by mastablasta on 2011-12-31
64 bit.... seems to have soem issues. 

Can this be of any help?: [http://blogs.skype.com/garage/linux/](http://blogs.skype.com/garage/linux/)

i am looking at this one: > Video  Your video capture might show seldomly green, scrambled or black image.  Please install one additional package which might solve your problem: 
 - Ubuntu 32 bit: install ""libv4l-0"" package and launch Skype with: LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype 
 - Ubuntu 64 bit: install ""lib32v4l-0"" package and launch Skype with: LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype 
 - Other distributions might have the same library, but may have a different path.

also any error messages thrown out when you launch it from terminal? if so might be worth posting them here and on Skype forums.

---

### Post by Paddy Landau on 2011-12-31
@mastablasta: Thanks for the link. Unfortunately, it makes no difference.

Running in the terminal, I get the following results.

[LIST]
[*][FONT=Courier New][SIZE=2]skype[/SIZE][/FONT]
```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: Loading IM context type 'ibus' failed
```
[/LIST]

[LIST]
[*][FONT=Courier New][SIZE=2]LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype[/SIZE][/FONT]
```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2420): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2420): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2420): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2420): Gtk-WARNING **: Loading IM context type 'ibus' failed
libv4l2: error turning on stream: Input/output error
```
[/LIST]
 The only significant difference is the very last message, and I have no clue how to diagnose or solve any of these.

---

### Post by mastablasta on 2012-01-01
ok i am no expert here, but it seems like it is trying to load a GTK library (it seems one of the older GTK libraries if i understand this correctly) and it is not there or it can't load it.

it seems skype is not the only programm with this issue. :
[http://askubuntu.com/questions/41920/why-i-am-getting-a-segmentation-fault-opening-guitar-pro](http://askubuntu.com/questions/41920/why-i-am-getting-a-segmentation-fault-opening-guitar-pro)

perhaps the answers in the above link could be applied to Skype?

otherwise this appears to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/788625](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/788625)

ok and here seems to be the solution:
> Had exactly the same issue. Removing the ~/.Skype folder helped for me. Skype works again.:-)

A less drastic solution:

[http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html](http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html)

> **Linux**

 
[LIST=1]     
[*]Go to the following folder:     /home/YourLinuxUserName/.Skype
     
[*]Delete the file **shared.xml**.     
[*]Restart Skype.
[/LIST]
 The Skype folder is a hidden folder - please check **Show hidden files** in your file browser to view and access it.


---

### Post by Paddy Landau on 2012-01-01
Thank you for the links. After some trial-and-error, I found this to work:


[LIST=1]
[*]Delete *both* shared.lck and shared.xml in ~/.Skype.
[*]Reboot.
[*]Then it works. But, the video is very dark, which is solved by starting and closing Cheese. :confused:
[*]But it works only as long as Skype does not close and restart, so to use it again (say, the next day), I have to repeat from step 1. :???:
[/LIST]

I don't use video at all often, so this odd workaround will have to do for now.

I have added my vote to the bugs.

I'll mark the thread as solved, as it seems to be a recognised bug. Thank you again.

---

### Post by beardfarmer on 2012-06-04
Thanks for directing me to this. I will try it tonight when I need it. Thank you so much dude! My GF will be so happy if this works. Thanks again brotha!

---

### Post by Paddy Landau on 2012-06-05
> **beardfarmer said:**
> I will try it tonight...
If it does work, please go [add your vote to the bug]("https://bugs.launchpad.net/ubuntu/+source/skype/+bug/788625") (the green writing on the top-left of the page).

---

### Post by Paddy Landau on 2012-06-19
Well well well.

I had completely given up on Skype as a bad joke.

But today, in the [Ubuntu Weekly Newsletter]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/"), I discovered that Skype has released [version 4 for Linux]("http://blogs.skype.com/linux/2012/06/skype_40_for_linux.html"). Yes, version 4!

And I am pleased to report that, for me at least, this version works. No more webcam nonsense!

---

