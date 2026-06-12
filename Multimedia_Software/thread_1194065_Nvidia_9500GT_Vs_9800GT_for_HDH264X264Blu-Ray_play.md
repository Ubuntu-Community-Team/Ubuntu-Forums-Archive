---
title: "Nvidia 9500GT Vs 9800GT for HD/H264/X264/Blu-Ray playback?"
date: 2009-06-22
forum: Multimedia Software
---

### Post by BB2008 on 2009-06-22
Hi All:

I am planning on converting my myth box into a full blown htpc. The config is as follows:

AMD Athlon 64x2 5200+ cpu
Gigabyte GA-MA78GM-S2H motherboard
ASUS EAH3450 graphics card
700 Watt ATX modular power supply

Currently, this rig stutters in any HD content playback - H264/X264 etc. I have tried practically everything - prop drivers, configuring crossfire with the on board HD 3200 graphics, vesa drivers - but it just does not work, and even gets unstable with prop drivers.

So, my plan is to get a NVIDIA 9xxx series card. I looked at two of them at newegg:
1. [EVGA 512-P3-N871-AR GeForce 9800 GTX+ 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130339")
2. [ASUS EN9500GT TOP/DI/512M GeForce 9500 GT 512MB 128-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121267")

I know that 9800 GT should be a lot more faster than a 9500 GT, but my intent is only to be able to playback HD content smoothly for my HTPC. Given that one card costs more than double the other, I would like to hear from all that have experienced these cards/similar spec'ed cards. Will I be able to use the 9500 GT for my intent, or do I need to go with 9800 GT? Please advise.

Thanks in advance!

---

### Post by xzero1 on 2009-06-22
The 9800GT may not be much faster for *video* playback. Get a card that supports gpu accelerated playback (vdapu) in linux. I think both cards support this but you may need to compile your own driver. I don't have a vdapu supported card so I don't know what quality you can expect. As an alternative you might try more of a software solution. You may have enough speed already. I would suggest getting the latest ffmpeg-mt and mplayer for playback. FFmpeg-mt allows mplayer to support multi-core playback for x264. The following threads should be of help:
[http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux](http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux)
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

---

### Post by BB2008 on 2009-06-23
> **xzero1 said:**
> The 9800GT may not be much faster for *video* playback. Get a card that supports gpu accelerated playback (vdapu) in linux. I think both cards support this but you may need to compile your own driver. I don't have a vdapu supported card so I don't know what quality you can expect. As an alternative you might try more of a software solution. You may have enough speed already. I would suggest getting the latest ffmpeg-mt and mplayer for playback. FFmpeg-mt allows mplayer to support multi-core playback for x264. The following threads should be of help:
[http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux](http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux)
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

Thanks xzero1. I tried the software method described in the thread you had linked to. Little improvement, but still not smooth. So i guess I am back to my original question - 9800 GTX+ or 9500 GT - which one is better, only for smooth HD playback...

---

### Post by ElectricBlue on 2009-06-25
If you only need HD playback the 9500 GT should be enough. If you wanted to play games then the 9800GT would be a better bet. 

I'm surprised your current card doesn't support HD video decoding. Although it just be a weak spot in ATI's driver.

---

### Post by BB2008 on 2009-06-25
> **ElectricBlue said:**
> If you only need HD playback the 9500 GT should be enough. If you wanted to play games then the 9800GT would be a better bet. 

Thanks ElectricBlue. My primary purpose is HD Playback, I am not heavy into gaming.

I guess this is where my blind spot is - I do not know how the processing (of breaking down the decoding of a H264/x264 encoded HD media) is split between the CPU and the GPU, especially in Linux/Ubuntu. If that work is done primarily by the CPU, then I guess I need to upgrade to a faster CPU since I can see (with "top") that my CPU maxes out while playing back HD encoded media. I do not know how much load is being carried by the GPU at that point in time, is there a way to find that out in linux/ubuntu?


> **ElectricBlue said:**
> I'm surprised your current card doesn't support HD video decoding. Although it just be a weak spot in ATI's driver. 

Maybe you got me wrong here - I do get HD playback, its not smooth, that is all. And it goes back again to the question I ask above, how is the processing split between CPU and GPU?

---

### Post by shirilover on 2009-06-26
In most cases, H.264 decoding is done by the CPU.
Hardware acceleration of H.264 video streams is a driver limitation.
Also, only a limited selection of encoding settings can be used.
So, if the video is not encoded with these settings, all decoding will be done by the CPU.

---

### Post by steefjeqv on 2009-06-26
Hi,

If you want to make full use of NVIDIA's VDPAU, then I suggest a passively cooled 9600 card.
Anything below a 9600 can't process HD deinterlacing fluently at the highest quality settings (temporal_spatial). This is certainly the case when using the Xine media player.
A 9500 will do HD with deinterlacing set to temporal or bob, again using Xine. The quality should be ok (no real experience with it though).
Watch out : There are 9500 cards (Gainward) who don't support VDPAU.

Always use a card with no less then 512 MB memory.

Greetings,
Steven

---

### Post by shaulch on 2009-07-26
> **steefjeqv said:**
> Hi,

If you want to make full use of NVIDIA's VDPAU, then I suggest a passively cooled 9600 card.
Anything below a 9600 can't process HD deinterlacing fluently at the highest quality settings (temporal_spatial). This is certainly the case when using the Xine media player.
A 9500 will do HD with deinterlacing set to temporal or bob, again using Xine. The quality should be ok (no real experience with it though).
Watch out : There are 9500 cards (Gainward) who don't support VDPAU.

Always use a card with no less then 512 MB memory.

Greetings,
Steven

Hi Steven ,

Are you sure regarding Gainward 9500 ?  which card you recommend ? (passive,Hdmi or DVI audio)

Thanks in advance,
Shaul.

---

### Post by steefjeqv on 2009-07-26
Hi,

I've attached a link with the non-VDPAU card in question. It seems the issue concerns the memory used (DDR2).

[http://www.gainward.com/main/vgapro.php?id=126](http://www.gainward.com/main/vgapro.php?id=126)

[http://www.nvnews.net/vbulletin/showthread.php?t=129996]("http://www.nvnews.net/vbulletin/showthread.php?t=129996")

I've been using a GigaByte 8400GS 512MB (passively cooled) for a while now. It works great, but it lacks a bit of power for HDTV with the highest quality deinterlacing. 

I prefer Gigabyte as they usually provide good (passive) cooling solutions. Even the 8400 (which runs quite hot) is kept relatively cool (60° celsius).

DVI and HDMI are basically the same regarding video quality. 
HDMI is used to prevent people from doing what they like with their hard & software. So, if you don't really need it then don't use it.

Greetings,
Steven

---

### Post by shaulch on 2009-07-26
> **steefjeqv said:**
> Hi,

I've attached a link with the non-VDPAU card in question. It seems the issue concerns the memory used (DDR2).

[http://www.gainward.com/main/vgapro.php?id=126](http://www.gainward.com/main/vgapro.php?id=126)

[http://www.nvnews.net/vbulletin/showthread.php?t=129996](http://www.nvnews.net/vbulletin/showthread.php?t=129996)

I've been using a GigaByte 8400GS 512MB (passively cooled) for a while now. It works great, but it lacks a bit of power for HDTV with the highest quality deinterlacing. 

I prefer Gigabyte as they usually provide good (passive) cooling solutions. Even the 8400 (which runs quite hot) is kept relatively cool (60° celsius).

DVI and HDMI are basically the same regarding video quality. 
HDMI is used to prevent people from doing what they like with their hard & software. So, if you don't really need it then don't use it.

Greetings,
Steven

Thanks , i'm very confused , on one side 8400GS is too weak but on the other side it has G98 GPU   (third generation of purevideo)
9400GT / 9500GT has G96 GPU (second generation - without VC-1 decoding)

which card  a person who build HTPC should buy ?

---

### Post by xzero1 on 2009-07-29
You may not need a new video card for HD playback! I recently upgraded my motherboard and am using its onboard ati 3300IGP to play hd videos in Jaunty. In fact with my cpu set at 800Mhz, I can smoothly play the itunes toy story 3 trailer (1920x1080x24) with compiz on! Even though this is a quad core Phenom II, I am convinced something is being accelerated by the gpu. According to this link  [http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45](http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45) your 3200 onboard graphics chip is close to my 3300 chip.

See this post [http://ubuntuforums.org/showthread.php?t=1224509](http://ubuntuforums.org/showthread.php?t=1224509) some xorg file options. Then try using mplayer with the -vo xv -fs option to play your videos. The playback is not perfect, but it is pretty good. It will only be accelerated when played back full screen. The key item I is to turn on textured video.

---

### Post by BroadArrow on 2009-08-09
> **shirilover said:**
> In most cases, H.264 decoding is done by the CPU.
Hardware acceleration of H.264 video streams is a driver limitation.
Also, only a limited selection of encoding settings can be used.
So, if the video is not encoded with these settings, all decoding will be done by the CPU.

Is this likely to change in the future? Is it just a matter of Linux drivers catching up with technology? 

If not, it seems to be a serious obstacle on the path to the silent HTPC nirvana. (A silent HTPC likely being dependent on splitting the heavy lifting between a fanless CPU and a GPU.)

Or am I missing some other obvious solution?

FYI, I'm currently looking for a quiet graphics card for a Mythbuntu front end HTPC. Not having had to know a lot about graphics cards before, it's a pretty steep learning curve -- and one that's not easy to climb!

---

### Post by xzero1 on 2009-08-09
I think Linux will catch up but the priorty for graphics cards is more likely getting 3d to work all/most systems rather than gpu accelerated video.

As far a HTPC, I guess it depends on how much silence you require. As I mendtioned, with my cpu running at 800Mhz, thereby reducing its fan speed and the fanless gpu doing the rest, thats a pretty good workload split -- still not totally quiet. A big consideration for HTPC needs to be case design especially in terms of cooling.
See [http://www.endpcnoise.com/cgi-bin/e/index.html?id=kvWBJK57](http://www.endpcnoise.com/cgi-bin/e/index.html?id=kvWBJK57)

---

### Post by steefjeqv on 2009-08-09
Hi,

@ xzero1 : try any of the h.264 encoded TV signals with a +5 Mbit/s bitrate. You'll be watching a slide show (or nothing).

@ BroadArrow : Nvidia's VDPAU works great. 
If I'm not mistaken you're using the DVB broadcast standard in New Zealand.
When you combine a DVB card and Nvidia graphics (8xxx or 9xxx series) with this PPA (thanks to Gerald Dachs), you'll have everything you need :

[https://launchpad.net/~gda-dachsweb/+archive/vdr]("https://launchpad.net/~gda-dachsweb/+archive/vdr")

Install everything nvidia-gda related using synaptic.
Install vdr + everything xineliboutput related. Make sure that you use the gda version.
Install everything VDPAU related, again make sure you have the gda version.

Create a channels.conf using w_scan and copy it to /var/lib/vdr.

[https://launchpad.net/ubuntu/+source/w-scan/20081106-0ubuntu1/+build/872551]("https://launchpad.net/ubuntu/+source/w-scan/20081106-0ubuntu1/+build/872551")

Start VDR with following command :

vdr-sxfe

That's it.

Greetings,
Steven

---

### Post by xzero1 on 2009-08-09
> @ xzero1 : try any of the h.264 encoded TV signals with a +5 Mbit/s bitrate. You'll be watching a slide show (or nothing).I am afraid you are mistaken....

```
ffmpeg -i toystory3-tsr**.mov
FFmpeg version git-d5ea5fc, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.23. 0 / 52.23. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on May  7 2009 20:11:39, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 5994.00 (5994/1) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'toystory3-tsr_h1080p.mov':
  Duration: 00:01:56.95, start: -9.-35035, bitrate: 9394 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1080, 23.98 tbr, 2997 tbn, 5994 tbc
    Stream #0.1(eng): Audio: aac, 44100 Hz, 5.1, s16
    Stream #0.2(eng): Data: tmcd / 0x64636D74
At least one output file must be specified
```

---

### Post by BroadArrow on 2009-08-09
> **xzero1 said:**
> I think Linux will catch up but the priorty for graphics cards is more likely getting 3d to work all/most systems rather than gpu accelerated video.

As far a HTPC, I guess it depends on how much silence you require. As I mendtioned, with my cpu running at 800Mhz, thereby reducing its fan speed and the fanless gpu doing the rest, thats a pretty good workload split -- still not totally quiet. A big consideration for HTPC needs to be case design especially in terms of cooling.
See [http://www.endpcnoise.com/cgi-bin/e/index.html?id=kvWBJK57](http://www.endpcnoise.com/cgi-bin/e/index.html?id=kvWBJK57)

Thanks for that. I've got a low power consumption dual core Intel CPU and it's sitting in a Silverstone case. It's pretty quiet currently but it needs a more powerful video card so I'm looking for a fanless nVidia card a powerful enough. I wish it were possible to search a hardware compatability list for hardware criteria (eg: video card memory, fanless, &c)

---

### Post by BroadArrow on 2009-08-09
Thanks for that steefjeqv. I think an nVidia card is my best option. I just need to find a fanless model powerful to do the job. As I posted above, it's not easy finding out (a) exactly what the requirements are (eg: for compiz, for HDTV) and (b) searching a hardware compatability list for specific components by feature (eg: fanless, memory over a given amount, &c).

---

### Post by steefjeqv on 2009-08-09
Hi,

If you're looking for decent H.264 decoding with quality deinterlacing, you'll need 512 mb memory and a 9600 card (although a 9500 might work too)

Greetings,
Steven

---

### Post by xzero1 on 2009-08-09
According to this link [http://techreport.com/articles.x/15559/10](http://techreport.com/articles.x/15559/10) the 9500GT should do fine and there will be less heat to dissipate. Notice some of the ATI cards do even better. Sadly for Linux, some of their drivers don't.

---

### Post by BroadArrow on 2009-08-13
> **steefjeqv said:**
> If you're looking for decent H.264 decoding with quality deinterlacing, you'll need 512 mb memory and a 9600 card (although a 9500 might work too)

Thanks for that. Does anyone make a fanless card with a 9600 chip? My usual vendor doesn't seem to have one from the usual suspects (ASUS, Gigabyte, &c) but maybe there are some unusual variants out there?

I've got a fanless ASUS 8400 in there in the moment which copes with low definition video and TV but of course wouldn't be up to HD. I'd love to be able to upgrade to a fanless card which could handle HD...

---

### Post by steefjeqv on 2009-08-13
Hi,

Some passively cooled cards :

[http://www.leadtek.com/eng/3d_graphic/overview.asp?lineid=1&pronameid=435]("http://www.leadtek.com/eng/3d_graphic/overview.asp?lineid=1&pronameid=435")

[http://www.sparkle.com.tw/product_detail.asp?id=82&sub_id=221]("http://www.sparkle.com.tw/product_detail.asp?id=82&sub_id=221")

[http://www.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&prod_no=1532]("http://www.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&prod_no=1532")

First I'd give your 8400 a try though. 
I'm currently watching Big Buck Bunny (1920x1080) on my system (Gigabyte 8400GS + low power AMD K9), and it runs surprisingly well.

Greetings,
Steven

---

### Post by BroadArrow on 2009-08-15
> **steefjeqv said:**
> First I'd give your 8400 a try though. 
I'm currently watching Big Buck Bunny (1920x1080) on my system (Gigabyte 8400GS + low power AMD K9), and it runs surprisingly well.


Thanks for that.

Have you had to do anything special to get it working? I've only just installed it and am using the binary drivers without having done much else. 

Seems to run OK -- except the video player (using mplayer on default Mythbuntu settings) occasionally hanging or crashing back to Mythbuntu. Might be something to do with memory settings -- I've tried Googling and searching the forums but haven't found any obvious answers yet.

---

### Post by steefjeqv on 2009-08-15
Hi,

I'm using a VDR setup (gda launchpad repository). The default Ubuntu VDR version isn't capable of using Nvidia's VDPAU. 

If you're using a standard Mythbuntu setup, I suppose you're going to have the same problem.

Have a look at this wiki, more in particular the Jean-Yves Avenard repository (Contents 2.3).

[http://www.mythtv.org/wiki/Vdpau]("http://www.mythtv.org/wiki/Vdpau")

Greetings,
Steven

---

### Post by ElectricBlue on 2009-09-01
I'm interested in an HTPC. I'd been looking at the ION options versus a more full featured system (C2D or Athlon with discrete GPU).

Can anyone share their experiences one way or the other? Please indicate what works well and what seems to be slow and/sluggish. I'm considering running a light file server off this machine as well.

---

