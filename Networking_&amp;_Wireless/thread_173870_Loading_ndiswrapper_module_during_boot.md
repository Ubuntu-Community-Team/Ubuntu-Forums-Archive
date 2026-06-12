---
title: "Loading ndiswrapper module during boot"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by gomezj00 on 2006-05-11
Hi everyone,
I'm new to linux so please bear with me.  I just loaded breezy and installed my nic driver for my wireless card.  Everything is working fine except I have to keep running "modeprobe ndiswrapper" inorder for my nic to work.  Anyway I can load the module during bootup?  Thanks!

---

### Post by Dr. Nick on 2006-05-11
add the word
ndiswrapper 
to the top of /etc/modules

---

### Post by gomezj00 on 2006-05-11
[QUOTE=Dr. Nick]add the word
ndiswrapper 
to the top of /etc/modules[/QUOTE]


- You are awesome!  Thank you very much.  That worked like a charm and I ended up  learning where alot of other things.  Now I can configure some more stuff.  Thanks again!

---

