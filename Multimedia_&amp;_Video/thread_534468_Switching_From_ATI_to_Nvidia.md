---
title: "Switching From ATI to Nvidia"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Hyperkill on 2007-08-25
Hello all.  I am planning on switching from an ATI card to an Nvidia card due to the terrible issues that arise with ATI.  My questions are as follows.

I am using Fiesty 7.04 currently.

1.  Do I need to install AiGLX or can I continue to use XGL?
2.  If I need to install AiGLX, how do I do that?
3.  What precautions should I take?

Thanks for any help!

---

### Post by tseliot on 2007-08-25
> **Hyperkill said:**
> Hello all.  I am planning on switching from an ATI card to an Nvidia card due to the terrible issues that arise with ATI.  My questions are as follows.

I am using Fiesty 7.04 currently.

1.  Do I need to install AiGLX or can I continue to use XGL?
No, but I don't know why you shouldn't (since AIGLX seems to be less buggy)

> **Hyperkill said:**
> 2.  If I need to install AiGLX, how do I do that?
There's no need to install anything. It's part of the Xserver.

> **Hyperkill said:**
> 3.  What precautions should I take?
Uninstall ATI's proprietary driver and set the driver to "vesa" in your xorg.conf before you plug in the new card.

and disable Compiz/Beryl (if you enabled it to start at boot).

---

### Post by Hyperkill on 2007-08-26
Thanks a lot!

---

### Post by Victormd on 2008-03-28
Same situation... Though my questions are very similar, I thought I'd elaborate a bit more to my needs.
I have an ATI X300 and just purchased a Nvidia 8800GT for the "swapin"... I still have a few days before the nvidia gets here but I want to be ready to swap without, hopefully, having to format and reinstall ubuntu. Here are my main questions:
1. Do I have to uninstall ATI + flglx software before making the switch? How?
2. Do I need to install any general video driver after the uninstall or is this automatic? How?
3. Can I simply remove one card and put the and expect Ubuntu to detect the change and "suggest" the proper driver?
Not sure I made much sense but...
Thanks!

---

### Post by Yellow Pasque on 2008-03-28
The last time you have your ATI card in, uninstall the fglrx drivers. If you installed the version that comes with Gutsy, it should be as simple as pressing Ctrl+Alt+F1 and entering this in the terminal:
```
sudo apt-get remove xorg-driver-fglrx
```
If you've downloaded updated Catalyst drivers from ATI's site somewhere along the way, then you have to:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

Now open your xorg.conf (gksudo gedit /etc/X11/xorg.conf) and make sure the Driver line in the Device section says "vesa". Now you can turn your PC off and make the switch. When you restart, Ubuntu should enter "low-graphics mode", which isn't pretty, but you should be able to install the nvidia proprietary drivers from there through the Restricted Driver Manager or with *sudo apt-get install nvidia-glx-new* in a terminal.

---

### Post by Victormd on 2008-03-28
Thanks!
that's going to be very handy!

---

### Post by Victormd on 2008-04-01
Ok, so I finaly received my 8800GT... tried the switch for about a day, better yet, a night, to no luck.  It just kept on jumping back to VESA and my xorg.conf went crazy! Added, I don't know, how many "mode" lines and whatnots... so I ended up formatting and am reinstalling Ubuntu right now... There might have been something else that I could have done but my ubuntu-knowledge limitations kept me from doing so... oh well... nice and clean Gutsy. If anyone has anything to add to this post, please do so for future reference...

---

