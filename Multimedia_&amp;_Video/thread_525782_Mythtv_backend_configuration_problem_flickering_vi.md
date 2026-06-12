---
title: "Mythtv backend configuration problem?: flickering video"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by kansei on 2007-08-14
I have just set up a new mythtv backend and I'm having some weird video glitches on _all_ remote frontends (including 3 frontends that were set up on the older backends I had).

Here's the basic hardware configuration of the master backend:
- Pentium 4 3.2GHz
- 2GB PC3200
- 1.5TB storage array (960GB usable storage.. a RAID5) on a 3ware escalade 12-port SATA controller
- 3U rackmount case with 8 hot-swappable hard drive bays (7 in use)
- nvidia fx5200 AGP (was using a geforce4 ti4400 as well, the issue was .. more prevalent then, but I also did updates before restarting with the new video card)
- Hauppauge PVR-150 tv tuner card (video0)
- Hauppauge PVR-500 tv tuner card (video1 and video2)
- intel motherboard (not sure on chipset/model)
- onboard gigabit networking.

It's running Ubuntu Feisty (not server because it also runs the basement front end), with the latest updates.

The issue happens on ANY frontend (mac or linux, 64 or 32 bit, laptop or desktop, wireless, or wired (the full house network is gigabit), so I won't go into the hardware/software config on those.

The video glitch (which I have a video of.. just gotta get it off the cam and onto youtube later) is basically just a weird flickering and shifted overlay of video signals. The strange thing is, it happens only on certain *types* of scenes. .. like during a specific commercial it'll happen like crazy, then the next commercial it won't do it at all. It definitely happens like craaazy if there's any on-screen text and such (like with a 1-800 number to call to sign up for digital cable for example), but it doesn't happen at all while watching the simpsons and many other cartoon-type shows.

Oh and here's the partition layout:
20GB ext3 /
2GB swap
2GB ext3 /home
871.61GB reiserfs /storage (where mythtv puts stuff)

I do have it set to flag commercials while recording but.. I did that before on my 2.3GHz athlon xp backend (with the same tuners, less hard drive space, etc).

Since all the video has to come through the hard drives to get to the frontends, perhaps performance there is an issue? I'll have to run some benchmarks.

This is my.. 6th or 7th mythtv backend, and the first time I've ever come across problems like this.

I do need to confirm that the frontend that runs on the server also has the same video glitches... I'm 95% sure I noticed it there too.

I have considered that it could be an issue with the coax cable going into the two tuners, but it's all 6 month old RG6U cabling, then a splitter about 8 inches from the tuner cards, then two short RG6U cables to the tuners. It's the same cabling I was using before.

Does anyone have a clue?

---

### Post by kansei on 2007-08-15
if anyone is reading this and sees an information omission, let me know and I'll get you what you need (logs, config files, etc).

I have a few things to try when I get out of work today, including

- removing the splitter, testing each tuner card individually (I know that they both do it right now, but who knows could be a splitter issue even though it's quite the expensive splitter).
- turning off the option to commercial flag while recording
- benchmarking the storage array, maybe the RAID controller is choking handling 7 SATA drives over a 32-bit PCI connection (sadly the board in the 3U case doesn't have PCI-X.. and the boards I have with PCI-X (the 3ware card is PCI-X) are all dell boards that are proprietary so I can't slap them in)

---

### Post by cobaltcopy on 2007-08-15
Two things:

1) Are you running any interlacing filters?
2) What's the CPU usage when you have the flicker?

---

### Post by kansei on 2007-08-15
1. none that I know of.. are you talking about *de*interlacing? On any frontends hooked to LCDs, yeah.. ones hooked to CRT televisions, nope. 
2. It was quite normal the last time I checked (somewhere around 14%). I'll check again though.

I'm watching tv right now and it isn't doing it, but it's the simpsons and like I said before, it doesn't do it on cartoons.

---

### Post by kansei on 2007-08-15
65% idle on the backend with three tuners recording and three frontends, each watching one of the shows that are currently recording.

edit: it started happening hardcore while just recording on a single tuner and watching a recorded show on a (I need to find out if the video glitch is actually in the recordings) frontend, so I connected to the server to check processor usage.. 86% idle, but mythcommflag was using more than the backend.. I just went and changed that option and initially when I launched the frontend after, I saw the glitch, but it hasn't done it for the past 5 minutes. hmm

---

### Post by kansei on 2007-08-15
The glitch is still apparent when watching pre-recorded shows.. but usually only during commercials when there's a CG background or computer-generated text on screen.

---

### Post by bjhom on 2007-08-16
I may have a similar problem.  On certain channels the video is jumpy. Here's a sample:
[http://www.homfamily.com/temp/example.mpg](http://www.homfamily.com/temp/example.mpg)

I have a PVR-150mce lp.  I didn't have this problem with dapper or edgy, but have been fighting with feisty to get this to work for quite some time.

---

### Post by borodark on 2007-08-16
I have exactly congruent problem of flickering  on some channels certain type of video.
I am using PVR-500 MCE on PIII 866Mhz/512M 
4 ATA100  HDD as single JFS formatted volume using LVM on :guitar: OpenSUSE 10.2

The same problems are on another Celeron 850  
 box of the similar setup. 
The cpu is load is around 5% during recording.
I have updated ivtv to the latest stable

Both machines run analog ATI tuner just fine :(

So I am even thinking of returning PVR-500 to the shop :confused:

---

### Post by kansei on 2007-08-16
Ok so one of you has a PVR-150 doing it, the other has a PVR-500 doing it, and I have both (my PVR-150 isn't the MCE, but the PVR-500 is).. and they all use the same driver. Could this be an ivtv/ubuntu bug? I'd rather not move to an unstable version of ivtv as I would like to treat my backend server as a real 'server' and not run software still in testing --just because I'm a sysadmin at work doesn't mean I should put my college roommates through that, they deserve something stable no?

I'll have to check out that vid posted when I get out of work today.

Do all of you have the option enabled on the backend (In page 1, General, of mythtv-setup) to flag for commercials while recording? I turned off that option, but the only stuff I watched last night was recorded before I switched off the option, and it still had the glitches -- i.e. they are encoded right into the stored video. I only turned off the instant commercial flagging (it now runs as a background job) because I noticed it was eating more CPU cycles than the backend was, no matter if I was recording 3 shows or just 1. Even with that though, the CPU usage was still quite low considering the tremendous data throughput of recording three channels and having 4 running frontends all watching different things.

I did *not* ever have issues like this running my backend on Arch Linux for years. Then I went straight from that to MythBuntu (gutsy of course), but the X session would crash every 30 minutes or so (no video glitches though), so I just built the new backend server using Feisty (not the server edition) and installed the ubuntu mythtv master backend metapackage.

My main frontend runs the ubuntu mythtv frontend metapackage which really does configure it to act EXACTLY like mythbuntu just without the mythbuntu logos.. it does the auto log in , auto launch mythtv frontend, auto restart the X session if it crashes, etc stuff

---

### Post by borodark on 2007-08-16
The AutoCommflagWhileRecording   is set to 1

I'll try to update BIOS then other MB and also check the stock kernel setting for some settings that could matter.

---

### Post by kansei on 2007-08-16
I turned off commercial flagging while recording and it completely cured it. Anyone else care to try it? I guess I should go check for a bug report.

---

### Post by bjhom on 2007-08-16
I'll have to try that when I get home from work

---

### Post by kansei on 2007-08-16
I lied.. it still does it, but just a tiny, tiny bit, during a specific commercial that used to do it like CRAZY.

And yeah, checked that vid out bjhom, that's *precisely* what it is doing. Maybe I should try rolling back to an older version of ivtv or something.

---

### Post by bjhom on 2007-08-16
I changed my commercial flagging option off, and it seems a bit better, but still has the occasional jump.  The end of my dmesg says 

> 
[947581.112522] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[947581.112527] ivtv0: Cause: the application is not reading fast enough.

the output of top reads:

> top - 20:36:18 up 10 days, 23:39,  5 users,  load average: 0.03, 0.27, 0.69
Tasks: 117 total,   2 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.3%sy,  0.0%ni, 96.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    970816k total,   957544k used,    13272k free,     9744k buffers
Swap:  1052248k total,    34036k used,  1018212k free,   489736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1765 mythtv    18   0  202m  20m  11m S  2.3  2.1   0:11.42 mythbackend
 ...


here's my lspci
> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


If there's anything else that might be useful in troubleshooting this let me know.

---

### Post by kansei on 2007-08-17
Thanks for that error from dmesg, for whatever reason I was looking at logs but forgot to look at that.

Here's what a quick google search dug up, haven't gotten a chance to read these pages yet though:
[http://malformed.org/2006/01/31/new-ivtv-error-from-mythtv-ivtv0-all-encoder-mpeg-stream-buffers-are-full-dropping-data/feed/](http://malformed.org/2006/01/31/new-ivtv-error-from-mythtv-ivtv0-all-encoder-mpeg-stream-buffers-are-full-dropping-data/feed/)
[http://www.gossamer-threads.com/lists/ivtv/users/36380](http://www.gossamer-threads.com/lists/ivtv/users/36380)
[http://www.mythtv.org/pipermail/mythtv-users/2007-July/186202.html](http://www.mythtv.org/pipermail/mythtv-users/2007-July/186202.html)
[http://www.gossamer-threads.com/lists/ivtv/users/35805](http://www.gossamer-threads.com/lists/ivtv/users/35805) <-- talks about PCI latency.. hmm

---

### Post by bjhom on 2007-08-17
So is it then just a matter of adding more RAM?

---

### Post by kansei on 2007-08-17
> **bjhom said:**
> So is it then just a matter of adding more RAM?

Gosh I  hope not. On Arch Linux 1GB of RAM handled the 3 tuners just fine, and now my new server has 2GB (dual channel)

I'm still holding out hope that it is an IVTV bug.

---

### Post by bjhom on 2007-08-17
The first link may have a potential fix in it, but I have to wait until I get home to try it.

---

### Post by kansei on 2007-08-17
[   25.524259] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   25.524305] ACPI: PCI Interrupt 0000:04:08.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.524314] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)

[   71.033742] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[   71.033747] ivtv0: Cause: the application is not reading fast enough.

Mine doesn't say MPEG streams.. interesting. But on the subject of that 4th link I posted, I see messages about ivtv setting the PCI latency and complaining about the existing settings.

Time to research more :)

---

### Post by kansei on 2007-08-17
Found the answer to my problem (I think). Go to mythtv-setup, the general section, then on one of the first pages it talks about VBI (the tech that encodes the closed captioning data). I changed the setting from "NTSC Closed Captioning" to 'none'.

Sadly bjhom, it looks like my problem wasn't the same as yours >_< well sorta still the same because it's an IVTV issue

---

### Post by kansei on 2007-08-17
Here's a link to the bug report I found related to it:

[https://bugs.launchpad.net/ubuntu/+source/ivtv/+bug/106881](https://bugs.launchpad.net/ubuntu/+source/ivtv/+bug/106881)

---

### Post by kansei on 2007-08-17
Ok I lied, still broken. I turned the max simultaneous jobs to 1 on the backend, and it isn't recording anything right now.. video choppy as hell! Also the VBI is off as well as the auto commercial flagging while recording..

Here's my stuff from dmesg:
> 
[   20.557225] ivtv:  ==================== START INIT IVTV ====================
[   20.557231] ivtv:  version 0.10.1 (tagged release) loading
[   20.557235] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   20.557239] ivtv:  In case of problems please include the debug info between
[   20.557243] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   20.557246] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   20.557333] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   20.634063] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   20.634079] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   21.295363] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   21.512568] ivtv0: Encoder revision: 0x02050032
[   21.512572] ivtv0: Recommended firmware version is 0x02060039.
[   21.578442] tveeprom 0-0050: Hauppauge model 26052, rev C185, serial# 7577763
[   21.578447] tveeprom 0-0050: tuner model is TCL 2002N 6A (idx 85, type 50)
[   21.578449] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   21.578452] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   21.578454] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   21.578456] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   21.578459] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   21.578461] ivtv0: reopen i2c bus for IR-blaster support
[   21.646387] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   21.800182] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   25.066711] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   25.144461] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   25.188928] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   25.189193] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   25.189490] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   25.189624] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   25.189940] tuner 0-0061: type set to 50 (TCL 2002N)
[   25.524135] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   25.524188] ivtv:  ======================  NEXT CARD  ======================
[   25.524193] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   25.524198] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   25.524259] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   25.524305] ACPI: PCI Interrupt 0000:04:08.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.524314] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   25.846248] intel8x0_measure_ac97_clock: measured 55286 usecs
[   25.846251] intel8x0: clocking to 48000
[   26.151242] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   26.369987] ivtv1: Encoder revision: 0x02050032
[   26.369990] ivtv1: Recommended firmware version is 0x02060039.
[   26.376702] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   26.376734] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   26.381845] tuner 1-0060: TEA5767 detected.
[   26.381848] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #1)
[   26.381882] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   26.382226] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   26.405481] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   31.465273] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   31.575588] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   31.653417] tveeprom 1-0050: Hauppauge model 23552, rev D592, serial# 2942947
[   31.653421] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   31.653424] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   31.653427] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   31.653430] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   31.653432] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   31.653434] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   31.653437] ivtv1: Autodetected WinTV PVR 500 (unit #1)
[   31.726854] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   31.727070] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   31.727382] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   31.727513] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   31.727845] ivtv1: Registered device radio1 for encoder radio
[   31.727868] tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
[   32.129589] ivtv1: Initialized WinTV PVR 500 (unit #1), card #1
[   32.129635] ivtv:  ======================  NEXT CARD  ======================
[   32.129639] ivtv2: Autodetected Hauppauge card (cx23416 based)
[   32.129745] ACPI: PCI Interrupt 0000:04:09.0[A] -> GSI 23 (level, low) -> IRQ 19
[   32.129757] ivtv2: Unreasonably low latency timer, setting to 64 (was 32)
[   32.756822] ivtv2: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   32.974554] ivtv2: Encoder revision: 0x02050032
[   32.974559] ivtv2: Recommended firmware version is 0x02060039.
[   32.981929] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #2)
[   32.981964] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   32.986504] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #2)
[   33.009764] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #2)
[   38.059502] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   38.169803] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #2)
[   38.247734] tveeprom 2-0050: Hauppauge model 23552, rev D592, serial# 2942947
[   38.247739] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   38.247742] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   38.247745] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   38.247748] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   38.247750] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   38.247752] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   38.247755] ivtv2: Correcting tveeprom data: no radio present on second unit
[   38.247757] ivtv2: Autodetected WinTV PVR 500 (unit #2)
[   38.321032] ivtv2: Registered device video2 for encoder MPEG (4 MB)
[   38.321311] ivtv2: Registered device video34 for encoder YUV (2 MB)
[   38.321615] ivtv2: Registered device vbi2 for encoder VBI (1 MB)
[   38.321751] ivtv2: Registered device video26 for encoder PCM audio (1 MB)
[   38.322079] tuner 2-0061: type set to 57 (Philips FQ1236A MK4)
[   38.722081] ivtv2: Initialized WinTV PVR 500 (unit #2), card #2
[   38.722102] ivtv:  ====================  END INIT IVTV  ====================
[   38.906975] fuse init (API version 7.8)
[   38.924422] lp0: using parport0 (interrupt-driven).
[   38.959179] Adding 2000084k swap on /dev/disk/by-uuid/7a4f1614-cde4-4076-bc0b-9f9b81d48142.  Priority:-1 extents:1 across:2000084k
[   39.097174] EXT3 FS on sda1, internal journal
[   39.310089] NET: Registered protocol family 10
[   39.310213] lo: Disabled Privacy Extensions
[   45.287913] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[   45.287927] ReiserFS: sda3: using ordered data mode
[   45.295954] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   45.296486] ReiserFS: sda3: checking transaction log (sda3)
[   45.317716] ReiserFS: sda3: Using r5 hash to sort names
[   45.332750] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   45.332776] ReiserFS: sda5: using ordered data mode
[   45.342635] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   45.343232] ReiserFS: sda5: checking transaction log (sda5)
[   45.411693] ReiserFS: sda5: Using r5 hash to sort names
[   49.517649] eth0: no IPv6 routers present
[   51.725617] No dock devices found.
[   51.742247] Using specific hotkey driver
[   51.888453] input: Power Button (FF) as /class/input/input4
[   51.888491] ACPI: Power Button (FF) [PWRF]
[   51.888560] input: Sleep Button (CM) as /class/input/input5
[   51.888596] ACPI: Sleep Button (CM) [SLPB]
[   51.958409] ibm_acpi: ec object not found
[   52.042782] pcc_acpi: loading...
[   56.287588] ppdev: user-space parallel port driver
[   58.384465] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   58.384472] apm: disabled - APM is not SMP safe.
[   58.733814] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   58.902258] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   58.913741] NFSD: starting 90-second grace period
[   70.574449] eth0: no IPv6 routers present
[   71.033742] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[   71.033747] ivtv0: Cause: the application is not reading fast enough.
user@57may-server:~$ 



Edit: ok, so now I have learned that it's a PCI latency problem after all. I had 6 hard drives in my old backend, but that was with an onboard 6 port SATA controller.. now I'm using a 12-port PCI-X card, but in a PCI slot.. with default latency of 32, and 64 for the tv tuners because ivtv forces it. 

[http://www.mythtv.org/wiki/index.php/PCI_Latency#Hauppauge_PVR_Cards](http://www.mythtv.org/wiki/index.php/PCI_Latency#Hauppauge_PVR_Cards)

I set the latency to b0, time will tell if that cures things. Now I need a new motherboard.. I have plenty of dell boards with PCI-X but none in a chassis that can hold 8+ hard drives.

In an effort to reduce the strain on the PCI bus of the system, I got rid of the AGP video card (yay onboard intel video lol). so far so good!

---

### Post by kansei on 2007-08-24
Six days later.. it's still running perfectly with the PCI latency adjusted.

---

### Post by borodark on 2007-10-25
I have learned it is all VBI CLose Caption problem after all:)
So I have rebuild the box using old Intel server 440BX board having 2XPII-333.
Plus RAM 512M, HDD: 1XSCSI 4G + 2X200G IDE on ATA 33 and infamous PVR500.
So after installing suse 10.3 (kernel 2.6.22.9-0.4) and carefully arranging IRQs and latency in BIOS I have installed mythtv 0.20.2. Most of the staff I have left default during mythtvsetup, including leaving "None" in "VBI Close Cuptioning". It started to work like charm. I was happy! But I had attributed it to new kernel and fresh ivtv. So wrong was I.
When I had turned on VBI to NTSC .... the flickering came back!](*,)
And here is the tricky one: to remove flickering knowing the reason of VBI being  other then None it is not enough to run mythtvsetup and select "None" again - the ivtv has to be unloaded and loaded again, so:
1. mythtv-setup->general->VBI...->None>....->exit
2. rmmod ivtv
3. modprobe ivtv
:lolflag:

---

### Post by skroops on 2007-12-28
I had the same problem and disabling VBI Closed captioning solved the issue. Thanks!

---

### Post by kansei on 2008-02-13
> **skroops said:**
> I had the same problem and disabling VBI Closed captioning solved the issue. Thanks!

yay this thread came up in google search results, then I realized it's a thread I made haha.

I re-set up my mythtv server today. With Debian Etch though, not Ubuntu anymore.

Also a RAID10 instead of a RAID5

after making my pci latency startup script it was still flickering, so I did more research and remember the vbl crap.

woohoo! Working great now watching tv from the ubuntu frontend. Maybe now that it isn't a RAID5 (with the same hard drives, went from 960GB capacity to 480GB :( switching to RAID10) it can actually write data fast enough that I didn't need to change the PCI latency.

Oh well couldn't hurt. I don't know why IVTV thinks my tuner cards are more important than my 3ware SATA RAId controller. bah

---

