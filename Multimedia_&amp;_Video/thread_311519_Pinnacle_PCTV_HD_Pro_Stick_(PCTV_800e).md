---
title: "Pinnacle PCTV HD Pro Stick (PCTV 800e)"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by padan on 2006-12-03
I just obtained one of these devices and I would love to get it working on my laptop which is running ubuntu edgy.  I have been looking at: [http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php](http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php) , however, when I fire up Kaffine it doesn't detect any DVB devices.  The module loads into the kernel just fine and shows up with lsusb as :

Bus 005 Device 002: ID 2304:0227 Pinnacle Systems, Inc. [hex] 

I have installed all the packages listed on the above website, is there anything else I am missing?  Perhaps Kaffine isn't working properly, does anyone know of an alternate dvb capable device that I could give a shot at?  Has anyone got this device to work properly?

---

### Post by gr33kdude on 2006-12-25
hey padan i got the same device for christmas and was wondering how to use it as well
xawtv nor tvtime work with it either

---

### Post by bucksgt on 2007-01-06
i have the same issue. i'll continue researching and see if we can get this damn thing to work.

-qk.

---

### Post by bucksgt on 2007-01-06
[http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/](http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/)

this got normal tv working for me in XawTV. i'm still trying to get kaffinne working right for digi.

-qk.

---

### Post by gr33kdude on 2007-01-20
it works for me now, thanks for that tutorial link bucksgt.
i'm using tvtime, and its good, but whenever i use it, i get this annoying green stuff at the top, and i can't get sound either.

---

### Post by Bashed on 2007-05-09
I followed this tutorial myself:
[http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/](http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/)

But on step 6 I get this:

root@Secured:/usr/src# hg clone [http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel](http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel)
destination directory: v4l-dvb-kernel
abort: 'http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel' does not appear to be an hg repository!

---

### Post by bucksgt on 2007-05-09
try:
  [http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel-history](http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel-history)
or:
  [http://linuxtv.org/hg/~mrechberger/v4l-dvb-stable](http://linuxtv.org/hg/~mrechberger/v4l-dvb-stable)
or:
  [http://linuxtv.org/hg/~mrechberger/v4l-dvb-usb1](http://linuxtv.org/hg/~mrechberger/v4l-dvb-usb1)
  
i've since switched to a hauppauge pvr-500 and it's worth every penny. works awesome with mythtv and ubuntu.

good luck with hd pro stick of crap.

-qk.

---

### Post by Bashed on 2007-05-09
If there is anyone else kind and mature, not sarcastic that can help that would be great.

I'm getting these errors:

had@Secured:/usr/src/v4l-dvb-kernel-history$ sudo make
make -C /usr/src/v4l-dvb-kernel-history/v4l 
make[1]: Entering directory `/usr/src/v4l-dvb-kernel-history/v4l'
scripts/make_makefile.pl
No version yet.
Updating/Creating .config
Preparing to compile for kernel version 2.6.20

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_PLANB: Requires at least kernel 2.6.99
VIDEO_ZR36120: Requires at least kernel 2.6.99
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/usr/src/v4l-dvb-kernel-history/v4l'
make[1]: Entering directory `/usr/src/v4l-dvb-kernel-history/v4l'
creating symbolic links...
ln -sf . oss
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/v4l-dvb-kernel-history/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.o
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_irq_check_work':
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:119: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_stream_control':
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:226: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:229: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_probe':
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: 'INIT_WORK' undeclared (first use in this function)
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: (Each undeclared identifier is reported only once
/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: for each function it appears in.)
make[3]: *** [/usr/src/v4l-dvb-kernel-history/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb-kernel-history/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb-kernel-history/v4l'
make: *** [all] Error 2

---

### Post by cowboyenvy on 2008-02-06
I have the pctv 800e Pro stick,

I do have scratchy audio, and video with a line on the top of the screen. I'm running MythTV.

Has anyone had any luck with this device and MythTV?

Kevin

---

### Post by RC Howe on 2008-02-24
TalkJesus, did you run ./configure, and do you have build-essential installed?

You may also want to try ```
sudo apt-get install linux-headers-`(uname -r)`
```

---

### Post by xefialtis on 2008-05-25
I cannot believe that these things are so buggy...
I have the same thing, and I have followed the instructions on the following web sites...
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
and
[http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/](http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/)
(as well as I could) 

But I am finding that things just aren't working right.
The dmesg gives me all kinds of info, but it does not assign the device in /dev (no dvb in /dev)
It also says "Your board has no eeprom inside it and thus can't be autodetected. Please pass card=<n> insmod option to workaround that."
Only, I try insmod em28xx card=47, but I get an error (even when using "sudo") "error inserting 'em28xx': -1 Invalid module format"

Also, I try the "scan ..." command, but I am in the USA, and there isn't an en-USA frequency file...but even if there were, I get an error "can't open /dev/dvb/adapter0/frontend0" because there isn't a /dev/dvb...

Everything else went off without error or incident...

So Kaffeine doesn't recognize the device, but Xine does, only it cannot get the channel listing, because of the above...

So, really, I think I have one issue...getting the device fully recognized...

Any suggestions on where to start?

---

