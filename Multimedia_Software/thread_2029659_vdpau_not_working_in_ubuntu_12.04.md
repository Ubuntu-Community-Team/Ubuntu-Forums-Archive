---
title: "vdpau not working in ubuntu 12.04"
date: 2012-07-20
forum: Multimedia Software
---

### Post by jakerock on 2012-07-20
Hi
Anyone's been able to get vdpau working in ubuntu 12.04? Card is nvidia 9200M GT, driver version 302.17 from ubuntu addition drivers.
Playing a 720p x.264 vid pushes cpu to 50%, in other linux distro's that i have installed earlier on this laptop would use 15% cpu playing the same vid.

---

### Post by bobsan on 2012-07-20
Bug report here. Maybe you should add an "affect me too" to it.

[https://bugs.launchpad.net/unity/+bug/993397](https://bugs.launchpad.net/unity/+bug/993397)

---

### Post by jakerock on 2012-07-20
Minimizing the smpalyer window while the video is playing brings cpu usage down to 5%. Bringing it to focus again and checking "top" shows Xorg and compiz each taking 20%, while mplayer still remaing at 5-6%. Looks like its GUI system thats the issue, not nvidia vdpau or mplayer.

Will add to that bug report, thanks bobsan!

---

### Post by sudodus on 2012-07-20
Try a lighter desktop environment, for example Xubuntu with XFCE or Lubuntu with LXDE. If you have a broadband internet connection, I suggest that you download the iso files and try these Ubuntu versions live (booted from a CD or USB drive).

I need Lubuntu to play high definition video (720p and 1080p).  Windows XP will outperform vanilla Ubuntu on my 'middle-aged but once powerful computer'.

---

### Post by james_xxx on 2012-07-20
I don't think this has anything to with your Desktop Environment.

I also ran into this problem on every machine I have with NVIDIA graphics, including a Core 2 Quad desktop.

The only solution I found was to add the xorg-edgers PPA, update and upgrade.

The instructions are here:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

@sudodus: Are you sure you know what vdpau is, and what it's for? (I'm not saying you don't.) 

If you are using vdpau with a compatible NVIDIA GPU, it should play 720p and 1080p videos just fine, even on fairly weak CPUs.

---

### Post by jakerock on 2012-07-20
Ok, installed gnome-shell. booted into it and played the same video. xorg uses 4%, mplayer uses 4% cpu and gnome-shell process uses 30%. This is very strange :-/

---

### Post by jakerock on 2012-07-20
[james_xxx]("http://ubuntuforums.org/member.php?u=118811") solution brought the cpu usage down considerably!

---

### Post by sudodus on 2012-07-20
> **james_xxx said:**
> ...

@sudodus: Are you sure you know what vdpau is, and what it's for? (I'm not saying you don't.) 
...

Yes, I can use it myself with mplayer in Lubuntu 12.04 and nvidia GeForce GT 430, it makes the computer use the GPU instead of the CPU. But it does not always make the video play well, although it decreases the CPU load to very low values. Sometimes I get better results with ultra-light DE and using the CPU (that is not using VDPAU).

---

### Post by james_xxx on 2012-07-20
sudodus,

Yes, you do clearly understand!

If things are working well for you, I would not want to tell you to do anything differently. 

However, after upgrading to 12.04, I was not able to get vdpau working well (if at all) on any machine, until installing the packages from xorg-edgers.

After doing that, things began working really well again, even on my Intel Atom-based mini-top.

---

### Post by sudodus on 2012-07-20
I see your point. When I get time for it, I'll try installing the packages from xorg-edgers and test if VDPAU will work better :-)

---

### Post by Lido on 2012-11-30
I installed the edgers update, but this doesn't fix the VDPAU playback in MythTV. Also, it doesn't even look like VDPAU or the nVidia driver is installed even though all the new entries in the Additional Hardware control panel seem to be active. Do I need to specifically download something from nVidia? Also, I'm still getting the "Failed to Initialize Video Playback" error message when I try to watch a recording with MythTV when VDPAU is selected in the playback settings. Has anyone gotten VDPAU working with MythTV under 12.04?

```
$ vainfo
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/nouveau_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

---

### Post by sudodus on 2012-11-30
Today I have VDPAU running in 12.04. I use a proprietary nvidia driver proposed and installed by jockey-gtk (no download directly from nvidia's web site). And after upgrading from 10.04 Ubuntu and 11.04 Ubuntu Studio, my card is better supported. Now VDPAU is doing well, so I get as good video rendering as when using the processor (and a light desktop environment).

But now I'm used to Lubuntu and its desktop, so I stay there even with VDPAU. I have no memory of installing the packages from xorg-edgers, I think the upgrade to a newer version of the OS and nvidia driver did it.

Sorry I have no experience of Myth TV.

---

