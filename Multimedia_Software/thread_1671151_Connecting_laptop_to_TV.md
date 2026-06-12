---
title: "Connecting laptop to TV"
date: 2011-01-19
forum: Multimedia Software
---

### Post by AlexBaranosky on 2011-01-19
Hi,

I just bought a new HDTV.  I want to use it as a monitor for my HP Pavilion dv6500 laptop.  I have connected a VGA cable from laptop to the tv, and when I restarted the computer.  I changed the TV input source to VGA.  I saw no change.  So I restarted the PC.  When booting up I saw the command line show up on the TV, and thought it was working, but once the purple Ubuntu screen showed up, my TV said "No signal".  What is my next move to getting this working?

My xorg.conf is:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Thank you for your help in advance,
Alex

---

