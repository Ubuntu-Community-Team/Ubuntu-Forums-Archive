---
title: "Guide to 1080p in mythtv/mythbuntu with Nvidia"
date: 2009-03-28
forum: Multimedia Software
---

### Post by knutz on 2009-03-28
Hi all mythbuntu and mythtv users.

I've been putting together my own mediacenter the past days, and i had som problems concerning the activation of the VDPAU acceleration (ie. H.264). 

First of all i installed mythbuntu 8.10.
Specs:
ASUS motherboard with a Geforce 8300 
AMD Athlon 4850E
ASUS Mycinema 7131
500 GB WD Greenpower HD
2 gb RAM
Samsung 40" flatscreen TV via HDMI

I downloaded a 1080p sample and tried playing it in mythtv (mplayer) and my cpu was loaded 100% and the audio and video was unsynced and the picture was laggy.

So what to do to to get the best video result using VDPAU acceleration(and it can be done very easily when knowing what to do):

First of all install mythtv/mythbuntu
Open your Synaptic Package manager.
Add 
```
 deb http://www.avenard.org/files/ubuntu-repos intrepid release
```
to your repositories.
Install the [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) key.
Update your synaptic package manager and install all upgrades.
Your mythtv and nvidia driver should be updated now. 

Reboot.

Open mythtv and go setup a playback profile where choosing the nvidia vdpau acceleration as decoder and VDPAU as renderer. (I use no deinterlacing)
Then under Video settings>Player settings and your default video player should be
```
mplayer -fs -zoom -quiet -vo vdpau -vc ffh264vdpau,ffvc1vdpau,ffmpeg12vdpau,ffwmv3vdpau %s
```

That should give you a player able to play FullHD video without chocking the life out of your CPU.
At last i opened a terminal and wrote:
```
sudo nvidia-xconfig --no-composite
```
This made the video stop flickering/interlacing and gave me a perfect picture. 

Hope this helps. 


/knutz

---

### Post by wolfen69 on 2009-03-28
thanks for this. it will go into my "how to" archive.

---

