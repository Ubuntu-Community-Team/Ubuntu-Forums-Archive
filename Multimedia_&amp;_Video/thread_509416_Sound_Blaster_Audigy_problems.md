---
title: "Sound Blaster Audigy problems"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by n&#647;unqn on 2007-07-25
Hi, I'm still pretty new to linux and I've been trying out some different distros. My sound card worked under Windows XP and Debian, but it doesn't work in Ubuntu or Ubuntu Studio, which is what I have installed right now. It's a Sound Blaster Audigy, and apparently the chipset is emu10k1. I tried following the guide [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449"), but for whatever reason it didn't work.

---

### Post by mohnkern on 2007-07-25
Do you have an Nvidia video card in your computer?

---

### Post by n&#647;unqn on 2007-07-25
Yeah, an Nvidea GeForce FX 5600

---

### Post by mohnkern on 2007-07-25
You might try this -- It's worked for me, and one other person:


sudo nvidia-xconf

---

### Post by n&#647;unqn on 2007-07-25
M'kay......I tried it and it says "command not found"

---

### Post by mohnkern on 2007-07-25
My bad...

nvidia-xconfig

---

### Post by n&#647;unqn on 2007-07-25
Okay, I did that and it told me this:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Still doesn't work though

---

### Post by mohnkern on 2007-07-25
Try typing asoundconf list 

What did you get?

---

