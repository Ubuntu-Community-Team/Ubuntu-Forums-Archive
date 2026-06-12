---
title: "Removing Totem removes ubuntu-desktop"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by 141N on 2007-04-05
Hey guys, I just downloaded and installed VLC Media Player, and went to remove Totem through Synaptic, but it says that it will remove "ubuntu-desktop" aswell :-k

Can I remove Totem without getting rid of the desktop, or is there any way I can set VLC as the default media player? It's just that when I download an mp3 or something Totem tries to view it first and its a pain in the @$$

Thanks guys

---

### Post by Belyel on 2007-04-05
the ubuntu-desktop package is what is known as a 'meta package.' It isn't really a package, but it contains links to all the actual software the makes up ubuntu.  When you remove totem, it detects that totem was listed in the meta package, so apt tries to remove the meta-package, too.  It won't hurt anything to have it removed.  Removing ubuntu-desktop won't remove any other software, just the meta-package.

---

### Post by 141N on 2007-04-07
Ah, I assumed it would remove the GNOME desktop :S anyway, I'm still having bother with going online! It's constantly crashing, so much so that I'm using FC-4 just now for a bit of stability until I can figure out what is wrong with it :(

---

### Post by gerdt on 2007-05-08
> **Belyel said:**
> the ubuntu-desktop package is what is known as a 'meta package.' It isn't really a package, but it contains links to all the actual software the makes up ubuntu.  When you remove totem, it detects that totem was listed in the meta package, so apt tries to remove the meta-package, too.  It won't hurt anything to have it removed.  Removing ubuntu-desktop won't remove any other software, just the meta-package.

Thank you very much for the information! I was afraid I might hurt my GNOME isntallation by removing this package.
I have a question, how do I know whether a certain package is a meta package or not?

---

### Post by ssam on 2007-05-08
which version of ubuntu are you using?

in feisty you should be able to remove the default programs without removing ubuntu-desktop

---

### Post by gerdt on 2007-05-08
edgy

---

### Post by Prometheus.172214 on 2007-05-19
I'll second that ..... Totem player is a royal pain in the place where the sun don't shine (No offence meant, some of you might find it usefull, I just can't use it though). I use VLC and Xine. Same problem. The default program is set to Totem and I can't play anything in it, atleast not the way I want to. So, how do I remove only totem or how do I make VLC or Xine the default????? Also, I just installed this program called Easy Linux and it shows me a list of codecs and stuuf that I can download, Are these codecs for Totem only, or do they work with any other movie software like VLC and Xine?
:guitar:

---

### Post by ricrac on 2007-05-19
The main issue with removing meta packages is during a version upgrade.
The meta package with include/remove software based on Ubuntu's decisions during the upgrade.

While in a release cycle, meta packages can be safely removed.  If removed, I would recommend an install rather than an upgrade for the next Ubuntu version.  You may upgrade with no errors, but the upgrades are only tested using meta package installs.  

Personally I like less installed and use mplayer.mencoder for everything, dvd, TV tuning, audio, video, recording, streaming audio, streaming video.  Works great, less codec issues.  Wireless and IR remote are easy to customize for it.

---

### Post by cdiem on 2007-05-21
to Prometheus --> If you want to make one of these players default, you can simply right click on the file you want to open (fo instance, .avi), and choose "open with", for instance, VLC. After that, every .avi file you open, will be opened with VLC as default. I think you have to do this for every file type you want.
As for the codecs, VLC comes with built-in codecs, so you do not need to install any for him; for xine, there are, as far as I remember, the libxine codecs, available through Add/Remove programs. You can use Automatix as well, it will download you the codecs you need and will install them. 
Hope that helps.

---

### Post by lgwwin on 2008-04-08
I removed all packages have the name of evolution, assuming that it wouldn't hurt my desktop. What would you guess? I had no desktop! Fortunately, I get it back after "sudo apt-get install ubuntu-desktop" in console.

If you don't really know what the packages do, don't remove it.

---

### Post by ubuntu-freak on 2008-04-08
Why not just make VLC default in System>Preferences>Prefered Applications? Also, my [how-to](http://ubuntuforums.org/showthread.php?t=661833) has a troubleshooting section you may find useful. Leave a message in my thread if you have problems.
 
I recommend the MPlayer plugin for streaming audio and video in Firefox, I don't get the prompts to use Totem. See part 2 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) for details.
 
Nathan

---

### Post by wolfen69 on 2008-04-08
> **lgwwin said:**
> I removed all packages have the name of evolution, assuming that it wouldn't hurt my desktop. What would you guess? I had no desktop! Fortunately, I get it back after "sudo apt-get install ubuntu-desktop" in console.

If you don't really know what the packages do, don't remove it.

obviously there is something wrong with your install. ive removed evolution and many other programs without a problem.

---

### Post by warp99 on 2008-04-08
> **141N said:**
> Ah, I assumed it would remove the GNOME desktop :S anyway, I'm still having bother with going online! It's constantly crashing, so much so that I'm using FC-4 just now for a bit of stability until I can figure out what is wrong with it :(

If you're afraid about what a package will do if you remove it you can add the '-s' parameters to do a simulation. Example:

```
sudo apt-get -s remove xserver-xorg
```
and the results:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx-new xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 42 to remove and 0 not upgraded.
Remv nvidia-glx-new [100.14.19+2.6.22.4-14.10]
Remv xorg [1:7.2-5ubuntu13]
Remv xserver-xorg-video-intel [2:2.1.1-0ubuntu9.1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-voodoo [1:1.1.1-2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-vmware [1:10.15.0-0ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-via [1:0.2.2-2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-vga [1:4.1.0-3ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-vesa [1:1.3.0-1ubuntu5] [xserver-xorg-video-all ]
Remv xserver-xorg-video-v4l [1:0.1.1-0ubuntu2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-tseng [1:1.1.1-1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-trident [1:1.2.3-1ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-tga [1:1.1.0-3ubuntu2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-tdfx [1:1.3.0-1ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-sisusb [1:0.8.1-3ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-sis [1:0.9.3-2ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-siliconmotion [1:1.5.1-1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-savage [1:2.1.2-6ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-s3virge [1:1.9.1-3ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-s3 [1:0.5.0-2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-rendition [1:4.1.3.dfsg.1-2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-nv [1:2.1.5-1ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-neomagic [1:1.1.1-5ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-mga [1:1.4.6.1.dfsg.1-3] [xserver-xorg-video-all ]
Remv xserver-xorg-video-i810 [2:1.7.4-0ubuntu5] [xserver-xorg-video-all ]
Remv xserver-xorg-video-i128 [1:1.2.1-2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-glint [1:1.1.1-6] [xserver-xorg-video-all ]
Remv xserver-xorg-video-fbdev [1:0.3.1-1ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-dummy [1:0.2.0-3ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-cyrix [1:1.1.0-4ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-cirrus [1:1.1.0-3ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-chips [1:1.1.1-4ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-video-ati [1:6.7.195-1ubuntu2] [xserver-xorg-video-all ]
Remv xserver-xorg-video-ark [1:0.6.0-6] [xserver-xorg-video-all ]
Remv xserver-xorg-video-apm [1:1.1.1-7] [xserver-xorg-video-all ]
Remv xserver-xorg-input-all [1:7.2-5ubuntu13] [xserver-xorg-video-all ]
Remv xserver-xorg-input-synaptics [0.14.6-0ubuntu10] [xserver-xorg-video-all ]
Remv xserver-xorg-input-mouse [1:1.2.1-1] [xserver-xorg-video-all ]
Remv xserver-xorg-input-kbd [1:1.2.0-1+1.2.1ubuntu1] [xserver-xorg-video-all ]
Remv xserver-xorg-input-evdev [1:1.1.5-3] [xserver-xorg-video-all xserver-xorg ]
Remv xserver-xorg-core [2:1.3.0.0.dfsg-12ubuntu8.3] [xserver-xorg-video-all xserver-xorg ]
Remv xserver-xorg [1:7.2-5ubuntu13] [xserver-xorg-video-all ]
Remv xserver-xorg-video-all [1:7.2-5ubuntu13]

```

Just a simulation, no harm done.

---

