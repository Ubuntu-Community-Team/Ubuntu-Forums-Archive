---
title: "Replacement/fork of k9copy?"
date: 2011-08-28
forum: Multimedia Software
---

### Post by MakOwner on 2011-08-28
According to the [k9copy web page]("http://k9copy.sourceforge.net/web/index.php/en/news") the author is no longer supporting or developing the application.

Anyone know if there is any replacement or continuation of this project planned?

---

### Post by BuddyThirteen on 2011-09-01
I had this same question. It's really sad that he's quit developing k9. It's the easiest I've used so far.

Does anyone know if anyone else is going to continue the project?

Failing that, does anyone know of an alternate program that is as user-friendly and easy to use? I test-drove a few other ones, but none were as intuitive as k9copy.

:confused::confused::confused:

---

### Post by MakOwner on 2011-09-01
I am trying this in korn shell script -- I have had a 50/50 success rate on two ARCcos corrupted DVDs.
I want full size ISOs, but once you get the ISO corrected, you can use k9copy again, so long as it doesn't crash :/


#!/usr/bin/ksh
DVD=$1
TITLE=`lsdvd | grep "Disc Title" | cut -f2 -d:`
print ":${TITLE}:"

read pause 

vobcopy -m -l -t $DVD
mkdir ${DVD}/AUDIO_TS
genisoimage -dvd-video -udf -V "$DVD" -o  ${DVD}.ISO "$DVD"

---

