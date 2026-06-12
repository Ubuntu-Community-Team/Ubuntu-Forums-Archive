---
title: "Microphone only inputs screeching sound"
date: 2014-10-08
forum: Multimedia Software
---

### Post by jack108 on 2014-10-08
I'm relatively new to Linux/Ubuntu, so just let me know if I leave out any crucial details.

I'm running 14.04, and I'm trying to use my Apple headphones that come with iPhones. They typically plug into a combo jack and just work (input and output). My system is an Asus UX31A, if that matters.

Basically all there is to say is that my microphone only seems to hear annoying screeching. My goal is to use the headphones for Teamspeak 3, but I've tested them using gstreamer-properties. Thanks in advance for any help!

---

### Post by Vladlenin5000 on 2014-10-09
Apple's "combo jack" isn't standard. Perhaps that's the problem...
Do you have any other like the ones bundled with Samsung, HTC, Meizu, etc. to test?

---

### Post by tgalati4 on 2014-10-09
Your laptop has a combo port:

> 1 x Headphone-out jack (Audio-in Combo)
2 x USB 3.0 port(s)
1 x micro HDMI
1 x Mini VGA
1 x SD card reader
*3
Audio
Built-in Speakers And Microphone
Bang & Olufsen ICEpower®

But it also has B&O sound, so it is possible it has a strong preamplifier.  Try turning off microphone boost.  Some Mac jacks have slightly different spacing of the rings--compare them to other sets and you will see that they seat slightly differently.  Sometimes you can use a very small o-ring to get them to seat correctly on non-iphones.  If you don't have an o-ring, wrap a few layers of dental floss around the plastic shoulder to increase the set-back.

---

### Post by jack108 on 2014-10-10
Thanks for your help. The dental floss thing worked! ...Kind of. It's super finicky, and even when everything is positioned perfectly, there's still a lot of static. I suppose this isn't an Ubuntu problem anymore, but does anyone have a good solution to this?

---

### Post by tgalati4 on 2014-10-10
Look for different headsets.  Try them first.  I have to use the floss to use Apple headsets with non Apple devices.  Funky and annoying for sure.

---

