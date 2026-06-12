---
title: "/dev/dsp"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by gherardo on 2006-08-20
Sound works fine with all distributed applications, especially mpg123, soundjuicer.

But I downloaded two apps (transcribe for voice recognition and transcriber for slowing down mp3's), they both complain being unable to write on /dev/dsp (permission denied).

What is /dev/dsp? 

Thanks, G.

--------------------------------------------------------------
#ls -l /dev/dsp
crw-rw---- 1 root audio 14, 3 2006-08-20 06:49 /dev/dsp
--------------------------------------------------------------
HP Pavillon dv4000 (laptop)
Ubuntu 6.06, 
kernel 2.6.15-26-386, 
CPU Pentium M, 
Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
---------------------------------------------------------------

---

### Post by twoseids on 2008-05-31
I have the same question a year and a half later!

---

