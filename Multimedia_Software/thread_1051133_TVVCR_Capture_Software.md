---
title: "TV/VCR Capture Software"
date: 2009-01-26
forum: Multimedia Software
---

### Post by ronchi on 2009-01-26
I have a Hauppauge WinTV-HVR-1800 card on 8.10.  The card appears to be recognized by Ubuntu.  However, I'm having trouble getting anything out of the card at all.  I'm aware of MythTV and Mythbuntu (the latter of which didn't find the card).  However, I don't need all those capabilities/complexities.  Instead, all that I want to do is capture the video/sound coming out of a VCR and a DVR and put those files into something that I can burn into a DVD.  

Is there a software application (or better yet a good website with instructions)?  I would be happy just to have the VCR conversion as there are many family films that I want to digitize.

FYI, the results of  dmesg | grep tv are:
[   15.731642] tveeprom 2-0050: Hauppauge model 78521, rev C1E9, serial# 4876695
[   15.731645] tveeprom 2-0050: MAC address is 00-0D-FE-4A-69-97
[   15.731648] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   15.731651] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   15.731654] tveeprom 2-0050: audio processor is CX23887 (idx 42)
[   15.731656] tveeprom 2-0050: decoder processor is CX23887 (idx 37)
[   15.731658] tveeprom 2-0050: has radio

---

### Post by ronchi on 2009-01-26
By the way, if you were going to suggest Zapping (the TV Viewer software for Gnome), it gives a segmentation fault on startup on 8.10 (amd64).

---

### Post by Macintosh SE on 2009-01-26
Did you verify that the card works by testing:
```
cat /dev/video0 > test.mpg
```

Do control-C to stop recording, and open the file. If it plays TV, the card works.

Once you have verified this, you can use a simple shell script that I wrote to capture from VHS tapes (I have done this before using a PVR-150 MCE TV tuner):
```

# SHELL SCRIPT FOR VCR-TO-DVD CONVERSION
#!/bin/bash
printf "%s\n" "< VHS copier > "
ivtv-tune -c 3
printf "ENTER to begin recording, ctrl-C to stop"
read ENTER
DATE=`date +%I%M%p`
echo "Recording started at $DATE "
cat /dev/video0 > /media/Television/VHS/VHS_$DATE.mpg
```

Paste this into your text editor and save it as something like vcr.sh. To run it from your home directory, type in a terminal window:
```
bash vcr.sh
```

This shell script assumes that your VCR is connected via coax cable to your TV tuner, and set to output on channel 3.

I've also written another shell script for scheduling TV recordings like a DVR. If you want, I'll post the code for it here.

---

### Post by ronchi on 2009-01-27
I set the output for the VCR to Channel 3.  Still no joy on the card.  The test.mpg file was large enough, but none of the players (KPlayer, mplayer, etc.) could read the file.  The error messages were along the lines of "Couldn't determine stream".

---

### Post by Macintosh SE on 2009-01-27
That's odd. What does your .ivtv-tune file (a hidden file in your home folder) look like?

---

### Post by ronchi on 2009-01-27
There is no .ivtv-tune file.  Incidentally, I already have the latest version if ivtv-utils installed.

---

### Post by Macintosh SE on 2009-01-27
> **ronchi said:**
> There is no .ivtv-tune file.  Incidentally, I already have the latest version if ivtv-utils installed.

That's bizarre. This could be your problem. Try using mine:
```
device /dev/video0
freqtable us-cable
```

Paste this into your text editor and save it as .ivtv-tune in your home directory. It specifies the device and channel frequency table to use.

---

### Post by ronchi on 2009-01-27
I added the code to the ~/.ivtv-tune file.  Still no luck after a cat /dev/video0 > test.mpg

Here is the output from KPlayer...

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.
Playing /home/ronc/test.mpg.
ID_VIDEO_ID=0
Exiting... (End of file)

---

### Post by ronchi on 2009-01-27
For extra diagnostic information, here are some partial results from lspci:

05:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
07:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)


I've read several threads that point out problems between the Hauppauge cards and nVidia cards.  Could this be part of the problem.  

Secondly, do I need to download/compile/install v4l-dvb?  Most of the v4l options in Synaptic have already been installed.

Do I need the cx18 driver installed?

---

### Post by ronchi on 2009-02-17
Okay, I think many of my problems were the result of using a 64-bit version of Ubuntu.  I dual booted the box by adding a new partition and installed a 32-bit version of 8.10 onto that.  Installed all the software (including v4l) and now get (for dmesg | grep tv), the following:

[   16.671941] tveeprom 2-0050: Hauppauge model 78521, rev C1E9, serial# 4876695
[   16.671945] tveeprom 2-0050: MAC address is 00-0D-FE-4A-69-97
[   16.671948] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   16.671951] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   16.671954] tveeprom 2-0050: audio processor is CX23887 (idx 42)
[   16.671957] tveeprom 2-0050: decoder processor is CX23887 (idx 37)
[   16.671960] tveeprom 2-0050: has radio
[   28.596034] bttv: driver version 0.9.17 loaded
[   28.596043] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   28.679582] ivtv:  Start initialization, version 1.4.0
[   28.679634] ivtv:  End initialization


Zapper works (on the 32-bit system.  However, still no joy.  Upon startup, Zapper comes up with a few error messages ("Cannot restore previous mode"; and "Cannot state capturing: /build/buildd/zapping-0.10~cvs6/src/tveng25.c:map_xbuffers:2578: ioctl VIDIOC_REQBUFS failed: 0, Success").  I've Googled around, but haven't found this same error message anywhere.  Strange...

The PC is able to see/utilize the card via Vista (Ultimate), so I know the card works.  The problem with Vista is that the WinTV utility is not stable.  It has trouble recording programs longer than about 25 minutes.

---

### Post by ronchi on 2009-02-17
By the way, Zapper gives one additional error message...

"Cannot open '/dev/vbi0': 2, No such file or directory"

This begs the question as to whether the output from the video card is going to /dev/video0.  Should I look for the stream elsewhere?

---

### Post by ronchi on 2009-02-17
By way of diagnostics, I looked up the Preferences for Zapper, and found the Device name to be correct (Hauppage WinTV-HVR1800) with the Current controller set to Video4Linux 2 and the Device file to be set to /dev/video0, so I don't know why Zapper was coming up with that third aforementioned error message.

---

### Post by ronchi on 2009-02-17
The /dev/vibi0 is the setting for the Kernel device.  Any idea what that should be set to?  Doesn't seem right to create a file /dev/vibi0 for this purpose.

---

### Post by ronchi on 2009-02-17
tvtime works, to some extent.  The picture is there, but it is in black and white -- without sound.

---

### Post by ronchi on 2009-02-17
I seem to have everything working.  I just can't get VLC (or anything else) to lock into the signal.  Supposedly the device is /dev/video0 (and I can't seem to figure out where the audio signal is coming from).  The actual source is using S-Video (composite?).  Does anyone know how to take the final steps to getting the signal?  There is something elusive that I'm missing.  ivtv-tune isn't much help.

---

### Post by maczilla on 2009-03-03
You want to use /dev/video1. That is the muxed mpeg2 output for the first tuner, /dev/video0 is the raw feed. /dev/video2 is the raw feed from the second tuner and /dev/video3 is the muxed mpeg2 output from the second tuner.  Neither /dev/video0 or /dev/video2 have sound. The digital tuners show up under /dev/dvb/. You may need to issue 'modprobe tuner' to get it working.

I have the card working on the analog side by tuning with tvtime and watching with mplayer. I haven't managed to get it working with anything else yet.

---

### Post by saedelaere on 2009-03-04
> **maczilla said:**
> You want to use /dev/video1. That is the muxed mpeg2 output for the first tuner, /dev/video0 is the raw feed. /dev/video2 is the raw feed from the second tuner and /dev/video3 is the muxed mpeg2 output from the second tuner.  Neither /dev/video0 or /dev/video2 have sound. The digital tuners show up under /dev/dvb/. You may need to issue 'modprobe tuner' to get it working.

I have the card working on the analog side by tuning with tvtime and watching with mplayer. I haven't managed to get it working with anything else yet.

You could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html") to get the analog part to work.

Oh and you should try the latest alpha. The last stable version won't work.

---

### Post by ronchi on 2009-03-04
Much better.  Almost there.  I now have color video, but still no sound.  Any hint as to what the problem with the sound could be?

---

### Post by ronchi on 2009-03-06
By the way, I know that the card is wired correctly to the dvr because the sound (and video) works in Vista.  Before you ask me why I just don't use Vista, the answer is the Hauppage WinTV software craps out after about one hour of taping, and requires a reboot.

---

### Post by ronchi on 2009-03-06
Here is the result of an lspci -vvv for the Hauppage card...

05:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
	Subsystem: Hauppauge computer works Inc. Device 7801
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdc00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

---

### Post by peter72 on 2012-11-23
I know this thread is a few years old, but I've been converting my old vhs-c tapes to video using an old vcr and a BT878 capture card (old ATI-TV PCI card).  I've found so far this is the best config:

```
date ; mencoder tv:// -tv channel=1:driver=v4l2:device=/dev/video0:normid=0:input=1:chanlist=us-cable:alsa:adevice=hw.0:brightness=0:contrast=0:hue=0:saturation=0 -vf pp=lb -oac mp3lame  -ovc x264 -x264encopts bitrate=1500 pass=1 nr=2000 -quiet -o video_out.avi ; date
```

Now granted, I'm on a core2 quad q6600 chip and using a lot of CPU, so your encoder milage may vary.  

The output is an avi container containing x264 encoded video at 1.5Mb/s and mp3 audio at 256kbps.  

Things to look out for:
[LIST=1]
[*]ALSA channel - my input was on linein - hw.0
[*]tv channel input - I used aux in and that was on input=1
[/LIST]

If you know how long the tape is, you can wrap the script in the ever awesome timeout function:

```
timeout 35m mencoder .... 
```

Hope this helps someone else.

---

