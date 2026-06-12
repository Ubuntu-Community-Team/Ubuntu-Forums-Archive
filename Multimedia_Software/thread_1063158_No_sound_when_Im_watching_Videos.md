---
title: "No sound when Im watching Videos?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Josshill on 2009-02-07
When I play a video on youtube, or some Sites :P There is no sound. Im lucky if the video even plays. I downloaded everything the guide told me to download if I was having any problems. Any help guys?

---

### Post by gandaran on 2009-02-07
are you using ubuntu 8.04 and flash 9? if correct then remove flash 9 and get the adobe flash 10 .deb package from adobe.com, flash 10 fixes the flash sound problem.

---

### Post by Josshill on 2009-02-07
> **gandaran said:**
> are you using ubuntu 8.04 and flash 9? if correct then remove flash 9 and get the adobe flash 10 .deb package from adobe.com, flash 10 fixes the flash sound problem.

Where do I get flash 10? The Jave Site?

---

### Post by gandaran on 2009-02-07
[here]("http://get.adobe.com/flashplayer/")

---

### Post by Josshill on 2009-02-07
> **gandaran said:**
> [here]("http://get.adobe.com/flashplayer/")

I downloaded it and I got an error: "Wrong Architecture i386"

---

### Post by gandaran on 2009-02-07
then you are using ubuntu 64-bits, right?

---

### Post by Josshill on 2009-02-07
> **gandaran said:**
> then you are using ubuntu 64-bits, right?

I believe so

---

### Post by gandaran on 2009-02-07
okay then, remove the flashplugin-nonfree, use synaptic for complete removal first
now get the 64-bits package [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz"), to install extract the package and move the libflasplayer.so file to /home/'user'/.mozilla/plugins (create the plugins folder) or if you have more than one user account place it in /usr/lib/mozilla/plugins.
I don't know if it'll fix the sound problem in 64-bits system but just try it

---

