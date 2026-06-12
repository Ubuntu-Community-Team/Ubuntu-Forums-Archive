---
title: "S3 Savage / Viper II Z200 Problems with tvtime, mplayer, xawtv, flash"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Easy_Rider9999 on 2008-07-19
Hello! I just installed Ubuntu 8.04 on an old Pentium 2 400Mhz PC, with 256 MB Ram and Viper II Z200 graphic card. When I run mplayer or tvtime I get a blurred picture with very false colors and I have to restart ubuntu. xawtv also doesn't work, I get disturbances spread over the screen. 

Here is my xorg.conf```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
``` 

lspci:> 01:00.0 VGA compatible controller: S3 Inc. 86C410 Savage 2000 (rev 02)


I already tried tu run dpkg-reconfigure xserver-xorg
but I couldnt change the driver to savage. So what is the correct driver and how do I change it?

Yours Hans

---

