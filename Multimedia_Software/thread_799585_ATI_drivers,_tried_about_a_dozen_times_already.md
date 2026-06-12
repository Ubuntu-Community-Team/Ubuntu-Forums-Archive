---
title: "ATI drivers, tried about a dozen times already"
date: 2008-05-19
forum: Multimedia Software
---

### Post by NoPantsJim on 2008-05-19
I've been having some trouble getting Ubuntu to work on an older PC with an ATI card. I've never had trouble with Nvidia cards in the past, and this is the first time I've ever tried linux with ATI.

The computer is using an AMD 2800+ and [this video card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814103017"). The monitor is a 42" lcd @ 1920x1080.

I've tried the normal route described [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882") and also tried using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to no avail.

What essentially happens every time is that I install Ubuntu, go to the desktop and install the drivers using one of the techniques above, and then restart when told to do so. When the computer restarts, I get the Ubuntu logo with the loading bar beneath it. As soon as it completes, the screen goes blank and is unresponsive. I've tried switching to different terminal windows with no success, the screen just stays blank.

Any ideas?

---

### Post by Panzerino on 2008-05-19
Same thing here- ATI Radeon 1650 Pro, AGP version.
Black screen before the log windows, or white screen after the log windows.

sudo apt-get remove --purge xorg-driver-fglrx

help you not to install endless times the Ubuntu from the LiveCD.
No solution for me.
No answer from anywhere... .
Many "opinions", but nothing WORKING.

These boys here simply kidding us.
My patience is over... .

---

### Post by totfit on 2008-05-26
I have the same problem with the same card. I have read that the fglrx package works for this card, but it does not for me. Been running gnome in safe mode since installing. I will delete it and see what happens. Hope to find a solution without putting back my nVidia 128mb card.

---

### Post by alecmg on 2008-05-30
nvm, wrong again

---

