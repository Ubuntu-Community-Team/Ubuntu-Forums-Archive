---
title: "Can't burn audio CDs with Brasero under Lucid"
date: 2010-05-12
forum: Multimedia Software
---

### Post by ka1ssr on 2010-05-12
I am having problems burning audio CDs with Brasero 2.30.0 after my upgrade to 10.04.  I was trying to burn a .wav file to CD but Brasero ejects the media without burning anything after transcoding the wav file and creating an image.  I'm attaching the error log to aid in debugging.

I can burn data CDs fine.  My burner, a Samsung SM-308B, can't burn DVDs so I don't know about burning them.

Thanks!

Bill

---

### Post by cdgugler on 2010-05-16
Same problem here.  The log seems to end abruptly too.  I was attempting to burn some mp3's with my Samsung SH-S223C burner.  Running 10.04 64 bit.  The Brasero log ends with this:

> BraseroAudio2Cue Writing cue entry for "/tmp/brasero_tmp_H5ZZCV.cdr"
BraseroAudio2Cue Writing cue entry for "/tmp/brasero_tmp_AU6WCV.cdr"
BraseroAudio2Cue Writing cue entry for "/tmp/brasero_tmp_6JS4CV.cdr"
BraseroAudio2Cue Writing cue entry for "/tmp/brasero_tmp_06HWCV.cdr"
BraseroAudio2Cue Writing cue entry for "/tmp/brasero_tmp_68V7CV.cdr"
BraseroAudio2Cue Writing cue entry for "/tmp/brasero_t
Downloaded GnomeBaker and it works fine, so I'll be using that for now.

---

### Post by Chrisco66 on 2010-05-19
Same here.  There are at least five other threads on this, but still no answer.  There is a bug report, so we will have to wait and see.  I have used Brasero since 7.04 and it was the simplest, easiest software to use.  What happened to CD/DVD Creator?  I dont know why it was not included in the last few versions..

---

### Post by sieve on 2010-05-21
I have the same problem.  Burning audio CDs worked fine until I upgraded from 9.10 to 10.04.

---

### Post by Chrisco66 on 2010-05-23
Look at this thread, [http://ubuntuforums.org/showthread.php?t=1486562](http://ubuntuforums.org/showthread.php?t=1486562)

---

### Post by ka1ssr on 2010-05-28
I'm using gnomebaker.  It works pretty good except for the fact that it has to go back and recode when you want to make copies of the same wav file.

Bill

---

### Post by ka1ssr on 2010-05-28
Crisco66,

I had problems with dvd creator seg faulting under 9.10.  Dunno if that's the reason why it's not included.

Is it still in the repositories?

Bill

---

### Post by Chrisco66 on 2010-06-03
Bill, Im not sure.  I got used to Brasero.  I finally gave up and went back to 9.10.  Im using 10.04 on the desktops, but the laptops and netbook gets 9.10.  

Between burning problems, wireless problems, ATI video problems, its just too much work to stay current.  I dont know why they removed all the drivers that laptops need.  I guess Im going to look for a replacement for Ubuntu.

---

### Post by ka1ssr on 2010-06-14
Snagged the latest Brasero release (2.30.1) via system update.  Everything seems to work.

Bill

---

### Post by Chrisco66 on 2010-06-17
Mine started working too.  I still have a problem with ejection though.  The tray opens, then closes again.  Then it says "unknown problem, eject manually", or something like that.  I can live with that, as long as I can burn..

---

### Post by XanII on 2010-06-18
CD-burning worked in 8.04 for me but then somethig went wrong. Havent tried much since 9.10 since all burnings just fail regardles if the media CD-RW,CD+RW,CD-R. 

Maybe i should try again with 10.04.

---

### Post by sanderella on 2010-06-18
Did you remember to convert your oga or ogg files to mp3?

---

### Post by wkulecz on 2010-06-18
Copying a data disk failed for me using 10.04 this morning.  This was my first try using the burner on Lucid :(

The CD/DVD reading functions so far all have seemed to work fine.

I had the 2.30.1 version already :(

Did the copy without issue on an old 8.04 system I still have.

IMHO this is a very serious problem with Lucid as the default install CD/DVD burning on 6.06 and 8.04 has been as good and easy as it gets -- way less hassle than using Nero on Windows.  But now that's gone :(

---

### Post by XanII on 2010-06-21
It seems to be a problem in the kernel level i think? 8.04 worked nice, then the default software got changed in next versions but installing the same software that i used yielded failed discs anyway.

---

### Post by snapback77 on 2010-06-30
Sanderella is correct. One must convert to a mp3 or wav to burn a CD in Brassero.

---

### Post by ka1ssr on 2010-07-05
Try disabling the burn directly to CD option.  I was having trouble with my 733 MHz PIII burning properly and turning this option off fixed my problem.

True I have to wait a while for the burning to start but at least I'm not making coasters anymore.

---

