---
title: "VDPAU and Crushed black levels"
date: 2009-10-12
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-10-12
I' getting crushed black levels (maybe white too) on MY Panasonic TX-42PZ80U plasma w/ VDPAU  Does anyone know haow to resolve this problem? is there an nvidia-xconfig argument for studio video (16-235) as opposed to pc (0-255)?  Output is through HDMI on a 9800 GT.

---

### Post by Gen2ly on 2009-10-12
Think this may be a bug in mplayer and HDMI.  

[http://wdtvforum.com/main/index.php?topic=261.10;wap2](http://wdtvforum.com/main/index.php?topic=261.10;wap2)

I've read a couple posts that this can be fixed to a degree by adjusting the gamma but haven't tried.

---

### Post by zeronothing on 2009-10-12
There is a PPA team that keeps up-to-date Nvidia drivers and mplayer packages that support vdpau. you might want to check out there page for more info. On there page they have there repositories available so you can download there packages. 

there pages is [[COLOR="Blue"]here[/COLOR]]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

---

### Post by epi 1:10,000 on 2009-10-13
I turned on Panasonic x.v Color (what ever that is/ maybe it = xvYCC complience) and moved to a custom video setting w/ really high brightness but it still feels like something is a little off.  I forgot to mention I'm using 180.60 drivers.

---

### Post by jyavenard on 2009-10-14
> **epi 1:10,000 said:**
> I turned on Panasonic x.v Color (what ever that is/ maybe it = xvYCC complience) and moved to a custom video setting w/ really high brightness but it still feels like something is a little off.  I forgot to mention I'm using 180.60 drivers.

VDPAU by default use PC levels for RGB (0-255), most TV use studio levels (16-235).

Feeding PC levels to a TV expecting sRGB will result in crushed blacks and whites.

I've added a patch to change the color levels to match your TV, as well as adding HDTV colorspace.

Few choices:
* Update to trunk >= SVN#22431
* Install that patch [http://svn.mythtv.org/trac/ticket/7307](http://svn.mythtv.org/trac/ticket/7307)
* Use my trunk daily repository, it has it compiled in ([www.avenard.org/media](www.avenard.org/media))
* Wait for mythbuntu weekly build to update trunk (though my understanding is that they move to 0.22-fixes branch)

To use it, edit the video playback profile and add the following line for the "Custom Filters" entry:
studio,colorspace=0

---

### Post by epi 1:10,000 on 2009-10-16
Thank you for taking the time to make a patch! I'm hesitant to move to trunk cause I'll have to update my backend machine too. I'm not quite sure how to transition to trunk without loosing my current recordings/settings/vdpau (I need to research it a little more). I guess I could wait till November to upgade to 9.10 and .22

---

