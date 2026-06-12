---
title: "Mythbuntu 9.04. All work but !!"
date: 2009-05-03
forum: Mythbuntu
---

### Post by arska_l on 2009-05-03
I have a one problem, about one channel does not appear. 

I use 2 pcs. WinTV Nova T USB2 box. I can scan all channel correclty. Signal strange is good in all channel. 70-92. 

I living in Finland and channells I use is:

Yle TV1
Yle TV2
MTV3
Sub-TV
Nelonen
JIM

When I hit to MTV3, I got only OSD screen, and information about signal strange and channel program info and so on... then OSD leave and I got only black screen without any sound and video. About 30 sec, it return to main menu. All other channels work correctly. My nearest link is Tammela and frequencies are. 482000000, 522000000, and 706000000. Those freq. are also scanned correctly to transportlist. When I turn my antenna to direction Lahti, I can switch to MTV3, but signal strange is very poor... about 20. All other channel signals also are very poor.  
I installed two fresh Mythbuntu, 8.10 and 9.04. This problem arrived with both installation.  

I removed my Nova T USB2 from mythtv-setup and configured it again. Nothing helped. When I watch mythfrontend.log there is RingBuffer error about 10 times and invalid file (fd -1). I use XFS filesystem, and it is scanned and no-fragmented. I tested also change recordings-folder to EXT4 filesystem. Nothing help. No I am confused !!... Can anyone help me little, please. :confused:

My hardware:

Intel P4 3.0Ghz Prescott, 1GB RAM, 1TB harddisk, and Nvidia GF6200. It work perfectly, with libXvMCNVIDIA.so.1.  Motherboard AGP-based.

When I stop mythbackend and watch TV with Kaffeine, all channel show correclty. I think, this is mythfrontend issue ??

---

### Post by ian dobson on 2009-05-03
Hi,

Maybe you should try enabling the amplifier on your card by adding a line to your modules options file with

sudo echo options dvb-usb-dib0700 force_lna_activation=1 >> /etc/modprobe.d/options

or maybe 
sudo echo options dib3000mc buggy_sfn_workaround=1 >> /etc/modprobe.d/options

You'll need to reboot the computer to activate the option.
 
Regards
Ian Dobson

---

### Post by arska_l on 2009-05-03
Thank you for SUPER FAST replay.. Nice !

Thx for hint. I'll try today, later.  My childer watch TV at this moment.
:guitar:

By the way... I use firmware dvb-usb-nova-t-usb2-02.fw.  I have also WinTV Nova-T 500, but I dont use it at this moment.

---

### Post by arska_l on 2009-05-03
It does not helped. 

This is log, whats going on, when I change channel to MTV3

```
2009-05-03 22:58:53.035 TV: Changing from WatchingLiveTV to None
2009-05-03 22:58:53.107 DPMS Reactivated.
2009-05-03 22:58:53.269 TV: Attempting to change from None to WatchingLiveTV
2009-05-03 22:58:53.271 Using protocol version 40
2009-05-03 22:58:54.622 NVP: Disabling Audio, params(-1,2,44100)
2009-05-03 22:58:54.641 VideoOutputXv: Desired video renderer 'xvmc-blit' not
available.
codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit'
instead.
2009-05-03 22:58:54.643 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video
Texture'
2009-05-03 22:58:54.674 DPMS Deactivated
2009-05-03 22:58:54.692 VideoOutputXv: Ack! Disabling ChromaKey OSD
We can't use ChromaKey OSD if chromakeying is not supported!
2009-05-03 22:58:54.693 OSD Theme Dimensions W: 640 H: 480
2009-05-03 22:58:55.263 TV: Changing from None to WatchingLiveTV
2009-05-03 22:58:55.266 Realtime priority would require SUID as root.
2009-05-03 22:58:55.367 Video timing method: USleep with busy wait
2009-05-03 22:58:57.140 RingBuf
(/var/lib/mythtv/media/recordings/4350_20090503225854.mpg): Waited 1.0 seconds
for data to become available...
2009-05-03 22:58:57.140 Checking to see if there's a new livetv program to
switch to..
2009-05-03 22:58:58.141 RingBuf
(/var/lib/mythtv/media/recordings/4350_20090503225854.mpg): Waited 2.0 seconds
for data to become available...
2009-05-03 22:58:58.141 Checking to see if there's a new livetv program to
switch to..
2009-05-03 22:58:58.171 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:00.142 RingBuf
(/var/lib/mythtv/media/recordings/4350_20090503225854.mpg): Waited 4.0 seconds
for data to become available...
2009-05-03 22:59:00.142 Checking to see if there's a new livetv program to
switch to..
2009-05-03 22:59:00.204 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:02.240 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:04.144 RingBuf
(/var/lib/mythtv/media/recordings/4350_20090503225854.mpg): Waited 8.0 seconds
for data to become available...
2009-05-03 22:59:04.144 Checking to see if there's a new livetv program to
switch to..
2009-05-03 22:59:04.272 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:06.304 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:08.344 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:10.383 NVP: Prebuffer wait timed out 10 times.
2009-05-03 22:59:12.147 RingBuf
(/var/lib/mythtv/media/recordings/4350_20090503225854.mpg) Error: Waited 16
seconds for data, aborting.
2009-05-03 22:59:12.147 NVP::OpenFile(): Error, couldn't read file:
/var/lib/mythtv/media/recordings/4350_20090503225854.mpg
2009-05-03 22:59:12.148 NVP, Error: JumpToProgram failed.
2009-05-03 22:59:12.148 NVP, Error: Unknown error, exiting decoder
2009-05-03 22:59:12.148 TV: Attempting to change from WatchingLiveTV to None
```

It is very odd that only one channel can do this.  :confused:

I named /etc/modprope.d/options to /etc/modprobe/options.conf.  Is that correct with Mythbuntu 9.04.  I think.

---

### Post by ian dobson on 2009-05-04
Hi,

Can you try scheduling a recording, anything just a recording and not liveTV.

Thanks for the tip about the name change for the modprobe files, I read something about it sometime ago and forgot all about it.

What I've read the WinTV Nova T USB2 has a problem with weak signals.

Regards
Ian Dobson

---

### Post by 999.raapr.org on 2009-05-04
It's not only limited to that card. Same happened to my system 1.5.09 at around 13:00 local time.

I am using two Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02) cards. It looks like MTV3 has done something weird on their channel.

Also my other backend running two cards like yours stopped functioning. It uses Mythbuntu 8.10.

---

### Post by 999.raapr.org on 2009-05-04
> **ian dobson said:**
> Hi,

Can you try scheduling a recording, anything just a recording and not liveTV.



Scheduled recording creates a 0 sized file.

(edit: corrected a typo)

---

### Post by rockhouse on 2009-05-04
Hi, 
I noticed the same problem. All other channels work but not MTV3.
I have two dual tuners and this problem happens in both of them.
 
I have Hauppage WinTV-Nova-T-500 and WinTV-Nova-TD-500 PCI cards.
 
The problem started on 1st of May.
 
Regards,
Juha

---

### Post by 999.raapr.org on 2009-05-04
I am receiving MTV3 from Teisko (Tampere).
(edit: or would be if it worked)

---

### Post by arska_l on 2009-05-04
I tested with MPlayer.  Open terminal.. ->  mplayer dvb://MTV3 and this is log, what appeared to terminal window.

```
Playing dvb://MTV3.
dvb_tune Freq: 522000000
TS file format detected.
VIDEO MPEG2(pid=305) AUDIO MPA(pid=561) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  5000.0 kbps (625.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         5.0% 4 0 
GNOME screensaver enabled 0.003 ct: -0.472 575/575  5%  1% 32.8% 4 0 
```

If this help for solving this odd problem. :lolflag:

I can watch MTV3 with Kaffeine and Mplayer

---

### Post by arska_l on 2009-05-05
:guitar::guitar::popcorn:

A new life started.. I Solved this odd problem.

I stopped alsa-utils and avahi-deamon services and start MythTV and change channel to MTV3 and VOILA !!!!  video appear.. !  Yesh!!

---

### Post by rockhouse on 2009-05-05
Well I don't know what happened but I can see MTV3 again. LiveTV and recording works again.

Maybe Digita changed something back...

Can you also see MTV3 now?

Regards,
Juha

---

### Post by arska_l on 2009-05-05
I restart my MythTV to seeing, what happening. Now Alsa and Avahi-deamon started and I still I can watch MTV3 correctly.  Maybe you are right. MTV3 chanched something.. (saakelin säätäjät).

5 days without MTV3 .. lol. :confused:

---

### Post by 999.raapr.org on 2009-05-06
Everything works again without me doing anything, so the problem must have been in the MTV3's data stream... My Topfield DVB-T receiver worked without a hitch all the time, strange.

---

