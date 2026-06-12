---
title: "problem with hybrid graphics laptop. Where is switcheroo?"
date: 2011-12-19
forum: Multimedia Software
---

### Post by hitman75 on 2011-12-19
Hi everyone,

I have the laptop sony vaio vpcse1e1e with two graphic cards : radeon hd6630 and integrated intel.
Ubuntu 11.10 use both of them(i think so) and there is big battery drain(moreless 1,5h on ubuntu and 4h on windows).
I want to turn off radeon by switchero and make my laptop works for longer time. So i used this tutorial:
[http://technologically-speaking.blogspot.com/2011/08/getting-ubuntu-to-work-with-dualhybrid.html]("http://technologically-speaking.blogspot.com/2011/08/getting-ubuntu-to-work-with-dualhybrid.html") , but when i type > sudo cat /sys/kernel/debug/vgaswitcheroo/switch then i see communication that there is no such a file or directory. I guess there is no switcheroo on my ubuntu. 
And the question: How can i add switcheroo to my system or to my kernel(or wherever it should be)?

---

### Post by BicyclerBoy on 2011-12-19
It is not in ubuntu repos..

[http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page)

---

### Post by hitman75 on 2011-12-20
ok, as i see switcheroo is a part of kernel 2.6.35 or later. My kernel is 3.0.0.12-generic, but still i see respond like there wasn't be switcheroo.
Or maybe should i install 2.6.35 kernel, but will it work with ubuntu 11.10?

---

### Post by BicyclerBoy on 2011-12-20
Being in the kernel means there is a kernel space driver..

There still needs to be some user-space program/driver to interact with the kernel driver..

May just be some scripts you can download from that linked site ?

---

### Post by hitman75 on 2011-12-23
Unfortunatly, i only see information about version of kernel. Any other ideas?

Ps. Thankyou for responses.

---

### Post by hitman75 on 2012-01-12
The problem is still unsolved.

---

### Post by Mark Phelps on 2012-01-13
See if anything in the link below helps:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by rojaasensei on 2012-01-13
> **hitman75 said:**
> ok, as i see switcheroo is a part of kernel 2.6.35 or later. My kernel is 3.0.0.12-generic, but still i see respond like there wasn't be switcheroo.
Or maybe should i install 2.6.35 kernel, but will it work with ubuntu 11.10?

I am in the same situation as hitman.  This is confusing as playing with the kernel seems risky

---

### Post by gordintoronto on 2012-01-14
Is there some reason you don't install Bumblebee?

---

### Post by hitman75 on 2012-01-14
> **gordintoronto said:**
> Is there some reason you don't install Bumblebee?

As i read, Bumblebee is working on Nvidia. I have Radeon.

---

### Post by gordintoronto on 2012-01-14
That makes sense.

And your BIOS won't disable the Radeon?

---

### Post by dnzz on 2012-02-01
Have you installed restricted drivers for ATI?

If you install, it removes switcheroo. I searched for a solution about a week and could not find one. I did a clean install to get switcheroo.

---

### Post by hitman75 on 2012-02-16
I think i move forward with my issue. I'm not completly sure if i turned off radeon graphic card, but i think so, because at the beginning my computer lasted 1h 10min with doing nothing. At the moment i can watch entire movie, but it is still not the same like under Windows. Under ubuntu it needs moreless 75% of battery to watch a normal movie (i mean 1h 30min). Under Windows it needs 50%.

Unfortunatly, i cant turn off discrete graphic card in BIOS - Sony sucks because of that.

Question
1. How to check if switcheroo works and only the intel integrated card is using?
If it is possible to check and it appears, that switcheroo turned off radeon, i will enclose the link with solution to the thread.  

Question about battery is for another thread, so i will not bother you about it.

---

