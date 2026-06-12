---
title: "looking for the right video card"
date: 2009-02-18
forum: Multimedia Software
---

### Post by cool2000m on 2009-02-18
hey guys.

I just installed ubuntu ultimate gamers edition and I've decided that I need a video card, but I am having difficulty finding one that meets my specifications, and I have some questions as well.

My Specs:
32-bit amd athlon
vga monitor
512 megabytes of ram

Here are my questions
-Does it matter if my video card is a 64-bit RAM and my processor is a 32 bit?
-are there any good websites I need to be aware of?
and, lastly...
-am I in the right forum?

Thanks!

---

### Post by Mercury_Alpha on 2009-02-18
It looks like you're limited to an AGP video card, but the bit width of the video card won't have any bearing on the bit width of the CPU. If you want to get more info about your hardware, you can enter "lshw" in the terminal (without the quotes). This will spit out a bunch of data about your CPU, amount of RAM, and what chipset your motherboard has. The chipset is listed as Host Bridge in the pci:0 entry. For example, mine says "K8T800Pro Host Bridge." From there, I can determine if it will take an AGP or PCI-E video card.

Keep in mind, though, that this "Ultimate Gamer's Edition" isn't technically Ubuntu. It uses a different set of sources for its software repositories (AKA "repos"), for one thing. Depending on how different it is, you may have trouble getting accurate support from the Ubuntu community. Using essentially third-party repos is kind of a big problem, because you can't be sure of how up-to-date they are, and you also can't be sure that the repos contain 100% legit software. The fact that their website doesn't contain any kind of contact info, or even an "About us" page, makes me leery. Judging by a light surfing of their forums, they seem all right, but "seem" isn't something I'm willing to base an entire operating system on :)

---

