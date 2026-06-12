---
title: "Mythbuntu 9:10: Nvidia 185.18 suckage and upgrading to 190.42"
date: 2009-11-02
forum: Mythbuntu
---

### Post by hackmeister on 2009-11-02
I was running 9.04 with the VDPAU backports for MythTV 0.21 (Avenard repo) and decided to do a clean install instead of upgrading for Mythbuntu 9.10. As with the Avenard packages Nvidia 185 driver HD playback is very choppy on my 8600GT card (both mpeg2 and h264). With Avenard this problem was fixed by upgrading to the Nvidia 190.24 driver. I don't see the 190.24 packages in the regular Karmic repos. For 185 driver I see the following packages:
nvidia-185-kernel-source
nvidia-185-libvdpau
nvidia-185-libvdpau-dev
nvidia-185-modaliases

My assumption I would need: 
nvidia-190-kernel-source
nvidia-190-libvdpau
nvidia-190-libvdpau-dev
nvidia-190-modaliases

I do see a Nvidia-vdpau PPA repo:
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main

Should I use this repo's packages or can I just remove the 185 driver thru Mythbuntu control center and use the official Nvidia 190 installer? Will I have to build the corresponding VDPAU packages?

Thanks

---

### Post by ZedThou on 2009-11-02
I tried installing the nvidia 190 driver through package repositories and ended up inadvertantly removing mythtv completely due to its depencence on the nvidia 185 package. I would not go that route again!

What I ended up doing was just using the nvidia installer to overwrite the nvidia 185 package files. I figure when a new kernel comes along, the dkms will rebuild the 185 driver and I'll have to do it over again, but not a big deal.

---

### Post by hackmeister on 2009-11-03
Just an update. I got acceptable playback for my HD recordings using the Bob 2x deinterlacer in my playback settings. What's bad is that my CPU usage spikes to around 40% for the first couple of minutes of playback then settles down to below 5%. Regardless 190.42 is a major improvement and I hope the Mythbuntu devs make the packages available in the main repos.

---

### Post by Skybolt83JL on 2009-11-04
I'm running Mythbuntu 9.04 with Mythtv 0.22. I'd also like to get the Nvidia 190.42 update for overscan adjustment and the compositing fix. The launchpad PPA version won't install due to the libvdpau dependency on Nvidia 180.

Will this be fixed in the Mythbuntu repositories any time soon, or should I manually install the 190 driver?

---

### Post by d2globalinc on 2009-11-09
This crap is stupid.. and exactly why the whole PPA / package management system in Ubuntu is broken.. You are stuck with outdated drivers and packages as soon as the new version comes out :S - the only hope is to install drivers manually - which defeats the entire purpose of package management..  This is just getting worse w/ every new version of ubuntu..

---

### Post by uncle hammy on 2009-11-09
I have installed the 190.42 drivers by simply continuing to use the Avenard testing repos...which will be turned over to release once 0.22 is officially released.  I am also under the understanding that his repos mirror the official Mythbuntu nightly build repos with the only 2 changes being 2 backports for improvements for the sound settings and color improvements for tv vs monitors.

---

