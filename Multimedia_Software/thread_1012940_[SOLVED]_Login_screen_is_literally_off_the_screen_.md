---
title: "[SOLVED] Login screen is literally off the screen Ubuntu 8.10"
date: 2008-12-16
forum: Multimedia Software
---

### Post by satellitex86 on 2008-12-16
Hi,

I have a bit of a problem, When my computer gets to the login screen, the whole screen resizes and goes off-screen.

I have Ubuntu 8.10 and can provide whatever other information that is needed to fix this.

[IMG]http://photos-g.ak.fbcdn.net/photos-ak-snc1/v1364/164/10/1346017153/n1346017153_168902_2863.jpg[/IMG]

I can still logon, but it is an annoyance.

Any help would be appreciated,

---

### Post by wolfen69 on 2008-12-16
try uninstalling and reinstalling gdm. go to synaptic package manager and completely remove gdm. then:
```
sudo apt-get clean
```then
```
sudo apt-get autoremove
```then
```
sudo apt-get install gdm
```

---

### Post by satellitex86 on 2008-12-16
Hi,
I tryed what you said, and that had no effect, so I did some more googling and found this [http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/]("http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/")
I edited part of the xorg.conf file from :
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2560 1056
	EndSubSection
EndSection

```

To 
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
#		Virtual	2560 1056
		Virtual 1280 800
	EndSubSection
EndSection

```

That brought the whole screen back on screen.

Thanks for the help!

---

