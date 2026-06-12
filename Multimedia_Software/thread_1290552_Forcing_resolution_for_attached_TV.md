---
title: "Forcing resolution for attached TV"
date: 2009-10-13
forum: Multimedia Software
---

### Post by Jeconti on 2009-10-13
I have a 27" Samsung DYNA flat HD hooked up to my box though an NVIDA card. The TV is capable of displaying 1080i, but I can't get the NVIDIA X Server to recognize a resolution higher than 1024x768

Here is my current /etc/X11/xorg.conf

```

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
```

Thanks in advance.

---

### Post by hellblazer on 2009-10-15
What screen card do you have?

Could you post your entire xorg.conf file?

I've never been able to get my TV on a higher resolution than that, but I have a normal TV ;)

---

### Post by hellblazer on 2009-10-16
I found another thread that might help you.

[Have a look]("http://ubuntuforums.org/showthread.php?t=444960")

---

