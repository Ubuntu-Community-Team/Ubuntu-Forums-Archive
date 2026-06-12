---
title: "[SOLVED] How well does mythbuntu handle a PVR 350 output?"
date: 2007-10-05
forum: Mythbuntu
---

### Post by purplerhino on 2007-10-05
Will PVR350 output just work, or will it require extra effort?  My mythtv box has been on gentoo for years, but I'm considering moving to something a little lower maintenance.  But if I go through the easy install of mythbuntu, but then have to do a bunch of hack work, well, hasn't made my life much easier!

:popcorn:

:EDIT:  

It is working, here's what I did.

install this deb:

> **superm1 said:**
> Okay guys, I've got this built on my ppa.  You can try this:

For i386:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb)

For amd64:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb)

The ivtv-fb module should already be included.

Follow the instructions at [https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out")

EXCEPT, the part when you download and copy the driver, "Add the ivtvdev_drv driver to X", skip.  That's in the package above.  and in the Device section of xorg.conf should have Driver "ivtv" instead of "ivtvdev"

> **wppaas said:**
> 
        # the driver we installed.
        Driver "ivtv" #WATCH IT not called ivtvdev anymore!!


then I was able to get into X, but mythtv wouldn't play any video.  I then added :

> **superm1 said:**
> 

** deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) gutsy main**



to my /etc/apt/sources.list file and updated mythtv with the packages from there.  And everythings works!  Not quite as automatic as I dreamed of, but not too bad either.  Thanks a ton superm!

Oh yeah, I also followed these directions to adjust the overscan so the gui fit the screen right

[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#How_do_you_resize_the_MythTV_UI_and_playback_overlay_to_fit_the_TV_screen_when_displaying_X_on_the_PVR-350_video_output.3F]("http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#How_do_you_resize_the_MythTV_UI_and_playback_overlay_to_fit_the_TV_screen_when_displaying_X_on_the_PVR-350_video_output.3F")

and I had the top panel showing up on the top corner of my ui, so I had to go into Preferences -> Panel and I set the top panel to hidden so it wouldn't interfere.

---

### Post by superm1 on 2007-10-05
There was a request for this a few days ago.  I just added the ivtv-fb module to the kernel image shipping in ubuntu/mythbuntu.  No automatic way of doing things as of yet, but if you can file a bug against mythbuntu, might be able to setup something automatic for the release candidate.

Need to have an idea of what needs to be added to the xorg.conf, and whether the ivtv-fb module will automatically load or what not.

The ivtv-fb module will be reflected in linux-ubuntu-modules-**[[B] 2.6.22-13.33**]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-gutsy-lum.git;a=commit;h=34e863e23d521677f635576b262a07033bdfe927")
[/B]

---

### Post by purplerhino on 2007-10-08
it's all described at [http://ivtvdriver.org/index.php/Howto:XDriver](http://ivtvdriver.org/index.php/Howto:XDriver)

being automatic actually isn't a huge deal to me, after using gentoo for five years, editing xorg.conf doesn't scare me... i grow a little tired of doing it, but it's no big deal.

I'm just more looking for the XDriver package to be included and tested in each release so it's kept working.  My setup now, Xorg updates often break compatibility with the X driver, I can't get the X driver to work with the new kernel ivtv driver, etc.

---

### Post by superm1 on 2007-10-08
Well gathering more people for testing is always a challenge.  Especially with obscure hardware.  Due to the popularity of the pvr-500 and pvr-150, most people don't purchase pvr-350's.

Can you please test the ivtv-fb module that should now be included?

---

### Post by dannyboy79 on 2007-10-08
i have a PVR-350 and just never bothered with setting  up the TV-Out on it  because every one says it's too hard and with MythTV going towards OpenGL OSD, they say that the PVR-350 won't even work.

I may need to get this working however as I am adding a new slave be/fe in my family room. It'll be using the pvr-350 and I currently don't have a video card for that machine that has tv-out. it only has a vga connector and the tv I am hooking it to is old and doesn't have vga.

I would definitely like to see this working with Mythbuntu because I am going to be installing Gutsy and then Mythbuntu Control Center using the weekly builds (20-fixes isn't it?) since it has fixed the firewire issue where listings don't get retrieved from SD lineups when adding the new firewire input. So I'll have 2 inputs in this machine, a firewire port hooked to a sa 3250hd STB and then the pvr-350.

---

### Post by purplerhino on 2007-10-08
Well if you have an older TV like I do, with just composite or svideo, do the extra effort for the 350 output.  It's much better than like nvidia tv-out.  Now yeah, most newer tvs have VGA, DVI, whatever, so the 350s usefulness is expiring...  but if you are protesting HD like I am, then hang onto that 350 ;)  It's not that HD is not lovely, but until I can plug my HD cable into the back of MythTV computer as easy as I do my analog cable, I want none of it.  I can't be bothered with the hassle of fighting encryption, converter boxes, ir blasters, etc.  :mad:

---

### Post by dawson64 on 2007-10-08
I've been working with superm1 to get the PVR-350 working.  We've got the driver added but I'm getting an error when i perform modprobe ivtv-fb
I am able to get modprobe saa7127 to display the veritcle colors.  I've been refrenced the Edgy PVR-350 how to: [https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out")
```
[  130.871682] ivtv0-fb: Framebuffer at 0x1510000, mapped to 0x00510000, size 1665k
[  130.871821] mtrr: type mismatch for 1400000,400000 old: write-back new: write-combining
[  130.871827] ivtv0-fb: warning: mtrr_add() failed to add write combining region 0x01400000-0x01800000
[  130.871865] BUG: unable to handle kernel paging request at virtual address 00510000
[  130.871869]  printing eip:
[  130.871872] f9f097cb
[  130.871873] *pde = 00000000
[  130.871878] Oops: 0002 [#1]
[  130.871880] SMP
[  130.871884] Modules linked in: ivtv_fb af_packet mga drm cx8800 cx88xx bttv video_buf ir_common compat_ioctl32 btcx_risc lirc_i2c lirc_dev ipv6 dock sbs button container ac video battery sbp2 lp i2c_viapro msp3400 saa7127 saa7115 tuner snd_cmipci gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_hwdep snd_mpu401_uart snd_seq_dummy snd_seq_oss pcspkr serio_raw snd_seq_midi snd_rawmidi snd_seq_midi_event parport_pc parport via_ircc irda psmouse matrox_w1 wire snd_seq snd_timer snd_seq_device crc_ccitt cn ivtv i2c_algo_bit cx2341x tveeprom i2c_core videodev v4l2_common v4l1_compat snd soundcore via_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic libata scsi_mod floppy via82cxxx ide_core 8139too mii ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 thermal processor fan fuse apparmor commoncap
[  130.871958] CPU:    0
[  130.871959] EIP:    0060:[<f9f097cb>]    Not tainted VLI
[  130.871961] EFLAGS: 00010216   (2.6.22-13-generic #1)
[  130.871972] EIP is at ivtvfb_init_card+0x16b/0x6f0 [ivtv_fb]
[  130.871976] eax: 00000000   ebx: e0244000   ecx: 00068100   edx: 001a0400
[  130.871981] esi: dfeb0000   edi: 00510000   ebp: df49fa1c   esp: e022be44
[  130.871984] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[  130.871989] Process modprobe (pid: 5691, ti=e022a000 task=e0316f90 task.ti=e022a000)
[  130.871991] Stack: f9f0a8dc 00000000 01400000 01800000 00000681 00000000 00510000 002c0800
[  130.872000]        00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  130.872005]        00000000 00000000 00000000 00000000 00000000 00000000 dfeb0000 00000000
[  130.872011] Call Trace:
[  130.872036]  [<f89d5057>] ivtvfb_init+0x57/0x10f [ivtv_fb]
[  130.872047]  [<c014a7d1>] sys_init_module+0x151/0x1a00
[  130.872058]  [<c01fb39f>] prio_tree_insert+0x1f/0x250
[  130.872111]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[  130.872132]  =======================
[  130.872134] Code: 40 10 c7 04 24 01 00 00 00 29 c2 e8 00 5b 20 c6 85 c0 0f 88 e3 04 00 00 8b 86 f0 f4 00 00 8b 50 0c 8b 78 08 31 c0 89 d1 c1 e9 02 <f3> ab f6 c2 02 74 02 66 ab f6 c2 01 74 01 aa a1 88 ca f0 f9 85
[  130.872164] EIP: [<f9f097cb>] ivtvfb_init_card+0x16b/0x6f0 [ivtv_fb] SS:ESP 0068:e022be44
 
```

---

### Post by superm1 on 2007-10-08
Well this is a bad sign.  It can be a variety of things.  Can we get a second person to verify?

Also, dawson64, fire an email off to the ivtv mailing list at [http://ivtvdriver.org/index.php/Mailinglists](http://ivtvdriver.org/index.php/Mailinglists) with this exact information.

---

### Post by ArVincentr on 2007-10-11
Hello Gents,

 I am new to this forum but would already like to give some contribution.

 I am also testing mythbuntu with the latest kernel available.
 I have got the same error running ivtv 1.0.0.

 I am getting crazy with the TV-OUT of the PVR-350. this is the only thing not working for me.  I  have been googling for some days now and I am unable to find anything.  furthermore if you want to compile the newest ivtv driver 1.0.2  the system does not complains about the compilation but the new drivers isn't taken into account. I still get IVTV 1.0.0 from my logs. 

I am running mythbuntu on an epia C-7 @ 1500 Mhz with 1 gig memory DDR2-533. a 2.5 inch Hd of 160 gigs. 

I have an LCD TV with an vga connector so I can look tv via the vga out but this chrages the cpu for nothing when you have an encoder/decoder on your tv card. 


Ok Now, if you want a tester / reporter  I can execute your commands on my box and give you the results. 

Kind regards

Vincent.

---

### Post by wppaas on 2007-10-11
> **superm1 said:**
> Well this is a bad sign.  It can be a variety of things.  Can we get a second person to verify?

I can verify this error. When modprobing ivtv-fb I'm getting the same error messages as dawson64. I'm using all the latest files and my kernel is  Linux version 2.6.22-14-generic (buildd@vernadsky) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Wed Oct 10 06:00:47 GMT 2007 (Ubuntu 2.6.22-14.43-generic)

cheers,
WP

---

### Post by wppaas on 2007-10-11
By the way, I found this post at the ivtv-devel list, It is about the same bug

[http://www.ivtvdriver.org/pipermail/ivtv-devel/2007-August/004988.html](http://www.ivtvdriver.org/pipermail/ivtv-devel/2007-August/004988.html)

WP

---

### Post by wppaas on 2007-10-11
A litte more info about the error when modprobing ivtv-fb

According to the post on ivtv-devel the wrong ivtv-driver.h file is used when compiling the module. I found the following lines in ivtv/driver/makefile

ivtv-driver.h:
ifeq ($(wildcard $(KDIR)/include/config/kernel.release),)
        @KVERNUM=`echo $(KVER) | sed 's/-.*//'`; \
        echo "Kernel version number: $$KVERNUM" ; \
        if [ "$$KVERNUM" = "2.6.22" -o "$$KVERNUM" = "2.6.22.1" ]; then \
                cp -v ivtv-driver1.h ivtv-driver.h; \
        else \
                cp -v ivtv-driver2.h ivtv-driver.h; \
        fi

And here you can see that in case of kernel version 2.6.22, the ivtv-driver1.h is used as ivtv-driver.h. But ivtv-driver1.h differs from the ivtv-driver used in the kernel. ivtv-driver2.h however does not differ from the one used in the kernel and in this case is the one that should be used.

So this is clearly the bug. The module is using the wrong header, 

cheers
WP

---

### Post by wppaas on 2007-10-11
I can confirm that the above fix works.

I've downloaded the ivtv-source.

In the ivtv source tree I've first done a sudo make all, then copied ivtv-driver2.h to ivtv-driver.h and finally rebuilt the ivtv-fb.ko module again using sudo make all.  

After copying ivtv-fb.ko to /lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/
modprobing ivtv-fb works

cheers
WP

---

### Post by dannyboy79 on 2007-10-11
SWEET!!! superm1, can we get this into mythbuntu before RC

---

### Post by superm1 on 2007-10-12
Not in mythbuntu before RC, but i'm querying ubuntu proper for final.  I'll see what can be done.

---

### Post by wppaas on 2007-10-12
Hi

Now that the ivtv-fb module is up and running, I've got to get the xdriver for the 350 working. 

Currently there seems to be no version of it in the multiverse repository. I think it should be called xserver-xorg-video-ivtv. 
I found this one however at
[http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtv_0.10.6-2_i386.deb](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtv_0.10.6-2_i386.deb)
and installed it using dpkg -i.

After doing a little hacking on my xorg.conf file I was NOT able to get it working. This is what I get now, it's the tail of my /var/log/Xorg.0.log file

```

IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 01:00:0
(WW) ivtvdev: No matching Device section for instance (BusID PCI:0:9:0) found
(--) Chipset PVR-350 found
(EE) ivtvHWProvbe failed to do IVTVFB_IOCTL_GET_STATE for device /dev/fb0
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

```

```

crw-rw---- 1 root video 29, 0 2007-10-12 13:30 /dev/fb0

```

I've checked a lot of howto's and my framebuffer device is /dev/fb0

```

0 cx23415 TV out

```

and the 350 is on the 0:0a:0 PCI bus. 
```

00:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)

```

This is part of my xorg.conf

```
Section "Device"
Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
Driver "ivtvdev"
Option "fbdev" "/dev/fb0"
Option "ivtv" "/dev/fb0"
Option "VideoOverlay" "on"
Option "XVideo" "1"
#Option "TVStandard" "PAL"
BusID "PCI:0:10:0"
Screen 0
EndSection

```

I''ve created /etc/modutils/ivtv
```

alias char-major-81-0 ivtv
options ivtv ivtv_debug=1 ivtv_std=2

```

and added 
```

options ivtv-fb osd_compat=1

```
to my /etc/modprobe.d/aliases file

The ivtv-fb driver has loaded correctly and so did my ivtvdev driver (part of my Xorg.0.log file

```
 LoadModule: "ivtvdev"
(II) Loading /usr/lib/xorg/modules/drivers//ivtvdev_drv.so
(II) Module ivtv: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.10.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2

```

Did anyone had more luck with this?

cheers
WP

---

### Post by superm1 on 2007-10-12
The ivtv-fb kernel module should be fixed in today's linux-ubuntu-modules upload.  As for xserver-xorg-video-ivtvdev, i'll see if it can be built on a PPA.

---

### Post by wppaas on 2007-10-12
Nice!

the x-driver I found is clearly too old and that's why it won't work. 
I'm trying to build the latest one too from 
[http://www.hellion.org.uk/ivtv/debian/](http://www.hellion.org.uk/ivtv/debian/)

---

### Post by wppaas on 2007-10-12
Yes, I've got it working now!

I built the latest x-driver found here [http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049.orig.tar.gz](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049.orig.tar.gz)

it creates an ivtv_drv.so object. 
I copied it to  /usr/lib/xorg/modules/drivers/

and I had to rename the driver in my xorg.conf 

```

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtv" #WATCH IT not called ivtvdev anymore!!

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"

        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        #Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:0:10:0"

        Screen 0

EndSection

```

By the way there's also a patch available for the xdriver, [http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049-3.diff.gz](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049-3.diff.gz)
but I did not yet apply it cause it seems to work without it too. I'll do this next.

cheers,
WP

---

### Post by dawson64 on 2007-10-13
> **wppaas said:**
> Yes, I've got it working now!

I built the latest x-driver found here [http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049.orig.tar.gz](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049.orig.tar.gz)

it creates an ivtv_drv.so object. 
I copied it to  /usr/lib/xorg/modules/drivers/

and I had to rename the driver in my xorg.conf 

```

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtv" #WATCH IT not called ivtvdev anymore!!

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"

        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        #Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:0:10:0"

        Screen 0

EndSection

```

By the way there's also a patch available for the xdriver, [http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049-3.diff.gz](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtvdev_1.0.0~svn4049-3.diff.gz)
but I did not yet apply it cause it seems to work without it too. I'll do this next.

cheers,
WP

I've worked on this for a few hours today but haven't been able to figure out how to get my display going out of the PVR-350 yet.  I downloaded the x-driver you recommended (& extracted it) but haven't figured out how to get the ivtv_drv.so.  I'm guessing i need to do some  sort of build for it.  I'm pretty new to this stuff & it's probably pretty obvious but what are the steps i need to do to get the driver?

Thanks!

---

### Post by wppaas on 2007-10-14
make sure to install the xserver-xorg-dev package first.

Then get into the downloaded  x-driver dir and do

./configure prefix=/usr
make
sudo make install

Now there should be a ivtv_drv,so file in /usr/lib/xorg/modules/drivers/

cheers
WP

---

### Post by superm1 on 2007-10-14
Okay guys, I've got this built on my ppa.  You can try this:

For i386:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb)

For amd64:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb)

The ivtv-fb module should already be included.

---

### Post by dawson64 on 2007-10-14
> **superm1 said:**
> Okay guys, I've got this built on my ppa.  You can try this:

For i386:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb)

For amd64:

[http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb)

The ivtv-fb module should already be included.

I was able to install this but it still won't output to the tv.  I'm not sure what to try next.  I've got the setting enabled in mythtv & have tried to go through some of the settings wppaas has mentioned (making the necessary adjustments for my card).

---

### Post by superm1 on 2007-10-14
Well the last part is that you need to modify your xorg.conf.  Look at the posts above for some info how to.

---

### Post by dawson64 on 2007-10-14
> **superm1 said:**
> Well the last part is that you need to modify your xorg.conf.  Look at the posts above for some info how to.

I'm gaining... i could have sworn i had tried that though.  i started with an original xorg.conf & commented out all the current monitor stuff & added the sections for my pvr-350 & the screen.

I'm still getting "unable to initialize video" when i go to watch TV.

I've looked through some logs but I'm not sure what logs to check.

---

### Post by wppaas on 2007-10-14
@dawson64:
Take a look at this howto
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)

I took the xorg.conf file from here and changed a thing or two to match my setup. The only thing that is not correct in there anymore is that the Driver in section Device is now called ivtv instead of ivtvdev.

If it still does not work, show us some of your logs :-), 

/var/log/Xorg.0.log.old or /var/log/Xorg.0.log (the one with the  
(**) |   |-->Device "Hauppauge PVR 350 iTVC15 Framebuffer" 
line in it)

and the output of dmesg

and your /etc/X11/xorg.conf file

@superm1:
I'll test it all tomorrow morning, my mythbox is busy recording now :-)

Cheers,
WP

---

### Post by sshparker on 2007-10-14
Hello,

I have been lurking on this forum because I was having the same problem.  I installed the final release candidate of gutsy to try and fix some lirc problems with mythtv.  After the installation the TV out from the Hauppauge 350 card stopped working.

I followed your instructions, and installed the new xorg driver.  I can now get X up on my TV and I can run the mythtv frontend, but whenever I try to watch live TV or a recorded show I get the same problem as dawson64 - Unable to initialize video.  There really is nothing in the logs at all.  The only change that I get in the /var/log directory at all is the mythtv backend log which outputs:

2007-10-14 19:22:28.032 TVRec(1): Changing from None to WatchingLiveTV
2007-10-14 19:22:28.038 TVRec(1): HW Tuner: 1->1

Just wanted to let you guys know more than one person is having the problem.  Thanks for the help so far!!

Cheers

---

### Post by sshparker on 2007-10-14
Forgot to mention one more thing...

If I run a vnc session on my mythtv box, run mythfrontend, and try to watch TV then I can.  It only seems to be a problem with the TV out.

Thanks again.

---

### Post by antoniuk on 2007-10-14
I am about 30 seconds from burning a cd and redoing my myth box with mythbuntu.

I have a pvr350 as well and could get it to do output from an ATI x850 but could not get the remote to work at all. I will be more than happy to test out anything.

---

### Post by dawson64 on 2007-10-14
Hey all,

I just wrapped up a fresh install and got my tv out working.  One thing **i didn't do **& maybe that is the problem I was having earlier is that I did not enable the TV out for the PVR-350 in the myth settings.

Here is a quick rundown of what I did tonight:
> install mythbuntu RC1
get & install updates thru the gui (specifically the linux-ubuntu-modules-2.6.22.14-generic)

Choose Hauppauge  TV? remote (not working yet :( though)

Download the xorg video driver (thanks superm1)
i386 version:  wget [http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb)
or
amd64 version: wget [http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb](http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_amd64.deb)

install it (choose the version you downloaded)...
sudo dpkg -i xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb


followed this to do some configuring and build xorg.conf [https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out")(didn't really need to install the drivers, that's already done)  

I'm not done yet, I'd like to get the remote working & need to adjust the overscan.

---

### Post by superm1 on 2007-10-14
Great!  Glad to hear this is working for you dawson64.  We'll get this moved over to the wiki and such before release. 

Thanks to everyone in this thread that helped to contribute to getting this sorted out.

dawson64, can you bring over the discussion about pvr-350's remote to this existing thread: [http://ubuntuforums.org/showthread.php?t=574953](http://ubuntuforums.org/showthread.php?t=574953)

Start out by posting /etc/lirc/hardware.conf, /etc/lirc/lircd.conf and ~/.mythtv/lircrc

We'll go from there.

---

### Post by wppaas on 2007-10-15
Ok, just updated all my packages, installed superm1's x-driver, rebooted and it still works like a charm.

done, next :-)

cheers
WP

---

### Post by superm1 on 2007-10-22
Would the original poster mind updating the post to show the correct way ( between  [http://ubuntuforums.org/showpost.php?p=3521248&postcount=19](http://ubuntuforums.org/showpost.php?p=3521248&postcount=19) and [http://ubuntuforums.org/showpost.php?p=3531905&postcount=22](http://ubuntuforums.org/showpost.php?p=3531905&postcount=22)
)
So people don't have to try to hunt through this thread?

Thanks!

---

### Post by frozenskunk on 2007-10-24
Thanks to all for your help on this. I switched from knoppmyth to mythbuntu over the weekend, and was able to get it up and running.

One question though, I have the same problem as a few others in getting 'unable to initialize video' when trying to watch TV or recordings if I have mythtv configured to use the -350's output. I currently have that de-selected, and can get video out that way. The only problem (and correct me if I'm wrong) is that since I don't have mythtv configured to use the -350's output, the main CPU is doing the video processing as opposed to offloading it to the -350.  

I tried googling this, and saw some other people having that error, but none that seemed to be similar to this set of circumstances....

Any ideas or help would be appreciated!
Thanks again!

---

### Post by dawson64 on 2007-10-25
> **frozenskunk said:**
> Thanks to all for your help on this. I switched from knoppmyth to mythbuntu over the weekend, and was able to get it up and running.

One question though, I have the same problem as a few others in getting 'unable to initialize video' when trying to watch TV or recordings if I have mythtv configured to use the -350's output. I currently have that de-selected, and can get video out that way. The only problem (and correct me if I'm wrong) is that since I don't have mythtv configured to use the -350's output, the main CPU is doing the video processing as opposed to offloading it to the -350.  

I tried googling this, and saw some other people having that error, but none that seemed to be similar to this set of circumstances....

Any ideas or help would be appreciated!
Thanks again!

I'm not totally sure how it works.  When watching a recording my CPU utilization is ~20% on an Athlon1800+.

---

### Post by frozenskunk on 2007-10-26
I think that unless you set mythtv to use the -350 tv output, then the main CPU does the work rather then offloading to the -350. This wouldn't really matter, except until now I have been able to get by without using a case fan, just the heatsink fan and PSU fan, so it kept the box very quite...With the CPU doing the work, I have had the box shutdown from CPU overheat a few tiimes, I would prefer to not have to install a case fan just to keep the noise down, if I could just figure out how to get mythtv to itialize the video out of the -350.

---

### Post by superm1 on 2007-10-26
Perhaps can you post /var/log/mythtv/mythfrontend.log from the results of trying to run it through the PVR-350's tv output port inside myth?  It might be a little more verbose about the problem.

---

### Post by superm1 on 2007-10-30
Can someone encountering the issue not being able to output to the 350 inside mythtv (but it working in X) try the package that i've added here:

** deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) gutsy main**

There should be an update to mythtv here.

---

### Post by onlynone on 2007-11-19
> **superm1 said:**
> Great!  Glad to hear this is working for you dawson64.  We'll get this moved over to the wiki and such before release. 

Thanks to everyone in this thread that helped to contribute to getting this sorted out.

Hey guys, this discussion has helped me out a lot, but I still can't get X to run on the frame buffer device. I've gone through this thread several times; I've installed the deb from ```
http://ppa.launchpad.net/superm1/ubuntu/pool/multiverse/x/xserver-xorg-video-ivtvdev/xserver-xorg-video-ivtv_1.0.0~svn4049-3~ppa3_i386.deb
```
I've added ```
deb http://ppa.launchpad.net/superm1/ubuntu/ gutsy main
``` to my sources.list. And I've made the necessary adjustments to my xorg.conf (I've had mythtv up and running on this box a while ago with tv-out so I'm familiar with everything that needs to be done).

This is the relevant portion of my xorg.conf:
```

Section "Device"
    Identifier "PVR"
    Driver "ivtv"
    Option "fbdev" "/dev/fb0"
    BusID "PCI:0:20:0" #lspci says 00:14.0
EndSection

Section "Monitor"
    Identifier "TV"
    HorizSync 30-68
    VertRefresh 50-120
    DisplaySize 183 122
    Mode "720x480"
    DotClock 34.564
    HTimings 720 752 840 028
    VTimings 480 484 488 504
    Flags "-HSync" "-VSync"
    EndMode
EndSection

Section "Screen"
    Identifier "TV Screen"
    Device "PVR"
    Monitor "TV"
    DefaultDepth 24
    DefaultFbbpp 32
    SubSection "Display"
        Depth 24
        FbBpp 32
        Modes "720x480"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "TV Screen"
    InputDevice "Generic Keyboard"
    InputDevice "COnfigured Mouse"
EndSection

```

And this is the end of my /var/log/Xorg.0.log.old:
```

(II) IVTV: driver for ivtv framebuffer: PVR-350
(II) Primary Device is: PCI 01:00:0
(--) Chipset PVR-350 found
(EE) Unsupported card 'VIA VT8623'
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtv"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found

```

It looks like it's using the wrong BusID (01:00:0 instead of 0:20:0) the 'VIA VT8623' is what's at BusID 01:00:0. So I decided to see what would happen if I changed the BusID in my xorg.conf to something I knew was bogus (0:10:0), and this was the output in my Xorg log:

```

(II) IVTV: driver for ivtv framebuffer: PVR-350
(II) Primary Device is: PCI 01:00:0
(WW) ivtv: No matching Device section for instance (BusID PCI:0:20:0) found
(EE) No devices detected.

Fatal server error:
no screens found

```

Everything else seems to be fine. Reading through dmesg doesn't show anything odd or alarming, and I can see the test image by doing:

```
modprobe saa7127 test_image=1
```

Any Ideas?

---

### Post by wppaas on 2007-11-19
@onlynone:

Are you using the correct framebuffer device? What is the output of 

cat /proc/fb

In your case it should return something like

0 cx23415 TV out

The messages about 

 Primary Device is: PCI 01:00:0
(--) Chipset PVR-350 found

are ok.
 
The next message should be like

 IVTV(0): using /dev/fb0

so I guess you're using the wrong framebuffer device

If not, 

Are you loading the new driver? 

Please post your complete xorg log and /var/log/messages

Hope this helps

Cheers
WP

---

### Post by therealbrewer on 2007-11-25
Thanks everyone for this post. I've finally got my pvr-350 running with X on the tv-out. Still need to tweak the remote and the overscan yet.

Howvever, one problem I've got is that after installing the debs and adding the repository and updating, I seem to have farked my wireless connection. The thing is, nm-applet still lists my network, but it shows no signal strength, and I can't connect. The wireless adapter worked out of the box after the initial Mythbuntu install. If I boot to the Mythbuntu CD, the wireless works again, so I know the network itself isn't having any problems. Any ideas?

---

### Post by superm1 on 2007-11-25
This shouldn't have affected anything.  That's rather odd.. I would be apt to think its a separate issue, so can you start a different thread on it so these dont get mixed up.

---

### Post by therealbrewer on 2007-11-26
You know, I would be happy to open a separate thread except I am certain they are somehow related. I did absolutely nothing to the system besides a fresh install of Mythbuntu, then I followed the procedure outlined above. I have found a clue however. I had to use the vga=791 trick in the grub menu.lst to successfully get X on the pvr-350 tv-out. Well, I noticed in the Edgy pvr-350 hardware guide, there is a suggestion to also use pci=noacpi, although no explanation is given, and it is not shown in the Feisty version of the same document. I also noticed that in the Ubuntu wireless troubleshooting guide, the same suggestion is given in the case where your wireless driver can communicate with your wireless card but can't associate with the router. Well, this is exactly my problem, so I tried pci=noacpi. Now I still can't associate with the router, BUT in the nm-applet, any networks that are running without keys will show a signal strength. whereas before, none of them did. Unfortunately, since my network is secured with WPA, even though it is listed in nm-applet, it looks like the strength is zero, and I can't associate.

Does this give you any ideas?

---

### Post by onlynone on 2007-11-26
> **wppaas said:**
> Are you using the correct framebuffer device?

Yeah, that was it. The ivtv-fb module wasn't loaded and the only framebuffer device available (/dev/fb0) wasn't what I wanted. As soon as I loaded ivtv-fb it created /dev/fb1 and that's what I needed to use in my xorg.conf.

Thanks for your help, my mythtv box has been up and running for about a week. I've got a few other issues, but I'll start a new thread for those.

-Steve

---

### Post by onlynone on 2007-11-26
I should have added this to my last post...

After adding the extra repository to my sources.list I'm always prompted to upgrade linux-ubuntu-modules-2.6.22-14-generic when I run apt-get upgrade. I must have responded yes half a dozen times, but whenever I run upgrade it's always in the list to be upgraded. It's annoying for a few reasons: 1. It just shouldn't be happening 2. It's not signed so I have to go through an extra step of saying yes to install it 3. It has to re-create initramfs every time which takes a while. 4. The upgrade notification tooltip appears all the time in xfce.

---

### Post by andrewb78 on 2007-12-18
> **superm1 said:**
> Can someone encountering the issue not being able to output to the 350 inside mythtv (but it working in X) try the package that i've added here:

** deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) gutsy main**

There should be an update to mythtv here.

The updates did solve the problem for me on amd64.  Thanks!

---

