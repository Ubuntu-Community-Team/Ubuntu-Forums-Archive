---
title: "NVIDIA 185.18.36 - very poor performance on ION"
date: 2010-02-16
forum: Mythbuntu
---

### Post by Captain_Bodge on 2010-02-16
A recent update from the daily builds repo installed an updated libvdpau and a few other bits of nvidia-related software. Since then, video playback on mythtv using VDPAU has been really poor - I mean poor in that I was using 'VDPAU high quality' and now I've had to switch to 'VDPAU Slim' and disable deinterlacing just to stop frames being dropped. I'm running on an Acer Aspire Revo (NVIDIA Ion). Has anybody else noticed this and can tell me what to do about it? Or can reccommend a way to revert to the previous set of drivers?

---

### Post by nickrout on 2010-02-17
probably you are better to go to 190.x or 195.x series drivers.

---

### Post by SammyC on 2010-02-17
I'm using the 190 series driver on my ION based mboard and its performing very well. Pretty good at dealing with corrupted streams (digital over the air) and no playback problems at all. Not tried it with HD though.

---

### Post by Captain_Bodge on 2010-02-17
Thanks for the tip - but the hardware drivers app only gives me the option to install the 185 series drivers. If I just install the 190 drivers using apt-get, will that work?

---

### Post by nickrout on 2010-02-17
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

Doesn't show up in restricted drivers manager as its not in the repos.

This is also an alternative:

[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

---

### Post by itlarson on 2010-03-02
Both 190 and 195 showed up in my restricted driver manager after I enabled the ppa. I was able to install by selecting the one I wanted and re-booting.  Note that if you need to revert to 185, you have to disable the ppa in "software sources", or it won't work.  

For anyone having trouble getting vdpau working, they should try the xorg mods and frontend settings changes described in the troubleshooting section of this wiki: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU) .  The 8300 graphics on my asus motherboard seem to be minimal for vdpau, and this was the only way I got them working.

I have completely messed up my graphics in the past to the point where x wouldn't start, but was always able to recover by simply renaming /etc/X11/xorg.conf and re-booting.  Xorg has always recognised my plasma tv well enough to generate a new xorg.conf which could display a 1280x720 desktop at least.  You do need to re-do any xorg mods if you do this.

---

