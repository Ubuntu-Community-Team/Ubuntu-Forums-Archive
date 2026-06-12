---
title: "Dual monitors: 13.1 &quot; and 22&quot;, resoultion problems"
date: 2009-04-12
forum: Multimedia Software
---

### Post by nimonika on 2009-04-12
I have a 13.1 " monitor with a resolution of 1280 X 800 When I try to connect it to a Dell 22 " monitor, I do not get the full laptop screen to appear on the big screen. Please can someone advise on how to get this sorted.

---

### Post by soapBAR2 on 2009-04-12
I'm by no means an expert, but I'll try and help anyway. I'm assuming you want the 22" monitor to show what's shown on the laptop screen?

The first place to try to change your settings is your WM's (Gnome/KDE/XFCE/etc)'s built-in System Settings panel. This should (stress SHOULD) be fully compatible with open source drivers, so try there first. However, if this doesn't work, you're probably running the non-free driver (as many people are) - so, your best bet is to install the control panel specific to your brand of graphics card. To find out what brand you have, open a terminal and type

```
lspci | grep Display
```

(Make sure to use a capital "D" on "Display"). On that line, in addition to a bunch of information about your display card, it will most probably have either;
-nVidia/GeForce
-Radeon/ATi
-Intel
-Silicon Integrated Systems/SiS
-VIA

If you have nVidia/GeForce, type
```
sudo apt-get install nvidia-settings && sudo nvidia-settings
```
A GUI menu will open, have a look in there (I think it's the second tab down?)

If you have Radeon/ATi, type
```
sudo apt-get install fglrx-amdcccle && sudo amdcccle
```
A GUI menu will open, click "Display Manager" and sort it out through there

If you have any of the others, you might have to wait until someone else answers, sorry - I've never had to play with the display settings outside of nVidia/ATi cards (although as far as I'm aware, Intel and VIA both have fairly decent Open Source support, so I'd be surprised if you were using the binary for either of those brands).

---

