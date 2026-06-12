---
title: "Desktop effects on ATI X600 Duel Monitors"
date: 2010-03-19
forum: Multimedia Software
---

### Post by xtjacob on 2010-03-19
Hello, I'm using two monitors with an ATI Radeon X600 card in Ubuntu 9.10. I got the duel monitors to work by running sudo Xorg -configure, but now my desktop effects don't work. :confused: How can I get them to work again?

---

### Post by Yellow Pasque on 2010-03-19
If the combined size of your monitors is greater than 2048 in either direction, direct rendering won't work (mesa limitation). This linked is aimed at Intel GPU's, but it illustrates what I mean very nicely: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen)

---

### Post by xtjacob on 2010-03-19
Well right now I'm using one monitor that is DVI and is at 1680x1050 and one that is on VGA and is at 1280x1024. Also do I have to have the binary driver from ATI instead of the open source one?

---

### Post by Yellow Pasque on 2010-03-19
> Also do I have to have the binary driver from ATI instead of the open source one?
It won;t work on newer Ubuntu versions because your card is considered a legacy card.

---

### Post by xtjacob on 2010-03-19
Oh I was afraid of that. Since ATI support stinks which NVIDIA card do you recommend I get?

---

### Post by Yellow Pasque on 2010-03-19
Unless you're a gamer, you can get a low-end Nvidia card to do what you're looking to do. A GT220 card should be fine.

---

### Post by xtjacob on 2010-03-19
Ok thanks for the help, I've been looking into getting a NVIDIA card for awhile.

---

