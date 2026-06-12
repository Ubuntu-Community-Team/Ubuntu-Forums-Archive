---
title: "Do I need info that I don't need in Windows to set up wireless Internet?"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by stevegoat on 2006-07-14
I've managed to install Ubuntu, thankfully not managing to delete my Windows partition like I planned on.

The network stuff really, really confuses me. Right now I have all security on my router turned off, with broadcast on. I didn't have it like this before, but if I was to boot into Ubuntu now, would it list my network anywhere now that it's public? Then I could just go into my router's settings and add the password again I'd imagine.

Do I need any info from my ISP that I wouldn't need with Windows?

And before I even go about doing this, is there any way I can resize my Ubuntu partition, or delete the Windows one completely after getting Ubuntu working?

I'm on a Compaq Presario V5101US (I believe that's the model, it's a laptop and the sticker's ink that had that info right now is currently somewhere in my blood, great idea to put stickers right where your wrists go)

I'm sure this question is answered somewhere on here, and I'm sorry for asking, it's just I really have a hard time finding things online.

---

### Post by stevegoat on 2006-07-14
I went to Compaq's site and apparently they don't have anything Linux related. I found a program called NDISwrapper, but just from reading the first three lines of this thing I'm already 10x more confused than what I already was.

It's not that I don't know anything about computers, it's just Ubuntu seems a tiny bit different than Windows, and I have a really hard time finding stuff online.

---

### Post by awaldram on 2006-07-15
this should get you going in the right direction
[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

steps required

1 get driver working (native or ndiswrapper/ndsgtk)
2 confirm working (iwconfig)
3 configure network (system -> administration) if wep else network-manager fo wpa only else wifi-radar if you want it all.

so no different than windows just more choice.

---

