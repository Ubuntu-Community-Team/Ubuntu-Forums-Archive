---
title: "Amarok 1.4 and NVIDIA 190.42 conflicts"
date: 2009-11-18
forum: Multimedia Software
---

### Post by aniruddha on 2009-11-18
Hello all, I have recently installed the new 190.42 drivers from NVIDIA by adding the "ppa:nvidia-vdpau/ppa" in Karmic 64bit. However, during install I was told that amarok14 (got via Bogdan's PPA) as well as libxine1 (and a few related entries) and nvidia-185-libvdpau would have to be removed. I chose to go ahead, figuring (pretty stupidly I suppose) that I could always re-install these later. The install of the 190.42 drivers went off successfully.

Now however, when I try to install amarok14, (both by apt-get and in Synaptic) I am told I would have to uninstall the nvidia-190-glx and nvidia-190-libvdpau entries. Has anyone else experienced this problem (and hopefully found a workaround?)? Any help would be greatly appreciated.

As an aside, I was able to install the 190.42 drivers manually using the method given at [http://ubuntuforums.org/showthread.p...ght=nvidia+185](http://ubuntuforums.org/showthread.p...ght=nvidia+185) and still retain amarok14. Nvidia settings should the system using the 190.42 drivers and amarok14 was able to install nvidia-185-libvdpau. Does anyone know why this was, and if this is indeed advisable?

Many thanks people.

[PS. I have posted a similar thread in the General Help section, but this seemed to be a useful sub-forum as well. If this such double posting is disallowed (or generally frowned upon), I would request the mods to remove whichever post they deem fit. My sincerest apologies if this is indeed the case.]

---

### Post by aniruddha on 2009-11-23
This issue seems to have been solved by an update in the 190.42 ppa itself. It resolves both the libvdpau and libxine1 conflicts. Awesomeness and many thanks to the maintainers of the ppa!!!

---

