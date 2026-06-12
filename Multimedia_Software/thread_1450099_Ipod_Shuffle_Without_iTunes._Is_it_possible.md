---
title: "Ipod Shuffle Without iTunes. Is it possible????"
date: 2010-04-08
forum: Multimedia Software
---

### Post by maxrpowell on 2010-04-08
I just got a new iPod shuffle (pink 4th gen model #A1271). I want to use this without windows or mac (both of which I do not have access to) I have searched forums and online to no avail and would like to know if anyone knows how. If you have any suggestions on how, please let me know.

---

### Post by WinterRain on 2010-04-08
It's my understanding that the upcoming release of ubuntu (10.04 to be released on the 29th) has support for ipods.

---

### Post by ron999 on 2010-04-08
Hi
Mine's a second generation iPod Shuffle (silver).
It works well with **gtkpod**.

---

### Post by mcduck on 2010-04-08
> **WinterRain said:**
> It's my understanding that the upcoming release of ubuntu (10.04 to be released on the 29th) has support for ipods.

Ubuntu (and Linux) has supported iPods for years. It's the IPhone and iPod Touch that are getting the support in 10.04... ;)

Anwyay, have you tried if Rhythmbox recognizes the Shuffle? If not, then you could try with gtkpod. That's what I've been using with my iPod, and it should support all iPods from generations 1 to 5...

---

### Post by tgalati4 on 2010-04-08
I think floola runs on it.  [http://floola.com](http://floola.com)

Choose floola for linux and put it in the root directory of your shuffle.  It should show up in your drive list when you plug it in.

You might need to find a mac to turn off journalling if it is formatted as HFS+.  If it is formatted with FAT32 you should be OK.

Plug it in, open a terminal, post the output of:

sudo fdisk -l

---

