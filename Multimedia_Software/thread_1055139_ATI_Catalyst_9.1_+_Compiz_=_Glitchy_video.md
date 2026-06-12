---
title: "ATI Catalyst 9.1 + Compiz = Glitchy video"
date: 2009-01-30
forum: Multimedia Software
---

### Post by jKaeno on 2009-01-30
My problem is short... when i instal ATI 9.1 official drivers video is glitchy more than before. On 8.12 video flickering (with compiz), however, after install 9.1 video playing is very bad with compiz (i must off it, but i don't want it). Video player window is looks like [[COLOR="SeaGreen"]**this**[/COLOR]]("http://starzaki.eu.org/~jkaeno/up_v1.0/files/buggyati91.png").

xorg.conf is default (i type *sudo dpkg-reconfigure -phigh xserver-xorg* and *sudo aticonfig --initial*).

Any cure?

---

### Post by sedawk on 2009-01-30
I haven't tested the latest driver, but when I want to watch
videos I always kill compiz and run metacity instead.
For playable videos (via xv) I had to add the "TexturedVideo" option to 
/etc/X11/xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"TexturedVideo"	"on"
	Driver		"fglrx"
EndSection

```

(This is not from my working xorg.conf - I'm not sure about the
 values (if any) I use for VideoOverlay and OpenGLOverlay)

---

### Post by jKaeno on 2009-01-30
Still the same after that :(

---

### Post by G.G on 2009-02-01
try mplayer

I've the same problem whit vlc & totem

---

### Post by SafeTinspector on 2009-02-01
> **jKaeno said:**
> My problem is short... when i instal ATI 9.1 official drivers video is glitchy more than before. On 8.12 video flickering (with compiz), however, after install 9.1 video playing is very bad with compiz (i must off it, but i don't want it). Video player window is looks like [[COLOR="SeaGreen"]**this**[/COLOR]]("http://starzaki.eu.org/~jkaeno/up_v1.0/files/buggyati91.png").

xorg.conf is default (i type *sudo dpkg-reconfigure -phigh xserver-xorg* and *sudo aticonfig --initial*).

Any cure?


I'm running SuSE, but I have the ATI Catalyst 9.1 installed along with Compiz 0.7.8-28.1
This combination not only works, but completely corrected the video flickering issue I had when I was running under Catalyst 8.12 and Compiz 0.7.8-9.1

Since I upgraded both at the same time (I know, bad form) I'm not sure which thing fixed my problems. *sigh*
That's why I'm browsing around today, because I wondered what other people experienced.

---

### Post by markbuntu on 2009-02-01
I am running Intrepid with my HD3650 and the new 9.1 driver and it has eliminated tearing video with totem with Multimedia System Selector set to X Window System (X11/XShm/Xv). vlc needs to be set to X11 and xine to xshm to eliminate tearing, for mplayer set video to X11/Xv.

In the Catalyst Control Center I set all the 3D controls to override and pushed all the sliders all the way to the right and got excellent video quality.

All this with compiz running. The videos play great even when rotating the cube/cylinder which they would not do before.

---

### Post by nibbana84 on 2009-02-03
> **SafeTinspector said:**
> I'm running SuSE, but I have the ATI Catalyst 9.1 installed along with Compiz 0.7.8-28.1
This combination not only works, but completely corrected the video flickering issue I had when I was running under Catalyst 8.12 and Compiz 0.7.8-9.1

Since I upgraded both at the same time (I know, bad form) I'm not sure which thing fixed my problems. *sigh*
That's why I'm browsing around today, because I wondered what other people experienced.

I have still flickering video with this Ati driver and Compiz 0.7.8.
Can I ask how you installed Compiz 0.7.8-28.1???
If I type compiz --version, I get: 
"compiz 0.7.8".

I tried to install the version from [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu), but even if more recent it results more unstable and it is not 0.7.8-28.1 anyway!

Thank you,

---

### Post by nibbana84 on 2009-02-04
> **nibbana84 said:**
> I have still flickering video with this Ati driver and Compiz 0.7.8.
Can I ask how you installed Compiz 0.7.8-28.1???
If I type compiz --version, I get: 
"compiz 0.7.8".

I tried to install the version from [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu), but even if more recent it results more unstable and it is not 0.7.8-28.1 anyway!

Thank you,

Anyone, please?

---

### Post by SafeTinspector on 2009-02-05
> **nibbana84 said:**
> Anyone, please?

Unfortunately I am unable to assist, as I am not in Ubuntu and my method (I nabbed it from a YaST repository called X11:Compiz) won't work for you.

But perhaps this link will help:
[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/]("http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/")

---

### Post by nibbana84 on 2009-02-06
> **SafeTinspector said:**
> Unfortunately I am unable to assist, as I am not in Ubuntu and my method (I nabbed it from a YaST repository called X11:Compiz) won't work for you.

But perhaps this link will help:
[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/]("http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/")

Nada... I guess ATI unlucky users like me will to have wait and hope... for the next release. Shame on ATI.

---

### Post by d-mart on 2009-02-19
Iam using the ATI Catalyst 9.1 + Compiz and I do not seem to have this problem.  Here is my xorg.conf.  My gpu is an ATI mobility x300

---

### Post by jahkob on 2009-02-20
look @ [http://ubuntuforums.org/showthread.php?t=1071815&highlight=jahkob](http://ubuntuforums.org/showthread.php?t=1071815&highlight=jahkob) for help :)

---

### Post by Melcar on 2009-02-20
The 9.1 driver resolves the flickering video (when using Xv) under composition managers.  It does have problems, however:

- X may crash with certain players
- X may crash if you switch playback from windowed mode to fullscreen mode
- X may crash after movie playback
- windowed videos with Totem and VLC appear off-center and their GUI corrupted

Remember guys that this functionality (flickerless video playback with composition) is lacking in X proper.  ATI is starting to kinda circumvent some parts of X and this will inevitably cause problems with the current driver framework.  The drivers are getting there but it's a process; you can't realistically expect a perfect driver overnight (specially a Linux driver).

---

