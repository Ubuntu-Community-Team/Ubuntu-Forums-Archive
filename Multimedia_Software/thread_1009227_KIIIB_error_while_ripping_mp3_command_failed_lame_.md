---
title: "KIIIB error while ripping mp3: command failed: lame -h --tt"
date: 2008-12-12
forum: Multimedia Software
---

### Post by mseeba on 2008-12-12
HI there. I recently installed 8.10 and now cannot rip cds into mp3 files using KIIIB. I get the following error:

command failed: lame -h --tt FILENAME --ta A...  (cannot see the rest of the message. 

Here is the debugging output:
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-7-generic
Devices
-----------------------
_NEC DVD+-RW ND-6650A 102C (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]

I can rip .ogg files fine but my ipod does  not support them. I read on a Debian forum that the new version of lame has a bug relative to mp3s.

Can anybody help me solve this one?

Thanks!

---

### Post by mseeba on 2008-12-12
So I see that Audio Extractor now support MP3 so I no longer need KIIIB. However, it is a nice program to use so if there are any ideas about fixing it please do reply.
-Mark.

---

### Post by apksr on 2008-12-18
This solution worked for me found it in the Mandriva forum ([http://www.linuxquestions.org/questions/slackware-14/having-some-trouble-w-k3b-and-encoding-with-lame-640386/](http://www.linuxquestions.org/questions/slackware-14/having-some-trouble-w-k3b-and-encoding-with-lame-640386/)). I just cut and paste the line:



1/ Start k3b and insert audio CD (allow cddb lookup)

2/ click "Start Ripping"

3/ select MP3 (lame) as filetype

4/ Click the config cog beside this

5/ highlight the Mp3 (lame) and click edit

6/ check your command line (mine is

lame -h -V2 --tt %t --tn %n --ta %a --tl %m --ty %y --tc %c - %f

)

7/ check both "swap byte order" and "write wave header" then OK, OK

8/ Save settings!!

9/ Start ripping

---

### Post by Kalrog on 2009-01-14
That worked for me.  I didn't change my command line at all (and it is different than what you have), but I did check the 2 boxes you indicate (swap byte order and write wave header) and saved.  It is now ripping the first CD since then - and then I'll listen to it and let you know if there is a further problem.

Thanks for the info!

---

### Post by commonplace on 2009-03-26
Huh, this seems to have worked for me too. Odd. Thanks! :)

/Kevin

---

