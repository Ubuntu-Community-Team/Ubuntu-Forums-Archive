---
title: "Graphics card problems"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by greeneggsnsam on 2007-06-23
Hi,
Running Feisty, i had no problems at all- but i recently got a new graphics card and all i get when i load it up is the blank "temnial only" type screen. I don't know how to install drivers or anything for it using this screen, so help is needed! My card is an ATI Radeon 9200SE. I can give more info if needed but i think that should be all...

Thanks

---

### Post by Crafty Kisses on 2007-06-23
> **greeneggsnsam said:**
> Hi,
Running Feisty, i had no problems at all- but i recently got a new graphics card and all i get when i load it up is the blank "temnial only" type screen. I don't know how to install drivers or anything for it using this screen, so help is needed! My card is an ATI Radeon 9200SE. I can give more info if needed but i think that should be all...

Thanks
Hey Try reconfiguring your X server.
```
sudo dpkg-reconfigure xserver-xorg
```
This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

---

### Post by greeneggsnsam on 2007-06-24
Thanks, it worked! (however i am always skeptical when things are this easy..)

---

