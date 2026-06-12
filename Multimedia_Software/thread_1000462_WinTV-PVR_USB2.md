---
title: "WinTV-PVR USB2"
date: 2008-12-02
forum: Multimedia Software
---

### Post by TwoEyesOnly on 2008-12-02
Hey guys, just updated the computer from an old k6-2 to a speedy dualcore AMD 5000+ (2.6ghz.)   First time I've been using Ubuntu (8.10 with the latest kernel & software updates) and its really been great, so far.   Just one problem left to figure out.. and that's how to get this WinTV-PVR USB2 unit working.  

Something just isn't right, when I plug it in, the red LED comes on for a just a moment and turns off again.   (this unit model is 24022.)   Here is the dmesg output

[INDENT][  212.204519] usb 5-4: new high speed USB device using ehci_hcd and address 4
[  212.342001] usb 5-4: configuration #1 chosen from 1 choice
[  212.413243] Linux video capture interface: v2.00
[  212.456185] usbcore: registered new interface driver pvrusb2
[  212.456941] pvrusb2: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[  212.456946] pvrusb2: Debug mask is 31 (0x1f)
**[  213.456160] firmware: requesting v4l-pvrusb2-24xxx-01.fw**
[  213.491075] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[  213.511663] usb 5-4: USB disconnect, address 4
**[  213.512102] pvrusb2: Device being rendered inoperable**
[  215.260518] usb 5-4: new high speed USB device using ehci_hcd and address 5
[  215.397596] usb 5-4: configuration #1 chosen from 1 choice
[  215.493726] cx25840' 1-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[  215.553996] tuner' 1-0043: chip found @ 0x86 (pvrusb2_a)
[  215.566353] tda9887 1-0043: creating new instance
[  215.566360] tda9887 1-0043: tda988[5/6/7] found
[  215.597452] tuner' 1-0061: chip found @ 0xc2 (pvrusb2_a)
[  215.602188] wm8775' 1-001b: chip found @ 0x36 (pvrusb2_a)
[  215.628868] tveeprom 1-00a2: Hauppauge model 24022, rev E1A3, serial# 8672151
[  215.628873] tveeprom 1-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[  215.628875] tveeprom 1-00a2: TV standards NTSC(M) (eeprom 0x08)
[  215.628877] tveeprom 1-00a2: audio processor is CX25843 (idx 37)
[  215.628879] tveeprom 1-00a2: decoder processor is CX25843 (idx 30)
[  215.628881] tveeprom 1-00a2: has radio, has IR receiver, has IR transmitter
[  215.628885] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[  215.628888] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[  215.628890] pvrusb2: Setting up 6 unique standard(s)
[  215.628893] pvrusb2: Set up standard idx=0 name=PAL-M
[  215.628895] pvrusb2: Set up standard idx=1 name=PAL-N
[  215.628897] pvrusb2: Set up standard idx=2 name=PAL-Nc
[  215.628898] pvrusb2: Set up standard idx=3 name=NTSC-M
[  215.628900] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[  215.628902] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[  215.628904] pvrusb2: Initial video standard guessed as NTSC-M
[  215.642001] pvrusb2: Device initialization completed successfully.
[  215.642910] pvrusb2: registered device video0 [mpeg]
[  215.643737] pvrusb2: registered device radio0 [mpeg]
[  215.655737] firmware: requesting v4l-cx25840.fw
[  217.838724] cx25840' 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  217.984070] tuner-simple 1-0061: creating new instance
[  217.984080] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  218.052042] cx25840' 1-0044: Video signal:              not present
[  218.052050] cx25840' 1-0044: Detected format:           NTSC-M
[  218.052052] cx25840' 1-0044: Specified standard:        NTSC-M
[  218.052053] cx25840' 1-0044: Specified video input:     Composite 7
[  218.052055] cx25840' 1-0044: Specified audioclock freq: 48000 Hz
[  218.058146] cx25840' 1-0044: Detected audio mode:       forced mode
[  218.058150] cx25840' 1-0044: Detected audio standard:   no detected audio standard
[  218.058152] cx25840' 1-0044: Audio muted:               no
[  218.058154] cx25840' 1-0044: Audio microcontroller:     detecting
[  218.058156] cx25840' 1-0044: Configured audio standard: automatic detection
[  218.058159] cx25840' 1-0044: Configured audio system:   BTSC
[  218.058163] cx25840' 1-0044: Specified audio input:     Tuner (In8)
[  218.058165] cx25840' 1-0044: Preferred audio mode:      stereo
[  218.058167] tda9887 1-0043: Data bytes: b=0x14 c=0x30 e=0x44
[  218.058169] tuner' 1-0061: Tuner mode:      analog TV
[  218.058171] tuner' 1-0061: Frequency:       175.25 MHz
[  218.058174] tuner' 1-0061: Standard:        0x00001000
[  218.058176] wm8775' 1-001b: Input: 2
**[  218.058183] firmware: requesting v4l-cx2341x-enc.fw**[/INDENT]

It seems to load the correct firmware to begin with.. but then "renders it inoperable" (whatever that means.)   And as I highlighted near the bottom it loads up the 2341x firmware .. which obviously isn't correct for the 24022 models.  The /dev/ links to video0 and radio0 still exist but obviously they are not working.

Anybody here have a hunch as to whats happening ?

---

### Post by valpyu on 2008-12-12
The 2.6.27-7 kernel shipped with Intrepid appears to have a number of faults which stop the wintv-pvr-usb2 working.

I had a similar problem (my unit uses different firmware, in the 29xxx series so I can't directly comment on your question about the 2400 series). 

On plugging the unit in, no /dev/video0 device would be created. Also, running 'lsusb' from a terminal to check the device would not result in any output – the terminal would hang.

There is a known kernel bug which causes this – see 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927)

... this was reported for earlier 2.6.27 versions but appears to apply to 2.6.27-7 also.

A workaround for this is described here: 

[http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html](http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html)

..... so I created a file pvrusb2 in directory /etc/modprobe.d/
then put the following line into it:

options pvrusb2 initusbreset=0

I saved the file, rebooted and the wintv-pvr-usb was recognised after it was plugged in (there was now a /dev/video0 device;  lsusb from a terminal reported a Hauppauge device connected – without hanging the terminal)

***WARNING*** a bit of googling suggests this fix may not work for kernels later than 2.6.27-7

The NEXT issue I found was that the 2.6.27-7 kernel support for Video4Linux has been broken by the changes made for V4L2.

VLC no longer recognised the PVR, and would not permit me to change the channel (a message “could not save settings” and no video window opened.

The workaround for this is mentioned here:

[http://ubuntuforums.org/showthread.php?t=976254](http://ubuntuforums.org/showthread.php?t=976254)

I ensured that package libv4l-0 was installed. Then instead of running

vlc


I ran the following command from a terminal

LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so vlc


..... and everything worked, letting me change channels on the PVR to pick up the composite input.

Then, after closing VLC  I could capture video by

cat /dev/video0 > out.mpg

Hope this helps

---

### Post by chrismrutherford on 2008-12-14
Hi, I'd just like to say thanks for this post, doing a google search for "pvrusb2: Device being rendered inoperable" brought me straight here, allowing me to fix the problem really quickly.  Since adding the modprobe option everything works fine.  I must also say that pvrusb2 quality seems better with kernel 2.6.27, so well worth the upgrade from 2.6.18, which I was using previously.  Hopefully Mike will fix the usb problem reset soon.  Chris

---

### Post by saedelaere on 2008-12-30
Just in case somebody is searching for a software to watch tv you could try [this one]("http://ubuntuforums.org/showthread.php?t=763698").

Regards

---

### Post by Mythgruntled on 2009-02-13
> **valpyu said:**
> A workaround for this is described here: 
 
[http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html](http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html)
 
..... so I created a file pvrusb2 in directory /etc/modprobe.d/
then put the following line into it:
 
options pvrusb2 initusbreset=0
 
I saved the file, rebooted and the wintv-pvr-usb was recognised after it was plugged in (there was now a /dev/video0 device; lsusb from a terminal reported a Hauppauge device connected – without hanging the terminal)I was having the same issue as described in that bug report - the box would hang at 'starting bluetooth' on bootup whenever the Hauppauge WinTV-PVR-USB2 was connected.
 
The modprobe.d workaround has fixed this, so the box now boots up and shuts down OK, but I still can't get MythTV Setup to recognise the WinTV-PVR-USB2.
 
In Capture Card Setup when I select "MPEG-2 encoder card (PVR-x50, PVR-500)" the Probed Info says "Failed to open" even if I manually type "/dev/video0" in for the Video Device.
 
I'm no expert, but the output of [FONT=Courier New]lsmod | grep pvrusb2[/FONT] looks OK to me, as does [FONT=Courier New]dmesg | grep pvr[/FONT] which results in this:
 
[ 10.840626] usbcore: registered new interface driver pvrusb2
[ 10.840673] pvrusb2: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[ 10.840677] pvrusb2: Debug mask is 31 (0x1f)
[ 10.841225] firmware: requesting v4l-pvrusb2-29xxx-01.fw
[ 13.060781] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[ 13.074350] pvrusb2: Device being rendered inoperable
[ 15.120940] msp3400' 0-0040: MSP3415G-B8 found @ 0x80 (pvrusb2_a)
[ 15.196467] saa7115' 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[ 15.434973] tuner' 0-0043: chip found @ 0x86 (pvrusb2_a)
[ 15.491866] tuner' 0-0061: chip found @ 0xc2 (pvrusb2_a)
[ 15.519625] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[ 15.519631] pvrusb2: Mapping standards mask=0xff00ff (PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K1/L/LC)
[ 15.519635] pvrusb2: Setting up 20 unique standard(s)
[ 15.519640] pvrusb2: Set up standard idx=0 name=PAL-B/G
[ 15.519643] pvrusb2: Set up standard idx=1 name=PAL-D/K
[ 15.519646] pvrusb2: Set up standard idx=2 name=SECAM-B/G
[ 15.519649] pvrusb2: Set up standard idx=3 name=SECAM-D/K
[ 15.519652] pvrusb2: Set up standard idx=4 name=PAL-B
[ 15.519656] pvrusb2: Set up standard idx=5 name=PAL-B1
[ 15.519659] pvrusb2: Set up standard idx=6 name=PAL-G
[ 15.519661] pvrusb2: Set up standard idx=7 name=PAL-H
[ 15.519664] pvrusb2: Set up standard idx=8 name=PAL-I
[ 15.519667] pvrusb2: Set up standard idx=9 name=PAL-D
[ 15.519670] pvrusb2: Set up standard idx=10 name=PAL-D1
[ 15.519673] pvrusb2: Set up standard idx=11 name=PAL-K
[ 15.519677] pvrusb2: Set up standard idx=12 name=SECAM-B
[ 15.519680] pvrusb2: Set up standard idx=13 name=SECAM-D
[ 15.519683] pvrusb2: Set up standard idx=14 name=SECAM-G
[ 15.519686] pvrusb2: Set up standard idx=15 name=SECAM-H
[ 15.519689] pvrusb2: Set up standard idx=16 name=SECAM-K
[ 15.519692] pvrusb2: Set up standard idx=17 name=SECAM-K1
[ 15.519695] pvrusb2: Set up standard idx=18 name=SECAM-L
[ 15.519698] pvrusb2: Set up standard idx=19 name=SECAM-LC
[ 15.519701] pvrusb2: Initial video standard auto-selected to PAL-B/G
[ 15.519711] pvrusb2: Device initialization completed successfully.
[ 15.519892] pvrusb2: registered device video0 [mpeg]
[ 15.519937] pvrusb2: registered device radio0 [mpeg]
 
so the device at least *looks* to me like it's being registered as video0.
 
From what I've read, no additional drivers should be required to be installed in Intrepid to get the WinTV-PVR-USB2 to work. So I've hit a brick wall. I don't know what to try next. Any suggestions would be much appreciated.

---

### Post by Dono on 2009-02-14
On my system, Mythbuntu fails to provide root access to the mythtv-setup program, when accessed via the menus. Because of this, you are not able to access the device.

Open a terminal, do a 'sudo mythtv-setup' instead and I suspect you will find the device is now recognized.

Cheers.

---

### Post by Mythgruntled on 2009-02-14
> **Dono said:**
> On my system, Mythbuntu fails to provide root access to the mythtv-setup program, when accessed via the menus. Because of this, you are not able to access the device.
 
Open a terminal, do a 'sudo mythtv-setup' instead and I suspect you will find the device is now recognized.
 
Cheers.That worked brilliantly, Dono, thank you so much! I note that was your first post, too :P
 
After I did 'sudo mythtv-setup' there was a popup that said "You must be a member of the mythtv group before starting any mythtv applications. Would you like to automatically be added to the group?"
 
Pressing OK to that brought up another popup that said "For the changes to take effect, your current login session will have to be restarted. Save all work and then press OK to restart your session."
 
I then did 'sudo mythtv-setup' again, and went to add a capture card. I did have to manually type /dev/video1 into the Video Device field, but after that, the Probed Info field said "WinTV USB2 Model Category 2".
 
It's odd how I was able to easily add my DVB capture card without having to worry about sudo access, yet sudo is required for the Hauppauge USB device.
 
I would never have guessed this by myself, so thank you once again.

---

### Post by LarryJ2 on 2009-02-14
This may not apply to all situations described here but on my pvrusb2,  in MythSetup,  I always get a "failed to open" after selecting an mpeg encoder.   I just ignore that and type in "/dev/video0" (The usb Wintv unit is my only mpeg encoder, if you haave more than one you might need to use /dev/video1 or /dev/video2 etc) .  Then the message about WinTVPVRusb2 "recognized" magically shows up in the mythsetup screen.


Larry

---

### Post by bb_145 on 2009-02-15
Just so you are aware, I updated my system with all the recommended updates a couple of days ago, and my winTV-PVR-USB card disappeared from the system.  

In the end, I had to remove  the "options pvrusb2 initusbreset=0".  Apparently there was a kernel update, and initusbreset doesn't work anymore and using it prevents the driver from loading.  Fortunately at the same time the original problem was fixed and it is no longer needed.:)

---

### Post by Mythgruntled on 2009-02-15
> **bb_145 said:**
> Just so you are aware, I updated my system with all the recommended updates a couple of days ago, and my winTV-PVR-USB card disappeared from the system. 
 
In the end, I had to remove the "options pvrusb2 initusbreset=0". Apparently there was a kernel update, and initusbreset doesn't work anymore and using it prevents the driver from loading. Fortunately at the same time the original problem was fixed and it is no longer needed.:)Thanks for that, bb_145, I'll bear it in mind if I update the system - but that brings me to another topic, which is Off Topic, because it's about a problem I had after I updated the system, but it's not with regard to the PVR-USB2. So I will send you a PM about it instead.

---

### Post by markackerman8@gmail.com on 2010-04-17
I am trying my fourth!! Tuner card to get analog cable working with MythTV. I have done everything in the Mythtv/WinTV-PVR-USB2 SITE and [http://www.isely.net/pvrusb2](http://www.isely.net/pvrusb2), but still NO LUCK when I select "watch tv".

Has anyone got this to work (its 4 years old and reported to work with mythtv, so I would hope so), and help me troubleshoot?

My dmesg compared to a known working one is identical with the exception of any mention of cx88XX? Does this mean anything here is my dmesg, and I surely promise replies to any responses,

thanks so much in advance. 

here is my dmesg
[ 3801.440277] usb 2-5.1: new high speed USB device using ehci_hcd and address 10
[ 3801.554934] usb 2-5.1: configuration #1 chosen from 1 choice
[ 3801.555176] pvrusb2: Hardware description: WinTV PVR USB2 Model 24xxx
[ 3802.552728] usb 2-5.1: firmware: requesting v4l-pvrusb2-24xxx-01.fw
[ 3802.559082] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[ 3802.741960] usb 2-5.1: USB disconnect, address 10
[ 3802.742201] pvrusb2: Device being rendered inoperable
[ 3804.512940] usb 2-5.1: new high speed USB device using ehci_hcd and address 11
[ 3804.625054] usb 2-5.1: configuration #1 chosen from 1 choice
[ 3804.626000] pvrusb2: Hardware description: WinTV PVR USB2 Model 24xxx
[ 3804.647299] pvrusb2: Binding ir_video to i2c address 0x18.
[ 3804.653483] cx25840 0-0044: cx25843-23 found @ 0x88 (pvrusb2_a)
[ 3804.654433] pvrusb2: Attached sub-driver cx25840
[ 3804.685854] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[ 3804.685866] pvrusb2: Attached sub-driver tuner
[ 3804.689778] wm8775 0-001b: chip found @ 0x36 (pvrusb2_a)
[ 3804.697949] pvrusb2: Attached sub-driver wm8775
[ 3804.707331] tuner 0-0043: chip found @ 0x86 (pvrusb2_a)
[ 3804.707412] tda9887 0-0043: creating new instance
[ 3804.707414] tda9887 0-0043: tda988[5/6/7] found
[ 3804.708218] pvrusb2: Attached sub-driver tuner
[ 3804.721548] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
[ 3806.920308] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 3807.024546] tveeprom 0-00a2: Hauppauge model 24012, rev D3A3, serial# 8596551
[ 3807.024554] tveeprom 0-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[ 3807.024560] tveeprom 0-00a2: TV standards NTSC(M) (eeprom 0x08)
[ 3807.024566] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[ 3807.024570] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[ 3807.024575] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[ 3807.024586] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[ 3807.024594] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)

---

### Post by muaythaimaster74 on 2010-04-17
Have you tried tv-viewer?

[http://sourceforge.net/projects/tv-viewer/](http://sourceforge.net/projects/tv-viewer/)

---

### Post by markackerman8@gmail.com on 2010-04-19
> **muaythaimaster74 said:**
> Have you tried tv-viewer?
[http://sourceforge.net/projects/tv-viewer/](http://sourceforge.net/projects/tv-viewer/)

Well, just an update.  I have for the first time had MythTV viewing Analog Cable, after 15 months of trying 4 different tuner cards!  

At this point Mythtv channels are often jittery, and I am thinking it may be best as a PVR and not live tv, so I have tried to install tv-viewer.  But so far no luck.  

I have installed tk/tcl8.5 (no easy task), and TV-viewer and it recognises my card but won't play anything.  It might be that I couldn't install tkimg, any suggestions?

Bu7t thank goodness for small miracles, I thought I might never see the day, I have for the first time in my life just paused a TV program while writing this.

And for those that want to know what made my card functional with MythTV, hmmmm not sure, but here are a few things that I did before it started to work.
1/ reinstalled the v4l-dvb drivers
2/ Copied the firmware images to the appropriate location
  &#8227; sudo cp *.fw /lib/firmware/2.6.3*.**-generic/
  &#8227; On Debian systems, viable locations include:
  • /lib/firmware
  • /usr/local/lib/firmware
  • /usr/lib/hotplug/firmware
3/ Upgraded to the newest stable linux kernel 2.6.33

I sure hope this can help someone!

---

