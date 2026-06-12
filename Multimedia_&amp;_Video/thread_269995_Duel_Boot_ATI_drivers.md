---
title: "Duel Boot ATI drivers"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by TheFlamingBush on 2006-10-02
Im about to update my drivers, as im running on a default ATI driver at the moment in Linux and it seems that this has been the problem with streams and Low frame rate when implementing programs that demand decent graphic capability.

I have a Toshiba L20-300, running a ATI Radeon xpress 200M.

There have been a number of discussions on this board, and i have read a lot of them. But i have a specific question, and for those that arent newbs please dont have a heart attack with the laughter if this appears to be a silly question.

I am running XP on a primary partition (NFTS), and duel boot my laptop with Ubuntu, on a tertiary Partition (EX?), with a shared secondary partition formatted in fat 32 that both write to.

I wanted to update the drivers, because my Linux tends to run a bit slow. I would like to maintain the duel boot situation for now, as i use some great programs in both, and each has its strengths and weeknesses. I am still checking them both out if the truth be known and comparing the two distro's.....although i have to say ive been massively impressed with Ubuntu and seem to be using it most of the time these days.

When i change my driver in Linux, and update it to the most up to date ATI driver, will it effect my XP when i boot back into XP, or does the driver depend upon the distro?, swapping at boot!. This does worry me, and im loathe to change drivers until im sure that it wont effect the XP boot.


If anyone has any advise for me along these lines please could you help....thankyou! :)

---

### Post by TheFlamingBush on 2006-10-02
anyone?

---

### Post by TheFlamingBush on 2006-10-03
bump

---

### Post by Aikon- on 2006-10-03
Drivers are installed on a per-OS basis. Furthermore, since Linux and Windows don't share the same code-base, installing a driver in Linux can't "install" something to the Windows OS. (If you have the NTFS partition mounted in READ/WRITE mode, its possible to update files, but again there's no overlap between Linux and Windows so there wouldn't be anything for you to over-write even if you somehow managed to tell apt-get to install the drivers to the NTFS partition).

Hope that clears things up for you!

-Aikon


p.s. [dual]("http://en.wiktionary.org/wiki/dual#Adjective") vs. [duel]("http://en.wiktionary.org/wiki/duel#Noun")

---

