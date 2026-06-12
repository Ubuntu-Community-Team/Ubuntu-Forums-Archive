---
title: "My ATI Radeon crashes upon login!"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by wty on 2007-11-02
Hello,

I have managed to install, and get the ATI driver to work on my computer. But the problem is that I want dual screens. And I have managed to sort that out to, except when I log in the graphic card fails. I have picture, and everything before I log in, but that disappears under the login process. The only way I get the picture back is to reboot the computer. This is what the syslog says:

> Nov  2 20:42:56 wetwilly kernel: [   48.582955] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov  2 20:42:56 wetwilly kernel: [   48.582961] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov  2 20:42:56 wetwilly kernel: [   48.582965] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
Nov  2 20:42:56 wetwilly kernel: [   48.583492] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov  2 20:42:56 wetwilly kernel: [   48.583663] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov  2 20:42:56 wetwilly kernel: [   48.583810] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov  2 20:42:56 wetwilly kernel: [   48.583955] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Nov  2 20:42:56 wetwilly kernel: [   48.697979] [fglrx:firegl_addmap] *ERROR* existing map 0xffff8100340e2960 (handle 0xffffc200001f6000)
Nov  2 20:42:56 wetwilly kernel: [   48.698227] [fglrx:firegl_addmap] *ERROR* existing map 0xffff8100340e29c0 (handle 0x00000000)


The even stranger thing is that if I log in to Failsafe Gnome, it works. But the soon as I log out or kill gnome, it happens again. And I don't want to log in to the Failsafe Gnome everytime. I want it to work as it supposed to! 

If there is anybody that could help me, or have been in my shoes I'd love to get some help. Because now im just out of ideas. I have used hours on this. 

Here you have my [xorg.conf]("http://dump.wty.se/data/xorg.conf") to

Thanks for your time - wty

---

