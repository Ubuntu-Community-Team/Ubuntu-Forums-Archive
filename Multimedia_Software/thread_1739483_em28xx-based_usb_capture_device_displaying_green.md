---
title: "em28xx-based usb capture device displaying green"
date: 2011-04-26
forum: Multimedia Software
---

### Post by Furyhunter on 2011-04-26
Hello, I have a em28xx-based USB video capture device, of a source I'm not sure of. The casing says "V-Stream", and has the part code VS-USB2800D. It seems to work, as the em28xx module is automatically probed, and a device mapping is made at /dev/video0. However, when I use mplayer tv:// it displays only a green screen with some corrupted colors at the top, and simply hardlocks VLC (in one case not even kill -9 was killing it)...

I compiled and installed the v4l-dvb modules from source and nothing was solved.

Any ideas? :\

EDIT:
> MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EM2860/SAA711X Reference Design
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = S-Video; 1 = Composite1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
Selected input hasn't got a tuner!
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
v4l2: select timeout
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 


and so on and so forth, there is the log.

---

### Post by Chronon on 2011-04-26
Isn't tv:// for analog TV?  I think dvb:// is for digital.  In my area there is no longer over-the-air analog TV.

---

### Post by Furyhunter on 2011-04-26
> **Chronon said:**
> Isn't tv:// for analog TV?  I think dvb:// is for digital.  In my area there is no longer over-the-air analog TV.

This device has no tuner, and has two inputs: a composite and S-Video. I set input=1 to get the Composite video but nothing different happens. I'll try dvb:// and edit this with the results.

EDIT: dvb reports it is not configured.

---

### Post by niksix00 on 2012-11-18
Hi 

i've seen that this thread is quite old but i've got exactly the same problem, did you figure it out the problem?

Thanks

[edit]
some additional info:
Ubuntu 12.04
uname -r: 3.2.0-33-generic

dmesg:
> 
[ 2594.478696] em28xx #0: Board not discovered
[ 2594.478700] em28xx #0: Identified as Unknown EM2800 video grabber (card=0)
[ 2594.478706] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[ 2594.478711] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[ 2594.478715] em28xx #0: Please send an email with this log to:
[ 2594.478720] em28xx #0: 	V4L Mailing List <linux-media@vger.kernel.org>
[ 2594.478724] em28xx #0: Board eeprom hash is 0x00000000
[ 2594.478729] em28xx #0: Board i2c devicelist hash is 0x1b800080
[ 2594.478733] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[ 2594.478739] em28xx #0:     card=0 -> Unknown EM2800 video grabber
[ 2594.478744] em28xx #0:     card=1 -> Unknown EM2750/28xx video grabber
[ 2594.478749] em28xx #0:     card=2 -> Terratec Cinergy 250 USB
[ 2594.478754] em28xx #0:     card=3 -> Pinnacle PCTV USB 2
[ 2594.478758] em28xx #0:     card=4 -> Hauppauge WinTV USB 2
[ 2594.478763] em28xx #0:     card=5 -> MSI VOX USB 2.0
[ 2594.478767] em28xx #0:     card=6 -> Terratec Cinergy 200 USB
[ 2594.478772] em28xx #0:     card=7 -> Leadtek Winfast USB II
[ 2594.478777] em28xx #0:     card=8 -> Kworld USB2800
[ 2594.478782] em28xx #0:     card=9 -> Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker / Kworld DVD Maker 2
[ 2594.478789] em28xx #0:     card=10 -> Hauppauge WinTV HVR 900
[ 2594.478793] em28xx #0:     card=11 -> Terratec Hybrid XS
[ 2594.478798] em28xx #0:     card=12 -> Kworld PVR TV 2800 RF
[ 2594.478803] em28xx #0:     card=13 -> Terratec Prodigy XS
[ 2594.478808] em28xx #0:     card=14 -> SIIG AVTuner-PVR / Pixelview Prolink PlayTV USB 2.0
[ 2594.478813] em28xx #0:     card=15 -> V-Gear PocketTV
[ 2594.478818] em28xx #0:     card=16 -> Hauppauge WinTV HVR 950
[ 2594.478823] em28xx #0:     card=17 -> Pinnacle PCTV HD Pro Stick
[ 2594.478828] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[ 2594.478833] em28xx #0:     card=19 -> EM2860/SAA711X Reference Design
[ 2594.478838] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
[ 2594.478843] em28xx #0:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[ 2594.478849] em28xx #0:     card=22 -> EM2710/EM2750/EM2751 webcam grabber
[ 2594.478854] em28xx #0:     card=23 -> Huaqi DLCW-130
[ 2594.478858] em28xx #0:     card=24 -> D-Link DUB-T210 TV Tuner
[ 2594.478863] em28xx #0:     card=25 -> Gadmei UTV310
[ 2594.478868] em28xx #0:     card=26 -> Hercules Smart TV USB 2.0
[ 2594.478873] em28xx #0:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[ 2594.478878] em28xx #0:     card=28 -> Leadtek Winfast USB II Deluxe
[ 2594.478883] em28xx #0:     card=29 -> EM2860/TVP5150 Reference Design
[ 2594.478888] em28xx #0:     card=30 -> Videology 20K14XUSB USB2.0
[ 2594.478893] em28xx #0:     card=31 -> Usbgear VD204v9
[ 2594.478897] em28xx #0:     card=32 -> Supercomp USB 2.0 TV
[ 2594.478902] em28xx #0:     card=33 -> Elgato Video Capture
[ 2594.478907] em28xx #0:     card=34 -> Terratec Cinergy A Hybrid XS
[ 2594.478912] em28xx #0:     card=35 -> Typhoon DVD Maker
[ 2594.478916] em28xx #0:     card=36 -> NetGMBH Cam
[ 2594.478921] em28xx #0:     card=37 -> Gadmei UTV330
[ 2594.478925] em28xx #0:     card=38 -> Yakumo MovieMixer
[ 2594.478930] em28xx #0:     card=39 -> KWorld PVRTV 300U
[ 2594.478934] em28xx #0:     card=40 -> Plextor ConvertX PX-TV100U
[ 2594.478939] em28xx #0:     card=41 -> Kworld 350 U DVB-T
[ 2594.478944] em28xx #0:     card=42 -> Kworld 355 U DVB-T
[ 2594.478949] em28xx #0:     card=43 -> Terratec Cinergy T XS
[ 2594.478954] em28xx #0:     card=44 -> Terratec Cinergy T XS (MT2060)
[ 2594.478959] em28xx #0:     card=45 -> Pinnacle PCTV DVB-T
[ 2594.478963] em28xx #0:     card=46 -> Compro, VideoMate U3
[ 2594.478968] em28xx #0:     card=47 -> KWorld DVB-T 305U
[ 2594.478972] em28xx #0:     card=48 -> KWorld DVB-T 310U
[ 2594.478977] em28xx #0:     card=49 -> MSI DigiVox A/D
[ 2594.478982] em28xx #0:     card=50 -> MSI DigiVox A/D II
[ 2594.478986] em28xx #0:     card=51 -> Terratec Hybrid XS Secam
[ 2594.478990] em28xx #0:     card=52 -> DNT DA2 Hybrid
[ 2594.478994] em28xx #0:     card=53 -> Pinnacle Hybrid Pro
[ 2594.478999] em28xx #0:     card=54 -> Kworld VS-DVB-T 323UR
[ 2594.479003] em28xx #0:     card=55 -> Terratec Cinnergy Hybrid T USB XS (em2882)
[ 2594.479008] em28xx #0:     card=56 -> Pinnacle Hybrid Pro (330e)
[ 2594.479014] em28xx #0:     card=57 -> Kworld PlusTV HD Hybrid 330
[ 2594.479019] em28xx #0:     card=58 -> Compro VideoMate ForYou/Stereo
[ 2594.479023] em28xx #0:     card=59 -> (null)
[ 2594.479028] em28xx #0:     card=60 -> Hauppauge WinTV HVR 850
[ 2594.479032] em28xx #0:     card=61 -> Pixelview PlayTV Box 4 USB 2.0
[ 2594.479036] em28xx #0:     card=62 -> Gadmei TVR200
[ 2594.479040] em28xx #0:     card=63 -> Kaiomy TVnPC U2
[ 2594.479045] em28xx #0:     card=64 -> Easy Cap Capture DC-60
[ 2594.479049] em28xx #0:     card=65 -> IO-DATA GV-MVP/SZ
[ 2594.479054] em28xx #0:     card=66 -> Empire dual TV
[ 2594.479058] em28xx #0:     card=67 -> Terratec Grabby
[ 2594.479063] em28xx #0:     card=68 -> Terratec AV350
[ 2594.479067] em28xx #0:     card=69 -> KWorld ATSC 315U HDTV TV Box
[ 2594.479072] em28xx #0:     card=70 -> Evga inDtube
[ 2594.479077] em28xx #0:     card=71 -> Silvercrest Webcam 1.3mpix
[ 2594.479081] em28xx #0:     card=72 -> Gadmei UTV330+
[ 2594.479085] em28xx #0:     card=73 -> Reddo DVB-C USB TV Box
[ 2594.479090] em28xx #0:     card=74 -> Actionmaster/LinXcel/Digitus VC211A
[ 2594.479095] em28xx #0:     card=75 -> Dikom DK300
[ 2594.479099] em28xx #0:     card=76 -> KWorld PlusTV 340U or UB435-Q (ATSC)
[ 2594.479104] em28xx #0:     card=77 -> EM2874 Leadership ISDBT
[ 2594.479108] em28xx #0:     card=78 -> PCTV nanoStick T2 290e
[ 2594.479112] em28xx #0:     card=79 -> Terratec Cinergy H5
[ 2594.479116] em28xx #0:     card=80 -> PCTV DVB-S2 Stick (460e)
[ 2594.785752] em28xx #0: Config register raw data: 0xb8
[ 2594.785757] em28xx #0: I2S Audio (5 sample rates)
[ 2594.785760] em28xx #0: No AC97 audio processor
[ 2594.849354] em28xx #0: v4l2 driver version 0.1.3
[ 2595.284474] em28xx #0: V4L2 video device registered as video1
[ 2595.284515] usbcore: registered new interface driver em28xx


---

### Post by niksix00 on 2012-11-18
i've been able to make it working removing the em28xx module and giving the card=8 option:


> 
rmmod em28xx
modprobe em28xx card=8


---

### Post by wildmanne39 on 2012-11-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

