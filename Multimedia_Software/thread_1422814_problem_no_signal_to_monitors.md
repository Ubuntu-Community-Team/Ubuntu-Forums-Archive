---
title: "problem: no signal to monitors"
date: 2010-03-05
forum: Multimedia Software
---

### Post by iwtws on 2010-03-05
Any suggestions on how to tell my built-in video card to output a signal? I know the card is being used, it's just not driving the output.

Here's my setup: Three monitors side by side. The left monitor is connected to an old computer running a VNC client to display the leftmost 1024x768 pixels of my new computer. The other two monitors are connected to my new computer and work fine. 

I can barely use it this way--even mouse movement is jerky with VNC, and it seems silly to use a computer as a display for a computer sitting right next to it.



This is my first post, so I'm not sure how much detail I need to give about hardware, etc. I'm using Ubuntu 9.10, I started with a command line system, then used aptitude to install xorg, etc.

If I remove the pcie card, the built-in card works fine. It's only when I try to use them together that there is no output from the built-in card.

In the attached xorg.conf and log, there are actually five monitors, but the problem is the same. The left two (one above the other) I have to view using VNC (the ones that should be connected to the built-in outputs) the middle two (one above the other) and the far right monitor are all connected to the new computer.

---

### Post by iwtws on 2010-03-14
I am now able to use all four outputs, two on the built in graphics and two on PCI-E graphics card. But not in Ubuntu 9.10, and not with open source driver. So I could still use some help.

First question, is it possible to use Ubuntu 8.04.4 open source drivers with an ATI HD 3300 built in graphics processor?

Second question, same as first, but for an ATI HD 4350 graphics card?

Third question, should I file a bug against the open source 9.10 driver?

Here's how I got it working in Ubuntu 8.04.4. First I installed Windows, and verified it's possible to use both the internal graphics and the PCI-E card at the same time. Then I installed Ubuntu 8.04.4. I downloaded the latest drivers from the ATI website (Catalyst 10.2) because the open source driver wouldn't even let me start X. With the fglrx driver and some xorg.conf tweaking, I now have a single desktop spanning four monitors. I had to use Xinerama to combine the left two monitors with the right two monitors since they are on different cards, and xrandr doesn't support more than one GPU.

---

