---
title: "Upgrade to Gutsy lost ivtv firmware"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by frkstein on 2007-10-20
I performed an upgrade to Gutsy today. Checking my system to see if everything went smoothly I noticed that mythtv wouldn't allow me to watch TV. Checking dmesg, I noticed that it can't find the ivtv firmware for my Hauppauge PVR 250. How can I fix the ivtv firmware?

---

### Post by kacheng on 2007-10-22
Some threads indicate that ivtv firmware is included in the kernel in Gutsy now.

Can anyone confirm this?

How do we 'enable' it?

---

### Post by frkstein on 2007-10-22
I discovered my problem. With some poking around, I discovered that with the upgrade to Gutsy I had two different kernel versions available to me: 2.6.22-14-386 and 2.6.22-14-generic. The 386 version was the default listed in grub and was the one I was using when ubuntu couldn't find the ivtv firmware. I rebooted the system and selected the generic 2.6.22-14 kernel and everything works fine. It is my guess that during the upgrade, the ivtv firmware files were not copied into the appropriate hotplug directory for the 2.6.22-14-386 kernel. Unless anyone states otherwise, I am going to edit grub to only offer the generic kernel version and just use that.

---

### Post by kacheng on 2007-10-22
Strangely, I am using 2.6.22-14-generic.

**# locate ivtv **
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Kconfig
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Makefile
/usr/src/linux-headers-2.6.22-14/include/media/ivtv.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/video/ivtv.h
/usr/src/linux-headers-2.6.22-14-386/include/config/video/ivtv.h

Any idea what is missing for me?

---

### Post by keithacole on 2007-10-23
im having the same problem

---

### Post by keithacole on 2007-10-23
i booted into the RT kernel, and it worked, so i just need to get it to work in the generic kernel

```
keith@keith-desktop:~/Miro-0.9.8.1/platform/gtk-x11$ locate ivtv
/var/lib/dpkg/info/ivtv-utils.md5sums
/var/lib/dpkg/info/ivtv-source.list
/var/lib/dpkg/info/libvideo-ivtv-perl.list
/var/lib/dpkg/info/libvideo-ivtv-perl.md5sums
/var/lib/dpkg/info/ivtv-utils.list
/var/lib/dpkg/info/ivtv-source.md5sums
/var/cache/apt/archives/ivtv-utils_1.0.2-2_i386.deb
/var/cache/apt/archives/ivtv-source_1.0.2-2_all.deb
/var/cache/apt/archives/libvideo-ivtv-perl_0.13-3_i386.deb
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.22-14-rt/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-rt/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/home/keith/.ivtv-tune
/home/keith_/.ivtv-tune
/usr/bin/ivtvfwextract
/usr/bin/ivtv-mpegindex
/usr/bin/ivtvplay
/usr/bin/ivtv-tune
/usr/bin/ivtvctl
/usr/bin/ivtv-radio
/usr/lib/perl5/auto/Video/ivtv
/usr/lib/perl5/auto/Video/ivtv/ivtv.so
/usr/lib/perl5/auto/Video/ivtv/ivtv.bs
/usr/lib/perl5/Video/ivtv.pm
/usr/share/doc/libvideo-ivtv-perl
/usr/share/doc/libvideo-ivtv-perl/copyright
/usr/share/doc/libvideo-ivtv-perl/README
/usr/share/doc/libvideo-ivtv-perl/changelog.gz
/usr/share/doc/libvideo-ivtv-perl/changelog.Debian.gz
/usr/share/doc/ivtv-utils
/usr/share/doc/ivtv-utils/copyright
/usr/share/doc/ivtv-utils/README.Debian
/usr/share/doc/ivtv-utils/README.vbi.gz
/usr/share/doc/ivtv-utils/modules.txt
/usr/share/doc/ivtv-utils/README.ivtvfb.gz
/usr/share/doc/ivtv-utils/README.devices.gz
/usr/share/doc/ivtv-utils/README.radio
/usr/share/doc/ivtv-utils/README.utils
/usr/share/doc/ivtv-utils/README.install
/usr/share/doc/ivtv-utils/video-quality.txt
/usr/share/doc/ivtv-utils/README.lirc.gz
/usr/share/doc/ivtv-utils/changelog.gz
/usr/share/doc/ivtv-utils/changelog.Debian.gz
/usr/share/doc/ivtv-source
/usr/share/doc/ivtv-source/copyright
/usr/share/doc/ivtv-source/changelog.gz
/usr/share/doc/ivtv-source/changelog.Debian.gz
/usr/share/man/man3/Video::ivtv.3pm.gz
/usr/share/modass/packages/ivtv-source
/usr/src/ivtv.tar.bz2
/usr/src/linux-headers-2.6.22-14-generic/include/config/video/ivtv.h
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Makefile
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Kconfig
/usr/src/linux-headers-2.6.22-14/include/media/ivtv.h
/usr/include/linux/ivtv.h

```

---

### Post by kacheng on 2007-10-24
I found there was some kind of conflict with the **xserver-xgl** package.

Once I removed that (I think it used to be used by Beryl, but has been superceded by CompizFusion), everything worked again.

---

### Post by eskay on 2007-10-25
> **kacheng said:**
> I found there was some kind of conflict with the **xserver-xgl** package.

Once I removed that (I think it used to be used by Beryl, but has been superceded by CompizFusion), everything worked again.

Hmm... same problem here (lose ivtv with PVR-150 on upgrade Feisty -> Gutsy). Will have to try alternate kernel version.

Don't have xserver-xgl installed so that isn't the issue here.

Any apt-gettable ivtv  on the horizon? Or should I just revert to Feisty until this is sorted out?

```
dmesg
[19349.202638] ivtv0: DMA TIMEOUT 00000001 0
[19353.227699] ivtv0: DMA TIMEOUT 00000001 0
[19357.447445] ivtv0: DMA TIMEOUT 00000001 0

```

```

cat /var/log/mythtv/mythbackend.log
....
2007-10-24 21:31:00.208 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
```

```
~$ locate ivtv
/var/cache/modass/ivtv-source.avail_version
/usr/src/linux-headers-2.6.22-14-generic/include/config/video/ivtv.h
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Kconfig
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Makefile
/usr/src/linux-headers-2.6.22-14/include/media/ivtv.h
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/ivtv-fb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/saa717x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/ivtv.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko

```

---

### Post by eskay on 2007-10-27
Just a note that I managed to resolve this problem. Running on an ASUS Pundit P1 AH2 I was getting ivtv errors and DMA error messages in dmesg, watching live TV was fine but whenever I tried to record the recording would end after a few minutes and the errors would appear.

The problem is apparently a combination of APIC support, PCI latency and the ivtv driver version included with Gutsy. In my case I was getting a MP-BIOS APIC error message on boot. Updating to the latest BIOS version 4.04 solved the APIC error message and since then haven't had any problems with ivtv.

This may not help you but I'd recommend enabling APIC in BIOS, and search around these forums for ivtv and PCI latency issues if that doesn't help.

---

### Post by ebs16 on 2007-11-07
I've lost IVTV support on my PVR-150 after upgrading to Gutsy.  These lines show up in dmesg:

```

[   14.764000] ivtv:  ==================== START INIT IVTV ====================
[   14.764000] ivtv:  version 1.0.0 (2.6.22-14-386 mod_unload 486 ) loading
[   14.768000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.768000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   17.640000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw (must be 376836 bytes)
[   17.640000] ivtv0: did you put the firmware in the hotplug firmware directory?
[   17.640000] ivtv0: Retry loading firmware
[   18.256000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw (must be 376836 bytes)
[   18.256000] ivtv0: did you put the firmware in the hotplug firmware directory?
[   18.256000] ivtv0: Error initializing firmware
[   18.260000] ivtv0: Error -19 on initialization
[   18.260000] ivtv:  ====================  END INIT IVTV  ====================

```I've unsuccessfully tried reinstalling the ivtv drivers.  Any ideas?

Thanks!

---

### Post by Rroet on 2007-12-08
I've just encountered the same issue. After a kernel upgrade ivtv suddenly stopped working. Unable to locate the firmware that's needed :(

What did the devs do wrong?

---

### Post by ebs16 on 2007-12-08
I've managed to solve this on my end. Try this:

1) Install **[FONT=Courier New]ivtv-source[/FONT]** and **[FONT=Courier New]ivtv-utils[/FONT]** via apt-get 

These are the utilities needed to manipulate the ivtv drivers once they're installed properly.

2) Download the newest ivtv drivers [COLOR=Blue][here]("http://ivtvdriver.org/index.php/Download")[/COLOR] [[http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)] ([COLOR=Blue][v1.0.3]("http://dl.ivtvdriver.org/ivtv/archive/1.0.x/ivtv-1.0.3.tar.gz")[/COLOR] [[http://dl.ivtvdriver.org/ivtv/archive/1.0.x/ivtv-1.0.3.tar.gz](http://dl.ivtvdriver.org/ivtv/archive/1.0.x/ivtv-1.0.3.tar.gz)] as of this post).

Extract the files to a temp directory.

3)  The IVTV driver tar contains three files (listed below) that need to be copied to [FONT=Courier New]**/lib/firmware/*[your kernel release name]*/**[/FONT].  My release name is [FONT=Courier New]**2.6.22-14-386**[/FONT], so I coped the files to [FONT=Courier New]**/lib/firmware/2.6.22-14-386/**[/FONT].  You can find your kernel release name by typing **[FONT=Courier New]uname -r[/FONT]** at the command prompt.

The files to be copied are: [FONT=Courier New]**v4l-cx2341x-dec.fw**[/FONT], [FONT=Courier New]**v4l-cx2341x-enc.fw**[/FONT], and[FONT=Courier New] **v4l-cx25840.fw**[/FONT].

4) Lather, rinse, reboot. You should now be in business.

Hope this helps! Please confirm on this forum if this method works for you.

---

### Post by wolfen69 on 2007-12-08
ivtv-utils are available in synaptic. always have been.

---

### Post by ebs16 on 2007-12-08
> **wolfen69 said:**
> ivtv-utils are available in synaptic. always have been.

Yeah, but it doesn't seem to install properly on Gutsy. The fix I posted above seems to take care of the issue.

I should have noted that something odd seems to be going on with my system.  I installed Ubuntu Server on my PC and immediately installed GDM, X, and Fluxbox to run MythTV with as little overhead as possible.  My kernel should read 2.6.22-14-server, and indeed there is a 2.6.22-14-server directory in /lib/firmware/ and in most other places in my system structure where I would expect to find kernel-specific files.  For some reason, however, my kernel boots into and identifies itself as 2.6.22-14-386. :confused:  When I installed ivtv-drivers via apt-get, the drivers were copied into /lib/firmware/2.6.22-14-server, not /lib/firmware/2.6.22-14-386.  This has happened on two of my machines.  Is this a problem with the ivtv-drivers package or with my setup?

---

### Post by wackston on 2008-01-14
You need to install the linux-ubuntu-modules and linux-backports-modules packages for your kernel.  They're not included automagically in the upgrade and the ivtv driver and firmware is part of them (its not a standard kernel driver).

-Andrew

---

