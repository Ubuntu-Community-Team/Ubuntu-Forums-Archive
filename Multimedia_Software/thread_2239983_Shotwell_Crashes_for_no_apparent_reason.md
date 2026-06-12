---
title: "Shotwell Crashes for no apparent reason"
date: 2014-08-17
forum: Multimedia Software
---

### Post by kd7sjt007 on 2014-08-17
Good Evening. I am using an HP Pavillion DV7-6135DX Entertainment PC with a fresh install of Ubuntu 14.04.1

I have about 24 thousand pictures and 1400 videos on an external USB 3 drive. When I import the pictures to my new install it seams to get them all on the drive. I open shotwell to try to view various
pictures and videos and it crashes. No reason is given. The standard "Ubuntu has experienced an internal error" comes up along with send report, yes or no? I always select yes. When I click more info button,
all it shows is the path to shotwell. Nothing else. 

Is there anything I should try? I can't use shotwell at all at this point. Any advise would sure be nice. Thank you.

Earl

---

### Post by ibjsb4 on 2014-08-17
A few things you can do.

Open shotwell in terminal and see if it gives any errors.
```
shotwell
```

Go to /var/crash/apport and look for shotwell crash report.

Try another image viewer just to be sure your not dealing with corruption.

---

