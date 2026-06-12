---
title: "Cant read TOC on DVD"
date: 2011-08-12
forum: Multimedia Software
---

### Post by Bandit on 2011-08-12
*Ok first off, I back up my media and I am allowed to. So I am not pirating.* 


Bought new movie the other day and trying to back it up with DVD::RIP. I have used this program for years but today I ran into something new. When I go to read the TOC from the disc I get an error:

```
Fri Aug 12 07:58:49 2011 Job 'Read TOC (lsdvd|tcprobe)' exited with error: Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.
```

Which is strange because I have every dependency installed and satisfied all the dvdrip requirements. Like Prague, its in there..
So I fought back and forth with it for about an hour and decided the check the dvd. The DVDs VIDEO_TS folder is like a whooping 24GB and I cant view the individual VOB files, they look and act scrambled just like if I did not have libdvdcss installed. But here is the kicker.. I can watch the DVD just fine if I go to watch it in my PC or in my TV DVD player. As clear as day..

Anyone else run into this or know a work around? :(

Thanks..

---

### Post by coffeecat on 2011-08-12
The phoney 24GB in the VIDEO_TS folder suggests that the DVD you are trying to rip is also protected with ARccOS.

[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

This confuses (most/some) ripper software but not (most) DVD players. Out of interest, which software were you using in your PC to watch it? Good to know it could cope with this.

The article suggests that ddrescue in Linux could be used to get round this. I've not tried it myself.

**EDIT**: re-reading that wikipedia article again, I was amused to see that ARccOS was developed by Sony but it confuses some Sony DVD payers. Nice one, Sony! :rolleyes:

---

### Post by Bandit on 2011-08-12
Both Totem w/Xine and VLC work great. I did notice MPlayer however will not play them.

---

### Post by Bandit on 2011-08-13
ddrescue was able to pull an image of the disc. But took over 3 hours and is still encrypted..

```
ddrescue -n /dev/dvd movie.iso rescued.log
ddrescue -r 1 /dev/dvd movie.iso rescued.log
```

---

### Post by coffeecat on 2011-08-13
> **Bandit said:**
> ddrescue was able to pull an image of the disc. But took over 3 hours and is still encrypted..

My guess is that you'll still have to "rip" the iso you got from ddrescue with an app using libdvdcss2. The wikipedia article says that ARccOS is a layer on top of CSS. You might want to google the title of the DVD you're working on to see what others make of it. ArccOS seems most likely but there may be other protection methods out there.

---

