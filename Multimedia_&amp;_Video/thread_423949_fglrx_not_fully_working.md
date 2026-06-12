---
title: "fglrx not fully working"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2007-04-26
Hello,
I've been having trouble getting fglrx to work completely. When I do fglrxinfo, it gives me the correct info (ATI Radeon 9000) but with glxgears, I'm only getting around 850 fps. It shows too that it's that slow because glxgears is running somewhat jerkey as are any 3d games. Sorry I'm not able to give you some output or my xorg.conf but I don't have that computer here in front of me. I followed method 2 at [this url]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"). The only difference being that I used 8.28.8  because that's what worked under Dapper and I couldn't get 8.35.5 working at all.

---

### Post by Steve H on 2007-04-26
A few questions i would look for to answer this:

> How many virtual desktop are you running?

have you got the TV-out running at the same time?

Have you checked for any processes running with high CPU load?

---

### Post by SteinbergerNate on 2007-04-26
Well, I have 4 virtual desktops running (nothing on them though) I don't know if the TV out is working or not. I haven't checked for any processes running a high CPU load yet but I don't think there should be anything since I check this as soon as I boot into gnome. By the way, what command should I use to find the cpu load of individual processes?

P.S.- While the FPS aren't up where I would like them, they are MUCH faster than they are with mesa. I.E. ~120 vs. 850.

---

### Post by Ferrat on 2007-04-26
Why not use the feisty version just incase and the latest ATi Driver?

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by SteinbergerNate on 2007-04-26
Well, I don't know how much all this is really going to matter. I'm planning on dl the feisty iso this weekend and doing a clean install sometime. Hopefully that will fix all my problems. Does anyone know if the restricted driver installer thingy that is on Feisty will get everything working properly or will I still have to install the fglrx driver manually?

---

### Post by Steve H on 2007-04-27
I've been having all sorts of transient problems since doing an "upgrade" to Feisty. But today i did a full clean install from the LiveCD, and everything works beautifully. I'd had problems with the Nvidia drivers previously and now all that seems to have gone. So my two cents is to definitely use the LiveCD to do a clean install, it seems to sort a lot of things out.

Good Luck, let me know how you get on.

---

