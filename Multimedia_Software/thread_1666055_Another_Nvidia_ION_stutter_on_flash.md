---
title: "Another Nvidia ION stutter on flash"
date: 2011-01-13
forum: Multimedia Software
---

### Post by Handonam on 2011-01-13
Hey all,

I was able to get this working a while ago, but I reinstalled Ubuntu 10.10 and I can't seem to get it this to work anymore.

The problem is that flash 1080p videos are stuttering. The CPU is under max load when i try to run the 1080p videos on youtube.  I have adobe flash 10.2 beta running, and i installed libvdpau1.


Also, I just tried running xbmc's youtube app, and that works perfectly. Here's a sample of the video debug info from xbmc:

[INDENT]D(Video: h264, yuv420p, 192x1080 [PAR 1:1 DAR 16:9], 3519kb/s) p(vq: 98%, dc:ff-h264_vdpau-vdpau, MB/s 3.01, drop:5, pc:1)

W( FPS:24.00 CPU0: 50% CPU1: 11% CPU2: 25% CPU3: 14%)[/INDENT]

batman beings 1080p .mov file works flawlessly as well.



So i'm pretty convinced something is wrong with the adobe flash. I've tried the two latest nvidia beta drivers for linux 64 (currently on 260.19.29)

Intel Atom
Nvidia Ion
4gb Ram
Ubuntu 10.10 64bit

edit: yea, i just right clicked it, showed video info, and it says "Software video rendering".  :(

---

### Post by tjones00 on 2011-01-13
Edit: nvm I thought you didn't install vdpau.[URL="http://ubuntuforums.org/showthread.php?t=1037625"]
[/URL]

---

### Post by Handonam on 2011-01-13
woow haha okay i figured out what i just did.  I downloaded the flashplayer10_2_p2_32bit_linux_111710.tar.gz, but extracted it to a typo'd folder.
"flashpluin-installer" instead of "flashplugin-installer".

it's still really bizzare though, because when i rightclicked the youtube video, it showed "About Adobe Flash Player 10.2.161.49".  That's probably one of the weirdest things i've ever seen.


in short: my stupidity.


Thanks though! gotta mark this as solved.  In case anyone needs to do a flawless 1080p installation:
1. Install Nvidia drivers that are around version 260+ (like [this one]("http://us.download.nvidia.com/XFree86/Linux-x86_64/260.19.29/NVIDIA-Linux-x86_64-260.19.29.run")).  This can be done by 
 a. closing the gdm 
> sudo etc/init.d/gdm stop 
 b. running the nvidia .run file. 
> sudo sh NVIDIA-linux-x86_64-260.19.29.run
 c. finish install, and start gdm 
> sudo etc/init.d/gdm start
2. Then install flash and libvdpau1 if you dont have that already: Instructions taken from [here]("http://askubuntu.com/questions/16172/getting-flash-10-2-gpu-acceleration-working"):
> 
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz)
tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz
sudo cp libflashplayer.so /usr/lib/flashplugin-installer/


Oh, and turn set your appearances  to "no effects" :)

---

