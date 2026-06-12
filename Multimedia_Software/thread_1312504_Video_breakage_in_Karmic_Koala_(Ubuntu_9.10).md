---
title: "Video breakage in Karmic Koala (Ubuntu 9.10)"
date: 2009-11-03
forum: Multimedia Software
---

### Post by kozjegyzo on 2009-11-03
Hi,

I have an issue with video playback too. Since the upgrade to Karmic, all my video players display the same problem. The video seems fine at first, but if there is fast movement in the film, the video shows horizontal breakage. This happens with all players. The videos are still watchable, but it's very annoying.
I tried reinstalling the codecs, but that didn't do anything. 

The other accruing problem is that sometimes the whole video playback freezes for a few seconds and the audio keeps going, and then everything is back to normal.

Anyone facing the same problem? Fixes?

THX in advance

---

### Post by atoztoa on 2009-12-04
I am also having issue with video in Karmic... in Jaunty it was working fine...

The video have a small jagged edge (a colored line at bottom edge)... I don't know what it is called...

When I pause the video and unpause it, it won't start playing, or it plays in slow motion... only after I rewind or forward it plays normal...

My system is up to date according to 'Update Manager'...

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by bgood on 2009-12-10
I'm having this problem too, you get a horizontal line either 1 third the way down from the top or 1 third the way up from the bottom, only seems to be evident on panning shots, it's like the screen is trying to split into 2 parts.

Has anybody got any suggestions on a fix?

I'm running on an Atom N230 with an ION graphics chip and have updated to the 190 drivers today but it's still the same :(

---

### Post by bgood on 2009-12-11
Well it seems changing visual effects in Appearance to none has resolved the issue for me :)

---

### Post by Slowjoe on 2009-12-16
Me too

---

### Post by ashwinrao on 2009-12-16
I'm also having the same issues.:( I have updated display drivers, searched in net, even [posted]("http://ubuntuforums.org/showthread.php?t=1355870") in this forum, no answers. Some body please help us. This issue even affect firefox for me. By the way, I'm using Nvidia display with AMD64 if this info gives some clue. Please guide me... :(

---

### Post by EricDrijv on 2009-12-16
Maybe installing the Gstreamer Ugly set will help
Or better all the Gstreamer plugins
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by ashwinrao on 2009-12-16
Thanks for your reply. However, the solution doesn't resolve the issue. I have already installed those plug ins. The output is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll
ashwinrao@ashwinrao-desktop:~$ 

I have noticed that the CPU load turns 100% while I use Firefox and while watching any movies. I can not pin point the process which is causing this load. Please guide me, This is the only issue I am facing other wise Ubuntu rocks!!

---

### Post by EricDrijv on 2009-12-16
There are some workarounds you can try:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

But first look at:
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by ashwinrao on 2009-12-17
Thanks Eric!

I have followed your suggestions. For the time being, I'm not experiencing any issues with Firefox. I have to check the video functionality. However, it seems that this issue is affecting all who are using compiz with 64 bit Nvidia display. I'll surely update this tread if I get better results. Thanks again for your help!

---

