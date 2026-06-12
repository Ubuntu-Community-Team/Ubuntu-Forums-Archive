---
title: "Xserver problems before installation"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by ki11.viru5 on 2006-07-19
I'm sorry if this is a repost but I've been having a lot of trouble  getting the livecd of Dapper to run correctly. Everything seems to work, but just as the GUI is supposed to come up, there is an Xserver error. 

It asks me if I want to find out what the Xserver problem is, but before I can do anything it goes straight into a command prompt(the command prompt goes diagonally across my screen not straight down).

So I guess my question is Is it a compatibility issue with my video card(a geforce Ti4200) and if so is there some way around it, or is something else wrong?

---

### Post by tseliot on 2006-07-19
Try using Safe mode as soon as the CD is loaded.

---

### Post by ki11.viru5 on 2006-07-19
> **tseliot said:**
> Try using Safe mode as soon as the CD is loaded.

I still get the same errors. I've also tried booting in various resolutions with no luck.

---

### Post by tseliot on 2006-07-19
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

