---
title: "ErrNo 5 Input/Output Error"
date: 2009-01-05
forum: Mythbuntu
---

### Post by gareththered on 2009-01-05
Hi,

I'm getting ErrNo 5 Input/Output Error when attempting to install Mythbuntu 8.10. So far, I've done the following:-
[LIST=1]I've downloaded the 64bit and 32bit versions of Mythbuntu onto two different machines.[*]I've burnt these onto CD-RW, CD-R and created a bootable USB drive.[*]I've installed onto my main machine and tested on an old laptop.
[/LIST]To me, that takes care of all possibilities.  But whatever I do, I get the same error message.  Originally, on the 64bit version on my desktop it was at about 27%.  Later, with the 32 bit version it was at 40% or so.  Same on the laptop.

My biggest concern is that the MD5 Checksums don't seem to match those on the website, but that could be my checking utility (Windows based).

Does anyone have any ideas?

Thanks in advance,

Gareth

---

### Post by UltramaticOrange on 2009-01-05
When you install, data gets copied from the disk into ram and then onto the hard drive. If any one of these three points is bad, you can get this error. I got this error when installing on a P4 system with bad RAM. 

Simple CD Tests:
- Download, burn, and install again to see if the problem persists. When you burn, burn at a slow speed like 4x. This will make a disk that's easier to read on older (or just plain crappy) CD/DVD drives.
- If the problem persists, swap CD/DVD drives (if you have a spare available) and install again.

Simple RAM test:
- If you have 2 (or more) sticks of RAM in your system, drop down to 1 stick and attempt to install again.
- If the problem persists, switch to the other stick of RAM. Note that in my case, both sticks of RAM were bad, so this method is not fool-proof.

Simple Hard Drive check:
- Scan the drive for errors. Most hard drive manufacturers have free diagnostic utilities available for download. Note that you can try to partition around any bad parts of a hard drive, but that's not for the faint of heart.

---

### Post by gareththered on 2009-01-06
Hi,

Thanks for your response, but by using a spare laptop I've effectively changed all the hardware.  I've downloaded onto a different machine which takes that out of the equation.  The only thing left that is common to all my efforts is the network.

Last night I installed from an older CD which went fine.  When I later attempted to upgrade 'over the wire' to 8.04 LTS (the plan was to upgrade to 8.10 afterwards) it kept failing with Hash Errors.  I changed the download server just in case, but that didn't help.

It seems to me that I have network issues!  I'm using one of those HSDPA 'mobile' dongles connected to a wireless hub and while it seems OK for small downloads, surfing and mail, it seems to suffer when attempting to download large files.  Strangely, it seems OK with Windows Update.  Seems like my Linux days are over until ADSL gets sorted properly in my area :-(

Thanks for your help.

---

### Post by Danbc on 2009-04-25
I have the same problem on a system I recently tried installing the RC on without problems. Tried swapping media drive, tried changing harddrive, burning, downloading, reburning.... Same problem :(

---

### Post by Danbc on 2009-04-29
Dunno if it helps here, but I initially burned a DVD media, then tried a CD media instead, problem fixed.... Worked with 9.04 RC on DVD media, so have no clue why the problem was there with the 9.04 final.

But install worked :)

---

### Post by Psyphre on 2009-04-30
me 2, same issue.

---

### Post by aaronrus on 2009-12-29
I have the same error.  I first tried to install the 32bit software CD that I used to install another computer with. Then I tried downloaded the 64bit version and burned another CD as slow as possible with an existing copy of unbuntu. Then I tried burning another CD of the 64bit version using windows and ISO recorder at 7x.

I did the md5sum checksum and it was good. I did the cd media check and the CD checks OK but I get the same input/output error telling me to try again. I also did the memory test and a badblock test every thing tests ok.

This also happened on a second computer I tried installing and after the 3 CD I made it installed. but when using the same CD on my computer  i get the same error as before.

on a second note i dont think any thing is wrong with my hardware due to successfully install fedora core 12 on the first try.

I would really like to switch to unbuntu 9.10 but cant get pasted this issue. please help

---

