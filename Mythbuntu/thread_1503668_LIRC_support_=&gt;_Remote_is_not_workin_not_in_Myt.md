---
title: "LIRC support =&gt; Remote is not workin not in Mythtv..."
date: 2010-06-07
forum: Mythbuntu
---

### Post by seppl82 on 2010-06-07
Hi all,

i've installed Mythbuntu V10.4 (Final Release).
After booting i can use the Remote Control after i've quit Mythtv to control the cursor and all those funny stuff.
But inside Mythtv
 - the IR Controller does nothing
 - the Display is showing nothing

Any ideas how to go deeper in debugging

---

### Post by larsolav on 2010-06-07
Which remote control are you using? Did you set it up in Myth Control Centre?

---

### Post by seppl82 on 2010-06-07
I'm using 

Bus 005 Device 002: ID 15c2:0038 SoundGraph Inc. 

Together wit a Logitech Harmony 555 which is programmed as "IMON_MultiMedian"
Yes, i've set it up as SoundGraph IMON IR/LCD

THX

---

### Post by larsolav on 2010-06-07
That is more complicated than I can help with...
Have you looked at the thread below, maybe that discussion is relevant?

[http://swiss.ubuntuforums.org/showthread.php?t=1391881](http://swiss.ubuntuforums.org/showthread.php?t=1391881)

---

### Post by seppl82 on 2010-06-07
I think the problem is that usbhid grabs the device.
Therefore it can not talk to lirc.

take a look here

```

[   10.263830] lirc_imon: iMON device (15c2:0038, intf0) on usb<5:2> initialized
[   10.265361] lirc_imon: iMON device (15c2:0038, intf1) on usb<5:2> initialized
[   10.265385] usbcore: registered new interface driver lirc_imon

```

I've created that file
```

frsc@frsc-desktop:/etc/modprobe.d$ cat usbhid.conf 
options usbhid quirks=0x15c2:0x0038:0x4

```

followed by
```

frsc@frsc-desktop:/etc/modprobe.d$ sudo rmmod usbhid 
frsc@frsc-desktop:/etc/modprobe.d$ sudo modprobe usbhid 
frsc@frsc-desktop:/etc/modprobe.d$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic

```

But, after the boot same behavior....
```

[   10.265385] usbcore: registered new interface driver lirc_imon

```

Any ideas what i did wrong?

---

### Post by seppl82 on 2010-06-08
Hi larsolav,

the Article you've sent me describes how to get the Display working.
But the Display is not the issue. The issue is the Infrared Reciever.

Kind Regards
Seppl

---

### Post by phroman on 2010-06-08
For clarification, how do you use your remote control outside of mythtv? Did you use some software that came with the remote?  

Did you run mythbackend, and enable a remote control there? If you did, you will probably need to tweak some of the files that were created to get your remote working when you're using mythtv.

---

### Post by seppl82 on 2010-06-08
Okay,
i've did not install any other software than Mythbuntu.
After i quit my Remote control acts like a mouse pointing device.

Nothing else.
irw does not show any signal

---

### Post by azmyth on 2010-06-08
What do you have in your /etc/lirc/hardware.conf file? Please post.

---

### Post by seppl82 on 2010-06-09
Hi,

after recommendation of jarod wilson (developer of the lirc plugin for imon)  iv'e added these files to my /etc/lirc directory (the hardware.conf file is named in this folder lirc.sysconfig)

[http://wilsonet.com/jarod/imon_stuff/imon-devinput-lirc/](http://wilsonet.com/jarod/imon_stuff/imon-devinput-lirc/)

---

### Post by seppl82 on 2010-06-17
This solved the issue [http://ubuntuforums.org/showthread.php?t=1506214](http://ubuntuforums.org/showthread.php?t=1506214)

---

