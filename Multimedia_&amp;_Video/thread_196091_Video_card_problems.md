---
title: "Video card problems"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by Carandol on 2006-06-13
I've just installed Dapper on a hand-me-down HP Brio (800MHz, 512Mb RAM), which has a VT8605 ProSavage PM133 video card, according to the device manager. I've discovered it's one of those which shares memory with the motherboard -- it can either be set at 8Mb or 16Mb. At 8Mb it won't play DVDs -- totem-xine loads, starts the DVD, then quits again. At 16Mb, DVDs will play (a little more jerkily than I'd like) but there are other graphic problems -- pop-up menus that don't disappear, strange coloured patches on web pages, etc. And a lot of the screen savers make the computer lock up. 

I did think of putting in the old card from my last desktop, a Matrox Millenium which worked well with Ubuntu. But when I tried it, the X-Server wouldn't start, and I have no idea how to change the config from the command line. 

Ideally, I'd like to get the internal card working properly, so I can pass on the old PC to someone else. Any help would be appreciated!

---

### Post by ianmac on 2006-06-15
Are you sure the X-Server isn't starting?  I'm not positive, but I wonder if the X-server is running and displaying on your main display, and you just get the regular terminal on the old card...  try plugging your monitor into the other card (or plug a monitor into each card) and see...  this might provide further information to sort out the problem...

Ian

---

### Post by Carandol on 2006-06-16
Well, you're right, it *was* still running, in a crashed sort of way. Running > gdm told me it was still running. Switching to the right console showed a black screen with an underscore in the top corner. 

But I managed to get the other card working in the end, by booting into console mode, and running > sudo dpkg-reconfigure xserver-org. It detected the new card fine, and set it up. Then I rebooted, and everything now works perfectly. The "new" card works so smoothly playing DVDs, and the 3D models in the screensavers work so beautifully that I've decided to keep this card in and forget about trying to get the other one working properly!

---

