---
title: "NVidia+8800gtx+GLX=horribly lost"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by oraldlight on 2007-09-23
I have:
  Kubuntu32bit 7.4 (Fiesty)
  AMD64 (using a low-latency kernel)
  NVidia 8800gtx

and can not get Beryl/Copmpiz to work.  I've tried Envy's installer which proclaims success, but refuses to allow any GLX functions. I'm fairly sure, I'm using, or used, the restricted-drivers. I've uninstalled, reinstalled, re-uninstalled, re-installed, included some extra repositories, hacked upon xorg.conf, but just can not get this rig to co-operate. 

  When I remove the Envy installed drivers and attempt a manual install of NVIDIA-Linux-x86-100.14.19-pkg2.run  it builds the kernel, does it's thing, fixes, xorg.conf and boots with GLX enabled. Re-start Xserver as much as I want, and all is fine. Reboot the PC and all this falls apart. I usually get the "prompt in upper left corner" screen after the "Kubuntu" splash, where the KDM login should be. Pop over to a command line, log in and either:

1) edit xorg.conf to use the "NV" driver and startx to a GLX free session
  or 
2) re-run the NVIDIA-Linux-x86-100.14.19-pkg2.run and I can have GLX

  The X error message I get, said something about "mismatched Kernel and Nvidia" which I read as version conflict between the NVidia driver and (???) kernel headers. (Sorry, not certain where to find this message for better quoting.)

  I know this is capable of Beryl/Compiz as I can boot a Gentoo livecd and see this fun eye candy. When I try installing it, I get all sorts of fubar results. Missing borders, failure to start, etc... Am I correct GLX _***IS***_ needed for Beryl/Compiz?

  If anyone can help point out where I've failed/wandered/borked, I'd be very appreciative. Browsing the forums serves to distract me and adds to experimentation, which I think is taking me further from resolution.

---

