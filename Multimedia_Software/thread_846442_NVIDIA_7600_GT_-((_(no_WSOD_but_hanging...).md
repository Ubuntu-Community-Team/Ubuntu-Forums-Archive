---
title: "NVIDIA 7600 GT :-(( (no WSOD but hanging...)"
date: 2008-07-01
forum: Multimedia Software
---

### Post by CDrewing on 2008-07-01
Hi there,

so I installed the new NVIDIA driver V173.14.05 with my Geforce 7600 GT. It compiled. But finally, it does not work.

The system is not hanging on startup or giving me a **W**hite**S**creen**O**f**D**eath, it is *just* giving me a white screen which I can exit by pressing STRG-ALT-F1 to the logon screen. Until to the logon screen the graphic display works perfectly with my native resolution of 1680*1050. I can also listen to my startup sound.

I am still able to start a recovery-mode GNOME session selecting "GNOME (recovery mode)" on the logon screen. The desktop loads (after hitting OK in the info box) but from this point no scrips will be executed during startup it tells me.

So I read a lot about WSOD-issues combined with AMD and NVIDIA (I have an Intel CPU) and powernowd. But I don't think that this is my specific problem.

Something that is different between a regular startup *after* login and the GNOME-recovery mode login from the logon screen is causing a white screen - but I still can see my cursor and I can move it, too. But there's nothing to click on.

Anybody here to help me?
I am really fed up.

Christian.

---

### Post by feenicks on 2008-07-01
Just yesterday I installed a 7600 GS in my machine and had no trouble.  I used Envy to install the nvidia driver.  I think it was already there from the previous card.  I did not use the the newest Envy, because 7600 is an older card.  I don't know the commands to install from the command line, but if you think your driver install is messed up that could really help.  On the other hand, if you get a mouse cursor, then the driver is probably working.  Have you tried running dpkg-reconfigure as root from the command line?

---

### Post by CDrewing on 2008-07-02
Oh, [Envy]("http://albertomilone.com/nvidia_scripts1.html"). Didn't know that. It looks nice :KS:KS

No, I didn't try dpkg-reconfigure. I will do that before I will drop any nvidia driver and try to install it with Envy.

By the way, yesterday more in the evening I could login to the system using a regular session. But when I tried to hit the right mouse button, the screen went white and didn't come back. Still the cursor to see.

So it seems that it is a driver issue.

When I got envy running I will give feedback here after my first try.

Thanks!

---

