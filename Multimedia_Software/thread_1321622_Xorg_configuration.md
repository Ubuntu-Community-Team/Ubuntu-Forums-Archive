---
title: "Xorg configuration"
date: 2009-11-10
forum: Multimedia Software
---

### Post by rogueleader12345 on 2009-11-10
I have a gutted Dell Precision 670 that I put all new parts in. While I was waiting for my video card to be delivered, I had an Ati X850 XT in it, and I pulled the IDE HDD from my old computer and put it in the new one. I started Ubuntu up, it scanned my HDD, said it found hardware changes, restarted and worked fine. I then got my Ati Radeon HD 3870 x2 and put it in my computer. I started Ubuntu up and it went through the load bar, then my screen went blank, and my monitor said "Input Signal Out of Range". So I went to a terminal and installed the Ati Proprietary Driver and figured that that would work. I ran aticonfig and it said "aticonfig:No supported adapters found." I figure it's either not in the right resolution or has the wrong refresh rate, and would like to know how to change the Xorg configuration for resolution and refresh rate from the terminal. Thanks!

---

### Post by markbuntu on 2009-11-10
The 3870x2 is specifically listed as not supported by the ati proprietary linux driver. I think it has to do with the way the two gpus were configured in the card.

But, you can try this

sudo aticonfig --adapters=all --initial -f

It might work, might not.

aticonfig --help

---

### Post by rogueleader12345 on 2009-11-11
So then is there a driver designed for the 3870 x2? Or do I just have to stick with the generic Ubuntu driver?

---

