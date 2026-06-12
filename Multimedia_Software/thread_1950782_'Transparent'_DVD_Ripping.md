---
title: "'Transparent' DVD Ripping"
date: 2012-04-01
forum: Multimedia Software
---

### Post by pmatos on 2012-04-01
Hi,

I have, by now, a huge collection of DVDs. Too many that I can store. However, I don't to throw them away. I want to rip them in a way that I can stream it as if it was a normal dvd, including, subtitle choices, audios, menus, etc. Is this possible?

I know I can use dvd::rip and rip specific tracks but that means that I don't rip extras, or that I have to go through each dvds and specific choose what I rip, etc.
I would like a more or less automated process to create a streamable dvd image.

Any hints, or tips, or solutions close to what I need?

Cheers,

Paulo Matos

---

### Post by mc4man on 2012-04-01
Well then rip as DVD_VIDEO, then it will be the same as the disk

If there is no structure protection then vobcopy in mirror mode will rip the complete disk as is & can easily be set up as the default action on dvd insertion on 1 or multiple drives (how depends on what release of Ubuntu you are using
Basic command
```
vobcopy -v -m -F 16
```

If there is structure protection then k9copy can handle some though k9copy isn't well suited to auto-ripping

If k9 can't deal with then either a windows ripper that can run in wine or dvdisaster can be 'mis-used' to produce an encrypted/structured protected iso that will play back the same as the orig. disk
The only limitation on dvdisaster is the number of unreadable sectors - anything over 7000 or so will take too long to work thru

---

### Post by pmatos on 2012-04-01
mc4man, thanks for the excelent reply with all the references. I will be looking at those.

Cheers,

Paulo Matos

---

