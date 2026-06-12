---
title: "Mythvideo wifi NFS slow and choppy, MythTV recordings fine"
date: 2008-12-10
forum: Mythbuntu
---

### Post by nowhere@cox.net on 2008-12-10
Title says it all! I mounted the videos folder via NFS over an 802.11g network and it is immediately choppy (like 1/2 second video, 1/2 second pause over and over). MythTV streams it's recordings flawlessly over the same connection. Mythmusic works fine too but that's a lot less data.  All video and recordings are standard def and some are transcoded to mpeg4 and some not. The choppy video doesn't depend on the type of video codec of the file being viewed either. The same video played locally on the front works fine with the same settings. I just didn't mount the video NFS folder and dropped a file there instead to test. 

Is there some setting I have goofed in Mythvideo or in setting up NFS? I just left mythvideo settings as default at setup. 

Thanks!

---

### Post by whosmatt on 2008-12-23
> **nowhere@cox.net said:**
> Title says it all! I mounted the videos folder via NFS over an 802.11g network and it is immediately choppy (like 1/2 second video, 1/2 second pause over and over). MythTV streams it's recordings flawlessly over the same connection. Mythmusic works fine too but that's a lot less data.  All video and recordings are standard def and some are transcoded to mpeg4 and some not. The choppy video doesn't depend on the type of video codec of the file being viewed either. The same video played locally on the front works fine with the same settings. I just didn't mount the video NFS folder and dropped a file there instead to test. 

Is there some setting I have goofed in Mythvideo or in setting up NFS? I just left mythvideo settings as default at setup. 

Thanks!

I'm not using wireless, but I had a choppy video problem when using NFS.  I fixed it by telling the video player to buffer more data.

my video player command in myth:

```
mplayer -fs -zoom -quiet -cache 8912 -cache-min 4 -vo xv %s
```

hope that helps.

---

### Post by ian dobson on 2008-12-23
Hi,

Or maybe try using Samba/CIFS, in my tests I found CIFS quicker than NFS on the same hardware/network configuration.

Regards
Ian Dobson

---

### Post by nowhere@cox.net on 2008-12-29
OK I'll try it. I already run a samba share on the mythdata folder to allow family to drop music there...

Thanks

---

### Post by SeanOB on 2008-12-29
I have a similar issue - except that I'm using a 1Gbit Wired Ethernet and nfs.

I have no issues with streaming HD shows from my backend.  Shows that I'd assume would take more network bandwidth to stream than a DVD - as 720p (or 1080i) > 480p.

CPU usage is ~80% when watching a DVD iso over mythvideo.
CPU usage is ~30% when watching an HD show.

I'm using the internal player with the 'High Quality' setting on the playback page.  I'd rather not switch to using mplayer or xine - since my lircrc is all setup for myth.

I can really see the problem when the camera is panning a full scene.

I have no idea of what to look for. Any help would be great!

-Sean

---

### Post by newlinux on 2008-12-29
just as an FYI, myth by default (I think, there is a setting for this, but I think the default is to use myth's own streaming protocol) uses it's own streaming protocol when viewing recordings, and uses whatever network streaming protocol you have setup (NFS, CIFS/SAMBA, FUSE/sshfs) for videos, music, and pictures. So that might be one reason recordings and livetv work fine and others do not. That points to an issue with your NFS connection. You probably need to tune it a bit, or use CIFS and tune that, or even try sshfs, but for me sshfs, although more secure and reliable, is slower.

---

### Post by newlinux on 2008-12-29
> **SeanOB said:**
> I have a similar issue - except that I'm using a 1Gbit Wired Ethernet and nfs.

I have no issues with streaming HD shows from my backend.  Shows that I'd assume would take more network bandwidth to stream than a DVD - as 720p (or 1080i) > 480p.

CPU usage is ~80% when watching a DVD iso over mythvideo.
CPU usage is ~30% when watching an HD show.

I'm using the internal player with the 'High Quality' setting on the playback page.  I'd rather not switch to using mplayer or xine - since my lircrc is all setup for myth.

I can really see the problem when the camera is panning a full scene.

I have no idea of what to look for. Any help would be great!

-Sean

I'd take a look at your frontend logs and see what is happening when you play dvds as opposed to HD - that CPU usage is strange. What CPU are you using? what GPU? Are you using xvmc? By default the Hight quality playback profile uses a much more processor intensive deinterlacing method (yadif or yadif2x) than it does for 1080i playback (linear blend). That could be part of the problem. Try using a less cpu intensive deinterlacer for your lower resolution playback.

---

### Post by SeanOB on 2008-12-29
My *new* frontend build:
ASUS P5N7A-VM LGA 775 NVIDIA GeForce 9300/nForce 730i HDMI Micro ATX Intel Motherboard
ASUS Black SATA DVD-ROM Drive Model DVD-E818A3T BULK
Western Digital 500GB GreenPower3.5" SATA Bulk/OEM Hard Drive WD5000AACS
Intel Core 2 Duo E8400 3.0 GHz 6M L2 Cache 1333MHz FSB LGA775 Dual-Core Processor
CORSAIR 450w VX Series 12v ATX 80 Plus Certified Power Supply
CORSAIR XMS2 4GB ( 2 X 2GB ) PC2-6400 800MHz 240-pin DDR2 CL5 Dual Channel Desktop Memory Kit - TWIN2X4096-6400C5

So - to answer your questions:
CPU - Core2Duo E8400 3GHz
GPU - GeForce 9300 (not using VDPAU (but I can't wait!))

I can try to tone down the scaling / deinterlacing for dvd isos.  Deinterlacing shouldn't make a difference - since DVDs are all progressive -- right?  Or are some interlaced?  I'll also try playing directly on the backend and with other players.

-Sean

---

### Post by nowhere@cox.net on 2009-01-11
Just to let you all know, I dumped the NFS mount and switch all my media mounts to Fuse/sshfs last night. Everything seems to stream much much better. Still using the 802.11g with a very weak signal on the frontend but all seems better.

---

### Post by SeanOB on 2009-03-30
Also switched to SSHFS/FUSE - and it's a dramatic improvement!
It seems to be all better now.

---

### Post by nowhere@cox.net on 2009-04-01
Hehe I love the April 1st color scheme LOL

Sean, I also built a cardstock and tin foil parabolic antenna reflector that I slip over the antenna of the router and it made a huge signal improvement. This also helped the choppiness/speed...

---

