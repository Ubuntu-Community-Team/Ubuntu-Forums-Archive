---
title: "Unable to change screen resolution using nv driver (Xubuntu Edgy)"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by homsar on 2007-04-14
Greetings all,

I've spent hours trying to install the nvidia-glx drivers under Xubuntu, each time coming up with some weird or wonderful error that will prevent the Xserver from starting (the closest I got was where I think an Xserver actually started, but my display would not display the output - rebooting killed that again). I've given up and switched to nv (from Vesa, which was awful), and now I'm stuck at the same resolution I was stuck at on Vesa - think it's 640x480. I'm outputting to a Toshiba 32WLT66 LCD TV through a GeForce 6200. I've edited xorg.conf in a hundred different ways, up to and including removing every reference to any screen resolution other than 1360x768 (native resolution is 1366x768, but nv apparently needs sizes in multiples of 8). I still get 640x480(ish) output, overscanned so I can't even see some of the important bits on the screen.

Is this a known problem using nv/do I **have** to use nvidia-glx to get this resolution working? Or have I misconfigured my xorg.conf (will post shortly if requested; I'm writing this on my XP laptop as it's rather easier than bashing around in 640x480 with missing edges)? Or does anyone have any advice on my nvidia-glx issue (it's reporting an API mismatch - apparently I have kernel module 8776 but X module 7184. Have tried sudo apt-get --purge remove nvidia-glx nvidia-kernel-common and reinstalling it. I installed nvidia-glx-legacy at one point (as I assumed (not noticing the list in 640x480) that my card wasn't supported in nvidia-glx, as nvidia-glx claimed (I think) that it couldn't find a supported card when it started after the very first time I installed it)?

All help gratefully received!

---

