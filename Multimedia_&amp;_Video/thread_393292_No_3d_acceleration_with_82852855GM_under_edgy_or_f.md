---
title: "No 3d acceleration with 82852/855GM under edgy or feisty"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by ajkessel on 2007-03-25
I'm unable to get 3d acceleration to work with an Intel 855GM card (Thinkpad X40) using xserver-xorg and drivers from either Edgy or the latest Feisty kernel and drivers. Everything looks okay in the logs, but glxinfo always reports "direct rendering: no."

I've tried both the 'intel' and the 'i810' drivers. I've tried the latest kernel and older kernels. I've tried unloading the VESA module. I've tried dropping the color depth to 16. I'm not using Xinerama or any other multi-monitor features right now.

I've also tried tweaking other options;  option "AIGLX" to true and false; explicitly enabling composite/render extensions. Nothing works.

Any ideas?

I've posted all the relevant logs and configuration files in [http://adam.rosi-kessel.org/debug/2007/03/25/drm]("http://adam.rosi-kessel.org/debug/2007/03/25/drm").

A similar question came up [before]("http://ubuntuforums.org/showthread.php?p=642607#post642607") in these forums but was not resolved.

---

### Post by Chuckaluphagus on 2007-03-25
That's odd, I have the same graphics chip on my notebook (Asus M3Np) and the drivers for 3D acceleration were set up by default when I installed Edgy.  I don't know enough to help you, but I can verify that the regular drivers work fine with the same chipset in my case. 

Hmm.  I don't even have the Intel-specific X.org installed and 3D acceleration still works for me.  Now I'm wondering what the result would be if I install that package.

---

