---
title: "both cores at 100% CPU usage with 1080p mkv video"
date: 2009-03-07
forum: Multimedia Software
---

### Post by heiNey on 2009-03-07
another issue...

i have a Gigabyte MA78GM-US2H (780G chipset), 500W PSU, 4 GB RAM, AMD X2 5050e (2.6 ghz) and im trying to play HD content with hardy heron 32-bit

i have the whole thing set up...and it plays 720p fine (cpu usage is still in the 20% range, for each cores, according to conky)....but trying to play a 10 gig 1080p movie has 100% cpu usage (EACH core), and it looks like its dropping frames and stuttering still

im playing the videos through XBMC's internal player, since that's the only player that is working nicely with this hardware.  i normally use mplayer, but it wont even give me any good video with this set up.

i have read on other forums with people who have much slower cpu's than mine with the same motherboard chipset and they can play 1080p mkv files fine.  so im thinking that the GPU is not doing any of the work?  im not even sure how to start troubleshooting this.  any help would be appreciated...thanks

---

### Post by binbash on 2009-03-07
Download svn version of mplayer and x264 decoder, and try with it.You may also want to use COREAVC with mplayer ( [http://www.ubuntu-inside.me/2009/02/howto-mplayer-with-coreavc-better-hd.html](http://www.ubuntu-inside.me/2009/02/howto-mplayer-with-coreavc-better-hd.html) )

---

### Post by heiNey on 2009-03-13
didnt work...went ahead and put windows 7 beta on and it works fine with windows media player classic - home cinema.  oh well.

---

