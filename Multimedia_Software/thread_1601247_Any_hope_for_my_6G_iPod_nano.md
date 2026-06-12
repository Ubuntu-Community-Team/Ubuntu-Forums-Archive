---
title: "Any hope for my 6G iPod nano?"
date: 2010-10-20
forum: Multimedia Software
---

### Post by electromage on 2010-10-20
I like the form and UI of the new nano and decided to pick one up. I was hoping I could sync it with Rhythmbox since I've had luck with several iPods in the past.

I connected it and Rhythmbox sees it, and was able to initialise it, but it doesn't seem to save any changes to the library. When I connected to iTunes, it was also unable to read the format, so I re-initialised it using iTunes.

Now Rhythmbox can read it and write files to it, but they don't update in the iPod library, they just get dumped on the file system, it's treating it like any other MSC device.

I've searched Google several times, and this forum, and tried to find info through Gnome and Rhythmbox resources, but can't really find anything conclusive. Does anyone know what the status of development is on this issue? What is the difference with this new nano that breaks everything?

Before anyone asks, I've also tried Banshee and Amarok with similar results.

---

### Post by squaregoldfish on 2010-10-20
libgpod, which is the underlying library for iPod/iPhone support, doesn't yet support the Nano 6G. Apparently some reverse engineering of the new software needs to be done.

Steve.

---

### Post by BartmanMN on 2010-12-26
I too have a new Nano 6G touch that I need help getting working with Rhthymbox.  I will be watching this thread for updates.

---

### Post by Pablhomme on 2010-12-29
Hello,

I have a nano 6g also.  

I was able to make it work from Itunes (v10.1.1) running in a VirtualBox emulating Windows 7.

I tried using Wine but it was not stable.

I tried also on with RythmBox but I can only play files.  If I try to copy files to the nano the files are copied but not played by the nano.

I hope there will be a solution coming up from the libgpod group!

PA

---

### Post by BartmanMN on 2011-01-13
Bump to top.  Still looking for help with 6G Nano.

---

### Post by squaregoldfish on 2011-01-13
You'll be better off looking at libgpod for updates rather than here.

Steve.

---

### Post by Matt Brooks on 2011-06-02
> **squaregoldfish said:**
> You'll be better off looking at libgpod for updates rather than here.

Steve.

Any idea when this release will occur? Notice thar I'm reviving this six month old thread - I'm still waiting.

---

### Post by Chronon on 2011-06-02
This is the game you must play when you buy new Apple products.  They seem to purposely change the format of the database file periodically to break compatibility of 3rd party tools.  Because the format/protocol isn't known it takes reverse engineering to figure out the proper format.  It is generally difficult to predict how much effort it will take to perform this step.  

If you want to use Apple hardware with Ubuntu, I would advise getting a device that is known to work and avoid doing any firmware updates.  For now you will just have to deal with workarounds (like iTunes inside of a VirtualBox or dual-booting).

---

### Post by Jota37 on 2011-07-01
Yeah, I've just seen that same behavior today: Rhythmbox seems to add or delete something, but when you look in the iPod itself, the supposedly deleted song is still there and the supposedly added one is not.

Opening Nautilus and navigating to the iPod directories shows a new directory structure with band name, then album folder inside of that, and finally song.

Anyway, my badly designed nano 6G (who was the retard who came up with the idea for a hold button instead of a slide switch as in the 1G nano?) broke yesterday anyway. The hold button got stuck, and searching online shows that lots of people have problems with that. Now the thing won't turn on. Connecting to USB activates it, and it all works, so the dead button is the only issue. From reports of people disassembling the nano 6G, it seems like the button is held with double-sided tape or something like that if I understood correctly. Rant over. ;)

---

