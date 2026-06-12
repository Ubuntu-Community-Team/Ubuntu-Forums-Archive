---
title: "Nvidia glx fails to load"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by zxee on 2006-02-07
I just recently installed 5.10 on my homebuilt sempron 1.6MHz  512MB ram.
To get the nvidia driver installed I orginally used a how-to in the ubuntu forum
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver)
and used method 2, but that didn't work. I had to return to the 'nv' driver to get x running. I saw the thread, again here at the ubuntu forums, on using Automatix and installed it and had it install the nvidia driver. I think Automatix is really an excellant idea. However now I'm getting the nvidia splash screen but when I try to check frame rates with glxgears I get this:
~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

In /var/log/xorg.log there is this:
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
dlopen: /usr/X11R6/lib/modules/extensions/libglx.so: undefined symbol: _nv001206gl
(EE) Failed to load /usr/X11R6/lib/modules/extensions/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

(Also adding the loading of the nvidia driver) As Reported by 'dmesg':
[4294688.048000] Linux agpgart interface v0.101 (c) Dave Jones
[4294688.083000] nvidia: module license 'NVIDIA' taints kernel.
[4294688.106000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294688.106000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667 Fri Jun 17 07:01:04 PDT 2005


Can anyone point me in the right direction on this? Thanks!

Added 2-9-06 What I ended up doing to resolve this was to go back to the nv driver rebooted ( I also installed the k7 kernel ) and going through the method 2 steps again ( see thread how-to link above ) I used the latest nvidia driver x86-2.0-8178. Also had to edit the bash.bashrc file to get fps.
It's working very well now! :)

---

