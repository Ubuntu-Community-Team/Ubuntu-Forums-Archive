---
title: "AGP graphics card upgrade question"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Miester_M on 2009-07-20
I'm a newbie in the ubuntu world but I'm starting to get the hang of it. I just bought a couple of trinkets for my aging socket 478 mobo to give a little boost in the horsepower department. I bought a p4 3.0 ghz prescott socket 478 cpu & a zalman 9500 cpu cooler. I wanted to turn my rig into a decent gaming machine that can also handle hd content while being ubuntu friendly. However, here lies the dilemma. Judging from what I read in the forums, the gpu(s) I want currently have driver compatibility issues w/ ubuntu. I was debating between ati radeon hd 3850 or 4650. They both have decent specs and have dedicated decoding @ least 720p hd content (i.e h.264). That's a major plus due to the fact that the prescott is an outdated cpu. Btw, my current specs are listed in my signature. :D

Here are the gpu(s): click on the "[COLOR=Red]@[/COLOR]" for the newegg link.

**[SIZE=1]SAPPHIRE 100228L Radeon HD 3850 512MB 256-bit GDDR3 AGP 4X/8X HDCP[/SIZE]** - [COLOR=Red][@]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102730")[/COLOR]
[SIZE=2]**[SIZE=1]XFX HD-465X-ZPF2 Radeon HD 4650 1GB 128-bit DDR2 AGP 8X HDCP[/SIZE]** [/SIZE]- [COLOR=Red][@]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150433")[/COLOR]

Do any of you guys experienced any problems running these cards on ubuntu 9.04? What's your take on it? What else would you guys recommend? Thanks guys!

- RL


[B][B][SIZE=1]

[/SIZE][/B][/B]

---

### Post by zetanuxi on 2009-07-21
I would go with the HD4650 because for playing HD and games, 512MB for memory on the other one might not be enough. I run an older AGP card (x1600 Pro) and I cant get it to work with Ubuntu at all. 

What distribution do you use? I'm running Jaunty and when I try to install the drivers from the ATI site, I'm told that my distribution is not supported. You might want to keep that in mind. I would go with Nvidia just because it seems to be supported more than ATI cards. And a lot less of a hassle to get working.

---

### Post by Miester_M on 2009-07-21
> **zetanuxi said:**
> I would go with the HD4650 because for playing HD and games, 512MB for memory on the other one might not be enough. I run an older AGP card (x1600 Pro) and I cant get it to work with Ubuntu at all. 
 
What distribution do you use? I'm running Jaunty and when I try to install the drivers from the ATI site, I'm told that my distribution is not supported. You might want to keep that in mind. I would go with Nvidia just because it seems to be supported more than ATI cards. And a lot less of a hassle to get working.
 
[SIZE=2]Thanks Zetanuxi! I was leaning towards the 4650 gpu myself. I'm a casual gamer so I'm not looking for a framerate monster or anything. I just want flawless performance when playing hi-def content (720p or maybe 1080p). I've asked others about this in other forums and they said that the 3850 would better as far as compatibility is concerned. Plus, they said that the 3850 gpu is already an overkill for my aging p4c800-e mobo. I know Nvidia's drivers have better linux support but they abandoned the agp game a long time ago. The latest Nvidia agp gpu (@ least in Newegg) is the 7600gs. I've read somewhere that it only does partial h.264 decoding. The 3850 & 4650 takes 90-100% of all the hi-def decoding off the cpu. Which is a big benefit in my case since I'm still using a single core p4. I'm currently running the Ubuntu 9.04 (Jaunty) distro. In my current setup, I'm running it w/ an OEM ATI Radeon 9800 pro w/ the default drivers that ran since the Jaunty install. I'm guessing its the default mesa drivers since I haven't messed w/ any other ATI drivers (open source & proprietary). I'm still a newb when it comes to this Ubuntu driver stuff. Should I downgrade my distro to Hardy or Intrepid?[/SIZE]

---

### Post by Miester_M on 2009-07-23
Bump. Anyone else wanna chime in?

---

### Post by roller on 2009-07-28
I have a Pentium 4 @ 3.06GHz socket 478 with (currently) 1GB DDR 400.
The computer had an Saffire ATI 9600 XT AGP 256MB but one day the VGA died so I stopped using this machine.

A few days ago I bought an Gigabyte ATI HD 4650 1GB AGP to bring it back to life and act as a media center.

The problem is I can't get the graphics card to work.
I even tried to download the ATI proprietary driver, build the debs and then install them.

All wen fine until "aticonfig --initial". I got a message saying there is no compatible hardware.

Is it because it is the AGP version?

This one does not passes audio through the HDMI port in Vista as stated in the box and the PCIe does as I've seen on their webste and they say to not install the ATI generic drivers in any version of Windows but run their own CD.


And the only purpose of this HTPC was to have Mythbuntu and XBMC standalone :(

I don't like M$. Stop.

---

### Post by shawnvdm on 2009-11-01
[LIST]
[*]I have a AMD X2 4400 and recently put a HD3850 sapphire card in. The xorg.conf was a real slog.
[*]The card works great except for h.264 playback. Well I am assuming card but it could be the processor.
[*]I play video from crunchyroll and I usually have to boot into XP to watch as on linux system the video is very jerky at 720p playback. I tried a few test video files for 1080p but the system can't do it. The video plays slow and audio goes out of sink. I have read that this may just be due to the poor support from the current video players.
[*]I bought the card hoping to keep my existing 939 system alive for a bit longer (cash) but enjoy some of the new video offerings, but I find the card has better performance under XP and delivers upscaled 1080p (720p to 1080p) without the jerking in XP.   It could be that there are still a few magic options to select in xorg.conf, but I have not read about them.
[*] [http://forums.amd.com/game/messageview.cfm?catid=279&threadid=106911&enterthread=y](http://forums.amd.com/game/messageview.cfm?catid=279&threadid=106911&enterthread=y)
[*]This seems to suggest that there is also a limitation to the type of h.264 the cards will decode
[*]Shawn
[*]PS - using indentation as my new lines keep getting stripped
[/LIST]

---

### Post by WSmart on 2010-05-01
Check out the Wiki GPU lists for Nvidia and AMD.  They show all the fill rates for the cards going back to forever.  Notice that each generation of cards has a full range of performance, so you can't just think newer is faster.  Some of the newer cards are slower then the Nvidia FX generation or the AMD R300's.  These lists are very helpful for finding the right card.  

Nvidia's 7950 runs about 13 GT/s fill rate while AMD's 3870 runs a bit less then that, maybe 12.  

With these newest AMD AGP cards, it looks like Ubuntu 8.10 will install a properly working driver from the driver install applet. Unless things have changed, it looks like support has been dropped after that. The Radeon driver is bring(ing) 3D support to these now, though you have to wonder if they (will) have the same problems with the newer AGP cards.

PCIe is very attractive.  For $50 bucks you can get a new, low end version of the newer GPU's that runs around 10 GT/s, and it comes with no fan, a heat sink. But you have to be careful, again, the slowest versions run about 3-5 GT/s.

Thanks all!

---

