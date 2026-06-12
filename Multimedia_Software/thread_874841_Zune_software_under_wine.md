---
title: "Zune software under wine"
date: 2008-07-30
forum: Multimedia Software
---

### Post by yon2501 on 2008-07-30
Anyone know if the zune software will work under wine, or if amarok can handle it?

---

### Post by Spydr4590 on 2008-07-30
Looks like the answer is no. Also this is the wrong forum. :)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741)

---

### Post by eschatologicalhumor on 2008-10-10
Essentially, the Zune is a bastardized Toshiba Gigabeat S-Series I believe with MS's proprietary Midas touch. The guys over at Rockbox are working slowly on using the Gigabeat-S firmware as an example for breaking the encryption with the help of the community so that we can bypass the Zune software completely and use the Zune the same as an iPod, whereas we just drag and drop music onto the player like a generic usb device and sync it with any media software that supports it such as Amarok.

From what I've read everywhere on the internet forums, the Zune software only works on Windows itself right now, or in a guest OS through VMware or such programs. The reason for this is twofold: firmware encryption on the Zune that no one can break (as of yet) and the fact that as far as I know, .NET3.0 or .NET3.5 cannot run in WINE (as of yet). But once we can run the .NET3.0/5 software in WINE, someone will find a way to run the Zune software and we'll be all set.


This is bad news, because I am a Zune owner myself, and would love to be able to knock the Zune off of my ever-shrinking list of reasons to keep Windows. Now WINE can run PhotoshopCS2 and maybe 3, so that's not an issue. More and more games are being supported, and that's a good thing, but not good enough for me. The 2 games I play won't run as well as I'd like them to in WINE, so that's a heartbreak for me. I boot into Windows maybe once a month to play games, and every time I look at what's installed otherwise, I think to myself, "I can just do that in Ubuntu, I'll wait."

I CAN attest however, that the Zune software runs absolutely flawlessly in VMware Server 2.0 with a WindowsXP guest OS. Try that. You may find that solution sufficient. I sure do. :)

---

