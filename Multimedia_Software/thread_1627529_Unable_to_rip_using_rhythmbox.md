---
title: "Unable to rip using rhythmbox"
date: 2010-11-21
forum: Multimedia Software
---

### Post by kaurie on 2010-11-21
I upgraded to 10.4 (64bit) Ubuntu and since then have been unable to rip CD's using the procedure in the Official Documentation

Ubuntu Documentation > Ubuntu 10.04 > Music, Video and Photos > Music > Extract from a CD

But when a CD is placed in the drive Rhythmbox would not run

Typing rhythmbox in a terminal (with a CD) in the drive shows the message segmentation fault.

using the code in [http://ubuntuforums.org/showthread.php?t=1467615&page=2](http://ubuntuforums.org/showthread.php?t=1467615&page=2) I reinstalled rhythmbox
> sudo apt-get purge rhythmbox
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install rhythmbox rhythmbox-plugins

There was no change

I found in the documentation that sound-juicer was used in the ripping process and as this was not installed - so I installed this.

I can now rip a CD using sound-juicer and can run rhythmbox when there is no cd in the computer but I am a little puzzled as to what is happening.

Has anyone else had this problem?

---

### Post by wilee-nilee on 2010-11-21
Brasero works fine is part of the stock install, just be sure your within the law when doing so.;)

---

### Post by kaurie on 2010-11-22
Thanks for the info on Brasero - I was unaware of this

I do have a solution in sound juicer. However the Ubuntu Manual does say that rthymbox is the way to go. Should I report a bug or what?

How does one suggest to the manual keepers that it should be changed?

I am very new to this and would appreciate some guidance.


And yes all the ripped CD's are my own.

---

### Post by vanman on 2011-01-03
I just solved this issue on my daughters computer. 
It was recently upgraded to Ubuntu 10.10 and running Rthymbox 0.13.
She got an ipod for christmas and I needed to resolve her issue.


I installed restricted extras and it gave me the mp3 support.

Vanman

---

