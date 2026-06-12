---
title: "S Video"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Karly on 2009-04-01
Hi,
I'm pretty new to Ubuntu, and I'm by far not a computer wiz, so please forgive me in advance. 
All I'm trying to do is watch a movie on my TV through my laptop. I have the S Video cable hooked up, and I was searching around on some sites for some help. There was mention of this Catalyst Control Center on one site, so I thought I'd give it a go, and it seemed promising, but unfortunately it got me nowhere. 
Anyone know how I can do this? 

Thanks 
Karly

---

### Post by xc3RnbFO8P on 2009-04-02
What is your computer spec?

---

### Post by Karly on 2009-04-02
I have a toshiba satellite A210, I think my graphics card is a ATI Radeon X1200. I don't know too much about my computer, I don't know if there are drivers I need, or how to find them... Ubuntu's confusing!

---

### Post by hristostoev on 2009-04-11
I have the same problem, my computer is also Toshiba Satellite 210 and the video card is ATI X1200 . I hope someone can help.
I've tried the 
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
 but this is the result:
xrandr: cannot find output "s-video"
hristostoev@hristostoev-laptop:~$ sudo xrandr --addmode s-video 800x600
xrandr: cannot find output "s-video"
hristostoev@hristostoev-laptop:~$ sudo xrandr --output s-video --mode 800x600
hristostoev@hristostoev-laptop:~$ xrandr --addmode S-video 800x600
xrandr: cannot find output "S-video"
hristostoev@hristostoev-laptop:~$ 

Thanks!

---

