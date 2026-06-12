---
title: "Unable to detect my sound card"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by zzmel on 2006-01-04
Hi Everyone: :confused: 

I am really a newbie when it comes to this type of Linux Kernel.  I am trying to find a way so as Ubuntu can recognize my sound card. I have a Creative Live 24-bit sound card which works well in Windows XP.  I had absolutely no problems installing Ubuntu itself but I really would like to have sound.  Does anyone have any suggestions?  Thanks lots.

Regards,

zzmel  :cool:

---

### Post by anshus@wwt.net on 2008-01-11
How do I detect the bit number on my sound card

---

### Post by Yellow Pasque on 2008-01-11
> **anshus@wwt.net said:**
> How do I detect the bit number on my sound card
What sound card do you have?
```
sudo lshw -C multimedia
```

---

### Post by AlexEagar on 2008-02-16
These two links will help if your card uses an ISA connector.

[ISA Solution]("http://ubuntuforums.org/archive/index.php/t-115697.html")
[ISA Explanation]("http://www.osnews.com/permalink?f298700")

I tested the snd-sbawe module by running 'sudo modprobe snd-sbawe' and then logging out and logging back in. It worked, so I added the following line to /etc/modules to get my Sound Blaster AWE64 CT4520 to work.

snd-sbawe

If you find the right module, which I image will have a .ko extension like snd-sbawe, you should be able to test it and install it in the same way. I haven't looked up any information about your card, so I don't know whether this solution will work for you.

Good luck.

---

