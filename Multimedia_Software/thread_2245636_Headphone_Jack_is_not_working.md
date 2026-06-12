---
title: "Headphone Jack is not working"
date: 2014-09-25
forum: Multimedia Software
---

### Post by 7-matthew on 2014-09-25
I am running a 64bit version of Ubuntu 14.04 on an Acer Aspire 5930 but my headphone jack is not working. I downloaded the asla information script and my computers info can be found at [http://www.alsa-project.org/db/?f=6f8e95f9fca1ad4e3966f921ef3c6f6e9c10152a](http://www.alsa-project.org/db/?f=6f8e95f9fca1ad4e3966f921ef3c6f6e9c10152a)
I am trying to get it to work so my speakers don't wake up my dad or my brother.

---

### Post by Yellow Pasque on 2014-09-27
I'm pretty sure you want it to say true here, but I'm not sure how/if you can manually turn it on, since it looks like you have everything set right in alsamixer:
```
	control.35 {
		iface CARD
		name 'Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
```

Double-check settings in alsamixer (remember 'm' key toggles mute, and up/down arrow changes values).

---

