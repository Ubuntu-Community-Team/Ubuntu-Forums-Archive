---
title: "Some information regarding RPC2 drives"
date: 2011-07-30
forum: Multimedia Software
---

### Post by arunb on 2011-07-30
Hi,

OS: Ubuntu 10.04 
Drive: Matashita Internal DVD Reader/Writer (RPC Phase 2)
Computer: Acer Aspire 5745
Region: 2

Output of regionset
> regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 3
drive plays discs from region(s): 2, mask=0xFD


---------------------------------------
DVD Disk Region: 1
---------------------------------------

After extensive research I have found these....

VLC does not play DVDs of all regions, only region 2 is played. 

This is because the DVD drive does a region match in the firmware and allows only matching regions to be played, so media players are helpless here.

I have tried other players like Kaffeine, xine etc. these have not fared any better than VLC.

I installed DVD43 on Windows XP (running through virtual box) and even this failed.

I installed k9copy, DVDrip etc. k9copy actually starts to copy file but fails due to '*Input/Output splicing error*' 

I tried to manually copy files from the DVD and this also failed.

I used another DVD (region 1) and the above problems/observations were repeated.

My inference is that RPC Phase 2 drives match DVD regions of the disk and the region set in the drive (on the firmware), a mismatched region will cause the DVD player to generate an error, so media players cannot retrieve data.

The same technique works when files are  copied, mismatched regions generate an error, so disk copying fails.

RPC phase 2 drives are very different from Phase 1 drives, Phase 1 drives read disks regardless of region encoding. Instead region control depends on media players. Players like VLC ignored region control standards and so were able to play DVDs of all regions.

Finally my conclusion....

I believe as of today there is no software workaround for playing DVDs of all regions on a RPC Phase 2 drive.

The only option is to 'flash' the drive, this disables the region encoding algorithm in the firmware. But remember 'flashing' can also render the drive useless, so be prepared to buy a new disk in case of failure.

I hope this was useful....

Thanks
ab

---

### Post by BicyclerBoy on 2011-07-30
Not true.
But you sometimes have to use the latest build of Handbrake..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
libdvdcss libdvdnav libdvdread

Some DVD drives seem to be extra painful to use..

---

### Post by mc4man on 2011-07-30
It has nothing to do with RPC2, everything to do with - 
> Drive:[COLOR="Red"] Matashita[/COLOR] Internal DVD Reader/Writer

Most Matashita laptop drives enforce region coding in the drive and will not allow access to encrypted sectors if there is a region mismatch

There is very little to be done about that, a Matashita model used on Mac's had a firmware flash
There has developed a means to do a firmware dump, edit, and flash back to fix some additional Matashita models - you'd need to research that.

Otherwise on most other drives region coding is not enforced, (encrypted sectors can be accessed & brute forced) and NO open source, unlicensed player will do so either.
The only difference is libdvdcss2 will use a different decrypting routine when there is a mismatch (brute force

Edit: - read post 3 in link, describes a bit better the difference between RPC1,2 and mentions matshita
[http://club.myce.com/f34/rpc1-rpc2-150215/](http://club.myce.com/f34/rpc1-rpc2-150215/)
(note that Vlad is one of the best at producing RPC1 firmware flash's

---

### Post by arunb on 2011-07-30
> But you sometimes have to use the latest build of Handbrake..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
libdvdcss libdvdnav libdvdread

Some DVD drives seem to be extra painful to use..

I don't think AnyDVD will work on a RPC Phase 2 drive, as regions are matched in the drives firmware and there is nothing a high level software can do about this.

I think its for the same reason why DVD43 fails in Windows XP

---

### Post by arunb on 2011-07-30
> But you sometimes have to use the latest build of Handbrake..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
libdvdcss libdvdnav libdvdread

Some DVD drives seem to be extra painful to use..

I don't think AnyDVD will work on a RPC Phase 2 drive, as regions are matched in the drives firmware and there is nothing a high level software can do about this.

I think its for the same reason why DVD43 fails in Windows XP.

The same problem occurs with ripping softwares, programs like AcidRip, dvdrip etc. will fail if the firmware refuses to read  data from the disk.

---

### Post by mc4man on 2011-07-30
> **arunb said:**
> I don't think AnyDVD will work on a RPC Phase 2 drive, as regions are matched in the drives firmware and there is nothing a high level software can do about this.
.
Again you're being much too general, only some RPC Phase 2 drives are region locked, matshita being the most notable, some RICOH/PHILIPS drives.
I have plenty of other region dvd's, and all my drives are "RPC Phase: II"
The only one that cannot be used for ripping or playing other region disks is the matshita be it an opensource ripper, player or anydvd in windows
For that and because i think the drives are pretty crappy otherwise I'll never purchase another laptop with one. (even as common as they are..

---

### Post by arunb on 2011-07-31
> Again you're being much too general, only some RPC Phase 2 drives are region locked, matshita being the most notable, some RICOH/PHILIPS drives.

You are probably right there. Since I could not experiment with other types of RPC Phase 2 drives I had to base my opinion on the one that I have now.

I could flash the drive, but maybe I can replace it with another drive.

---

### Post by arunb on 2011-07-31
> Again you're being much too general, only some RPC Phase 2 drives are region locked, matshita being the most notable, some RICOH/PHILIPS drives.

You are probably right there. Since I could not experiment with other types of RPC Phase 2 drives I had to base my opinion on the one that I have now.

I could flash the drive, but maybe I can replace it with another drive.

---

### Post by mc4man on 2011-07-31
> I could flash the drive, but maybe I can replace it with another drive
I may be getting another laptop, if so then I'm going to see  if I can 'fix' the matshita drive on this one
If it bricks it no big loss though the method, if it can be used on this one, is a bit safer than flashing with an outside created firmware, ie. it dumps the existing firmware, edits and uses that to flash back.

Edit:
The only issue when there is a region mismatch and the keys are brute forced is some small sample titlesets may fail in aquiring keys (like a small extra, ect.

There is a workaround there if one has access to a region matched drive.
You use that drive to get the keys and then transfer the disks folder in ~/.dvdcss to other machine. That set of keys will be used (libdvdcss2 always looks to ~/.dvdcss first

---

