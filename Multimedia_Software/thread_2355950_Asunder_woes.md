---
title: "Asunder woes"
date: 2017-03-18
forum: Multimedia Software
---

### Post by hemmo on 2017-03-18
Cheers from a forum noob.

I'm having problems with Asunder on Ubuntu 16.04. In short, it does not asunderize anything. My goal is to transfer all my audio CDs into FLAC files, and here's what I'm getting so far (my assumptions in paranthesis):

- it recognizes the CD and gets the correct album information from freedb.org (I take this to mean it finds the DVD/CD drive correctly and is able to read data from the CD).
- it lets me choose FLAC enconding without any warnings (so it seems it came with all the necessary codecs for this - if I try to change encoding from FLAC to something restricted / proprietary I correctly get a warning message about missing codecs).
- it claims to start ripping but takes a LONG time per track. In the order of 4x the duration of the track. FLAC compression setting has no effect on this. I have no reference, but isn't this excessive? I cannot hear the CD spinning up / down at any point during the ripping process.
- progress percentages shown don't increase gradually. At the end of each track there's a "bulk" increase of percentage points to all three meters. If I'm ripping a CD with 10 tracks, each increase is 10% points, regardless of duration of  tracks (this seems incorrect and an indication that nothing actually happens).
- it gradually wades through the tracks, and after the final track it displays an error message saying tracks could not be ripped.
- it does create a folder in the designated place for the album, and it does write a .flac.m3u file for the album (so it has write access to the designated directory).
- it does not write a log, despite of the "write log" checkbox in Preferences having been checked.

Any ideas on what could be wrong would be greatly appreciated. Thank you in advance.

--hemmo

---

### Post by Yellow Pasque on 2017-03-18
So, obvious question: Have you tried another ripper?

EDIT: I would recommend abcde. Despite the fact that it's CLI, ripping to flac is easy: [http://www.andrews-corner.org/linux/abcde/abcde_lossless.html#flac](http://www.andrews-corner.org/linux/abcde/abcde_lossless.html#flac)

---

### Post by hemmo on 2017-03-18
No, not yet. This would of course be the perfect time to change, as I don't have much time and effort invested in this yet. But from what I've read, those who like Asunder *really* like it, a lot. It would seem a solid candidate for what I'm trying to do.

abcde is actually the next one on my short list. It's just that I gave up command line when I got my first Mac+ back in previous millenium and haven't really missed it at all.

---

### Post by speartip on 2017-03-20
First try installing all the relevant codecs, if you haven't already:
```
sudo apt install ubuntu-restricted-extras flac lame
```
See if that helps.

---

### Post by hemmo on 2017-03-21
Thanks for the suggestion (and for providing the command line :)), tried it but no change.

---

### Post by mc4man on 2017-03-21
> **hemmo said:**
> 
- it lets me choose FLAC enconding without any warnings (so it seems it came with all the necessary codecs for this - if I try to change encoding from FLAC to something restricted / proprietary I correctly get a warning message about missing codecs).
Then you would be be good to go for flac, otherwise it would complain..
> **hemmo said:**
> 
- it claims to start ripping but takes a LONG time per track. In the order of 4x the duration of the track. FLAC compression setting has no effect on this. I have no reference, but isn't this excessive? 
Seems excessive, have you tried the "Faster ripping" setting?
> **hemmo said:**
> 
- progress percentages shown don't increase gradually. At the end of each track there's a "bulk" increase of percentage points to all three meters. If I'm ripping a CD with 10 tracks, each increase is 10% points, regardless of duration of  tracks (this seems incorrect and an indication that nothing actually happens).
Here it would increase gradually (1 or 2 % at a time) though it seems not time based, just 100/number of tracks

> **hemmo said:**
> 
- it gradually wades through the tracks, and after the final track it displays an error message saying tracks could not be ripped.
- it does create a folder in the designated place for the album, and it does write a .flac.m3u file for the album (so it has write access to the designated directory).
- it does not write a log, despite of the "write log" checkbox in Preferences having been checked.
That is the problem, rips are failing but no log to see why. It seems asunder changed it's log routine & what it uses to create logs, the effect of that is no logs in Ubuntu & maybe Debian..

I use abcde, far better & currently maintained, ect. It can be set up to autorun on cd insertion if desired (in interative or non-interactive mode, the latter allows you to insert cd & it rips/encodes on it's own.

---

### Post by speartip on 2017-03-22
Just a thing. Have you tried various CDs. One thing i've noticed is that if the CD is in A1 condition, the rip is a lot faster than one that isn't.
I would still try mc4man's suggestion though & try abcde.

---

### Post by hemmo on 2017-03-22
Yes, I've tried several CDs. Also to see if it can reliably find the album metadata. Same results.

> **mc4man said:**
> Seems excessive, have you tried the "Faster ripping" setting?Yes, Faster ripping is selected.

> **mc4man said:**
> Here it would increase gradually (1 or 2 % at a time) though it seems not time based, just 100/number of tracksOK, so it's a feature, not a bug. :)

> **mc4man said:**
> It seems asunder changed it's log routine & what it uses to create logs, the effect of that is no logs in Ubuntu & maybe Debian..OK.

Thanks for the replies and if there's something else anyone can think of, please bring it up. But I'm starting to get the impression I may be heading back to CLI world in not so distant future.

---

### Post by speartip on 2017-03-22
There is another CD ripper in the repos called ripperx. You could try that 1st if you want a gui.
You could also run Asunder from a terminal & see if spits out any unusual error messages.

---

