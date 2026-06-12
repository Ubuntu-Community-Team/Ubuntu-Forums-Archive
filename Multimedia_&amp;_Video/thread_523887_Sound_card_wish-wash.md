---
title: "Sound card wish-wash?"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by Onay on 2007-08-12
I have two sound cards apparently installed. I have the Intel ICH5 as well as a Creative Sound Blaster Audigy. Whenever I boot up ubuntu, I usually have the Intel card set as default. I can NEVER get sound to work when that is default.

However, on occasion the Sound Blaster Audigy card is set to default, and after a bit of tweaking the switches and levels in volume control, I can manage to get sound working.

Why does it switch? I need to have the SBA card set to default or else Alsamixer won't set it to default either, then I get zero sound. How can I set a default card and keep it that way and the way the switches are set every time I boot up?

---

### Post by wolfen69 on 2007-08-12
go into BIOS and disable the Intel (onboard) sound. ubuntu will only see the soundblaster now.

---

### Post by Onay on 2007-08-12
My BIOS doesn't even seem to have that setting. Do I need to update it? I just installed using Wubi, so will it mess that up if I flash my BIOS?

---

### Post by Onay on 2007-08-12
Wow it worked! Thanks soo much!!

---

