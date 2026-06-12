---
title: "Resolution problems"
date: 2009-06-05
forum: Multimedia Software
---

### Post by 000zero on 2009-06-05
Hello i have lenovo with a intel g43 mother board, im using the built-in graphics card.  I have a 22 inch Asus monitor and when i first installed Ubuntu 8.10 the maximum resolution was available, but now its not. I dont know what happened, this is my xorg.conf file:

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

Can anyone help me figure out why i cant use the screens native resolution anymore?

---

### Post by JCoster on 2009-06-05
Attempt to enable desktop effects (Compiz).  That should install a different set of drivers, after which point you should be able to use the maximum resolution available.

---

### Post by 000zero on 2009-06-05
The desktop effects are enabled, still no luck. Any other ideas?

---

### Post by bootdoc on 2009-06-05
yeah same here.  I logged out a couple hrs ago and then logged back in to 1024x768 and can't get anything higher!  Whats up with that.

---

