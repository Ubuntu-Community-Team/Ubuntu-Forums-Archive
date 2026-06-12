---
title: "Microphone's don't work properly."
date: 2011-06-03
forum: Multimedia Software
---

### Post by Linux_Geek_595 on 2011-06-03
I run ubuntu 10.10 with an 870-g45 motherboard which contains a VIA VT1828S integrated sound chip with 8 audio channels as it states on Newegg.com
I am having issues with getting microphones to work properly on my computer. Sound output works great but microphones don't. I've noticed when I tested mic's on the sound configuration it would act like it gets input but it would be choppy or laggy sound. Anytime i talk to people on voice chat they say my voice sounds like it keeps clipping in and out and they can't understand a thing I say. I have tried looking on google but any fix I looked at didn't seem to work for me. I don't know if it's motherboard related but I'm hoping I can get this issue resolved. Thanks

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Linux_Geek_595 on 2011-06-04
here is the output that was uploaded:

[http://www.alsa-project.org/db/?f=3d60ca3c8d825cea8af617fa7b5f95bf77f3c81b](http://www.alsa-project.org/db/?f=3d60ca3c8d825cea8af617fa7b5f95bf77f3c81b)

---

### Post by lidex on 2011-06-05
Which input are we talking about, internal mic or external?
You should try with a non-pae kernel just to rule that out, I
have seen recent issues.

---

### Post by Linux_Geek_595 on 2011-06-05
It's an external mic being plugged into a Port. Speaking of pae... Don't I need that if I have more than 4 gb if ram? (I have 12gb at the moment.)

---

### Post by lidex on 2011-06-07
> **Linux_Geek_595 said:**
> It's an external mic being plugged into a Port. Speaking of pae... Don't I need that if I have more than 4 gb if ram? (I have 12gb at the moment.)
Yes, for 32 bit, but I have seen recent issues surrounding a pae kernel so just try your stock kernel to rule it out.

---

### Post by Linux_Geek_595 on 2011-06-08
I don't mean to sound newbish but how do i do that on a 32-bit Ubuntu?

---

