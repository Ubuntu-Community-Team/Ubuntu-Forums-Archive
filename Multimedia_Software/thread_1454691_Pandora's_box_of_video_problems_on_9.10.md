---
title: "Pandora's box of video problems on 9.10"
date: 2010-04-15
forum: Multimedia Software
---

### Post by rswoods on 2010-04-15
I have built a pretty standard 'nettop' system, using an intel atom (D945GCLF)mobo/proc combo which is handling the video output.  Poorly I might add.  I'm trying to determine if this is a problem with my hardware or a problem with 9.10.  I'm not very familiar with these sorts of issues as ubuntu has worked flawlessly on every other machine I've used, but I'm sure those of you who keep up with this forum will know whether this is a common issue or not.  I'll just run through the laundry list of symptoms:

When using 1280x1024 (the proper resolution for my monitor) the display leaves about 3/4in dead space at the bottom of the screen.  I can use the monitor's manual adjustment controls to move the display down but there is some sort of glitch in the lower right corner.  It looks like a mirror-facing-a-mirror effect almost, it's hard to describe but if you've seen it you'd know what I meant.  It doesn't show up in screenshots.  Text-mode and 1024x768 display with the proper screen positioning and without the flaw.

I apt-get installed LXDE and set it as my default DE as this is a low-powered machine.  When the system boots and logs in automatically the graphics are huge, I mean GIANT.  Fonts, widgets, everything.  If I log out and log back in things display "normal" (albeit with the dead space and graphical glitch described above).  This is preventing me from installing, say, the ubuntu-based Crunchbang from their openbox-based livecd, because the huge graphics still persist even there.  I want to be very clear that **I do not expect any help with LXDE, Openbox, or Crunchbang from you but I wanted to mention this problem just in case it is related and helps diagnose the underlying cause behind these issues.**

I have already concluded that this is not a monitor problem, and I'm worried either about buggy compatibility of Ubuntu with my hardware or the physical integrity of the hardware itself.  I'm hoping this is something common that can be fixed with some tweaking or maybe trying another distro.  Thanks for your time.

---

### Post by cchhrriiss121212 on 2010-04-15
Have you tried the new crunchbang? It's debian based and although it is still an alpha release, it is very stable, and even more lightweight than the old one. I'm using it on my old inspiron 1100 which required a host of fixes to get X running correctly, but it works with no fiddling on the new crunchbang.

---

### Post by guy.tarded on 2010-11-17
hi, i'm installing this at the moment on my inspiron 1100. What are the x fixes? Can you help me ? thx

---

### Post by cchhrriiss121212 on 2010-11-17
See here:
[http://ubuntuforums.org/showthread.php?t=1358862](http://ubuntuforums.org/showthread.php?t=1358862)


Keep in mind these fixes are for 9.10. In the other thread you have posted you state that you are using 10.10, which I have not tested yet with this laptop.

It is the intel chipset that causes the trouble, browse through google and you will see that it is a nightmare for running any linux OS. Currently I have a stable setup but it still fails to load X 10% of the time when booting up, and I also cannot update anything.

---

