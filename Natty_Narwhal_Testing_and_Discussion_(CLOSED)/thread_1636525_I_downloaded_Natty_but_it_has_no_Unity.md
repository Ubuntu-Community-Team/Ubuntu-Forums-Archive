---
title: "I downloaded Natty but it has no Unity?"
date: 2010-12-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2010-12-03
Hi, I just downloaded the following iso and installed it in VBOX. How I can enable Unity to see how it looks like?
[http://cdimage.ubuntu.com/releases/natty/alpha-1/natty-desktop-amd64.iso](http://cdimage.ubuntu.com/releases/natty/alpha-1/natty-desktop-amd64.iso)

Thanks

---

### Post by wojox on 2010-12-03
You should have two sessions in GDM to choose from.

---

### Post by Gremlinzzz on 2010-12-03
This says u should have it
[http://www.webupd8.org/2010/11/ubuntu-1104-natty-narwhal-update.html](http://www.webupd8.org/2010/11/ubuntu-1104-natty-narwhal-update.html)
Unity (which now shows up as a plugin in CompizConfig Settings Manager)

---

### Post by 3Miro on 2010-12-03
To use Unity, you need to enable hardware acceleration, which doesn't work very well in Virtual Box (if at all).

I intend to use that at home on a multi-boot machine. It will be standalone and hopefully work.

---

### Post by Oxwivi on 2010-12-03
> **3Miro said:**
> To use Unity, you need to enable hardware acceleration, which doesn't work very well in Virtual Box (if at all).

I intend to use that at home on a multi-boot machine. It will be standalone and hopefully work.
[Jono Bacon posted how to install it on an USB stick]("http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/"), which will be safer, IMO.

---

### Post by 3Miro on 2010-12-03
> **Oxwivi said:**
> [Jono Bacon posted how to install it on an USB stick]("http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/"), which will be safer, IMO.

I will not let it overwrite my MBR (I will use Grub from my Gentoo install) and I will not overwrite an existing working installation. It should be safe enough. The USB is the safest way.

---

### Post by nilarimogard on 2010-12-03
> **Gremlinzzz said:**
> This says u should have it
[http://www.webupd8.org/2010/11/ubuntu-1104-natty-narwhal-update.html](http://www.webupd8.org/2010/11/ubuntu-1104-natty-narwhal-update.html)
Unity (which now shows up as a plugin in CompizConfig Settings Manager)

Yes, but Unity is only enabled if your hardware supports it. And VirtualBox doesn't... See here: [http://www.webupd8.org/2010/12/ubuntu-1104-natty-narwhal-alpha-1.html]("http://www.webupd8.org/2010/12/ubuntu-1104-natty-narwhal-alpha-1.html")

---

