---
title: "nvidia module not found after upgrade"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by richard.hunt500 on 2006-12-10
I have just used the upgrade tool in Dapper Drake for the first time and now I can't get the nvidia driver to work. I don't know if it makes any difference in this case but I am using an Asus GeForce 6200, on a K8M800 motherboard with a Sempron 3400+, 512Mb ram.

I originally got nvidia working by some version of these commands:

sudo aptitude install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
sudo nvidia-glx-config enable

This was working fine until I ran the upgrade by clicking on the orange icon next to the clock. Eventually that program told me to reboot, and when I rebooted gdm wouldn't start.

The error that I get is that the nvidia module cannot be found by xorg. There is nothing in /usr/X11R6/lib/nvidia, although I'm not sure if there should be :)

I didn't have to install using the nvidia .run installer last time, but is this something that I need to do now?

At the moment I have switched to the nv driver just by editing nvidia to nv in xorg.conf, and have made no other changes to that file. For some reason after I made that change gdm would not start.

Does anyone have any idea what I might have done wrong? Sorry about the length and lack of the correct info (probably)...

---

### Post by richard.hunt500 on 2006-12-10
I forgot to mention that I am using and AGP 8x 128Mb version of that card. I am using the 32bit version of ubuntu and the 386 kernel (I assume this was the default, since there is a k7 kernel too).

I saw that there is a module nvidia-agp which I am not using, I am using amd64_agp.

Oh and glx was definitely working before, I was running Unreal Tournament 2004, and Nexuiz was running at over 100fps.

---

### Post by richard.hunt500 on 2006-12-10
Ok, I have worked out what my problem is. I only have restricted drivers for the 2.6.15-23-386 kernel, and I need them for the 2.6.15-27-386 kernel. Unfortunately the restricted modules listed in synaptic and aptitude are for the 2.6.15-23-386 kernel. Does anyone know if the newer package exists, and what I need to do to install it?

Thanks,
Richard

---

