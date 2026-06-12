---
title: "nVidia Video Drivers??"
date: 2009-01-30
forum: Multimedia Software
---

### Post by aar0on on 2009-01-30
Installed Ubuntu 8.10 on a virtual machine.  Everything is cool so far, except I can't find drivers for my nVidia card.  I'm using the 5200 chipset.  800x600 pretty much sucks, if you know what I mean.

---

### Post by howefield on 2009-01-30
Is this virtualbox you are using ?

You are most likely restricted to the graphic drivers supplied by your vm, you can install guest additions if it is virtualbox, which should allow you better resolutions.

---

### Post by aar0on on 2009-01-30
Yeah, I'm using VirtualBox.  Explain to me how to do this, if you could, please.  Talk to me like I'm a 5-year-old. ;)

---

### Post by howefield on 2009-01-30
I am not in Ubuntu right now, but there should be a menu option on your vm window which is self explanatory, prob easier for me to give you this link..

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by aar0on on 2009-01-30
Actually, it looks like it might not even be possible since I'm using VB.  I guess I'll just dual-boot with XP, how I had initially intended to.

---

### Post by howefield on 2009-01-30
It is possible. :p

---

### Post by aar0on on 2009-01-30
Well, I tried to follow the instructions you linked to above, and I got as far as "sudo bash ./VBoxLinux*", after which it asked for my password.  I tried to type it in, but it would accept any key strokes whatsoever.

---

### Post by yther on 2009-01-30
If you are running Ubuntu *inside* VirtualBox, you would not need to install drivers for your actual video card, because Ubuntu will not be seeing that.  What it sees is the virtual video screen, and to get better resolutions for *that*, you need to install the guest additions.  The link given above pretty much explains that very early.

Once you've done that, you'll be able to either select different resolutions, or (as with me) be stumped because you still can't -- until you find that you can simply resize the VM window by dragging the edges around.  ><

Edit:  Do you realize that when entering your password for sudo, by default your keypresses will not be displayed?  It should still work, you just don't see any indication that you're typing stuff.  :)

---

### Post by aar0on on 2009-01-30
Yeah, the link above explained it perfectly.  However, I'm unable to put in a pssword when prompted for one.  I can't really get any further than that.

---

