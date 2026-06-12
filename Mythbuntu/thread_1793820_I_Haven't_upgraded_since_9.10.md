---
title: "I Haven't upgraded since 9.10"
date: 2011-06-30
forum: Mythbuntu
---

### Post by jonnybignote on 2011-06-30
Anyone care to weigh in?
 
I haven't looked in in a while.  My 9.10 64bit has had multiple hacks, scripts and kludgy fixes to get it to do what I want.  It fully works with STR S3 and is on and off all day with more or less 99% success.
 
You know that niggling feeling though?  Wondering what great new stuff and performance/cool features might be in the newer versions...
 
I just wondered if anyone had had any great success/failure.  My hardware is fairly low to average - 2 hdtv-wonder cards, 2GB ram and a 250GB HD together with a 4600 Athlon and an MSI mobo I can't remember.
 
I really don't want to get into a situation of finding half my hardware is obselete or, as I've heard rumblings of, standby won't work on it.
 
Any ideas gratefully recieved
 
Thanks

---

### Post by ninjaaron on 2011-06-30
I would at least upgrade to the latest LTS, 10.04, just so you can keep getting software and security updates.  You can check the compatibility with the hardware lists.  Usually if something doesn't work out of the box, it can be tweaked to work.

I really like the new cloud services.  Backing up important files is completely worry-free now, and syncing programs across different machines is nice too.  That's the main thing I would say you are missing.  The new social networking integration are kinda neat, but not really a big deal.  Unity isn't really a big deal either way for me.  I think it will be better than gnome eventually, but it still needs work.

---

### Post by ian dobson on 2011-06-30
Hi,

I can't give you any tips about your specific hardware apart maybe try booting from a LiveCD and see how it goes.

If you box is running and doing exactly what you want, why upgrade? Rule number 1,2&3 of computing is "If it isn't broken, don't fix it" and rule number 4 is "never touch a running system".

Regards
Ian Dobson

---

### Post by ktmom on 2011-06-30
I was in the same boat.  I wanted to get the security updates, but I had my system stable and reliable on 9.10.  I did just upgrade to 10.04LTS and it took me several hours to get back to where I was, but I'm glad now that I did the work.

I now have mythtv .24-fixes (using the ppa) and regular security updates.  I am using a 2250 card and the driver (digital side) is now in the kernel so no worries there. I used this as an opportunity to document the specific mods that I made to customize my system and create a script to back-up those files.  I am anticipating not having to touch my system for another year and a half but I'll still be able to get the security updates and stay as current with the mythtv releases as I choose.

The picture quality appears to me (and my daughter) to have improved.  I like the fact that under .24 it's straightforward to code theme customizations (it's xml based and straightforward) since my daughter can't read any of the prepackaged themes and my older eyes appreciate the changes I've made to the theme. It's nice to be able to download video metadata in a straightforward manner again.  And from my point of view, it has to be updated at some point, I am of the opinion that if you let to much time go by, it becomes harder to get your head in the game and get the subtle things back to where you want them.

---

### Post by klc5555 on 2011-06-30
I completely agree with Ian. The system works nearly perfectly -- don't upgrade unless you know you need some sort of support or new feature that the later version supplies.

If, however, you like to use the internal mythdvd ripper with mtd, or if you rely on nuvexport with the higher-quality "transcode" option instead of ffmpeg or mencoder, or if you've ever used myth.rebuilddatabase.pl to rebuild portions of your recordings database after a problem, or have occasionally relied on myth.find_orphans.pl to fix a database issue, then you will want to think carefully about your proposed upgrade from 0.22. Because those features/utilities (and possibly others that I don't actually use on a daily basis) are long gone in 0.24.

---

### Post by psusi on 2011-06-30
If it is connected to the Internet, then you need the security updates, which 9.10 is no longer getting.

---

### Post by itlarson on 2011-06-30
Why not buy a new hard drive and install on that.  If there are problems you can just plug the old drive back in.  To me there hasn't been a killer feature added to mthtv since vdpau in .22, which I think was in 9.10, but the upgrade is probably worth it for the security updates.  

Personaly I just moved my system to a 2tb [raid 1]("http://ubuntuforums.org/showthread.php?t=1791483").  I stuck with 10.04, since I have decided to run only LTS versions.

---

