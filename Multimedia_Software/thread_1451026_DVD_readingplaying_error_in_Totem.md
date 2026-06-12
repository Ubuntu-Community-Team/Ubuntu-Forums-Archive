---
title: "DVD reading/playing error in Totem"
date: 2010-04-09
forum: Multimedia Software
---

### Post by Peregrina on 2010-04-09
I'm running Ubuntu 9.10 on a Gateway LT netbook, it's about 4 months old.  I'm using an LG external CD/DVD drive which is also new and I have no trouble with audio or data discs.

When I try to play DVDs in Totem I get this error message: Cannot read from resource.
OR it does nothing (only the "waiting" icon forever)
OR Totem just closes down on its own.

I have scoured the forum pages, I've gone through almost everything in these two threads: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  and  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Maybe two days ago I had installed libdvdread4 and whatever else needed to play commercial DVDs and it worked when I tested it.  Today, no deal.  For everything I've seen to download or update I seem to already have the latest versions.  I don't have a DVD region set (I assumed it was best NOT to set the region if I can avoid it...but is that maybe the problem?).  I've tried VLC and it just doesn't do anything.  I downloaded the Totem xine back-end from the "Software Centre" and still the same problems.

It's all the more frustrating because I thought it was working before.  I don't understand what could have changed.
Can anyone think of anything else I could try?

Thanks a ton!

---

### Post by WinterRain on 2010-04-09
Did you install **libdvdcss2**?

---

### Post by Peregrina on 2010-04-09
I tried what you said:
> $ sudo apt-get install libdvdcss2This is what it told me:
> Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by PRC09 on 2010-04-09
I also always add the Medibuntu repos as well.Then install libdvdcss2,and then add the w32 codecs, reboot and everything should work.... 



[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by wilee-nilee on 2010-04-09
Besides the additional programs you might consider installing vlc or smplayer they will play things that sometimes just wont go on totem.

---

### Post by Peregrina on 2010-04-09
> **PRC09 said:**
> I also always add the Medibuntu repos as well.Then install libdvdcss2,and then add the w32 codecs, reboot and everything should work.... 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Oh man, bingo!  I guess the libdvdcss2 was there before and then wasn't?  Anyway everything works now.  I hope it stays that way!

Thank you SO so much!

---

