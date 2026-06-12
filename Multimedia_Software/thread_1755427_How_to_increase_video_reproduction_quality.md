---
title: "How to increase video reproduction quality"
date: 2011-05-11
forum: Multimedia Software
---

### Post by johncoss on 2011-05-11
Hi,
I am relatively new to Ubuntu so don't scram if I ask something stupid. :)
When I watch movies on Ubuntu I noticed that quality of reproduction is not good as in Windows. All movies seems to have some sort of contrast problem which I don't know how to fix. This problem is not present in Windows (XP/7) and stand-alone DVD players play them also correctly.
Here are images (AVI, DivX format)
Windows version:
[http://i52.tinypic.com/125hlis.png](http://i52.tinypic.com/125hlis.png)
Linux version:
[http://i56.tinypic.com/tz53t.png](http://i56.tinypic.com/tz53t.png)

Also here is MKV format which is noticeably even sharper in Windows:
Windows version:
[http://i53.tinypic.com/2lmqxqe.png](http://i53.tinypic.com/2lmqxqe.png)
Linux version:
[http://i53.tinypic.com/15gfmlt.png](http://i53.tinypic.com/15gfmlt.png)

Note: I didn't wanted to include them in post since they are quite big and I didn't want to do JPG compress since they might lose quality. Try not to resize them.

On Ubuntu I installed some 'extra' codecs (might be proprietary) via Software center. I use standard movie player that comes with 10.10, but for MKV I use VLC since mkv don't run in standard movie player. On Windows I use k-lite codec pack and GOM player. My guess is that Windows solve those sharpness and contrast issues by using some playback filters (possibly contained in k-lite codec pack) that are unavailable in Ubuntu. I installed proprietary video driver for ATI RADEON 2600. 

Sorry for long post, but I really want good quality reproduction in Linux. Thanks in advance :)

---

### Post by Duncan Williams on 2011-05-11
I dont know if your card uses the catalyst (ati-proprietory) drivers as available in `additional hardware' (not the open source ones).
If you have catalyst control centre you can adjust settings while video is playing.

---

### Post by no2498 on 2011-05-11
i can change settings in totem
i had to really look hard to find them this time on 10.04 
but you can change them on the fly

---

### Post by johncoss on 2011-05-12
I tried to install ati drivers for my card from their site (some file that ends with .run). However when I installed those drivers my system became sooooooo slow, so I uninstaled them. I tried to install them from restricted drivers managers, but it says some error about installArchiveError. Strangely, this worked first time when I installed system, so I guess that manufacturer's drivers didn't uninstall correctly. Now I have to uninstall manually driver to restore 3D functionality...
Will continue researching on reproduction when I fix this problem :)

---

### Post by Duncan Williams on 2011-05-13
What I sort of did. a few week back.
In synaptic package manager, search for ati, disable everything relating to it.
reboot (in failsafe graphics mode if need be)
goto `additional drivers'
install ati proprietory drivers (fglrx).

---

### Post by WannabeFantasma on 2011-05-13
Try decreasing brightness in the media player (Not sure if it has that)

If not try xbmc(standalone), and try it with that, I get good Movie Quality with that.

Note: Tested XBMC and VLC both in windows couple of months ago, VLC colours where washed out like your linux version screenshots.

---

