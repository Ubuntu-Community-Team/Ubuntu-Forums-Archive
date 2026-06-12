---
title: "Screen resolution"
date: 2008-12-22
forum: Multimedia Software
---

### Post by cr526 on 2008-12-22
Just Installed Ubunutu 8.10 on ASRock K7S41GX. Everything (Sound,Video,,) works fine, except screen resolution.
Problem is I am getting the max resolution 960x600. Trying to configure 1200+
Configuration details:
/etc/X11/xorg.conf has the following contnet -
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Hardware Video details:
Graphics  	- Integrated Mirage Graphics
		- Shared Memory Max. 64MB

Tried following things:
1) sudo dpkg-reconfigure xserver-xorg
2) sudo dpkg-reconfigure -phigh xserver-xorg

- sudo dpkg-reconfigure xserver-xorg, is configuring keyboard only, no options for video
- sudo dpkg-reconfigure -phigh xserver-xorg Showing the message
  xserver-xorg postinst warning: overwriting possibly-customised configuration
  file; backup in /etc/X11/xorg.conf.20081222230619

Not sure what else to do, any pointers will be appreciated.

Thanks!!!

---

### Post by coolethan on 2008-12-23
ok this is what i did, i could never figure out how to edit the xorg.conf file so i used the live disc for 7.10 and it was able to recognize my screen properly or else i could change it with screens and graphics. anyways i took the xorg.conf file from the 7.10 disc with the proper res. settings and copied it to a usb thumb drive and then rebooted up with 8.10. found out where the xorg.conf file goes and replace the one in there with the one from 7.1 and it worked perfectly.

---

