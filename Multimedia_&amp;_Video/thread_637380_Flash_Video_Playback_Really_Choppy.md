---
title: "Flash Video Playback Really Choppy"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by nbaes on 2007-12-10
Hi, 

I have a reasonably powerful PC with an Nvidia FX5200 PCI video card (correct drivers installed via restricted drivers manager) running Ubuntu 7.10. For some reason, I am getting absolutely the choppiest playback of Flash videos that I have ever seen this side of a 486. I have no clue what is causing this; I have turned off Compiz and lowered color depth to 16 bits in xorg.conf, but still Flash videos play back absolutely terribly (like 15 FPS or so). I installed Flash from Adobe's site (latest build) because I had the "md5sum" error when trying to do it via Firefox. Has anyone run into this issue before? I can run Windows XP on this same PC and I get excellent Flash playback (even with the exact same sites and videos). What is the deal here? I love Ubuntu, but Flash is a huge part of what I do with my PC (I don't have a TV b/c I'm a ridiculously poor student), and having this limited performance totally bums me out. I know there are about a billion people on here that are way smarter than I am...any suggestions at all? Any help would really be appreciated!

---

### Post by markusf21 on 2007-12-10
I would suggest uninstalling flash and then running this in a terminal:```
sudo apt-get install flashplugin-nonfree
``` should fix it

---

### Post by ihatethetv on 2008-06-27
I was running into this problem too with my 8600GT...I pulled it and tried my ATI onboard video just for kicks...turns out that fixed it...or at least made it a lot better. 

This suggests to me that it's a video driver problem. I'm running the most current nvidia driver as of today 6/27/2008.

I went over and bellyached at nvidia in their forums here:  I encourage you to do so as well if you're having this problem.

[http://forums.nvidia.com/index.php?showtopic=70881&st=0&p=401485&#entry401485](http://forums.nvidia.com/index.php?showtopic=70881&st=0&p=401485&#entry401485)

Good luck,
Glen

---

### Post by slyn4ice on 2008-06-28
Actually if you install wine, then firefox for windows and the windows flash plugin you get a perfectly working flash - no choppines, not even in fullscreen. And since i only care about flash when i am watching videos (youtube, etc.) i just use the windows firefox for that purpose.

Just a suggestion

---

### Post by almalaci on 2008-07-11
> **slyn4ice said:**
> Actually if you install wine, then firefox for windows and the windows flash plugin you get a perfectly working flash - no choppines, not even in fullscreen. And since i only care about flash when i am watching videos (youtube, etc.) i just use the windows firefox for that purpose.

Just a suggestion

Not for me: Under wine it's the same choppiness. I have now flasplayer 10 installed under ubuntu which also doesn't make any difference.

---

