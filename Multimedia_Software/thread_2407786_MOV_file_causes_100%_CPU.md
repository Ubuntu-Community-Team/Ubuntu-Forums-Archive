---
title: "MOV file causes 100% CPU"
date: 2018-12-09
forum: Multimedia Software
---

### Post by lambchopper71 on 2018-12-09
When I try to edit/play a MOV file captured on an iPhone using OpenShot, the CPU pegs at 100%.  When I play it in any other media player (mplayer, vlc...) the video is choppy and sometimes crashes the player.  I think it's a codec or driver issue, but I'm not sure how to resolve it.  Here's the output from mplayer on the command line, can someone help me interpret this output?

Thank you in advance.

```
 mplayer ./IMG_0332.MOV 
MPlayer 1.3.0 (Debian), built with gcc-7 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ./IMG_0332.MOV.
libavformat version 57.83.100 (external)
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7f83fc5d42a0]Protocol name not provided, cannot determine if input is local or a network protocol, buffers and access patterns cannot be configured optimally without knowing the protocol
[lavf] stream 0: video (hevc), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [HEVC]  1920x1080  24bpp  240.000 fps  54215.3 kbps (6618.1 kbyte/s)
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 57.107.100 (external)
Selected video codec: [ffhevc] vfm: ffmpeg (FFmpeg HEVC / H.265)
==========================================================================
Clip info:
 major_brand: qt  
 minor_version: 0
 compatible_brands: qt  
 creation_time: 2018-12-02T19:56:14.000000Z
 com.apple.quicktime.location.ISO6709: +41.6237-075.0416+242.418/
 com.apple.quicktime.make: Apple
 com.apple.quicktime.model: iPhone X
 com.apple.quicktime.software: 12.1
 com.apple.quicktime.creationdate: 2018-12-02T14:56:14-0500
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, floatle, 88.6 kbit/6.28% (ratio: 11079->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 1ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:   1.3 V:   0.2 A-V:  1.137 ct:  0.004   0/  0 ??% ??% ??,?% 50 0 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:   6.5 V:   1.3 A-V:  5.234 ct:  0.004   0/  0 453% 22% 18.4% 314 0 
No bind found for key 'MOUSE_BTN2'.
A:   7.2 V:   1.5 A-V:  5.748 ct:  0.004   0/  0 449% 22% 18.7% 349 0 

Too many video packets in the buffer: (1199 in 33587002 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  13.3 V:   7.6 A-V:  5.714 ct:  0.386   0/  0 465% 24%  6.6% 631 0 


```

---

### Post by 23dornot23d on 2018-12-09
I am no expert on video - but the frames per second for playback seems a little high ......

> 
VIDEO:  [HEVC]  1920x1080  24bpp  240.000 fps



---

### Post by lambchopper71 on 2018-12-09
It's a video shot in slow motion.  So I think I'd expect a different frame rate, I think....

---

### Post by 23dornot23d on 2018-12-09
Have you tried it in Openshot ..... v 2.4.2
I found this .....

[URL="https://www.openshot.org/blog/2018/06/30/openshot-242-released-more-effects-more-stable-more-fun/"]**OpenShot Video Editor | OpenShot 2.4.2 Released | More Effects ...**


[/URL][https://www.openshot.org/.../openshot-242-released-more-effects-more-stable-more-f](https://www.openshot.org/.../openshot-242-released-more-effects-more-stable-more-f)...
Jun 30, 2018 - Increase valid frame rates to *240 fps* since many cameras now support ... based on the # of processors, to better support high framerate videos.

[B]sudo apt install inxi

inxi -Fz[/B]

give some details of your system ..... too maybe will give a start point for people to work out if it is anything related to that too ..........

---

### Post by lambchopper71 on 2018-12-09
I just tried OpenShot 2.4.2, now the file takes around 5-10 minutes to importing the video which it didn't do before.  Then another 5-10 minutes to move the video to a track. Playback behavior is the same, high CPU.  The CPU doesn't peg at 100% as before, but it does get between 77 and 87%.  Oddly enough, now when the CPU is high, I lose the ability to click with the mouse in this window.  Moving the mouse works and when I force quit OpenShot mouse clicks returned, so that's related.

Here's the machine info:

```
userID@userID-ThinkPad:~$ inxi -Fz
System:    Host: userID-ThinkPad Kernel: 4.15.0-42-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: LENOVO product: 20BXCTO1WW v: ThinkPad T450s serial: N/A
           Mobo: LENOVO model: 20BXCTO1WW v: SDK0K11826 WIN serial: N/A
           UEFI: LENOVO v: JBET51WW (1.16 ) date: 07/08/2015
Battery    BAT0: charge: 19.9 Wh 98.7% condition: 20.2/23.2 Wh (87%)
           BAT1: charge: 19.0 Wh 99.9% condition: 19.0/23.2 Wh (82%)
CPU:       Dual core Intel Core i7-5600U (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3200 MHz 1: 2934 MHz 2: 2934 MHz 3: 2934 MHz 4: 2932 MHz
Graphics:  Card: Intel HD Graphics 5500
           Display Server: x11 (X.Org 1.19.6 ) drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.05hz, 1920x1080@60.00hz, 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2) version: 4.5 Mesa 18.0.5
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-42-generic
Network:   Card-1: Intel Ethernet Connection (3) I218-LM driver: e1000e
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Intel Wireless 7265 driver: iwlwifi
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 516.1GB (55.3% used)
           ID-1: /dev/sda model: ST500LM021 size: 500.1GB
           ID-2: /dev/sdb model: SanDisk_SSD_U110 size: 16.0GB
Partition: ID-1: / size: 327G used: 247G (80%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 21.35GB used: 0.00GB (0%) fs: swap dev: /dev/sda7
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 82.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 3941
Info:      Processes: 300 Uptime: 3:23 Memory: 3569.8/19951.3MB Client: Shell (bash) inxi: 2.3.56 
userID@userID-ThinkPad:~$ 


```

---

### Post by 23dornot23d on 2018-12-09
> 
 I lose the ability to click with the mouse in this window.  Moving the  mouse works and when I force quit OpenShot mouse clicks returned, so  that's related.



That to me sounds like running out of memory to work in ...... so then I look for things like swap space ..... but you seem to have 21.35 Gig on a 16 Gig ssd card - which seems impossible to have .......... yet it seems to report that back ....... unless it is using a file and something else as well ..... the ssd card will be slow possibly .... also similar happens on my own ssd card - the screen dims and the mouse freezes until its finished its process ....... maybe someone else knows more about this ........ but that is all I can relate
the mouse click stopping working to ......
**SanDisk_SSD_U110 size: 16.0GB**

> 
Drives:    HDD Total Size: 516.1GB (55.3% used)
           ID-1: /dev/sda model: ST500LM021 size: 500.1GB
           **ID-2: /dev/sdb model: SanDisk_SSD_U110 size: 16.0GB**
Partition: ID-1: / size: 327G used: 247G (80%) fs: ext4 dev: /dev/sda6
           **ID-2: swap-1 size: 21.35GB** used: 0.00GB (0%) fs: swap dev: /dev/sda7


---

### Post by CatKiller on 2018-12-09
```
VIDEO: [HEVC] 1920x1080 24bpp 240.000 fps 54215.3 kbps (6618.1 kbyte/s)
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
```

This is the critical bit. You aren't using hardware acceleration, it's just software rendering on the processor. As the output says, your computer isn't fast enough for that.

---

### Post by lambchopper71 on 2018-12-09
> As the output says, your computer isn't fast enough for that. 				

I'm not buying this.  This Laptop is an Intel Dual Core i7-5600 @ 2.6Ghz with 20 Gib RAM.  Also, I dual boot this PC with Windows 10 because I occasionally need it for work and there are a few tools work requires that are Windows only.  Under Windows on the same computer, I was able to load and edit the file.  This has to be a driver issue under Linux.

---

### Post by CatKiller on 2018-12-09
> **lambchopper71 said:**
> I'm not buying this.  This Laptop is an Intel Dual Core i7-5600 @ 2.6Ghz with 20 Gib RAM.  Also, I dual boot this PC with Windows 10 because I occasionally need it for work and there are a few tools work requires that are Windows only.  Under Windows on the same computer, I was able to load and edit the file.  This has to be a driver issue under Linux.

You should probably read more closely. You aren't using your hardware acceleration. That's why it's struggling.

It's like trying to cut down a tree with a spoon.

---

### Post by 23dornot23d on 2018-12-10
Have a look for updated drivers for your graphics ...... Catkiller is correct if its using the CPU so much - then its possibly not making the best use of the intel graphics card you have in that computer

> 
Graphics:  Card: **Intel HD Graphics 5500**
           Display Server: x11 (X.Org 1.19.6 ) **drivers: intel** (unloaded: modesetting,fbdev,vesa)
           **Resolution: 1920x1080@60.05hz, 1920x1080@60.00hz, 1920x1080@60.00hz**
           OpenGL: renderer: **Mesa DRI Intel HD Graphics 5500** (Broadwell GT2) version: **4.5 Mesa 18.0.5**


I did some searches on this and these links are of a few that mentioned using a later mesa driver ..... 

They mention gaming - but its for the same reason - they want better performance ....... possibly a way forward ..... you can wait for better answers though.
at least this gives your thread a bump as such .....

[https://news.softpedia.com/news/ubuntu-18-04-lts-users-can-now-install-mesa-18-1-1-to-improve-their-linux-gaming-521543.shtml](https://news.softpedia.com/news/ubuntu-18-04-lts-users-can-now-install-mesa-18-1-1-to-improve-their-linux-gaming-521543.shtml)

[https://www.omgubuntu.co.uk/2018/06/mesa-18-1-1-ubuntu-18-04-ppa](https://www.omgubuntu.co.uk/2018/06/mesa-18-1-1-ubuntu-18-04-ppa)

---

### Post by CatKiller on 2018-12-10
> **23dornot23d said:**
> Have a look for updated drivers for your graphics

It's not the graphics driver, it's the lack of [VDPAU]("https://en.wikipedia.org/wiki/VDPAU"). There is a package to translate Intel's VA-API into the VDPAU that the application is expecting. Or the OP could use the *-vo vaapi -va vaapi* mplayer options directly. But the OP would prefer not to use hardware acceleration for some reason, apparently.

---

### Post by Yellow Pasque on 2018-12-10
> It's not the graphics driver, it's the lack of VDPAU. There is a package to translate Intel's VA-API into the VDPAU that the application is expecting.

IIRC, the package you are referring to is libvdpau-va-gl1. But if you have an Intel GPU, you should not be using VDPAU unless it's your only option. Using VA-API directly will give better performance.

```
sudo apt-get install i965-va-driver vainfo
```

Then, you need a player capable of using VA-API. I'd recommend mpv (with smplayer as a front-end GUI if you wish). I don't think the old mplayer supports VA-API unless you get the specially patched version of it.

---

### Post by mc4man on 2018-12-10
Install & run vainfo, see if hevc (h.265) is supported. If so you can use vaapi hwdec though not in mplayer. In that case try mpv instead.

Edit: The video likely is supposed to be played back at either 30 or 60 fps, that's what creates the slo-mo. Maybe your players are trying to play at 240fps?
(- you could try something like ```
mplayer --no-correct-pts --fps=30 or mplayer --no-correct-pts --fps=60
``` mpv  has similar options..

---

