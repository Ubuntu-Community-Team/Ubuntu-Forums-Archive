---
title: "Lucid - 1080p Playback Issue - CoreAVC??"
date: 2010-05-08
forum: Multimedia Software
---

### Post by AP0ll0UK on 2010-05-08
Hi Everyone

As the title suggests I'm still having problems with with HD playback. I resolvedf the issue with normal Divx playback in VLC by making the cache bigger, for HD it just doesn't seem to make any difference, particularly in scenes where there is a lot of detail and things are moving fast.

I've had a look around and seen CoreAVC mentioned. I've seen Ripps guide which suggested installing CoreAVC through Wine, versions up to 2.0 should work according to the notes but unfortunately the installer for 1.9.5 crashes as does v2.0 under Wine. 

I've tried the installers on a Windows box and they work fine.

I must say this is becoming really frustrating and I can't seem to find a complete idiots guide to getting my system setup to do this. My PC is more than capable of playing these files and they ran fine under Windows 7, I just can't seem to either get the right config setup, or the right apps installed so that playback is much smoother.

Can anyone please help as I'm tearing my hair out over it, and for a bald guy that ain't good!

---

### Post by mistermentality on 2010-05-08
Not sure if this will help but someone else on the forums had a hd video playback in vlc and solved it. Check the post at [http://ubuntuforums.org/archive/index.php/t-1389943.html]("http://ubuntuforums.org/archive/index.php/t-1389943.html")

I find VLC plays hd fine for me when tweaked to the right video output module but the post above may be of use.

---

### Post by gradinaruvasile on 2010-05-08
For HD playback you have to have:

Hardware:

- Good CPU - core2duo or something similar, best is 2.3+ GHz - Ati (some seem to have a technology called Avivo -that helps with decoding, but didnt really lowered CPU usage in my tests) , Intel etc.
The decoding is done in software, thus the big CPU need.
I absolutely recommend mplayer-mt - this is a newer version of mplayer that supports multithreading, it is in experimental stage though - look around for it in PPAs

or

- VDPAU-compliant nvidia video card (series 8 or better - [[COLOR="Blue"]_list_[/COLOR]]("http://en.wikipedia.org/wiki/Nvidia_PureVideo")- in this case the CPU is not really relevant. The decoding is done in the video card, i ran 1080p movies on Athlon 3200+ single core at about 15% CPU usage on 8200 IGP.
To use the vdpau capabilities you need [[COLOR="Blue"]_vdpau-enabled nvidia driver and vdpau-enabled mplayer_[/COLOR]]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") .
I use the driver from nvidia's site - that one has everything needed, but i dont recommend it for beginners only if they look around a bit for its drawbacks before installing.

Software:

- Codecs: Install the [[COLOR="Blue"]_Medibuntu repository_[/COLOR]]("http://www.medibuntu.org/")
Here you need to install the w32codecs package. But the repository is a must have because it has newer codecs and players.

- Movie players:
 I recommend smplayer (or mplayer from command line but that isnt that elegant). I found it to be the best player around, but i have VDPAU capable nvidia cards and smplayer can use VDPAU unlike VLC. So i might be a bit biased here. Also, Xine has VDPAU support too (i personally dont like it) and its really fast.
VLC is quite good too if you dont have nvida card. Try them out and see for yourself.

Also, stuff installed in Wine works slower than in Windows - there are very few curious exceptions, but those dont have to do with hardware acceleration AFAIK.

---

### Post by xzero1 on 2010-05-08
> **gradinaruvasile said:**
> For HD playback you have to have:

Hardware:

- Good CPU - core2duo or something similar, best is 2.3+ GHz - Ati (some seem to have a technology called Avivo -that helps with decoding, but didnt really lowered CPU usage in my tests) , Intel etc.
The decoding is done in software, thus the big CPU need.
I absolutely recommend mplayer-mt - this is a newer version of mplayer that supports multithreading, it is in experimental stage though - look around for it in PPAs

or

- VDPAU-compliant nvidia video card (series 8 or better - [[COLOR="Blue"]_list_[/COLOR]]("http://en.wikipedia.org/wiki/Nvidia_PureVideo")- in this case the CPU is not really relevant. The decoding is done in the video card, i ran 1080p movies on Athlon 3200+ single core at about 15% CPU usage on 8200 IGP.
To use the vdpau capabilities you need [[COLOR="Blue"]_vdpau-enabled nvidia driver and vdpau-enabled mplayer_[/COLOR]]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") .
I use the driver from nvidia's site - that one has everything needed, but i dont recommend it for beginners only if they look around a bit for its drawbacks before installing.

Software:

- Codecs: Install the [[COLOR="Blue"]_Medibuntu repository_[/COLOR]]("http://www.medibuntu.org/")
Here you need to install the w32codecs package. But the repository is a must have because it has newer codecs and players.

- Movie players:
 I recommend smplayer (or mplayer from command line but that isnt that elegant). I found it to be the best player around, but i have VDPAU capable nvidia cards and smplayer can use VDPAU unlike VLC. So i might be a bit biased here. Also, Xine has VDPAU support too (i personally dont like it) and its really fast.
VLC is quite good too if you dont have nvida card. Try them out and see for yourself.

Also, stuff installed in Wine works slower than in Windows - there are very few curious exceptions, but those dont have to do with hardware acceleration AFAIK.

You are out of date concerning ati hardware ati playback. See
[http://ubuntuforums.org/showthread.php?t=1385896]("http://ubuntuforums.org/showthread.php?t=1385896")

---

### Post by AP0ll0UK on 2010-05-08
Hey thanks for your advice, it now works!! :D

I got a modified version of mplayer from here - [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

Installed it, installed smplayer, then in the smplayer preferences I set it to use both cores of my CPU and low and behold playback is perfect!

For information purposes in case anyone else stublmes across this thread, I'm using an Intel Core2Duo E6600 [2.2Ghz], 1GB ram and a 512mb X1900XT connected to a 40" Samsung LCD. Some .mkv's worked ok but others were stuttering and skipping when playing back prior to going through the steps above.

Thank you very very much for your advice :D

---

