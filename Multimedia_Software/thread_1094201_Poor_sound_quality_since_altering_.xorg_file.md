---
title: "Poor sound quality since altering .xorg file"
date: 2009-03-12
forum: Multimedia Software
---

### Post by thomasboleyn on 2009-03-12
Hi there. I am using Xubuntu 8.10, and since adding nohz=off to my kernel options and adding 'Option "AGPMode" "1"' to the first paragraph of my xorg file to allow my Sony Vaio PCG-K215Z to work wirelessly, I have noticed that the sound quality is very poor, whereas it wasn't before. 

Before this I was using 'acpi=off' as a permanent kernel option, and using a wired internet ethernet cable straight to the modem, rather than wireless, as I couldn't get it to work. The sound was fine, even with 'pcm' turned up high. Now I get lots of crackling when a song plays. I have played with different slider options but nothing seems to improve it at all. I have also tried different media players, and tried my speakers on my ipod, and everything suggests the problem lies with the laptop. 

Just wondering if the recent changes I've made explain the problem I'm having.

Any help woud be greatly appreciated, thanks.

---

### Post by thomasboleyn on 2009-03-20
Bump:popcorn:

---

### Post by markbuntu on 2009-03-20
The nohz=off kernel option is causing the 64k alsa buffer to run out before it gets cpu access to reload.

---

### Post by thomasboleyn on 2009-03-20
> **markbuntu said:**
> The nohz=off kernel option is causing the 64k alsa buffer to run out before it gets cpu access to reload.

Thanks for replying, is there any way of getting round this problem?

---

