---
title: "Creative Soundblaster X-Fi Platinum"
date: 2012-07-18
forum: Multimedia Software
---

### Post by arigram on 2012-07-18
I am running Kubuntu 12.04 and decided to dust off my old Soundblaster X-Fi Platinum card to see if after all these years I had it forgotten in a box, it was destined for a better fate.
It is recognised and it works well, but for one thing:

- In my 5.1 sound set up, I can't get the Center channel with the Subwoofer to work. All other four speakers work fine.

I dual boot with Windows 7 and with the Creative drivers, all channels work fine in the 5.1 set up, so I gather its not a hardware problem but it lies in software.
I've looked around the net to no avail.

Any ideas?

---

### Post by arigram on 2012-07-23
Nothing eh?
I've noticed that I also get crackling and sound distortion, so I guess the driver will never be up to scratch and so I will just return the card to its slumber.

---

### Post by obedlink on 2012-08-31
I have the same problem, no audio in center speaker and subwoofer.

please report this problem to kubuntu

---

### Post by obedlink on 2012-09-03
> **arigram said:**
> Nothing eh?
I've noticed that I also get crackling and sound distortion, so I guess the driver will never be up to scratch and so I will just return the card to its slumber.

I found the solution, in the console type:
[COLOR="Red"]alsamixer[/COLOR] and with the arrow keys, Step onto [COLOR="red"]Center / L[/COLOR] and press [COLOR="red"]m[/COLOR], what happens is that the subwoofer and center speaker are muted.

Center/Subwoofer Muted
[IMG]http://img834.imageshack.us/img834/3222/subwooferandcenteroff.jpg[/IMG]

Center/Subwoofer On
[IMG]http://img29.imageshack.us/img29/6632/subwooferandcenteron.jpg[/IMG]

---

