---
title: "Timeout / No Signal / No Lock in MythTV scan for channels."
date: 2008-02-24
forum: Mythbuntu
---

### Post by memps001 on 2008-02-24
I'm trying to configure my new pCHDTV 5500 card to work with MythTV on Ubuntu Gutsy. I never installed the tuner drivers, because when I attempt to compile the driver, I get a message that looks like an error (it's long, but I can post it here if it'd help).

Anyway, I think the card works alright regardless, because I've gotten MythTV to recognize that there's a signal. But this is as far as I can get. After hours of trying different settings, I had found one that gave me a 100% signal reading, but the channel scan always times out and says "No Signal". I don't pay for TV service, but the cable coming out of my wall does get a few HD channels (which work like subchannels of the major networks: 5-1, 9-1, 9-5, etc). When plugged right into the TV, I get both HD and SD channels.

Anyway, I've searched through forums, and how to's, and blogs, but I'm at a loss. I think that perhaps I need some more specific troubleshooting. How can I get MythTV to recognize the channels I get? If there's a signal, shouldn't it just add it as a channel?

---

### Post by volkswagner on 2008-02-24
In setup does myth list your card by name?  Are you selecting QAM for the HD channels?  You can try different settings for QAM64, QAM256, etc.  There are also different freq to check, like high cable.

You may need the drivers.  I had the same experience with my Kworld.  My card was listed and The scan would not lock on a channel until I loaded the firmware and drivers.

If you go into status is your tuner listed as avail?  If it is not you probably need the drivers.

---

### Post by memps001 on 2008-02-24
Yeah, in the tuner card setup, MythTV recognizes that it's a pcHDTV 5500.  I decided that I ought to use QAM-128, as it would generally keep a 100% signal, whereas 256 or 64 would just bounce up and down around 70%.  I used cable, over high cable, since all of the channels I get are between 2 and 21.

And here's a long bit of code that I get when I try to compile the driver:

```
matt@HTPC:~/Desktop/v4l-dvb$ make
make -C /home/matt/Desktop/v4l-dvb/v4l 
make[1]: Entering directory `/home/matt/Desktop/v4l-dvb/v4l'
scripts/make_makefile.pl
creating symbolic links...
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/matt/Desktop/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.o
In file included from /home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:10:
/home/matt/Desktop/v4l-dvb/v4l/flexcop-common.h:11:26: error: linux/config.h: No such file or directory
In file included from /home/matt/Desktop/v4l-dvb/v4l/dmxdev.h:40,
                 from /home/matt/Desktop/v4l-dvb/v4l/flexcop-common.h:20,
                 from /home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:10:
/home/matt/Desktop/v4l-dvb/v4l/dvbdev.h:30:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_irq_check_work':
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:119: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_stream_control':
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:222: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:225: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_init':
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:300: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:300: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:379:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_probe':
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:379: error: 'INIT_WORK' undeclared (first use in this function)
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:379: error: (Each undeclared identifier is reported only once
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:379: error: for each function it appears in.)
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c: At top level:
/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.c:435: fatal error: opening dependency file /home/matt/Desktop/v4l-dvb/v4l/.flexcop-pci.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/matt/Desktop/v4l-dvb/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/home/matt/Desktop/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/matt/Desktop/v4l-dvb/v4l'
make: *** [all] Error 2

```

I'm not experienced enough to know whether this was successful enough, and what I ought to do next.

---

### Post by newlinux on 2008-02-24
I realize this is a cross post with mythtvtalk forums but I post here too...

pchdtv 5500 is supported out of the box with mythbuntu: [https://help.ubuntu.com/community/MythTV/Install/Gutsy/Tuners](https://help.ubuntu.com/community/MythTV/Install/Gutsy/Tuners)

I used to have one before mythbuntu, and even then, all i had to do was load a module. No firmware or drivers from V4L were needed.

Even if your channels are 2-21 on your TV you should still do a full QAM 256 and QAM 64 scan (not just high or low). Where they map to (2-21) and where their QAM frequency is are two different things. Also, make sure you have it setup as a DVB card in mythtv-setup, not as the pchdtv 5500 card (counterintuitive, I know).

Can you tell us specifically how you set it up?  Are you using the analog options?

---

### Post by memps001 on 2008-02-24
Well, I just ran the channel scan again with QAM-256, only this time I let it run all the way through.  Before I was getting impatient when I saw all the "no signal"s popping up.  The scan was able to recognize a few of my channels, so I closed the backend setup, let it run that mythfill database thing, and then opened MythTV.  But when I tried to Watch TV, all I get is a black screen.  And when I try to go back, I get logged out of my ubuntu desktop, and have to log back in to my desktop.

---

### Post by newlinux on 2008-02-24
make sure you have it set to a good channel as your start channel. Some of the stations you tune might just be music stations with no video. Try changing through the stations. Also check your logs when you get the black screen.

---

### Post by memps001 on 2008-02-24
Ok, I set it to start on a channel that it recognized, but now I just get logged out immediately when I try to go to Watch TV.

---

