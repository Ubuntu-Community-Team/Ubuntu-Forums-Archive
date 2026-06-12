---
title: "Matrox G550 and Dual Screen Setup"
date: 2008-06-15
forum: Multimedia Software
---

### Post by jp734 on 2008-06-15
I have a matrox g550 with vga and dvi outputs and been trying to set it up to where I can use two displays on Hardy Heron. Here's what happens when I try to boot pc.

Start computer with both connections:
- Low resolution on dvi and screen is off to the left. Nothing on vga.

Start computer with dvi and connect vga after:
- Low resolution on dvi and screen is off to the left. Nothing on vga.

Start computer with vga and connect dvi later:
- normal on vga and nothing on dvi


I have attached my xorg.conf file.

---

### Post by jp734 on 2008-06-16
Does anybody know the trick to make this work?

---

### Post by Esa on 2008-09-16
> **jp734 said:**
> 
Start computer with vga and connect dvi later:
- normal on vga and nothing on dvi

Same problem here, few days ago I decided to move my display to DVI and I can't figure out how to make it work.

It was working before Hardy... maybe someday again.

But I never again buy Matrox, it has always been difficult when something is updated.

  Cheers, Esa

Ok, now I got dualscreen working :)  (hope I managed to upload xorg.conf .. no? Upload says "invalid file" - Why? .. file extension needs to be .txt - strange...? ).

1600x1200 mode on Samsung 204B is still a headache :confused:  ](*,)

---

### Post by Esa on 2008-09-26
> **Esa said:**
> 
1600x1200 mode on Samsung 204B is still a headache

Not any more :)  Thanks to tuxx-home.at and 
[http://www.nvnews.net/vbulletin/showthread.php?t=82982](http://www.nvnews.net/vbulletin/showthread.php?t=82982)

Samsung 204B(R) needs a bit lower frequencies, modelines were OK, but my last missing bit of information was:

Option "ExactModeTimingsDVI" "yes"

After that Hardy - Xorg agreed to use new modeline. Attached xorg.conf is now using two displays with xinerama. I'm sure there are still extra lines and absurdities, but its working :)

---

