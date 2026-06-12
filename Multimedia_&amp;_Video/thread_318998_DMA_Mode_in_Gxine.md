---
title: "DMA Mode in Gxine"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by faithsnathan on 2006-12-14
I've been trying to play DVDs in Ubuntu for the longest time.  I'm looking at Gxine right now.  I went through the set-up wizard and it showed everything was green (good to go) except for one thing, and that was the "Check for DMA mode on DVD drive."  I clicked on "Details" beside it and it said the following:

```
FAILED - DMA not turned on for /dev/dvd.
If you are using the ide-cd module ensure
that you have the following entry in /etc/modules.conf:
options ide-cd dma=1
 Reload ide-cd module.
otherwise run hdparm -d 1 on your dvd-device.
```

Does anyone speak computer?  I think this might be what's holding me up w/ playing movies on my computer.

A little extra info:
1.  The movie won't play in Gxine (I tried it, even though that error was on the wizard).
2.  The DVDs won't play in any other program I've been able to find.
3.  Yes, I have it in the right drive.
4.  If it's any consolation, I can't get it to mount that volume by right clicking on it and selecting "Mount Volume."
5.  Sys info:  Ubuntu Dapper, 750Mhz AMD, 30 GB HD, 256MB RAM, whatever.

I'd sure appreciate any help anyone could give me on this.  Thank you for reading all this!

---

### Post by Shatrat on 2006-12-14
You definitely want DMA enabled on your DVD drive if you want to do anything useful with it.
You might want to check this out.
[http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by faithsnathan on 2006-12-16
[SIZE=4]> **Shatrat said:**
> You definitely want DMA enabled on your DVD drive if you want to do anything useful with it.
You might want to check this out.
[http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

[/SIZE]  [FONT=Verdana][SIZE=4]Well, that seemed to be a good idea.  I went in to enable the DMA (whatever that is), but it was already enabled.  I still cannot watch DVDs, though.  :-k

If it matters to anyone, this is the ONLY reason I'm still dual booting with Windows XP.  As soon as I can resolve this, I'm going to use Gparted to write over XP and (hopefully) expand Ubuntu to take over the hard drive.  :D[/SIZE][/FONT][SIZE=4]

[/SIZE][FONT=Verdana][SIZE=4]Thank you to anyone for reading this post.

Nathan[/SIZE][/FONT][SIZE=4]
[/SIZE]

---

### Post by Jetcjcski on 2006-12-16
I'm not even close to a good Ubuntu user, but did you look in the modules.conf file for "options ide-cd dma=1"?

---

### Post by faithsnathan on 2006-12-16
> **Jetcjcski said:**
> I'm not even close to a good Ubuntu user, but did you look in the modules.conf file for "options ide-cd dma=1"?

[FONT=Courier New][SIZE=4]I think I got "options ide-cd dma=1" added in to that file, but to no avail.  I'm about to give up.  Maybe I'll just have to wait a year or two until I can get a new computer to really use Linux.  :mad:
[/SIZE][/FONT]

---

### Post by faithsnathan on 2007-03-13
Well, I finally go this problem fixed:  I bought a new computer, this time a laptop.  The DVD player works in it, after some minor tweaking.

---

