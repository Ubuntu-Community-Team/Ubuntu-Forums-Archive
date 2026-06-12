---
title: "1080p HD content: terrible performance"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by djbon2112 on 2008-01-17
Laptop Specs:

Intel T7300 @ 2.0 GHz
2 GB Generic Dell DDR2-667
GeForce 8600M GT
Dell WUXGA display (1920x1200)
500 GB external USB 2.0 HDD for media
Ubuntu 7.10 Gutsy Gibbon

Well, I'm using Mplayer to play some 1080p HD content I have, but the performance is extremely sluggish. Sometimes frames will stall and freeze for seconds at a time (usually until the camera changes shots), be corrupted (grey squares and ghosting), and other times just run extremely slow (2-4 FPS max). I've tried using VLC but it's even worse. Furthermore, I get a lot of "Error: Too many packets in buffer" in Mplayer during playback. CPU usage is always at 50% (one core maxed out) during playback.

I'm using a stock install of Ubuntu 7.10 (x86), with the nVidia driver installed, Mplayer, VLC, and the default codecs for x264 (the restricted ones, not sure the name off hand). A guy on an HD video forum recomended I recompile Mplayer with the i686 instruction set, but I've got no idea how. I'm a Linux AND HD video noob, so I'm kinda oblivious to both parts of this issue, so if anyone has any advice, please share

---

### Post by cor2y on 2008-01-17
Whats the hidef format?
Avi, mp4,mov, wmv?
And the codecs, vc1, H264, X264, Divx, Xvid, WMV3?
Your system looks like it meets the requirements to play 480p, 720p and 1080i or 1080p Bitrates, i could be wrong of course i know ms and apple recommend a minimum of 3.0ghz for wmvhd and quicktime H264 1080i/1080p video playback.
Over lets say a video bitrate of 7000k might be a problem, if its just one core in use since hidef video playback is cpu intensive, on newer hidef capable vid cards the gpu is supposed to take that burden off of the cpu but i only know of this with windows and don't know if the linux drivers for those type of hidef cards are ready or even work.
Too many packets sounds like it could be video @ 8000k video bitrate but only one core working so it looks like the cpu is not powerful enough.
If you do complie use this [mplayer guide]("http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer").
For getting 1080i/1080p playback on a cpu with less power try this [recommendation]("http://ubuntuforums.org/showthread.php?t=629701&highlight=mplayer").
Hopes that helps.
EDIT
I686 is recognized by default or it should when you are compiling mplayer (since it should recognize your cpu type when configuring)

---

### Post by djbon2112 on 2008-01-19
The container is MKV, and the codec is x264. Trying the suggestions in that thread th ough, I have to wait for some new HD content (data hard drive was borked by Gparted last night :()

---

### Post by tgm4883 on 2008-01-19
I remember reading that in order to get HD from mplayer you need to compile in order to enable certain features.  This should be fixed in the hardy version i believe.

---

### Post by djbon2112 on 2008-02-08
Well, I've been trying again to no avail. Even the "older computer" fix doesn't seem to work. I've tried every player I can get my hands on, and a couple more movies. Almost all of them are the same: stutters, freezes, low FPS, etc.

I'm more than willing to recompile Mplayer, but I need a tutorial or something similar to do it. Do you have any tips?

EDIT: Nevermind, I saw cor2y's link: [http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer)

Thanks!

---

### Post by djbon2112 on 2008-02-08
I tried the guide, and it's much better, but it's still VERY choppy in places, and I still get "Too many packets in buffer" errors at certain places. Is there a way to compile Mplayer as multicore? I tried the slow-CPU fix with this compiled Mplayer, but I get this:

```
joshua@joshua-laptop:~/Desktop/mplayer$ nice -n 0 gmplayer -vfm ffmpeg -lavopts lowres=2:fast:skiploopfilter=all:threads=8
MPlayer dev-SVN-r25962-4.1.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Unknown option on the command line: -lavopts
Error parsing option on the command line: -lavopts

```

Any suggestions?

---

### Post by djbon2112 on 2008-03-22
A little new action.

After reinstalling Gutsy again for various reasons, I'm back to trying to get this to work. I've compiled it from scratch from the SVN but I've still got playback issues, too many packets in buffer, choppy, etc.

I've heard it mentioned that mplayer can be compiled for multi threading support, but I don't know how. Is this actually possible? If so, what's the ./configure command for this?

---

### Post by gsmanners on 2008-03-22
Which version of the nvidia driver are you using? It could be that you really need the latest version of the driver to get the kind of performance you want.

---

### Post by gunthergloop on 2008-03-22
Or which version of 7.10 (32 or 64-bit) are you using?

I don't know if that might be an issue, but as per another thread, I've been having trouble with the 64-bit Ubuntu release (pauses in 'general' non-video s/w) where I had none with 32-bit. My spec is very similar to yours.

I'm waiting for new ram to arrive to up it to 2GB (currently only 1) to see if that sorts it, but I'm itching for a blu-ray drive and I just checked into this thread so as to be prepared for what might arise.

---

### Post by djbon2112 on 2008-03-22
I'm using the latest nVidia driver and 32-bit Ubuntu.

---

### Post by zgornel on 2008-03-23
Try using different mplayer video drivers: xv/xvmc/x11/gl/gl2 . ```
mplayer -vo <driver> <file.mkv>
``` and check that the cpu is operating at full frequency.

---

### Post by talon95 on 2008-03-23
To original poster.  Your processor is too slow.  I've found I need a C2D running @3 Ghz or above to play 1080p MKV's on one core.

---

### Post by zgornel on 2008-03-24
> **talon95 said:**
> To original poster.  Your processor is too slow.  I've found I need a C2D running @3 Ghz or above to play 1080p MKV's on one core.
This is the case if no acceleration from the video card is used. The 8 series of Geforce cards should reduce processor usage to a minimum for h.264.

---

### Post by Melcar on 2008-03-24
Same problem here.  Odd thing is that my laptop with a Sempron 2GHz and a measly 200M can play HD content rather well (with a few slow downs here and there) while my much bigger desktop can't.  Using the same players too.  Must be the drivers I think and how well they support certain chips.

---

### Post by bsmith1051 on 2008-03-24
> **zgornel said:**
> This is the case if no acceleration from the video card is used. The 8 series of Geforce cards should reduce processor usage to a minimum for h.264.
On Windows, sure, but what player/codec on Linux can do h.264 acceleration?

---

### Post by djbon2112 on 2008-03-24
> **zgornel said:**
> Try using different mplayer video drivers: xv/xvmc/x11/gl/gl2 . ```
mplayer -vo <driver> <file.mkv>
``` and check that the cpu is operating at full frequency.

This doesn't help.

> **talon95 said:**
> To original poster.  Your processor is too slow.  I've found I need a C2D running @3 Ghz or above to play 1080p MKV's on one core.

Well, since it's a laptop, I guess I'm SOL then, until nVidia makes a driver for Linux that allows hardware decoding of h.264. Oh well, I'll wait until I make by HTPC in May :p

---

### Post by drdrewdown on 2008-03-24
i just built my media center computer over the weekend.. running mythbuntu + mythtv ofc which is really pretty slick. kudos to those cats..

720p video plays exceptional. i watched a few movies over the weekend & was happy with the performance, no lag whatsoever

so i tried to play a 1080p with mkv container using x264 codec & vlc about crapped itself trying to play the video.  mplayer works alot better but still is unwatchable. 

this is a new build(i kinda skimped) but should be able to play 1080p imo.. apple trailers in 1080p play decent with a few lags via mplayer, but movies are out of the question..specs are as follows

athlon x2 4200+ dual core
asus m2ne-sli (nice board)
xfx nvidia geforce 8600gt
2gb corsair xms (2*1gb)
500gb sata 16mb buffer
mythbuntu 7.10 32bit
latest stable nvidia driver from repos running 1920x1080 dvi>hdmi cabled to my new samsung 56" dlp

i am just at home on my lunch break, so tonite i will be trying all sorts of things, if anyone has an idea their curious about, i can try it tonite & let ya know how it turns out. 


cheers

---

### Post by JoshLukas on 2008-03-24
Hello. I have a similar computer.

X2 4200+
MSI K9A+ Plat.
6 GB of RAM
8600GT Gigabyte
M-Audio 2496

using repo drivers. I tried running my nVidia card with the latest drivers, but then all other video is kinda blue in totem. The system runns under gutsy x_86_64. I tried many sw players. The best results I got with mplayer, but still unwatchable when playback 1080p HD material.
I came to the conclusion, the processor is way too slow for this kind of media to playback. Even on WindowsXP with CoreAVC, 1080p HD material is unwatchable. Audio gets out of sync.
While overclocking the cpu to 2,6 GHz the results got better, but still not satisfactionable. Maybe a 5200+ black edition cpu running at >= 3 Ghz will result in a good performance.
Next week I'm gonna setup a new system for my friend using a 5200+ black edition X2 CPU. Will report then later.

The system is a:

X2 5200+ black edition
Gigabyte SB700 based µATX board
9600GT nVidia card
2 GB RAM

Ubuntu gutsy + WinXP


Josh

---

### Post by ultima on 2008-03-25
If you have coreavc and you know how to compile mplayer,  you can patch mplayer to use coreavc.

[Coreavc with mplayer guide]("http://code.google.com/p/coreavc-for-linux/w/list")

Works like a charm. Uses both cores as well if you have a dual core.

Ps. try to get coreavc 1.3 if possible, I had trouble with other versions and works with MPlayerv1.0rc2 you don't need to use SVN

---

### Post by IsawSp4rks on 2008-03-25
> **zgornel said:**
> This is the case if no acceleration from the video card is used. The 8 series of Geforce cards should reduce processor usage to a minimum for h.264.

nvidia doesn't support full acceleration of video in GNU/Linux.  Setting output to xv only accelerates video in the sense of overlay being properly support with scaling.  Purevideo/PurevideoHD isn't supported in linux as it is Windows DirectXVideoAcceleration (DXVA) geared and so far I've not seen a way to get linux to support it in OpenGL.

The instructions in this thread:-

[http://ubuntuforums.org/showthread.php?t=636277&highlight=mplayer+compiz&page=2](http://ubuntuforums.org/showthread.php?t=636277&highlight=mplayer+compiz&page=2)

may provide for better acceleration as they force OpenGL Compositing support for XV in Mplayer.  It certainly helps with ATI hardware, so I think it may provide for better performance in certain nvidia cards (probably older chipsets though).

Otherwise VLC will probably perform better than mplayer with x264 content.

---

### Post by IsawSp4rks on 2008-03-25
> **ultima said:**
> If you have coreavc and you know how to compile mplayer,  you can patch mplayer to use coreavc.


Yeah but CoreAVC is a software codec, with limited profiles and deblocking.  It's very efficient but does not accelerate x264, AVC and other Mpeg4 profiled codecs via the GPU.  We really need nvidia to open the PurevideoHD spec to linux.

---

### Post by ultima on 2008-03-26
That may be so but with h264 encoded video I now get smooth playback at 1080p. Where as before it was completely unwatchable. Besides Purevideo never worked for me on windows so I doubt it would work for me anyway.

---

### Post by drdrewdown on 2008-03-26
> **ultima said:**
> That may be so but with h264 encoded video I now get smooth playback at 1080p. Where as before it was completely unwatchable. Besides Purevideo never worked for me on windows so I doubt it would work for me anyway.

how smooth are you talkn about?  does it still drop a bunch of frames(especially in fast action scenes?)

---

### Post by stefangr1 on 2008-03-26
Unfortunately, mpeg4 acceleration is - even though supported by some modern graphical cards - not yet implemented in Linux. This means that your cpu has to do all the work!

Your processor does not meet the neccesary requirements to play 1080p x264. I have an E6750, and still can't play about half of the files.

About the options u use:

it is _lavdopts_ ! I don't think lowres is going to help, since that won't speed up the x264 decodation (xorg is runned in a separate thread on the other proc), and the threads option (do you really have a hexacore?) almost never works, since the movies have to be encoded using very specific options regarding slices and deblocking. 

Wat should work is: -lavdopts fast=1,skiploopfilter=all

But not on your system I think, it just won't be enough. 

I estimate that, in order to play all 1080p content smooth, I would need a processor that is at least 25% faster than my 2.67Ghz Core2 E6750. Meaning that I have to wait untill better drivers / vaapi / mpeg4 acceleration is out, or next gen processors arrive!

---

### Post by JoshLukas on 2008-04-20
Okidoke. I've setup a new system for my friend with following hardware:

X2 5000+ black edition (2x 2,6 GHz @ 3,0 GHz @ default VCore)
Gigabyte GA-MA78GM-S2H (SB700 based µATX board)
9600GT nVidia card from Leadtek
2 GB DDR2 RAM @ 800 MHz

Tried to playback some mkv (h264) files. Casino Royale and Sunshine. Both full HD 1920x1080. On a WinXP SP2 the performance was terrible. Had some framedrops in critical scenes and the audio was out of sync. Same performance with Ubuntu Hardy Beta5 64bit, but audio was not out of sync. While overclocked @ 3 GHz with just adjusting the multiplyer from 13 to 15, the X2 black edition ran @ 3,0 GHz. Now I was able to watch Casino Royal and Sunshine almost without framedrops. All in all the movie was very watchable. Under Windows the performace was worse. Audio was still out of sync.

I think. Next time, I will do some adjustments on the PC and software. Hope all HD media will play smooth at any time.

I've tested with following software:

_**WinXP**_
Mediaplayer Classic
K-Lite codec pack
CoreAVC
[U][B]
Hardy 64bit[/B][/U]
Codecs from the Ubuntu repos
Totem
VLC (best results)

---

### Post by bsmith1051 on 2008-04-20
you should scrap the K-Lite codec pack on Windows, that's almost certainly why you had sync issues.  Keep It Simple!  Personally, I use the new Media Player Classic - Homecinema edition and it plays almost everything perfectly.  Also, have you tried the windows version of VLC?

In general, of course, it's disappointing how much better the multimedia software is on Windows compared to Linux.  VLC is as good as it gets for Linux but the current stable version has terrible h.264 decoding.  There's a newer 0.90 version supposed to come out sometime which will have a newer generation of the h.264 codec....

---

### Post by Fatec on 2008-04-27
> **JoshLukas said:**
> Hello. I have a similar computer.

X2 4200+
MSI K9A+ Plat.
6 GB of RAM
8600GT Gigabyte
M-Audio 2496

using repo drivers. I tried running my nVidia card with the latest drivers, but then all other video is kinda blue in totem. The system runns under gutsy x_86_64. I tried many sw players. The best results I got with mplayer, but still unwatchable when playback 1080p HD material.
I came to the conclusion, the processor is way too slow for this kind of media to playback. Even on WindowsXP with CoreAVC, 1080p HD material is unwatchable. Audio gets out of sync.
While overclocking the cpu to 2,6 GHz the results got better, but still not satisfactionable. Maybe a 5200+ black edition cpu running at >= 3 Ghz will result in a good performance.
Next week I'm gonna setup a new system for my friend using a 5200+ black edition X2 CPU. Will report then later.

The system is a:

X2 5200+ black edition
Gigabyte SB700 based µATX board
9600GT nVidia card
2 GB RAM

Ubuntu gutsy + WinXP


Josh

You must have something setup very wrongly if you cant get perfect HD/1080p/h264 playback on XP with that setup.

I have a lower spec'd PC and i playback H264(1080p) just fine...same with bluray/hd-dvd, mkv and what not.

---

### Post by Fatec on 2008-04-27
> **JoshLukas said:**
> Okidoke. I've setup a new system for my friend with following hardware:

X2 5000+ black edition (2x 2,6 GHz @ 3,0 GHz @ default VCore)
Gigabyte GA-MA78GM-S2H (SB700 based µATX board)
9600GT nVidia card from Leadtek
2 GB DDR2 RAM @ 800 MHz

Tried to playback some mkv (h264) files. Casino Royale and Sunshine. Both full HD 1920x1080. On a WinXP SP2 the performance was terrible. Had some framedrops in critical scenes and the audio was out of sync. Same performance with Ubuntu Hardy Beta5 64bit, but audio was not out of sync. While overclocked @ 3 GHz with just adjusting the multiplyer from 13 to 15, the X2 black edition ran @ 3,0 GHz. Now I was able to watch Casino Royal and Sunshine almost without framedrops. All in all the movie was very watchable. Under Windows the performace was worse. Audio was still out of sync.

I think. Next time, I will do some adjustments on the PC and software. Hope all HD media will play smooth at any time.

I've tested with following software:

_**WinXP**_
Mediaplayer Classic
K-Lite codec pack
CoreAVC
[U][B]
Hardy 64bit[/B][/U]
Codecs from the Ubuntu repos
Totem
VLC (best results)

With MKV files your best bet is ffdshow...usually is the best filter.

Some mkvs require coreAVC, it depends on how the encode was done, if its x264 you should have no problems with CoreAVC, with those sort of specs you must be doing something seriously wrong.

DO not install codec packs...that is just a serious no no.

---

### Post by JoshLukas on 2008-04-28
Well as far as I know only PowerDVD in a particular version which I don't know ad hoc, is able to use the geforce hardware acceleration for hd content. A X2 4200+ which clocks at 2.2 GHz each core the cpu is not powerfull enough to decode full hd 1920x1080 material coded with x264 algorythm. I tried to overclock my cpu to 2.6 GHz where a full hd 1920x1080 content coded in x264 packed in matroska mkv, was almost watchable. Anyway. The X2 5000+ clocked at 3.0 GHz playback hd content at its full beauty, except some µsec. in extreme situations like in Casino Royal at the very beginning, where the picture is shuttering.
... but what am I doing wrong? I use ffdshow. Windows is a no way. Was just testing with it on how it performes compared to linux x64. By the way. I wasn't able to compile mplayer to work with coreAVC like described in the howto. :(


Best Regards,

Josh

---

### Post by acrane1 on 2008-05-05
Hey i am having the same problem. I can play 720p videos fine but 1080p videos are a problem. I was thinking that it could be that the players have a problem playing such a large file. Since the 720p videos I download are 4-5 gbs and the 1080p are 8-9 gbs. Now reading through the forums I am wondering if my computer isn't powerful enough. I just built it about two months ago. I have.

AMD Anthlon 64 X2 Dual Core processor 4000+
2.0 Gib of ram
Nvidia 8500GT graphics card with latest driver(not the beta but full release)
I'm running Hardy 32bit up to date

does anyone know if its my computer thats the problem or a hardware problem?

---

### Post by bsmith1051 on 2008-05-06
Your Athlon 4000 isn't powerful enough -- even on Windows -- to playback 1080p.  But your 8500GT videocard supports full h.264 acceleration... under Windows!

One possible bright spot in all of this: CoreAVC is coming to Linux?!
[http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/)

---

### Post by unlotto on 2008-05-09
I'm fairly certain an athlon x2 4000 would be enough with mplayer and CoreAVC. I've just had success with my dell m1330 with a core2duo 2.1ghz (t8100), where any 1080p file plays perfectly with coreavc. ffh264 which is the codec that ffmpeg and mplayer uses is unfortunately not quite up to speed yet. If you can spare the 15bucks that CoreAVC costs you can take a look at [http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation) It does require you to compile mplayer. There is an easier way with apt-build, which i've written about [_here_]("http://utilitybox.org/ubWiki/index.php?title=Mplayer_h264_linux"). It's in rough steps and not particularly clear, so it is not fit to be pasted as a tutorial here.

---

### Post by pwn on 2008-05-23
I had the same problem when using -vo gl in mplayer for playing 1080p. The performance was horrible that the movie was not watchable at all. It was bearable when using -vo xv.

I compiled mplayer from svn today, and patched it to use coreavc for linux. Now it plays using -vo gl much better.

---

### Post by olavjunior on 2008-05-24
Do you need to pay for the coreavc codec? And I'n not quite up to speed on this how to [http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall](http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall) > 3) Install CoreAVC to /usr/lib/win32/CoreAVCDecoder.ax  Should I just copy CoreAVCDecoder.ax to this folder, or install through wine?

---

