---
title: "Can't get wireless drivers working; in 2 threads nobody could help"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by thewasteland on 2011-01-12
I've been posting this in the Beginner Talk section as I only installed Maverick Meerkat (10.10) on Sunday for the first time, but nobody can help there so I thought I'd come here.

Here are my two previous threads:
1) [http://ubuntuforums.org/showthread.php?t=1664054](http://ubuntuforums.org/showthread.php?t=1664054)
2) [http://ubuntuforums.org/showthread.php?p=10345734#post10345734](http://ubuntuforums.org/showthread.php?p=10345734#post10345734)

To summarise: My wireless card has no drivers and I don't know how to install them. I've phoned the laptop company and they can't help me, they did however give me the link to the Windows drivers without even knowing what the wireless card is. I downloaded the Windows drivers but for every one of them, ndiswrapper says either that there's no hardware found or that it's an invalid driver. I even tried doing the AutoRun through Wine in a moment of desperation, obviously failing.

If you've looked at my other threads, you'll know that the complete lack of drivers has made my card basically invisible to all Terminal commands, so I don't know which wireless card it is.

Can anyone please help me? I desperately need wireless.

---

### Post by chili555 on 2011-01-12
In neither of the threads you linked is there the slightest indication of anything that remotely resembles a wireless card. They are either PCI or miniPCI, that is, built in to the chassis of the laptop; or USB and then, with only a very few exceptions, you'd see it sticking out of the laptop; or PCMCIA and, likewise, you'd see it sticking out of the slot on the side of the laptop.

I suspect that either the laptop didn't come with a wireless card or it has been removed or it's electrically defective and won't report its details to *lspci*.

I don't know how to locate and install drivers for what we can't show even exists.

---

