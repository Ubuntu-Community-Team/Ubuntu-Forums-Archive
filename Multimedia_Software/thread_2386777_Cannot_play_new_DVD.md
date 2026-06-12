---
title: "Cannot play new DVD"
date: 2018-03-10
forum: Multimedia Software
---

### Post by Autodave on 2018-03-10
DVD works fine in a regular player, but I cannot get it to work at all in any of my 3 Xubuntu PCs. Other DVDs play fine.  I have reinstalled all of the normal things, but still no luck. Any ideas?

---

### Post by TheFu on 2018-03-10
Any ideas?  Well ... I've had a few DVDs that refused to play in computers, but worked fine in $35 old-school DVD players connected directly to TVs.  Research on those specific discs showed they were using "enhanced" DRM protections. Basically, they have disc defects designed specifically to fail in computer DVD drives, but still work in legacy home-theatre DVD and blueray players.  A common defect is to have hundreds of titles, some pointing to non-existent chapters. Just figuring out the main  title is non-trivial because they will put 20+ versions of the main title with about the same total runtime, but with all the chapters in different order.

I use **vobcopy -I** to learn about the DVD and titles.

Commercial DVD rippers might work ([https://www.makemkv.com/](https://www.makemkv.com/)) or there is the analog whole (which we cannot discuss here).

---

### Post by mc4man on 2018-03-10
You may want to discern the actual real titleset number of the main movie. Usually you can do that on a hardware dvd player.
Then maybe try vlc > Media > Open Disc > DvD > check no disc menus box  > Starting position >  use actual tile number >  chapter 0 sould be ok or set to 1

---

### Post by tnthomas on 2018-03-11
[VLC]("https://www.videolan.org/index.html") player seems to pull all the necessary packages to play play newer DVDs without issue.

---

### Post by Autodave on 2018-03-11
VLC was my go-to player. Nothing.

---

