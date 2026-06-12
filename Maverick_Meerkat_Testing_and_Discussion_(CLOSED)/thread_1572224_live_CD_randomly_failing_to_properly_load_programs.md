---
title: "live CD randomly failing to properly load programs sometimes?"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yfrwlf on 2010-09-10
Has anyone ever had a live CD not properly fully boot at random?  Some programs load, but not all, or certain programs that do load don't work properly?  It's very odd, but I've seen it happen a few times.  Then, after a reboot, you load the live environment again and everything is fine.  I'm thinking it may be due to the way programs are loaded off the CD.  They need to be more adamant about retrying to load and waiting perhaps.

It's not on a particular CD drive or computer or anything like that, it's something that I've seen for a very long time.  Anyone else have a similar experience?  Just curious. ^^

Thanks.

---

### Post by cariboo on 2010-09-10
I had this with the Lucid Live CD, I tried it just after I got it from Canonical and it hung during boot. Since then I've booted several computers with it including the one that hung the first time, with zero problems.

---

### Post by Yfrwlf on 2010-09-10
> **cariboo907 said:**
> I had this with the Lucid Live CD, I tried it just after I got it from Canonical and it hung during boot. Since then I've booted several computers with it including the one that hung the first time, with zero problems.

I've seen that happen before as well, and you're like "damn, hardware compatibility" or whatnot but then you try it again and suddenly it is working fine.  Maybe it has something to do with CDs and/or CD-ROMs in general sucking at random, but I'm really curious.  This is something that has happened since as far back as I can remember on Linux live CDs.

As is always the case, intermittent issues like these are so hard to figure out.

---

### Post by VMC on 2010-09-10
> **Yfrwlf said:**
> I've seen that happen before as well, and you're like "damn, hardware compatibility" or whatnot but then you try it again and suddenly it is working fine.  Maybe it has something to do with CDs and/or CD-ROMs in general sucking at random, but I'm really curious.  This is something that has happened since as far back as I can remember on Linux live CDs.

As is always the case, intermittent issues like these are so hard to figure out.

That's what the log files are for. Look through them. Its time consuming, but may yield good results. Look at both "/var/log" and "/home/.session-errors". Look for the "EE" errors.

---

### Post by Yfrwlf on 2010-09-10
> **VMC said:**
> That's what the log files are for. Look through them. Its time consuming, but may yield good results. Look at both "/var/log" and "/home/.session-errors". Look for the "EE" errors.

Thanks for the suggestion, although since this is a random issue affecting random programs, the errors are also going to be random.  Of course, eventually you might find a common error.  It may be something like a casper or ram-fs issue perhaps?  In any case, I wanted to see how widespread it was and if others had experienced it.  It is too late to diagnose my own problem as I am no longer in that live environment.

---

### Post by cariboo on 2010-09-10
Personally I would like to see the verify burn feature brought back to brasero, I used Fedora 13 to burn a DVD the other day and the feature was still used there.

---

### Post by Yfrwlf on 2010-09-10
> **cariboo907 said:**
> Personally I would like to see the verify burn feature brought back to brasero, I used Fedora 13 to burn a DVD the other day and the feature was still used there.
That would be nice, just an option in preferences somewhere or maybe even one in the burning dialog.

However, that does not explain it.  It can't be a burning error because in that case it would load incorrectly each time, and would never work flawlessly.

---

### Post by ranch hand on 2010-09-11
Bad idea, not simple enough.  Might scare an MS user.  Might work.

---

### Post by Yfrwlf on 2010-09-11
> **ranch hand said:**
> Bad idea, not simple enough.  Might scare an MS user.  Might work.

I hope that was sarcasm. :P

I'm all for having a clean GUI using the most common options, and that is why I mentioned putting it in preferences instead of in the main burning options before burning a disc, if it wasn't a desired enough thing to want in the main window.  I think it IS a desired enough feature to want in the main window though, but whichever.

---

### Post by cariboo on 2010-09-11
Actually the first time I saw the verify burn option was in Nero 4 or 5 on Windows, the only Linux burning gui app that had it at the time was K3B, and If I remember right, that was about the time that KDE 3.0 came out.

---

### Post by Yfrwlf on 2010-09-11
> **cariboo907 said:**
> Actually the first time I saw the verify burn option was in Nero 4 or 5 on Windows, the only Linux burning gui app that had it at the time was K3B, and If I remember right, that was about the time that KDE 3.0 came out.

That's why I sometimes still use K3B, is a real nice program if you want more options for burning, but usually Brasero is good enough, but this is all very off-topic since as I said, if there were burning errors, it'd never load right obviously. :P

---

### Post by cariboo on 2010-09-11
The reason I brought it up, was that when the option was available, I very rarely had any problems with burned CD/DVD's.

---

### Post by recluce on 2010-09-11
"Good" and "bad" burns are not just black and white, but shades of grey as well. A marginal burn may read fine on the drive that wrote it, but may cause trouble on other drives, especially marginal ones (there is a lot of "marginals" here, isn't there?) - and that trouble may appear random.

If I really get paranoid, I fire up Windows (YUCK!) to run Plextools and check C1/C2 errors and jitter. Disks with low error rates usually work on every drive - those with high error rates (note that C1 and C2 are not fatal errors, but correctable) tend to work on most, but not all drives.

Does all of the above help to solve the problem? Probably not. Using good media and a good drive (both are getting increasingly hard to find) is just about the only remedy. I have yet to encounter a bad or marginal burn with a Plextor PX-760 (or any other drive actually manufactured by Plextor) and genuine Tayo Yuden media.

---

### Post by Yfrwlf on 2010-09-12
> **recluce said:**
> "Good" and "bad" burns are not just black and white, but shades of grey as well. A marginal burn may read fine on the drive that wrote it, but may cause trouble on other drives, especially marginal ones (there is a lot of "marginals" here, isn't there?) - and that trouble may appear random.

If I really get paranoid, I fire up Windows (YUCK!) to run Plextools and check C1/C2 errors and jitter. Disks with low error rates usually work on every drive - those with high error rates (note that C1 and C2 are not fatal errors, but correctable) tend to work on most, but not all drives.

Does all of the above help to solve the problem? Probably not. Using good media and a good drive (both are getting increasingly hard to find) is just about the only remedy. I have yet to encounter a bad or marginal burn with a Plextor PX-760 (or any other drive actually manufactured by Plextor) and genuine Tayo Yuden media.

Thanks for the comment, I was going to suggest this but it happening at random seemed odd to me, especially if you leave the CD in the drive and simply reboot and the problems don't occur the 2nd time.  You may be right though and this is all due to random CD jitter.  In that case, it's too bad that even with all the modern error correction mechanisms in place, on the drive hardware level as well as software, this is still sometimes happening.  Weird, but you might be right!

---

### Post by recluce on 2010-09-12
> **Yfrwlf said:**
> Thanks for the comment, I was going to suggest this but it happening at random seemed odd to me, especially if you leave the CD in the drive and simply reboot and the problems don't occur the 2nd time.  You may be right though and this is all due to random CD jitter.  In that case, it's too bad that even with all the modern error correction mechanisms in place, on the drive hardware level as well as software, this is still sometimes happening.  Weird, but you might be right!

Actually, if it is a case of a marginal media/burn/drive, this is one of the few cases where "modern technology" works against you. There was a time when a CD burner cost around $500 and a single CD-R ran $5. Drives and CD-Rs were very high quality - I have audio CD-Rs from that time that spend a decade in a car CD changer (hot climate, cold climate, whatever) and still have fewer C1/C2 errors than a fresh burn on modern hardware.

Then, at some point, prices for DVD burners went to the $150 to $200 range, with media prices all over the place. You could still buy good quality burners, but media was hit and miss. Many DVDs and CDs I burned during that time are unreadable today - and it is always the same brands of media. Note that some companies like Yamaha dropped out of that market around that time.

Now, optical media may be on their last legs, bound to be obsoleted by thumb drives and cheap hard drives. Prices are rock bottom, I saw a special for a $19 DVD burner, media are just pennies. What kind of quality can be expected for that kind of money? Exactly. Many big name brands have dropped out of the market now or are just selling rebadged stuff (Plextor, Verbatim etc).

Practical advice: try to burn the same live image on a different drive and different media - and see if the the problem persists. Also try to burn to a CD-RW or DVD to see if that changes anything.

---

### Post by Yfrwlf on 2010-09-12
> **recluce said:**
> Actually, if it is a case of a marginal media/burn/drive, this is one of the few cases where "modern technology" works against you. There was a time when a CD burner cost around $500 and a single CD-R ran $5. Drives and CD-Rs were very high quality - I have audio CD-Rs from that time that spend a decade in a car CD changer (hot climate, cold climate, whatever) and still have fewer C1/C2 errors than a fresh burn on modern hardware.

Then, at some point, prices for DVD burners went to the $150 to $200 range, with media prices all over the place. You could still buy good quality burners, but media was hit and miss. Many DVDs and CDs I burned during that time are unreadable today - and it is always the same brands of media. Note that some companies like Yamaha dropped out of that market around that time.

Now, optical media may be on their last legs, bound to be obsoleted by thumb drives and cheap hard drives. Prices are rock bottom, I saw a special for a $19 DVD burner, media are just pennies. What kind of quality can be expected for that kind of money? Exactly. Many big name brands have dropped out of the market now or are just selling rebadged stuff (Plextor, Verbatim etc).

Practical advice: try to burn the same live image on a different drive and different media - and see if the the problem persists. Also try to burn to a CD-RW or DVD to see if that changes anything.

Haha thanks for the reply.  To some degree you are right of course and price does equal quality, though ironically I bought a really nice Sony CD/DVD/DVD-DL burner and it died a year later, while this cheapo NEC DVD drive which I bought before it that can do the same thing is still going strong.  Is it burning accurately though and was the cause of my issues?

Also, burning at lower speeds can of course help as well.

Any way, I appreciate the comments and perhaps that is the cause of this issue.  If it happens again, AND I'm on a USB drive though, and the stick's memory tests fine, THEN we'll have a problem. ^^

---

### Post by cariboo on 2010-09-12
This is slightly off topic, when I was in the audio/video repair business, a good 90% of CD/DVD player problems where because of bad lasers, the majority of which were manufactured by Sony.

---

