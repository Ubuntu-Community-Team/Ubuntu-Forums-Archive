---
title: "Can any one else confirm this Asus My Cinema U3100 No longer works"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Jason Weiss on 2008-12-27
I was just about to buy a Asus My Cinema U3100 usb stick when I saw this thread.

[http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini](http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini)


Anyone else experenced probblem with this tv stick in the last couple of months?


> Notes Nov 14, 2008

   * I purchased an ASUS My Cinema U3100 Mini USB ATSC card recently. Asus seems to have done an unannounced hardware change. My card is not autodetected by Ubuntu 8.04, Ubuntu 8.10, Fedora Core 8, Fedora Core 9, Fedora Core 10 (Preview), Mythdora 5, or freshly built dvb-usb drivers from Linuxtv.org
   * ASUS provides a Linux package that it turns out is only compiled for their eeePC Debian kernel (no sources).
   * Taking the package apart, it installs the following modules: dib0700, dib7000m, dib7000p, dibx000_common, dvb-core, dvb-drxj, dvb-usb-dib0700, dvb-usb-drxusb, dvb-usb, and mt2266.
   * It appears that my version of the card has a MicroNAS DRXJ ATSC demodulator chip, which is currently unsupported by dvb-usb.
   * The device id reported by lsusb is 0b05:1747, which is not recognized by the Linuxtv dvb-usb drivers.
   * ASUS support has not been terribly helpful on this issue. If anyone has been able to get them to release source files, please post them here. 
   * Boycott ASUS until they provide source code for the GPL drivers they've modified.


---

### Post by jrothney on 2008-12-28
Yes,

I got one of these for Christmas and have not been able to get it work with Hardy.

I see the exact symptoms as described on:
- [http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini](http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini)

Anxiously awaiting some resolution on this...


> **Jason Weiss said:**
> I was just about to buy a Asus My Cinema U3100 usb stick when I saw this thread.

[http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini](http://www.mythtv.org/wiki/index.php/Asus_My_Cinema_U3100_mini)


Anyone else experenced probblem with this tv stick in the last couple of months?

---

### Post by Jason Weiss on 2009-01-04
I was hoping this would not be the case

---

### Post by oedenfield on 2009-01-04
I found the same mythtv article the original poster linked and haven't had any luck with this device either.  I was hoping to use this with Intrepid.

---

### Post by Jason Weiss on 2009-01-04
It would be really sad to think that yhis was done intentionally to force peopl to use eeepcs?

I hope someone comes up with a fix for this soon.

---

### Post by jrothney on 2009-01-05
some more (discouraging) news on this topic:

Re: Pinnacle 80e support: not going to happen...
- [http://www.spinics.net/lists/linux-dvb/msg30598.html](http://www.spinics.net/lists/linux-dvb/msg30598.html)

---

### Post by Jason Weiss on 2009-01-08
I know this question has been asked a million times before, but can anyone recomend a plug and play tv card or preferably a USB?  I have tried some many cards I am sick of wasting my money.

---

### Post by thisweb on 2009-01-12
I am looking at buying one too (also sick of wasting money on experimenting).  There is no information that I can find anywhere on the web that gives a simple explanation to novices of how to install a TV tuner or which ones are ready to go plug and play.  Linuxtv and mythtv only have information about how to install drivers but that is way to complicated and assumes too much linux coding knowledge for even the most competent layman.  Any advise would be welcome.  I love ubuntu but its a real let down that theres no media centre easy to set up for the average user looking to switch from windows/vista.   Hardware installation and finding compatability information is just far to difficult to figure out unless your experienced.

---

### Post by jrothney on 2009-06-18
Hi all,

I thought I'd check the asus site for any update on the driver:
- [http://usa.asus.com/products.aspx?l1=18&l2=84&l3=255&l4=0&model=2299&modelmenu=1](http://usa.asus.com/products.aspx?l1=18&l2=84&l3=255&l4=0&model=2299&modelmenu=1)

Looks like they may have released the source for the driver:
- [http://dlsvr04.asus.com/pub/ASUS/vga/tvtuner/Driver/EeePC_TVDrv_Src_12.zip](http://dlsvr04.asus.com/pub/ASUS/vga/tvtuner/Driver/EeePC_TVDrv_Src_12.zip)

I opened up the zip and don't see anything specific to the product I have (0b05:1747). It all just looks like dvb and v4l sources from Oct. 2007.

Any ideas?

---

### Post by dalcom on 2010-03-13
I finally had the U3100 (0b05:173f from lsusb) working on Karmic Koala with VLC, on an Intel MacMini.

I did so many things that I'm sure I'll forget some here, but in general I:
1) Downloaded the generic driver (EeePC_TVDrv_Src_11) from the ASUS website ([http://www.asus.com/product.aspx?P_ID=7KqG3FwyUeVB41W2](http://www.asus.com/product.aspx?P_ID=7KqG3FwyUeVB41W2) - I haven't tried the players on the same page yet)
2) run make config and kept only what seemed to be necessary (which must include Dib0700 (or DiB7000?), whichever appears. Just for info: I ruled out v4l first version, but kept v4l compatibility layer and disabled all the radio drivers. 
4) make
5) make install
6) modprobe dvb-usb and modprobe dib0700 (one is wrong and failed, I think).
7) Restarted PC (was it necessary)?
8) Installed dvb-utils and vlc
9) Installed kaffeine (1.0-pre2) and phonon-backend-xine to fix a problem with it. This step is probably not necessary.
10) Installed gxine, Me Tv and Myth Tv, tried with them and kaffeine. Probably all useless for the DVB-T to work.
11) Opened VLC, Media, Open Capture Device, Capture Device, Capture Mode: DVB, DVB Type: DVB-T, selected Enqueue from the little button near 'Play' and pressed Enqueue. The settings window closed and I pressed the play button with the triangle on the main window. VLC started scanning, then I left it in background. It took some time for it to finish scanning. Suddenly, after something like possibly 15-20 minutes, it started to play BBC Red Button.
Unfortunately, it seems that saving the generated playlist of channels doesn't work (fails silently), so I have to rescan every time.

Other notes: I connected it to the main house aerial, not the little thing that comes with it and its led light went all green.

My uname -a: Linux mac-mini-ubuntu 2.6.31-20-generic #57-Ubuntu SMP

---

### Post by dsimcha on 2010-05-15
Is it just me or is this code horribly buggy?  I keep trying to reconfigure it using make config to make it leaner and get rid of the parts that don't compile cleanly.  Every time I do, I get a different error message that seems to indicate a bug in the code itself.  For example, here are the errors when I just do make all:

/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1268: error: (Each undeclared identifier is reported only once
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1268: error: for each function it appears in.)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_switch_overlay':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1777: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_prepare_buffer':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1888: error: 'STATE_NEEDS_INIT' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1898: error: 'STATE_PREPARED' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'buffer_queue':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:1937: error: 'STATE_QUEUED' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_common_ioctls':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2115: error: implicit declaration of function 'v4l2_video_std_construct'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2310: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2310: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2310: error: too many arguments to function 'v4l2_chip_match_host'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2313: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2315: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2315: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2317: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2317: error: dereferencing pointer to incomplete type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'setup_window':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2610: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2627: error: implicit declaration of function 'videobuf_pci_alloc'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2627: warning: assignment makes pointer from integer without a cast
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2632: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_s_fmt':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2813: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2822: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_do_ioctl':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2851: error: implicit declaration of function 'v4l_print_ioctl'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2924: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:2955: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3029: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3067: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3090: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3093: warning: assignment makes pointer from integer without a cast
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3102: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3111: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3123: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3141: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3148: error: 'STATE_QUEUED' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3149: error: 'STATE_ACTIVE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3164: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3175: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3184: error: 'STATE_ERROR' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3187: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3198: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3212: error: implicit declaration of function 'v4l_compat_translate_ioctl'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3361: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3387: warning: assignment makes pointer from integer without a cast
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3393: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3602: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3620: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3646: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_ioctl':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3682: error: implicit declaration of function 'video_usercopy'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_read':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3695: error: 'v4l2_type_names' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_poll':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3739: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3743: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3746: warning: assignment makes pointer from integer without a cast
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3748: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3756: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3762: error: 'struct videobuf_queue' has no member named 'lock'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3767: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3768: error: 'STATE_ERROR' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_open':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3801: error: 'v4l2_type_names' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3813: error: implicit declaration of function 'videobuf_queue_pci_init'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_mmap':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3898: error: 'v4l2_type_names' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: At top level:
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3910: error: 'v4l_compat_ioctl32' undeclared here (not in a function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3921: error: unknown field 'type' specified in initializer
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3923: warning: initialization from incompatible pointer type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3930: error: unknown field 'type' specified in initializer
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3931: warning: initialization from incompatible pointer type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'radio_open':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:3962: error: 'AUDC_SET_RADIO' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: At top level:
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4077: error: unknown field 'type' specified in initializer
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4078: warning: initialization from incompatible pointer type
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_irq_timeout':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4361: error: 'STATE_ERROR' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_irq_wakeup_top':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4397: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_irq_switch_video':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4446: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_irq_switch_vbi':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4479: error: 'STATE_DONE' undeclared (first use in this function)
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'vdev_init':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4620: error: incompatible types when assigning to type 'struct device' from type 'struct device *'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c: In function 'bttv_register_video':
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4658: error: 'struct video_device' has no member named 'type'
/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.c:4671: error: 'struct video_device' has no member named 'class_dev'
make[3]: *** [/home/dsimcha/src/v4ldvbpb-1.1-src/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/home/dsimcha/src/v4ldvbpb-1.1-src/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dsimcha/src/v4ldvbpb-1.1-src/v4l'
make: *** [all] Error 2

When I do make config to disable the offending module, I get different but similar error messages in different modules.  If anyone actually got this working on 10.4 x64, could you please post the binaries?

---

### Post by snakeroll on 2010-06-17
My Cinema-U3100 mini USB2.0 digital TV receiver.
Well I've been trying to get this device going om my desktop for about a week now. I was hoping to have it going for the start of the world cup (football).
As stated previously the drivers supplied on the installation CD are specific to eeePC linux. I checked the ASUS software repositary and I've got the most up-to-date drivers, but They are not installing cleanly on my desktop running Ubuntu 9.10. I have an oldish compaq Intel pentium4 with 1GB RAM.
Looks like the only person to get it going is Dalcom from post #10, but I've tried doing the same things without success. I'm not very adept on Linux - a relative newcomer, so may be missing an important step. I got a message that newer versions of same of the packages were already installed when I ran eeePc-TVDrv-U3000-1.2 and the install failed (I think!).
If anyone has got a complete set of installation instructions for 9.10 I would be most grateful if they could post the whole thing.
I also tried installing an older version of XUbuntu 8.041 on a spare hard drive - the EeePC drivers seemed  to install OK on this, but it still does not see my supposed plug'n'play device and I can't find the TV tuner programme to open it.

---

### Post by daehenoc on 2010-08-11
Hey, try these instructions on the LinuxTV wiki: [http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T](http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T)

I'm just looking around for a U3100, not a mini :)

---

