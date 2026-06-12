---
title: "[SOLVED] Broken MP3 player"
date: 2008-07-10
forum: Multimedia Software
---

### Post by absolutezero1287 on 2008-07-10
So, here's the thing. I bought an mp3 player about a year ago. It's screen shattered a few months after I purchased it. However, I didn't sit on it, I didn't drop it, nor did I leave it in the sun. I didn't abuse the mp3 player (Creative Zen Vision M) in any way. So naturally, I demanded a refund.

I called up Creative and explained the issue. I even sent them a link to a website where over 30 people had had the same problem. The offered to replace the screen at a "modest" $70. Naturally, I was pissed because it was almost $300. I wasn't going to pay that so I just stuffed it somewhere in my closet.


I found my forgotten media player while rummaging through my closet and I had a great idea. Why not put Ubuntu on it? It may have a broken screen but it can be connected to a TV It can be plugged into a USB port...so why not?

I plan to use debootstrap to make a minimal install of Ubuntu on it. I'll get rid of all modules relating to internet use since it doesn't support Wi-Fi or anything like that. This custom build will have one purpose, to play media, that's it. And if that idea fails then I'll turn it into an external hard drive. It holds like 60 GB.

Now this is all great except for the fact that Ubuntu isn't detecting it. I plug it into the USB port and unlike my external hard drive, the mp3 player doesn't show up.

---

### Post by absolutezero1287 on 2008-07-10
Update:
Got Gnomad due to the fact that the Zen Vision M uses MTP. This could complicate the process..

---

### Post by absolutezero1287 on 2008-07-11
Update: booted into my XP partition and used the software that came with the mp3 player (Zen Removable Disk Manager) to create a partition. 
Booted into Ubuntu and used Gparted to format partition to ext3 and add boot flag to partition. I then used debootstrap and made a minimal Ubuntu build. Installed grub, x11 and related packages, fluxbox, and English language support.

Everything was done perfectly. A normal external hard drive would have booted Ubuntu by now. But when I reset the player it doesn't boot Ubuntu. 

Any ideas? If anyone needs any extra info just ask.

---

### Post by absolutezero1287 on 2008-07-12
Update: Discovered the architecture and OS used by the player. and I think I'm pretty much going to keep the player as an external hard drive. I'll mark this solved since putting Linux on it would require making a distro made for the Zen.

Wikipedia: Creative Zen Vision M
look it up.

---

