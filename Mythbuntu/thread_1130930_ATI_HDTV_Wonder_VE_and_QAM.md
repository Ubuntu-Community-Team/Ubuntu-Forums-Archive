---
title: "ATI HDTV Wonder VE and QAM"
date: 2009-04-20
forum: Mythbuntu
---

### Post by tombongo on 2009-04-20
I have the full version of this, and I want to add a second.  I can get the VE version for cheap.  The MythTV wiki states that the VE works for digital only.  When the wiki says digital, does it mean ATSC, QAM, or both?  Is anyone using the VE version for QAM?  Thanks in advance.

---

### Post by novellahub on 2009-08-31
I have 4 of these cards and they work in ATSC and QAM.  They just need a little work to get going (I have it set up in Mythbuntu 8.04)

Copy the firmware to the /lib/firmware directory:

[https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder](https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder)

Force the tuner type:

[http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient](http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient)

Reboot and set up the cards. :)

---

### Post by jeremyjjbrown on 2009-11-19
> **novellahub said:**
> I have 4 of these cards and they work in ATSC and QAM.  They just need a little work to get going (I have it set up in Mythbuntu 8.04)

Copy the firmware to the /lib/firmware directory:

[https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder](https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder)

Force the tuner type:

[http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient](http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient)

Reboot and set up the cards. :)

If I do this firmware update to my tuner card can I still use it with xp? the device is very difficult to install with the ATI installers and I don't want to mess it up.

---

### Post by novellahub on 2009-11-19
Yes.  You are not really updating the firmware on the ATI card itself.  It just gets loaded at boot up time for use in Linux. Think of it more as a driver.

---

### Post by jeremyjjbrown on 2009-11-29
> **novellahub said:**
> Yes.  You are not really updating the firmware on the ATI card itself.  It just gets loaded at boot up time for use in Linux. Think of it more as a driver.

Thanks!

---

### Post by rp_linux on 2010-07-02
Hi, 

Iam trying to get a Diamond ATI HD wonder 600 card recognized in mythbuntu 10.04 but struggling so far :(

Thought this was supported in linux based on reading these wiki pages for ATI Wonder HD card. 

[http://www.mythtv.org/wiki/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/ATI_HDTV_Wonder)
[http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder](http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder)

Looks like some  of you in this thread have successfully gotten it to work, hope you can  help.

Followed the instructions to download the firmware and compiled v4l drivers from mercurial as in the wiki links above. 

I see the card when I do a lspci.
$ lspci -nn | grep ATI
01:05.0 Multimedia controller [0480]: ATI Technologies Inc Theater 600 Pro [1002:ac00]

But get this error when I try to load cx88-dvb.
$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.32-22-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I do see the .ko file is present.

$ ls -l /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko
-rw-r--r-- 1 root root 55000 2010-07-01 23:33 /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko

$dmesg shows these entries when I try the above.
[  543.784485] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[  543.793360] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[  543.793369] cx88/2: registering cx8802 driver, type: dvb access: shared

There is no /dev/dvb/adapter0 created. So haven't been able to  try scanning for channels. 

This is the only tuner card in my system. I really like the low profile form factor and was hoping to get it working for ATSC/QAM in mythtv. 

I noticed the PCI ID is different compared to the ones shown in the wiki. The HD 600 PCI ID is:
[1002:ac00]

whereas the ATI card described in the wiki has PCI ID of 1002:a101 or 1002:a103.

Did I get an unsupported version of the ATI wonder card? This is the one I got.

[http://www.amazon.com/ATI-Wonder-600-PCI-Tuner/dp/B00138GQ60/ref=sr_1_1?ie=UTF8&s=electronics&qid=1278054718&sr=1-1](http://www.amazon.com/ATI-Wonder-600-PCI-Tuner/dp/B00138GQ60/ref=sr_1_1?ie=UTF8&s=electronics&qid=1278054718&sr=1-1)

Appreciate any advice on the right model # that is supported in linux.

Thanks.

---

