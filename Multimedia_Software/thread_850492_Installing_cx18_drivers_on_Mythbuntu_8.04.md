---
title: "Installing cx18 drivers on Mythbuntu 8.04"
date: 2008-07-05
forum: Multimedia Software
---

### Post by Dashman403 on 2008-07-05
I am having trouble installing the cx18 drivers on mythbuntu 8.04.  i have a Hauppauge HVR-1600 and want to record tv on my computer.  I do not know any terminal commands and very little with mythbuntu.  PLEASE HELP ME!

---

### Post by bawilson2 on 2008-08-25
This does require terminal commands but is pretty much copy and paste.  Ask any questions.  I got it working without any problems.

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

---

### Post by dennis.ayala on 2008-10-29
> **bawilson2 said:**
> This does require terminal commands but is pretty much copy and paste.  Ask any questions.  I got it working without any problems.

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

I'm following this same instructions but Im getting some errors when I do the **sudo make unload ** command. 

These are the errors:

scripts/rmmod.pl unload
found 264 modules
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod compat_ioctl32
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x,videodev
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by ivtv,videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x,videodev
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by ivtv,videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
Couldn't unload: tveeprom v4l1_compat v4l2_common videodev cx2341x ivtv


Any help will be appreciated since I'm new to all this.

Regards,

Dennis.

---

### Post by bawilson2 on 2008-10-30
I haven't seen that problem before but it looks like something is trying to use the tuner you already have installed.  Do you have a PVR-150 already in use?  

Just a guess but maybe if there are other things running in the background you might try shutting them down.  Stop all mythbackend processes and give it a try again.

---

### Post by redboy33 on 2009-01-13
I'm getting the same exact errors.  I'm a complete NEWBIE to the UBUNTU world.  I'm following the directions posted here:

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

here's a screenshot of the errors I'm getting.

NEWBIE@MythtvBE:~/v4l-dvb$ sudo make unload
make -C /home/NEWBIE/v4l-dvb/v4l unload
make[1]: Entering directory `/home/NEWBIE/v4l-dvb/v4l'
scripts/rmmod.pl unload
found 294 modules
/sbin/rmmod compat_ioctl32
ERROR: Module compat_ioctl32 is in use by ivtv
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
/sbin/rmmod compat_ioctl32
ERROR: Module compat_ioctl32 is in use by ivtv
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
Couldn't unload: tveeprom v4l1_compat videodev v4l2_common cx2341x ivtv compat_ioctl32
make[1]: Leaving directory `/home/NEWBIE/v4l-dvb/v4l'
NEWBIE@MythtvBE:~/v4l-dvb$ 

How can I free up all those modules so they can be "unloaded?"

Please, is there anyone out there that has had this problem?  and fixed it?

Thanks

---

### Post by Thought_Criminal on 2009-03-10
I was having the same exact issue with the Hauppauge 1600 and an nvidia 6600GT.

My video card has 2 DVI outs, I switched which one I was using and it installed smooth as butter. Hope that helps you if you are still struggling with this.


> **dennis.ayala said:**
> I'm following this same instructions but Im getting some errors when I do the **sudo make unload ** command. 

These are the errors:

scripts/rmmod.pl unload
found 264 modules
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod compat_ioctl32
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x,videodev
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by ivtv,videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
/sbin/rmmod ivtv
ERROR: Module ivtv is in use by lirc_pvr150
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by ivtv
/sbin/rmmod videodev
ERROR: Module videodev is in use by ivtv
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by ivtv,cx2341x,videodev
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by ivtv,videodev
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by ivtv
Couldn't unload: tveeprom v4l1_compat v4l2_common videodev cx2341x ivtv


Any help will be appreciated since I'm new to all this.

Regards,

Dennis.

---

### Post by Weidbrewer on 2009-04-08
I don't know if anyone is still following this thread, but I'm having a slightly different problem.  I followed the instructions from the mythtv wiki mentioned above, and everything seemed to go well until the last step:

```
weidbrewer@********:~$ dmesg | grep cx18
[   27.320646] cx18:  Start initialization, version 1.1.0
[   28.422856] cx18-0: Initializing card 0
[   28.422859] cx18-0: Autodetected Hauppauge card
[   28.424210] cx18 0000:03:08.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.424928] cx18-0: ioremap failed, perhaps increasing __VMALLOC_RESERVE in page.h
[   28.425166] cx18-0: or disabling CONFIG_HIGHMEM4G into the kernel would help
[   28.440229] cx18-0: Error -12 on initialization
[   28.440386] cx18: probe of 0000:03:08.0 failed with error -12
[   28.440739] cx18:  End initialization
[ 2131.769726] cx18:  Start initialization, version 1.1.0
[ 2131.769837] cx18-0: Initializing card 0
[ 2131.769845] cx18-0: Autodetected Hauppauge card
[ 2131.773331] cx18-0: ioremap failed, perhaps increasing __VMALLOC_RESERVE in page.h
[ 2131.773339] cx18-0: or disabling CONFIG_HIGHMEM4G into the kernel would help
[ 2131.773361] cx18-0: Error -12 on initialization
[ 2131.773385] cx18: probe of 0000:03:08.0 failed with error -12
[ 2131.773431] cx18:  End initialization

```

Anyone know where I can go from here?

---

### Post by araudan on 2009-04-11
When running Mythbuntu you need to disable the mythtv backend.  Not disabling the backend will cause errors when installing.

---

