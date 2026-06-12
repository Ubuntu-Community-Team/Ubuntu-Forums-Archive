---
title: "Intel graphic drivers and compiz/beryl"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by jpolanco on 2007-01-07
I have a HP dv1000 laptop, with an Intel 915GM graphic card. I recently reinstalled Ubuntu Edgy. Before doing it, I could use compiz or beryl with almost no problems (only that the water plugin didn't worked), and I was using the i810 driver. I could also suspend the laptop with no problem.

Now that I reinstalled it, with a little bit more of experience in Ubuntu, I downloaded the drivers from [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/). I mean Mesa drivers, DRM modules and the X.org 2D driver, and I believe I compiled them right. I also installed the xserver-xorg-video-intel package from Synaptic. But when I used the i810 driver (in my xorg.conf file), neither Compiz or Beryl started fine, they only showed me the panels, and not even the entire panels. BTW I configured my xorg.conf file according to [this guide]("http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy").

Later I decided to use the "intel" driver instead of i810 (which was showed when I did sudo dpkg-reconfigure -phigh xserver-xorg). That one now allows me to use compiz (with a few graphic problems and bugs) and beryl (almost perfectly). I have a few problems, like the login window, which sometimes doesn't look as it should (the colors are changed), and now when I come back from suspension, it only shows a black window, and I have to restart X, losing all of what I was doing.

Maybe I'm a little confused about the drivers, maybe I could use some help about that. Sorry for my bad English :???:  And thanks in advance :)

---

### Post by jpolanco on 2007-01-09
Come on, I can still use some help here...

---

### Post by whistlerspa on 2007-01-22
I'm having the same issue onlt xgl and beryl won't work with either driver. This doesn't help you much I know - but there must be a solution out there somewhere

---

### Post by jpolanco on 2007-01-22
Well I finally found a solution some time ago. In Section "Device" I added the following line:

VideoRam	131072

which is the memory in kB of my graphics card. Then compiz and beryl worked fine (with aiglx). And I'm running the i810 driver :) I hope this helps you now

---

