---
title: "unable to use 1 specific channel"
date: 2010-01-26
forum: Mythbuntu
---

### Post by 4dognight on 2010-01-26
I have a kworld 110 atsc tuner. It worked perfect while I was running 8.04.
When I upgraded to 9.10 I am unable to watch 1 specific channel, my local ABC channel. I get my local HD(QAM256) from my cox cable. 

I just finished installing a hdhomerun dual tuner box. I have the exact same results when trying to get that same channel on both hdhomerun tuners!

So, what would have changed in 9.10 that would make just this one channel unusable?

---

### Post by LowSky on 2010-01-26
I'm assuming you used splitter when yu added the newer tuners, Rescan your channels, and buy a better splitter, digital signals are not as strong as analog, so you may lose a channel or two due to lower signal stregth.

---

### Post by 4dognight on 2010-01-26
That wouldnt explain why my original kworld tuner fails. I only just added the hdhomerun. I didnt split the cable the kworld tuner was on either. I get a 100% signal strength with a 100 snq on the hdhomerun. 
I beleive this to be a problem mythtv not 'locking' onto the stream. At least thats my gues at the moment.

---

### Post by laceration on 2010-01-26
Cable Cos. will periodically change frequencies for channels to make room for new channels.  It happens to me periodically.  Rescan.

---

### Post by 4dognight on 2010-01-27
rescanning didnt help.

---

### Post by laceration on 2010-01-27
If you think its myth you can use scan with "scan" from the dvb-utils package.  For all I know myth could be using that too though.

---

### Post by 4dognight on 2010-01-27
Im going to try VLC and see if it works. If it does then its a mythtv bug.

---

### Post by 4dognight on 2010-01-27
I just tried using VLC. It works perfectly.
The problem isnt with the tuner. It tunes the channel fine,
It has must have something to do with mythtv unable handle the stream.

I did some googling around and I did find some ppl having  similiar problems. They mention something to do with PMT . I do recall seeing some errors referencing PMT. 

They were pretty old posts using older  versions of mythtv. I'm wondering if 9.10 reintroduced some old bug?

---

### Post by 4dognight on 2010-01-27
OK, I think I got this working now. I found a previous posting referencing 'quick tune' setting in the 'input connections' of the backend setup . I changed it to 'always' on both the kworld tuner and the hdhomerun. I was able to tune in that channel now!

:p

---

