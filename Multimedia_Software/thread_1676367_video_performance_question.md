---
title: "video performance question"
date: 2011-01-27
forum: Multimedia Software
---

### Post by parish on 2011-01-27
I'm running Ubuntu 10.10 on an old small form factor PC with an AMD Sempron 2400, 1GB RAM, and an nVidia 5200 graphics card 128MB. OK, so a low-spec machine (but that's the great thing about Linux right? Don't need high-end h/w) but it works just fine, except that it can't play full HD (1920x1080) MPEG-4 video. Very jerky and lots of dropped frames. Same in both Movie Player and VLC.

I can't afford to increase the RAM and as it's a SFF I can't just swap the mobo and CPU for something faster so I'm wondering whether getting a higher spec graphics card would make any difference?

I'm using the nVidia proprietary binary driver (latest version) and searching the forums I found a post where someone said that the nVidia driver needs at least a 512MB card for HD video.

A colleague has a higher spec nVidia card (7600 IIRC) that he'll sell me, but before I spend any money, is this likely to improve things? How much does the graphics card affect performance, or is it simply a case of the machine overall just isn't high enough spec?

---

### Post by cascade9 on 2011-01-27
The machine just isnt a high enough spec to play 1080p. You might just get away with 720p, but only just. 

Upgrading your video card to a 7600 wont help much, if at all. To play 1080p on a system of that level, you would ned VDPAU (nVidia hardware video decoding) and the earliest nVidai models to support that are (most) of the 8XXX cards. 

A PCI 8400GS might work. I'm assuming that you've only got PCI slots and an AGP slot. If you have a PCIe slot you should be able to get a cheap GT210/220 that would do VDPAU. But I'd doubt that a sempron 2400+ system will have a PCIe slot. All the sempron 2400+ I know of are socket A, and I've never seen a socket A motherboard with a PCIe slot.

---

### Post by parish on 2011-01-27
Thanks for the prompt and detailed answer.

You are correct, AGP slot only.

I guessed it would probably be the case that the machine is just too low spec. It's no big deal really though, but it would have been nice to get it working.

---

### Post by cchhrriiss121212 on 2011-01-27
You can try a few tweaks:
[http://crunchbanglinux.org/forums/topic/10510/fix-lag-with-hd-video-on-vlc/](http://crunchbanglinux.org/forums/topic/10510/fix-lag-with-hd-video-on-vlc/)

---

