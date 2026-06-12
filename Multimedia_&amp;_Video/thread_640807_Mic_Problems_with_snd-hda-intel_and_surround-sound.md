---
title: "Mic Problems with snd-hda-intel and surround-sound speakers."
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by Patriot1776 on 2007-12-14
My custom built PC uses the STAC9220 onboard sound chip and I've got a full-surround sound setup using a 5-speaker Logitech speaker set with subwoofer.  The line-in, line-out, and I guess mic jacks are all taken up in the back, and the system is not seeing my front mic input and front headphone jacks.  I'm trying to get a front mic working.

Using ALSA 1.0.15, with the snd-hda-intel kernel module.  Currently, in /etc/modprobe.d/alsa-base, I have the following added at the bottom:

```
options snd-hda-intel model=ref
```

I've tried setting this to '5-stack', with no luck. 

I've got a sinking feeling that my surround-speakers are using every port/jack up that the kernel module recognizes.  Any ideas?

---

### Post by Patriot1776 on 2007-12-14
Oh, don't know if this would matter, but kernel is 2.6.22-14-generic

---

