---
title: "what's my dvd::rip doing?"
date: 2008-08-14
forum: Multimedia Software
---

### Post by Rohbart on 2008-08-14
Hello, I started DVD::rip and wanted to rip a video. I thought for the first time that I finally made it after installing some furhter packages. Dvd::rip was working very fast and ripped about 90% in 10 minutes. I could see the film growing very fast on the status indication, but now it has stopped. But there is no error shown. Is my dvdrip still working and I just have to wait because of the copy protection? I'll add a schreenshot of the logfile

---

### Post by Rohbart on 2008-08-14
no answers?

---

### Post by Rohbart on 2008-08-14
it still hasn't finished. I think I waitet long enough to let it finish. Where is the erroer?

---

### Post by semisweets on 2008-10-03
My dvd::rip does the same thing. It goes to 70% and stops. Anyone know how to get it to work?

---

### Post by semisweets on 2008-10-04
I fixed the problem!
I went to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and pick my verison of ubuntu. Then I searched for w32codecs and downloaded the tar.gz file. It took awhile for it to download on my computer. 

I then extracted the file. I opened a root nautilus and went to /etc/local/lib. I then created a folder called "codecs" without the quotes. I copied the files that were in the tar.gz to the new folder.

Dvd::rip took 6 hours instead of 10 minutes. It still went to 70%, but this time went I looked in the folder that it copied the dvd to the files were there.

Enjoy the movie! :popcorn:

---

### Post by s1300045 on 2008-10-05
I am having the same problem! However, I am using x64 8.10 beta as my system and not sure if that could be the cause, too. I was running Hardy with no problem.

I will try to rip a DVD again and see if I can get it working.

---

