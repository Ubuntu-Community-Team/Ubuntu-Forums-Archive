---
title: "Vlc plays some files with  green borders"
date: 2015-02-03
forum: Multimedia Software
---

### Post by Evil Wayz on 2015-02-03
Not sure why, but I am getting a green border on the right side and sometimes the bottom of video when I use VLC player.  I do not get this effect when I use Totem or gnome mplayer.  
[IMG]http://i59.tinypic.com/2afdegn.jpg[/IMG]
I also get gray lines at the top and sides of the video if I am playing video and i shift focus to another window, i have to back down from fullscreen and then fullscreen again to make them go away.  

Any suggestions?

---

### Post by %(gej%) on 2015-02-03
I also noticed the same problem :(

---

### Post by mc4man on 2015-02-03
What version of vlc?

---

### Post by Evil Wayz on 2015-02-03
VLC media player 2.2.0-rc1 Weatherwax (revision 2.2.0+ppa2.5)

---

### Post by mc4man on 2015-02-03
> **Evil Wayz said:**
> VLC media player 2.2.0-rc1 Weatherwax (revision 2.2.0+ppa2.5)
I had seen the green line thing at some point in the past, maybe early in the life of 2.2 
(whether it was just the vlc version,  some setting or format of video  I unfortunately  don't recollect. 

I just tested that build a while ago & it is fine here with vids I have. 
When you say "some"  can you post the vid type/format, I seem to remember something about mpeg2 (dvd video),  mediainfo will supply if you don't know

---

### Post by Evil Wayz on 2015-02-03
I checked real quick and avi seems to be fine, its MPEG-4 video (video/mp4) that produces the green lines.  However, all video is now producing hte gray lines at the edges when I shift focus, so I suspect that might be a driver issue with my HDTV.

---

### Post by mc4man on 2015-02-03
The focus issues I've never seen, as far as the green line -
Do they happen with the default settings? You can check by renaming .config/vlc/vlcrc to vlcrc.bak & restarting vlc
Do they occur if you change the vo or hardware acceleration options?
(- Tools > preferences > Video or Input respectively

If you can provide a small sample of problem file would take a look. This is a decent upload site
[http://www.datafilehost.com/](http://www.datafilehost.com/)
Or the vlc master ppa has resolved their 14.04 builds to some extent, maybe try vlc-3.x from there.
(- you could also try 2.2rc2 which is in the media ppa though can't see it being different than rc1 in this regard

---

### Post by Evil Wayz on 2015-02-03
Right now I can't get VLC to start except from command line.   What should I try changing the vo and hardware accel settings to, respectively?  I had to set them back to automatic because otherwise the HEVC codec wouldn't work.

---

### Post by Evil Wayz on 2015-02-03
disabling hardware acceleration got rid of the green line, but don't I need that?  This is my video card:
```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

```

---

### Post by mc4man on 2015-02-03
> **Evil Wayz said:**
> disabling hardware acceleration got rid of the green line, but don't I need that?  This is my video card:
```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

```
Well 2 things - 
The value these days of hwaccel is debatable, depends heavily  on the video source & obviously the hardware. Older hardware that can benefit  usually has crappier support for hwaccel & newer hardware with good to excellent support doesn't really need it in many cases. 

Ex. - playing a vid with fairly high bitrate, scr. 1 with hwaccel, screen 2 without - 
> Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 3 frames
Format settings, GOP                     : M=3, N=33
Muxing mode                              : Header stripping
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 59s 977ms
[COLOR="#0000CD"]Bit rate                                 : 49.0 Mbps[/COLOR]
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels



For me it really doesn't matter, ck. the system use numbers. So while the individual # for vlc is dramatically lower,  overall of little consequence...

But for the version of vlc in 14.04 or in the Media ppa it's a moot point for nvidia, those builds don't have vdpau enabled in vlc.
(vlc requires that the libav or ffmpeg it's built off of supporting vdpau, in 14.04 libav doesn't.

So if you were inclined to see if vdpau benefits you & your hardware you'd need to use a vdpau enabled vlc. Options for that are - 
Build vlc yourself
I have another ppa with vlc 2.2 (rc2) that has vdpau support. It does require that you use some newer libraries, ect. I can point you to if desired though not sure what your gains will be with a GeForce 9400 GT

Or go to a 15.04 install where libav does support vdpau so vlc in 15.04 will also (to me 14.10 is already dead but that is another option..

---

### Post by Evil Wayz on 2015-02-04
I believe we have passed the bounds of my knowledge of linux.  Although, is there any functionality in rc2 that could benefit someone with an older computer/ graphics card?

---

### Post by mc4man on 2015-02-04
> **Evil Wayz said:**
> I believe we have passed the bounds of my knowledge of linux.  Although, is there any functionality in rc2 that could benefit someone with an older computer/ graphics card?
No, rc2 just has a couple of very minor bug fixes & 3 security related commits.

So if "disabling hardware acceleration got rid of the green line" then just leave it that way in vlc's settings

---

### Post by Evil Wayz on 2015-02-04
If you feel like it, post the ppa with vdpau support, who knows it might be worth something.

---

