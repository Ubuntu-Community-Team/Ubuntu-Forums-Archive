---
title: "Video choppy after upgrade to Lucid"
date: 2010-06-14
forum: Multimedia Software
---

### Post by VOLKOV9 on 2010-06-14
I just upgraded from Karmic to Lucid.  I've never had problems with playing video files before, but now that I've upgraded to Lucid, I am, regardless of Compiz and other visual effects being on.  What I know of my hardware specs are in my sig.  I have "NVIDIA accelerated graphics driver (version current) [Recommended]" activated (and in fact, one of my reasons for upgrading was the supposedly improved NVIDIA drivers in Lucid).  VLC, MPlayer, and Totem are all choppy playing .avi's: they play smoothly for several seconds, then start skipping (audio and visual, separately), though VLC does so less violently than the others.  Similar problems, though slightly less severe, with watching flash movies in chromium.

Anyone know how to help?

---

### Post by warkior on 2010-06-28
I'm also experiencing a very similar problem.  Upgraded from Karmic to Lucid and now video playback seems choppy.  It's like the video codec can't keep up with the audio.  At times it'll freeze for a few seconds, then rapidly progress through the video stream until it catches up.

At first I thought it might be the flash plugin as I was seeing it on Youtube... however I tried playing some of my home videos in "Movie Player" and the same thing was happening.

Any suggestions or help would be appreciated.  Running an NVIDIA card with the proprietary drivers.

---

### Post by config.sys on 2010-07-08
Hi all.

I was having a similar problem with a fresh install of Lucid 10.04. I must have reinstalled it at least 6 times in the last few days trying to resolve this issue. I have a new Geforce 210 card running the latest drivers. VDPAU is installed as well. What finally resolved the issue for me was installing XBMC. I followed these directions from their site:

sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

I think this is the line that resolved the issue:

sudo apt-get install libvdpau1 nvidia-185-libvdpau



I'm not sure what it does but now videos upto 1920 by 1080p play fine in smplayer. I am still have the problem with VLC. In smplayer go to options - preferences - general. On the Video Tab change the output driver to VDPAU. I hope this helps. 

BTW - the files also played fine in XBMC.

---

