---
title: "can't mount commercial dvd's"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by tedrampart on 2006-09-16
I just converted my work computer (which I share with 12 other folks on shift work) to dapper from windows, people love it, but there's a problem I can't fix.

I've searched high and low, but I can't mount commercial DVD's.  when I insert the dvd it flashes the light twice, then nothing, no icon on the desktop, and no programs recognize it.

I read through this thread [http://ubuntuforums.org/showthread.php?t=205467&highlight=dvd+mount](http://ubuntuforums.org/showthread.php?t=205467&highlight=dvd+mount)
but found no answer.  everythings installed as far as modules and such. 

I can mount burnt dvd's no problem, which is sort of boggling.  anyone have any help?

here's my /ect/fstab :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

if thats of any help...

its frustrating to come in and have 12 people asking why their movies aren't worknig on a system thats "better" than windows.. 

please help
thanks

---

### Post by tedrampart on 2006-09-16
oh yea

forgot to add that I installed the libdvdcss2, also installed and used automatrix, and all that jazz, but no workie.. all the restricted modules are installed.. 

why won't this work?  I have the same install on my laptop, and dvd's play no problem.. I don't get this...

---

### Post by Imsati on 2006-09-16
Ok, so I'm still very new to Linux/Ubuntu, so I'm not sure on the programming/packaging end of it, but...

You mentioned it's a work computer, yes? Perhaps something with the actual DVD drive itself? Maybe one of the other 11 folks might have done something to it? Easiest way I can think of to troubleshoot is to remove the drive and install another one that you know works 100%.

Just a thought.

---

### Post by tedrampart on 2006-09-16
well its only just hit the desk.. the computer was donated with windows on it and everything worked, but I wiped it clean to do a fresh install.. maybe its an older dvd-rom that doesn't work well with the driver.  I'll probably take the dvd burner out of our old system and try that the drive was put in alot sooner..

---

### Post by Imsati on 2006-09-16
Do you have a DVD rom and CD rom? How did you use the Live CD? Was it in the DVD Rom drive or the CD Drive? If the DVD drive, then obviously it works because you installed the system. However, if you used the CD drive for the Live CD, and DID NOT use the DVD drive while Windows was still active (to see if it worked there), I would replace the DVD drive first, as mentioned. 

No sense spending 20 minutes looking through troubleshooting guides for software and have it be a fualty drive when you can spend 5 minutes and rule out/accept a hardware issue.

Heading to bed now. Post up with the results if you do it tonight.

EDIT: And I just saw that you can read burnt DVD's. Could you at first, and now you can't? Or can you still and just not 'real' DVD's?

---

### Post by tedrampart on 2006-09-17
I could always read dvd's.. just not commercial ones.  there's only one drive in there, and its a dvd-rom (I can't remember what exact manufacturer/model but I assume thats not a big deal).  I've looked high and low on the forum here and even on google..

I thought the libdvdcss2 would fix it but that didn't help.  followd the instructions and all that.  still didn't work, then decided to try the automatrix, that didn't work either.  (rebooted between attempts).  all the  stuff is on there that it would need to read them.  

its strange because when I put a burnt dvd (data, video...) it mounts right away, loads up the screen, or the movie player (depending on which type of disc it is), and it runs fine, no glitches, or errors, or lag at all.  put a commercial dvd video in it, and nothing.  doesn't see the disc at all.

like I said earlier, its not a faulty drive because it had windows on it before switching to dapper, and it worked fine.

now I just don't know.

---

### Post by Imsati on 2006-09-17
only other thing i can think of is the Region setting. 

Did you use this page? It was a gold mine of information for me.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

