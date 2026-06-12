---
title: "Can't establish wireless connection in live mode"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Toske on 2011-10-15
Hi,

I have tried Lubuntu in live mode and even though I can see my router I can't connect to it. Connections dialog is grayed when I try adding new wireless connection and when I click it from the pop up menu nothing happens. Have enabled wireless and networking in the same pop up.

The usb dongle which I use works perfectly in Oneiric and Lubuntu 11.10 seems to recognize it. Any ideas how to make it run? I would very much like to switch to Lubuntu admiring its speed and simplicity.

---

### Post by Toske on 2011-10-15
Sorry for bother, I found what it was all about on my own.

It appears that Lubuntu doesn't like to have the dongle plugged in while booting. After the system is all up and running, no problem establishing a connection.:)

---

### Post by Toske on 2011-10-15
:( nope, I was wrong. It happens every now and then even if the dongle is not plugged in. And it's not the only thing I've spotted. What also happens is the live boot doesn't load the gui, startx is necessary, and when that happens the icons in the panel look different. And of couse I can't connect.

So, yet again I'd like to ask anyone who resolved this problem for the fix.

---

### Post by Craig-W on 2011-10-19
I have the same behavior on my Inspiron 700m.  Live CD boots to command line, and StartX starts a LXDE desktop, but not the standard lubuntu desktop.  My access point shows up on the dialog, both from internal wireless and from a TP-Link USB wireless dongle, but no option to connect is available for either.  I've been running Xubuntu 11.04 with no problems on this machine, and the LiveCD for Xubuntu 11.10 seems to work okay.  I had similar problems when I tried to run the lubuntu 11.04 LiveCD on this machine, which is why I ended up running Xubuntu.  (Also crunchbang linux works okay on this machine)

---

