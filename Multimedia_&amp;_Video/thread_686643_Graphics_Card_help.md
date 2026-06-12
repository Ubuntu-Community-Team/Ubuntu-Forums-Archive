---
title: "Graphics Card help"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by nazgul42 on 2008-02-03
I just upgraded (kinda) my graphics card with one that was laying around, and is probably better, and I don't know what brand or model it is.  I need the driver so I can get a higher resolution and other things, but what software will detect what card it is?  Thanks in advance.

---

### Post by perixx on 2008-02-03
Hi! 

The most simply procedure should be, to enter your Menu > System > Restricted Manager. There you can both see what kind of card (ATI/Nvidia) you have and also enable the proprietary driver that comes with Ubuntu. I'd recommend you to use that one, if you're new to Ubuntu and don't bother to set up the newest drivers - if you've seen some of my posts here, you can see what kind of trouble you might run into ;)

To see a more detailed printout of your card's type, enter in a terminal: ```
lspci | grep "Display controller"
```Besides, you'll get a quick glance at your card's official model label at every bootup sequence (it's the very first message you get when turning on the computer). Also checking the bios could reveal info.
Oh, and, I hope that you've uninstalled your previous drivers before thinking of upgrading - most especially if it's a different brand!

perixx

---

### Post by nazgul42 on 2008-02-03
Neither of those work... the first one says I don't need any restricted drivers, and the second doesn't display anything

I never really installed any drivers for the first card, it worked from the start

---

### Post by perixx on 2008-02-03
Ok, try to fetch the card info when rebooting the system, right after the screen goes blank and the boot-up sequence starts. You can press CTRL+ALT+DEL over again a few times, if you can't catch up with it the first time...
I suppose there was no label printed on the card somewhere?

Or maybe this command gives some output: ```
$ lspci -nn | grep VGA
```.
Another way to find out indirectly might be: ```
less /etc/X11/xorg.conf | grep "Driver"
```If the output shows "ati", "radeon" or "fglrx" (unlikely), then you've got an ATI card. If it's "nv" or "nvidia", you've got a Nvidia card. If "vesa" is displayed, you can't tell this way. For installation of the restricted drivers, see those links here:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

perixx

---

### Post by nazgul42 on 2008-02-03
I tried the first command, and it said:
01:05.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 86C326 5598/6326 [1039:6326] (rev 0b)

What do I do with that?

---

### Post by perixx on 2008-02-03
Well, generally, 'altavista' or 'google' are good candidates to find out about vendor-specific questions ;)

I see you've got an integrated graphics chip (notebook?)...

If you can't find any drivers here:
[http://www.sis.com/download/agreement.php?url=/download/]("http://www.sis.com/download/agreement.php?url=/download/")
[http://www.sis.com/support/support_faqs_16.htm]("http://www.sis.com/support/support_faqs_16.htm")
I'm afraid there's not much hope for Linux-drivers. Unless there are some open source drivers, but I don't know of any.

In this case, you'd have to stick to the Vesa drivers, I guess. Did you check: ```
mousepad /etc/X11/xorg.conf 
``` What's your graphics driver in use? Vesa or sth. different? If the latter, then you might already have the open source drivers in use for you chip...

perixx

---

### Post by perixx on 2008-02-03
I just discovered, that there's an 'xserver-xorg-video-sis' package in Synaptic; no idea, whether that's an accellerated and /or 3D driver package, but perhaps you can give it a shot...

I suppose 'sis' should be the respective driver to put into the 'driver' section of xorg.conf for this - no guarantee, though.

perixx

---

### Post by TorqueyPete on 2008-02-04
Hi Naz
Here's how you should be able to view the spec of most of your hardware.


System
Preferences
Hardware Information

That gets you into the device manager. I think the info is 'open' by default, but you can open and close each item with the little triangles on the left hand side.

Then you'll be scrolling down till you see something like, in my case, this.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/Screenshot-6.jpg[/IMG]

Hope this helps.

---

