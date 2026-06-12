---
title: "DVD won't play and yes, I do have libdvdcss2 :("
date: 2009-08-15
forum: Mythbuntu
---

### Post by Coume on 2009-08-15
Hello,

Ok, I have been stuck for a week on this issue and I can't see what I am doing wrong...

I recently built a new frontend and I installed Mythbuntu 9.04 on it. I may be missing something about with Mythbuntu as it is my first time with Ubuntu but frankly, I don't see what :(

Basically, I cannot play a single of my DVD on this frontend (Neither with the Internal player nor xine / vlc and mplayer). I do have the libdvdcss2 installed from the medibuntu repo but it still does not work! I can read and copy data dvds so the problem does not come from the HW in itself, I did double check just in case...

Here is the error messages that I am getting with all the previously mentioned players!
**Mythfrontend**
```
2009-08-14 21:01:27.824 TV: Attempting to change from None to Watching DVD
libdvdnav: Using dvdnav version svnR1169
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LEON_D1
libdvdnav: DVD Serial Number: 38313A53
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/lcoumetou/.dvdnav/LEON_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000761
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001f295e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001f295e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001f29b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001f39e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001f3a3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f3ab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f3b0e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001f3bb4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001f3c0b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001f3fab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001f4002
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001f41de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001f4235
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
2009-08-14 21:01:31.914 Opened DVD device at /dev/dvd
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
2009-08-14 21:01:32.418 There are 7 titles on the disk
2009-08-14 21:01:32.418 Title 0 has 0 parts.
2009-08-14 21:01:32.419 Title 1 has 28 parts.
2009-08-14 21:01:32.419 Title 2 has 2 parts.
2009-08-14 21:01:32.419 Title 3 has 2 parts.
2009-08-14 21:01:32.419 Title 4 has 3 parts.
2009-08-14 21:01:32.419 Title 5 has 9 parts.
2009-08-14 21:01:32.419 Title 6 has 2 parts.
2009-08-14 21:01:32.423 TV: StartPlayer(0, Watching DVD, main) -- begin
2009-08-14 21:01:33.336 Error reading block from DVD: Error reading from DVD.
2009-08-14 21:01:33.336 RingBuf(/dev/dvd) Warning: Peek() requested 4096 bytes, but only returning -1
2009-08-14 21:01:33.336 NVP::OpenFile(): Error, couldn't read file: /dev/dvd
2009-08-14 21:01:33.337 TV: StartPlayer(0, Watching DVD, main) -- end error
2009-08-14 21:01:33.387 ScreenSaverX11Private: DPMS Deactivated 1
2009-08-14 21:01:33.389 ScreenSaverX11Private: DPMS Deactivated 1
2009-08-14 21:01:33.390 ScreenSaverX11Private: DPMS Deactivated 1
```

**mplayer**
```
lcoumetou@ouranos:~$ mplayer /dev/dvd
MPlayer SVN-r29352-4.3.3 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing /dev/dvd.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [libmad] libmad mpeg audio decoder
Cannot sync MAD frame
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [hwmpa] MPEG audio pass-through (fake decoder)
Cannot sync MPA frame: 0
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x50.
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x576 => 768x576 Planar YV12
V:   0.0   1/  1 ??% ??% ??,?% 0 0

Exiting... (End of file)
```

**vlc**
```
lcoumetou@ouranos:~$ vlc /dev/dvd
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-b$
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LEON_D1
libdvdnav: DVD Serial Number: 38313A53
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/lcoumetou/.dvdnav/LEON_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000761
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001f295e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001f29b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001f39e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001f3a3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f3ab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f3b0e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001f3bb4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001f3c0b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001f3fab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001f4002
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001f41de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001f4235
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted
```

Any idea on how to fix this problem would be more than welcome!

Thanks
Ludo

---

### Post by khelben1979 on 2009-08-15
I think that [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") can solve your problems.

Read the documentation and add the Medibuntu repository to your /etc/sources.list file.

Your system is most likely lacking important system packages.

---

### Post by Coume on 2009-08-15
> **khelben1979 said:**
> I think that [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") can solve your problems.

Read the documentation and add the Medibuntu repository to your /etc/sources.list file.

Your system is most likely lacking important system packages.

Hiya,

I do have the medibuntu repo in my sources.list and that's from this repo that I installed libdvdcss2 hence why I really don't see what I missed :(

Any other idea?

Thanks
Ludo

---

### Post by khelben1979 on 2009-08-15
You could try experimenting with different versions of [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss2")2 to see if it helps, but before you do so you should check out the documentation which belongs to each version of the library.

---

### Post by Coume on 2009-08-15
Ok, I checked the region setting for the dvd drive and it was set to none.
I tried to set it to 2 (Europe) and I am now *kind of able* to play the dvd.

The playing is abnormally choppy and slow and it is basically impossible to watch a DVD.

```
$ hdparm -i /dev/sr0 

/dev/sr0:

 Model=MATSHITADVD-RAM UJ-846S                 , FwRev=F100    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode

```

I tried activating the DMA but it won't let me do so...
```
$ sudo hdparm -d1 /dev/sr0 

/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

So basically, I'm stuck :/

I wonder if the problem could come from the fact that it is a IDE drive connected through a SATA adapter as my motherboard only accept SATA drives...

---

### Post by khelben1979 on 2009-08-15
Hmm, are you using native graphic drivers? Open source graphics drivers are always very slow.

---

### Post by Coume on 2009-08-15
I use the nvidia driver with a quite powerful video card/MB (zotac ion D)

I'm really puzzled with this one :(

I have been using MythTV for years and that's my first frontend, which creates me hassle :/

---

### Post by KillerKiwi on 2009-08-15
Check the drive has its region set

Many drives can not decode DVD's unless there region is set
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

---

### Post by Coume on 2009-08-15
> **KillerKiwi said:**
> Check the drive has its region set

Many drives can not decode DVD's unless there region is set
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

Hello Killer,

I did set it (cf Post 5), which sorted the first problem but then, I discovered that the play back is abnormally slow/choppy.

I guess I will have to buy a SATA drive to solve this one...

Thanks
Ludo

---

### Post by khelben1979 on 2009-08-15
I have always experienced that [Plextor]("http://en.wikipedia.org/wiki/Plextor") is a good brand. I have had mine for several years now and it still works.

Other than that you have [these reviews]("http://www.driverheaven.net/reviews.php?category=7") from DriverHeaven.Net if you're interested.

---

### Post by korgman on 2009-08-16
i've been having choppy DVD playback since upgrading to 9.04 myself.  Did setting the region help fix it?  I'm using an old IDE drive, but ithe Internal player worked fine with 8.x. I've gone to using xine for the time being.

[http://ubuntuforums.org/showthread.php?t=1225698](http://ubuntuforums.org/showthread.php?t=1225698)

xine is OK, needed to redo all the lirc settings and it is not as good as the Internal player IMO.

---

### Post by stinger30au on 2009-08-16
if u have medibuntu i suggest you also do this

sudo apt-get install non-free-codecs


sudo apt-get install w32codecs  (only if your pcu is 32 bit otherwise if it is 64)

sudo apt-get install w64codecs


hope this helps

---

### Post by Coume on 2009-08-16
> **stinger30au said:**
> if u have medibuntu i suggest you also do this

sudo apt-get install non-free-codecs


sudo apt-get install w32codecs  (only if your pcu is 32 bit otherwise if it is 64)

sudo apt-get install w64codecs


hope this helps

Hello there,

I already had the w64codecs installed. I just tried to install the non-free-codecs just in case, but exactly the same issue.

I spent over a week on this problem and I am now 98% sure that everything is due to the DMA that cannot be enabled as it is a slot-in IDE drive connected through an adapter to SATA...

If anyone has any other idea, please do not hesitate to post.
Otherwise, I will report once I have been able to test with a SATA drive...

Thanks
Ludo

---

### Post by derrickadean on 2009-08-17
im not an expert but maybe you should try setting the location of your dvd device to /dev/sr0 or what ever the dvd device number is on your system

utilitis/setup>setu>media setting>video settings>general settings

the default setting my be different than the setting you need. so when you reinstalled it went back to its default setting and we know you have the right codecs

---

### Post by stinger30au on 2009-08-18
> **Coume said:**
> Hello there,

I already had the w64codecs installed. I just tried to install the non-free-codecs just in case, but exactly the same issue.

I spent over a week on this problem and I am now 98% sure that everything is due to the DMA that cannot be enabled as it is a slot-in IDE drive connected through an adapter to SATA...

If anyone has any other idea, please do not hesitate to post.
Otherwise, I will report once I have been able to test with a SATA drive...

Thanks
Ludo

ok, well my final suggestion is to click applications, add remove

set show to - show all available applications

search on 

restricted

and tick next to ubuntu restricted extras if using ubuntu or kubuntu restricted extras if u use kubuntu

let it install, restart pc and try again

---

### Post by kreegor on 2009-08-27
Hey,

Sorry to take over the thread but I am having a similar issue. I am unable to play a few DVD's using the internal player. When I try to play them they either don't play (e.g. freeze on a black screen until restart or until the frontend is shutdown, black screen for 2 seconds then straight back to the Play DVD menu etc) or crash the frontend completely. I am using Mythbuntu 8.04.1.

I tested one by running mythfrontend from the termianl and the error that I get when trying to play this certain dvd is:

> 2009-08-27 19:00:40.936 NVP: Enabling Audio
2009-08-27 19:00:40.938 AFD: Warning, audio codec 0xabfe1570 id(AC3) type (Audio) already open, leaving it alone.
2009-08-27 19:00:40.938 AFD: codec AC3 has 2 channels
[B]2009-08-27 19:00:40.942 FilterManager: failed to load filter 'none', no such filter exists
2009-08-27 19:00:40.942 Couldn't load deinterlace filter none
2009-08-27 19:00:41.074 FilterManager: failed to load filter 'none', no such filter exists
2009-08-27 19:00:41.074 Couldn't load deinterlace filter none
2009-08-27 19:00:41.297 DPMS Reactivated.[/B]

The dvd opens in VLC with no problems just not the internal player. Any ideas what is going on or where to start looking?

---

### Post by mathog on 2009-08-28
> **kreegor said:**
> 
The dvd opens in VLC with no problems just not the internal player. Any ideas what is going on or where to start looking?

The internal DVD player has issues.  I set up my system so that with the remote control I could wipe out the front end and start Xine instead.  So far Xine has been able to play all of the disks that the internal player couldn't.  I posted the scripts involved in this forum, search and you will find them.  Alternatively, just deactivate the internal player and set Myth to use Xine (or I suppose VLC) by default.

---

### Post by kreegor on 2009-08-31
Thanks for that. I will give xine a go and see how it goes against vlc. I have found a dvd that vlc fails on so if xine can play it then xine wins.

I really hope they fix dvd playback and support in 0.22. The only thing I hate about mythtv is the constant crashing or issues that occurs when trying to watch dvd's. It is brilliant otherwise!

---

### Post by korgman on 2009-09-07
I'm having all kinds of problems now.  I tried to update the system with the codecs and and something is really conflicted.  I can't upgrade anything now.  

```
matt@mythbuntu:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-installer: Depends: ia32-libs (>= 2.2ubuntu18) but it is not going to be installed
  nspluginwrapper: Depends: ia32-libs (>= 2.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

matt@mythbuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
48 not fully installed or removed.
Need to get 0B/28.0MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 180298 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu6.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu6.1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libGL.so.1', which is also in package nvidia-glx-180
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu6.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

i get this error for ever apt-get update I try.

---

### Post by timswait on 2009-09-24
I also can't get 'proper' DVDs to play. If I insert a DVD disc with an avi file burnt onto it, I can play the avi file, but when I insert a 'proper' DVD and try to play it the screen goes black for about 2 seconds and then goes back to the main menu. Xine won't play them, it says:
```
-xine engine error-
There is no input plugin available to handle 'dvd:/'
Maybe MRL syntax is wrong or file/stream source doesn't exist.
Then
The source can't be read. Maybe you don't have enough rights for this or the source doesn't contain data (e.g.not disc in drive). (/dev/dvd)

``` 
and neither will VLC either (unable to open the MRL).
In Mythbuntu control centre I have checked all the options to enable Medibuntu Proprietry codec support, enable w64codecs, enable libdvdcss2 and enable ffmpeg. I have also used regionset to set the region of my DVD drive to region 2 and I have installed xubuntu restricted extras.  I also have Windows installed on the same machine and this does play DVDs, so I don't think it's a hardware issue, it must be some plugin I don't have, but what?

---

