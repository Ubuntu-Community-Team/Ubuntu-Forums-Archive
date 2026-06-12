---
title: "No sound in Totem but general sound VLC &amp; MPlayer OK"
date: 2009-06-12
forum: Multimedia Software
---

### Post by Johan-Steyn on 2009-06-12
Hi All,

I have a AMD desktop pc with a Asus Via motherboard & VIA AC97 audio controller & on-board sound.

Jaunty upgraded from Intrepid fine, all applications fine. Full 3D ATi video acceleration. Sound in all applications VLC, MPlayer, etc, except Totem.

I have Ubuntu restricted extras enabled; libdvdcss2; w32codecs etc. installed.

Pulse audio enabled. Master volume, turned up full.

Tried everything but could not enable sound in Totem.

Any ideas?

Thanks,

JS

---

### Post by jerrrys on 2009-06-12
in Synaptic there are Totem plugins. have you tried those?

---

### Post by Johan-Steyn on 2009-06-12
Hi jerrrys,

Thanks for the reply.

I have installed everything except the dev packages.

Would those necessarily help?

Regards,

JS

---

### Post by gradinaruvasile on 2009-06-12
The totem volume is up? Totem has a separate volume control.

---

### Post by Johan-Steyn on 2009-06-12
>                                   [B]gradinaruvasile

Re: No sound in Totem but general sound VLC & MPlayer OK[/B]             
                                                                The totem volume is up? Totem has a separate volume control.
Yes. I double checked. Both the master volume (top) and internal Totem volume controls are at max.

Regards,

JS

---

### Post by jerrrys on 2009-06-12
no, my mistake...not a plugin.  was talking about totem gstreamer in Synaptic...

---

### Post by Johan-Steyn on 2009-06-12
Hi Jerrrys,

>  				 				**Re: No sound in Totem but general sound VLC & MPlayer OK** 			
 			 			 		   		 		 		no, my mistake...not a plugin.  was talking about totem gstreamer in Synaptic...


I have the gstreamer 0.10 plugins installed for pulse & alsa (good bad & ugly sets).

Also totem plugins & plugins-extra.

Any suggestions?

Regards,


JS

---

### Post by gradinaruvasile on 2009-06-12
Try running totem from a terminal. Do u got error messages?

---

### Post by Johan-Steyn on 2009-06-12
Hi gradinaruvasile,

This is the output from terminal when running totem:

```
:~$ totem
/var/lib/python-support2.6/gdata/tlslite/utils/cryptomath.py:9: DepreciationWarning: the sh module is depreciated; use hashlib module instead import sha
```

For the record it starts OK, renders OK but still no sound.

Regards,

JS

---

### Post by jerrrys on 2009-06-12
you have probably been there, done that, but throwing it out there anyhow...

[ATTACH]117405[/ATTACH]

also in your OP you said:

"VIA AC97 audio controller & on-board sound"

are you running both, are you using both? 

and last.  howbout just doing a reinstall of totem and extra totem packages.  you may get lucky...

---

### Post by Johan-Steyn on 2009-06-12
Hi jerrrys,

Actually I meant to imply that the Via AC97 audio controller _is_ the on-board sound.

But I think I should take you up on the suggestion to reinstall Totem. Just maybe that will do the trick.

Will post back.

Thanks,

JS

---

### Post by jerrrys on 2009-06-12
im out of ideas, but here's a good source...

[http://www.google.com/search?q=no+sound+totem&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=no+sound+totem&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Johan-Steyn on 2009-06-13
Hi jerrrys

Thanks I will give it go.

Appreciate your assistance.

Regards,

Johan Steyn

---

