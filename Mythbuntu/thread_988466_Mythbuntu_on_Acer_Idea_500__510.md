---
title: "Mythbuntu on Acer Idea 500 / 510"
date: 2008-11-20
forum: Mythbuntu
---

### Post by xpress on 2008-11-20
I have an Acer Idea 500 which I have installed Mythbuntu on.

The receiver for the remote does not seem to work out of the box.
The receiver is however compatible with the lirc_mceusb2 driver, it just lacks the correct usb vid and pid in the list.
With the following changes to the /drivers/lirc_mceusb2/lirc_mceusb2.c the receiver works.

You need to download the sources to lirc and recompile it.
The new kernel module is put in /lib/modules/2.6.27-7-generic/misc/lirc_mceusb2.ko
This needs to be moved to /lib/modules/2.6.27-7-generic/kernel/ubuntu/lirc/lirc_mceusb2/

Additions to lirc_mceusb2.c :

-----------------------------------------------------------------------

/* Added Wistron vendor id */
#define VENDOR_WISTRON          0x0fb8


/* Added new entry for the Wistron receiver in the Acer Idea 500  */

/* Wistron Corp. eHome Infrared Receiver */
{ USB_DEVICE(VENDOR_WISTRON, 0x0002) },

-----------------------------------------------------------------------

See attachment for full file.

---

### Post by tgm4883 on 2008-11-21
please file a bug at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)

Also, how well does Mythbuntu work on this device?  What features of the device have you tried to use?

---

### Post by xpress on 2008-11-22
I did send an email to the maintainer of lirc so hopefully the receiver will be included in the next release of lirc.

I have not tried to use a lot of the features yet. It has got the intel 945 gma chipset so the graphics seem to work ok.
When I installed it the database for mythtv wasn't populated correctly but that is probably not hardware dependent.

There was also a problem with setting the TV resolution to 640x480 (yes, crap tv) but keeping the resolution for the DVI to 1280x1024.
Can you specify to run mythtv on one screen, the TV, and keep another bigger screen for when you plug a monitor in.

The tuners are detected by the kernel but I have not yet tried to use them in mythtv.

---

### Post by tgm4883 on 2008-11-22
> **xpress said:**
> I did send an email to the maintainer of lirc so hopefully the receiver will be included in the next release of lirc.

I have not tried to use a lot of the features yet. It has got the intel 945 gma chipset so the graphics seem to work ok.
When I installed it the database for mythtv wasn't populated correctly but that is probably not hardware dependent.

There was also a problem with setting the TV resolution to 640x480 (yes, crap tv) but keeping the resolution for the DVI to 1280x1024.
Can you specify to run mythtv on one screen, the TV, and keep another bigger screen for when you plug a monitor in.

The tuners are detected by the kernel but I have not yet tried to use them in mythtv.

Which disk did you use to install Mythbuntu?

I believe there is a way to do dual screen setups, whether the specs of the device would allow that i'm not sure.

Let us know how well the tuners work.

---

### Post by tgm4883 on 2008-11-22
also, if you could post the output of "lspci" maybe we can see what tuners this thing has

---

### Post by xpress on 2008-11-24
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by xpress on 2008-11-24
I can setup the screens manually to two different desktops. I was just wondering whether I could make MythTV default to the second screen i.e. the TV while keeping a bigger desktop for when I plug my monitor in. I only do that to configure the system, normally only the TV will be plugged in.

---

### Post by tgm4883 on 2008-11-24
this might help with your tuners  [http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

---

### Post by spf on 2009-06-07
Hi, just curious if anyone managed to get the "acer aspire idea" working with mythtv?  I've been trying for several weeks now, and slowly getting there, but unable to get the tuners working. Analog works fine outside myth e.g. cat /dev/video0 | "SOMEVIDEOPLAYER", but I'd really like to get dvb-t working (PAL). My "PlayTV PS3" tuner works in myth, so I've been able to play with some of the features but I'd now like to give this back to my kids for their PS3! and use the ACER internal tuners. Alternatively, can someone recommed a V4L supported mini-pci tuner card for UK DVB-T?

---

### Post by xpress on 2009-11-15
I have not tried to get the tuners working, in the end I went for a standard Ubuntu install with XBMC as frontend.
With Ubuntu 9.10 most of the stuff I'm using works pretty much out of the box.

If you want to enable the digital sound optical or coax, you need to change one of the config files. The information for the Acer Idea does not match, the driver does not enable anything but stereo.

If you want to make the vfd display work, let me know. It takes a bit of hacking at the moment.

---

### Post by francesco_r on 2010-01-10
> **xpress said:**
> 
If you want to make the vfd display work, let me know. It takes a bit of hacking at the moment.
I have installed Karmic on Idea 500 with XBMC/TVHeadend and works very well but i didn't find any info for the VFD. Which driver you used in LCDProc?
I see that the display is seen as USB device:
```
 idVendor           0x0fb8 Wistron Corp.
  idProduct          0x0010
  bcdDevice            0.10
  iManufacturer           1 Wistron Corp.
  iProduct                2 Media Center VFD Display

```and i found this patch ([http://lists.omnipotent.net/pipermail/lcdproc/2009-January/012565.html](http://lists.omnipotent.net/pipermail/lcdproc/2009-January/012565.html)) with a native driver for LCDProc but the kernel module is absent.
Can you point me in the right direction?
Thank you

---

### Post by xpress on 2010-01-11
The kernel driver does not compile on karmic due to some deprecated defines. I will have a look at it after work to see if I can get it working again.

---

### Post by xpress on 2010-01-11
I've tried to fix the errors, I am attaching the source to the module.

Unzip somewhere on your drive.
To compile just run make in the directory.
that should create a acer_idea_vfd.ko file
check your  kernel version with 'uname -a'
copy the file to somewhere under /lib/modules/<kernel version>/kernel
Example: 'sudo cp acer_idea_vfd.ko /lib/modules/2.6.31-17-generic/kernel/ubuntu/misc/'
run depmod
Example: 'sudo depmod /lib/modules/2.6.31-17-generic/kernel/ubuntu/misc/acer_idea_vfd.ko'
run modprobe to load the module
run 'lsmod' or 'lsmod | grep acer' to check the module is loaded
check /dev/ for an lcd0 device with 'ls /dev/lcd*'
Test the display with 'echo "Test" > /dev/lcd0'

---

### Post by francesco_r on 2010-01-12
Thank you Erik!
Installed and worked immediately with the imon driver from lcdproc. What are the differences between your lcdproc module posted in the mailing list and the imon?
Why your work was not merged in the official package?

Thank's again
Francesco

---

### Post by xpress on 2010-01-13
The reason for a separate driver was some extra functionality, I think there is a volume bar in the display and some non standard icons. The text should work with the text- or imon-driver in lcdproc.

The kernel driver should really go with the linux kernel to keep it updated with API changes. I sort of lost interest once I had it running.

I noticed the VID/PID for the IR reciever had been included in lirc on Karmic so that should work out of the box now.

---

### Post by spf on 2010-04-09
Hi,
    just to close my previous question down: I do have mythtv working 100% now on my acer idea, including tuners etc etc. I had a LOT of help from the v4l team but the latest releases of myth/ubuntu (0.22/9.10) include these changes and work fine.


 I do NOT have the VFD working, as I just saw your post. I'll try it out this weekend.

Thanks
spf

---

### Post by tgm4883 on 2010-04-09
> **spf said:**
> Hi,
    just to close my previous question down: I do have mythtv working 100% now on my acer idea, including tuners etc etc. I had a LOT of help from the v4l team but the latest releases of myth/ubuntu (0.22/9.10) include these changes and work fine.

 I do NOT have the VFD working, as I just saw your post. I'll try it out this weekend.

Thanks
spf

Thats good to hear. Any additional tweaking you have to do to get Mythbuntu to run on there? Does it do HD?

---

### Post by spf on 2010-04-26
> **tgm4883 said:**
> Thats good to hear. Any additional tweaking you have to do to get Mythbuntu to run on there? Does it do HD?

I've not tried to do an install via MythBuntu, as I've had problems in the past with the install menus. I have only tried a seperate Kubuntu + Myth install. No other tweaks were necessary EXCEPT manual inclusion of lirc files if you want the remote to work. And if you want a dual-boot machine (as I have) then you'll need to be careful with the initial disk partitioning.

Your question about HD is a little more complicated.....

Backend HD
--------------
I live in UK, so DVB-HD is only transmitted as DVB-T2 or DVB-S2. The ACER only has DVB-T(1) tuners. I understand that some countries transmit HD on DVB-T(1) e.g France and Australia, so it may be possible to get HD in these countries on the ACER, but I am unable to try this out. This is the same story as happened with PlayTV on the Sony PS3: Australia can get HD TV with the existing tuner hardware and a simple software patch, the uk cannot.

Summary of BE: Maybe ? depending on where you live. For UK no.

Frontend HD (tricky answer)
----------------------------------
Using a seperate BE with a DVB-S2 (satellite) card I can just about get HD playback, however, it stutters for a fraction of a second every 3-4  seconds, so the simple answer is "no".

     DVB-S2 is transmitted here in H264 format and afaik xvmc doesn't support this, so I'm unable to get any benefit from the hardware acceleration. Some countries (USA?) transmit HD in MPEG2 format, and thus HD FE may work in these countries, but I'm just speculating. 
  
      I see rumours that xvmc may include h264 at some point  (possibly via libva), but it's not clear to me when/what/how. So without hardware acceleration HD-FE struggles, ironically the xvmc hardware acceleration works for SD (MPEG2), but isn't needed. The CPU usage drops from ~40% to ~15% as I toggle xvmc SD hardware acceleration off/on respectively.

   During HD playback the CPU hits 100% and stays there! Maybe the 510i had a better processor? Mine is the T2300 1.66GHz. I'm surprised that it's even as good as it is.

 One trick that seems to help is to turn off the sound buffering (I have no idea why!), HD is then "almost" watchable and almost-stutter-free, though the sound is very poor! I'm able to get sound from another TV in the same room, this is tolerable, but not really a proper solution. 

Summary of FE: Maybe on the 510i (T2600 CPU)?, or if/when some hardware acceleration is possible of H264, or maybe it's already possible in US?

BluRay
---------
 I'm not sure which HD FE sources you are thinking of using, other than live-tv but for example BluRay installed as e.g. an external drive would never work. The datarate for bluray can be as high as 40M (compared with 15->20M for live tv) as you can see from above, even at live-tv datarates the Acer 500 isn't really upto the job.

---

### Post by spf on 2010-04-28
> **tgm4883 said:**
> Thats good to hear. Any additional tweaking you have to do to get Mythbuntu to run on there? Does it do HD?

 Hi, What else do I need to get the VFD working "properly": I can echo "Hello World" using your driver patch but I can't seem to divert "real" myth status to it. Do I need to change some other files?

---

### Post by tgm4883 on 2010-04-28
> **spf said:**
> Hi, What else do I need to get the VFD working "properly": I can echo "Hello World" using your driver patch but I can't seem to divert "real" myth status to it. Do I need to change some other files?

I have a driver patch for that? News to me.

---

### Post by spf on 2010-04-29
> **tgm4883 said:**
> I have a driver patch for that? News to me.

Whoops, sorry, too many tabs open in Firefox +  too little sleep = wrong person, wrong thread.

---

### Post by MarcAngelo on 2012-07-15
Hey xpress,

I hope you can help me out.
I'm using an Acer Aspire Idea 500 in combination with XBMCBuntu.
(XBMC distro 11.0 "Eden").

I have everything working, except for the VFD display (Wistron Corp.).

I tried to compile your driver, but no luck so far.
I get the following messages, when I run the "make" command:

------------
# make
make -C /lib/modules/3.0.0-20-generic/build SUBDIRS=/usr/src/acer_idea_vfd/module modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-20-generic'
  CC [M]  /usr/src/acer_idea_vfd/module/acer_idea_vfd.o
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:139:8: warning: type defaults to âintâ in declaration of âDECLARE_MUTEXâ [-Wimplicit-int]
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:139:1: warning: parameter names (without types) in function declaration [enabled by default]
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c: In function âacer_idea_vfd_openâ:
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:260:9: error: âdisconnect_semâ undeclared (first use in this function)
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:260:9: note: each undeclared identifier is reported only once for each function it appears in
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c: In function âdevice_probeâ:
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:544:3: error: implicit declaration of function âinit_MUTEXâ [-Werror=implicit-function-declaration]
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c: In function âdevice_disconnectâ:
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:588:9: error: âdisconnect_semâ undeclared (first use in this function)
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c: At top level:
/usr/src/acer_idea_vfd/module/acer_idea_vfd.c:139:8: warning: âDECLARE_MUTEXâ declared âstaticâ but never defined [-Wunused-function]
cc1: some warnings being treated as errors

make[2]: *** [/usr/src/acer_idea_vfd/module/acer_idea_vfd.o] Error 1
make[1]: *** [_module_/usr/src/acer_idea_vfd/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-20-generic'
make: *** [default] Error 2
------------

Could you point me in the right direction, to get the driver compiled?

Thanks in advance for your help!!

Marc

---

### Post by tgm4883 on 2012-07-15
Please look at the age of the thread before posting. This thread is over 2 years old. Closing for Necromancy.

---

