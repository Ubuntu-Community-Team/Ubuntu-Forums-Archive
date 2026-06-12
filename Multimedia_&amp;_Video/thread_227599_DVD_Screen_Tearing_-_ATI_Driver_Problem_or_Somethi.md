---
title: "DVD Screen Tearing - ATI Driver Problem or Something Else?"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by datek2517 on 2006-08-02
I'm fairly new to Ubuntu, and I've been trying to deal with DVD playback on Dapper 6.06.  I have VLC, mplayer, Kaffeine, and Xine installed.  I have followed the walkthrough [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") to install and use what I assume are the latest ATI Linux drivers (I'm running 8.27.10, confirmed by fglrxinfo).  I'm trying to use my myriad of movie players to watch a DVD movie (on disc), yet I am getting noticeable screen tearing.  At times of higher motion, such as when the screen pans, the effect is pronounced.  I have checked the options of both Xine and VLC to enable the Xv package for video playback and enable de-interlacing, to no avail.  

The problem is, I don't know what's causing this.  I used Automatix to obtain the players and some video codec packages, so I'm not sure what could be causing it.  Is there a certain DVD codec package that I could try out?  Does this seem like it could be caused by a slow DVD drive, or by my ATI driver set?  I have Windows XP Pro on a separate partition with dual boot, and the DVD runs without screen tearing under Windows XP.

Here are some details for my system:

Ubuntu Dapper Drake 6.06 (latest i686; has both CPU cores enabled)
AMD Athlon 64 X2 4200+
ATI Radeon X1800 XT 256MB
250 GB SATA HDD
2 GB DDR2 RAM
BenQ FP202W 20.1 widescreen LCD monitor
1680 x 1050 @ 60 Hz screen resolution (DVI)

Thanks for your help!

---

### Post by whatever on 2006-08-02
it's a driver problem.
on X1k series cards the Xvideo port does not use classical overlay, but pixelshaders instead. this is a known issue, see [http://rage3d.com/board/showpost.php?p=1334385433&postcount=6](http://rage3d.com/board/showpost.php?p=1334385433&postcount=6)

---

### Post by datek2517 on 2006-08-02
Well that's good to hear, I guess.  But is there any kind of temporary solution until the new release?

---

