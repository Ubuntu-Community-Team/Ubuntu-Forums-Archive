---
title: "Radeon 9200 problems with fresh 5.10 install"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by alexweber15 on 2005-10-18
hi all i just installed breezy badger a few mins ago and when it was all done and booted up the screen was kinda weird and garbled.. i could see and move the mouse but everything else was just messed up and undecipherable... i think the same screen image was being tiled over a couple times but the mouse could move over everything... either way **i cant see or do anything!** :(

here are my relevant specs:
Asus K8V-X mobo
Athlon64 2800+
1.5GB PC2700
ATI Radeon 9200SE 128mb

I had a similar problem with Mandriva LE 2005 a couple months ago and i expected ubuntu to support Radeons out of the box...

What can I do about this?  Keep in mind I am pretty much a linux n00b... i reckon i gotta install the right drivers and xfree or something of that sort but i'm not sure at all.... any help is greatly appreciated!

thanks! :)

---

### Post by mlomker on 2005-10-18
You can press Ctrl-Alt-F2 to login at another terminal and run **sudo dpkg-reconfigure xserver-xorg**.  Select the ati or vesa driver and see if that takes care of it for now.

---

### Post by alexweber15 on 2005-10-18
thanks for the reply!  i'll give it a try and see if that helps... :)

---

