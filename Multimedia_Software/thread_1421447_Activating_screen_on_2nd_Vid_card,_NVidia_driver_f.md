---
title: "Activating screen on 2nd Vid card, NVidia driver failed to parse X conf"
date: 2010-03-04
forum: Multimedia Software
---

### Post by rben13 on 2010-03-04
Just got Ubuntu 9.10 installed. Haven't done much with Linux for a while and between when I last used it and now, I've added a second video card, a NVidia 9800 GTX to go with my 9800 GT. They are not linked together. I got the second card so I could have 3 monitors.

When I try to activate the third monitor, the NVidia software reports that it 'failed to parse existing X config file '/etc/X11/xorg.conf'!'

That file contains:
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

Any ideas?

Thanks for taking the time to read and respond,
  Ray

---

### Post by darkBuntu on 2010-03-27
That's because by default the nvidia tool doesn't have the permissions to write to "/etc/X11/xorg.conf"

To solve this problem you have 2 options, or you chmod /etc/X11/xorg.conf to something like 777 for the time it takes to play with your display options and afterwards put it back to 644. Or, you can open a terminal and type this command :

gksudo nvidia-settings

This will bring up the nvidia tool, but with root permissions. That way, it can write to /etc/X11/xorg.conf.

When playing with the nvidia-settings don't forget to apply the changes first and then save it to  /etc/X11/xorg.conf! Otherwise you can start from scratch after next reboot / X restart ;)

---

