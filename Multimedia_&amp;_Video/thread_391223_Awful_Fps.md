---
title: "Awful Fps"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by SavageNick on 2007-03-22
Hey guys - having a bit of a problem with my ati card. Yeah I know, the first thought should be "Go buy an nvidia card" but the X1950pro I've got is a massive upgrade over my old NV card and didnt cost very much...

I have installed the latest ati website drivers (both "manually" from the wiki and using envy) with rather mixed results. Basically - everything works properly except for 3D apps. AGP seems to be working (detected the correct value), Direct Rendering is "Yes" and the OpenGL drivers are the ati ones. The problem I have is that my fps is absolutely terrible. I ran lsmod and for some reason I didnt see agp gart newhere - is that supposed to be true (i.e. does the ati driver use an internal agp module of some kind?) 

I've been scouring the web for answers but cant find any - I've disabled AIGLX and Composite in xorg.conf and tried basically every tweak I can find. 

Any1 got any ideas? If you want me to post any program logs or confs i'm happy to if it helps... Oh and btw I've got XGL and Beryl installed - ofc Direct Rendering is switched off if they are loaded. The weird thing is that in Cedega, with GNOME loaded it passes on direct rendering but fails on 3d acceleration (the fps is too low), and with XGL loaded it fails on the direct rendering but the 3d acceleration test passes easily (massive fps). 

I'm using an ATI X1950 Pro, AMD64 with Ubuntu 6.10 edgy (64bit edition), Gigabyte GA-K8NS-Ultra mobo and 1.5GB RAM. Oh, and I'm using the kernel version that came with ubuntu - thats 2.6.17-10.


Thanks in advance.


Nick

---

