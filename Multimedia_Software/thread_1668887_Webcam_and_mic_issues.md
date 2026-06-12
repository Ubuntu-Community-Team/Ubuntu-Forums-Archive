---
title: "Webcam and mic issues"
date: 2011-01-16
forum: Multimedia Software
---

### Post by joe.w.fro on 2011-01-16
I just got a new [ASUS U52f laptop]("http://www.bestbuy.com/site/Asus+-+Laptop+/+Intel%26%23174;+Core%26%23153;+i5+Processor+/+15.6%22+Display+/+4GB+Memory+/+640GB+Hard+Drive+-+Dark+Navy/1257685.p?skuId=1257685&id=1218243754694") (if link doesnt work just search for it on the Best Buy site) for Christmas and everything works on it except that the internal webcam and microphone, which are malfunctioning. The webcam actually displays a picture, but it vertically inverts it (for direction n00bs: the image goes from a M to a W) for no obvious reason.
The mic issue is that it simply refuses to work. When i tried every audio driver available, none seemed to work.  I think it detects it, as "Internal Audio Analog Stereo," but it just will not any sounds in the sound preferences.
Ideas?

---

### Post by kiki298 on 2011-01-22
I have the same laptop as you, and this thread was really helpful, it already has the solution for the webcam problem:

[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

As for your mic problem, I haven't experienced it. I did have a problem with the speakers, so I don't know if what I did fixed the mic problem before I noticed. If you want to try what I did, open gksudo gedit /etc/modprobe.d/alsa-base.conf, and add this line to the end: options snd-hda-intel model=auto, and save. If it doesn't work for you, just open the file again, and erase the line you entered in and save. 

Hope this helps!

---

### Post by kiki298 on 2011-01-22
Just checked the thread again and there was a solution for the microphone, so maybe you'll be able to sort out all of your problems

---

### Post by joe.w.fro on 2011-01-22
> **kiki298 said:**
> Just checked the thread again and there was a solution for the microphone, so maybe you'll be able to sort out all of your problems

wow dude thanks that totally solved my problem :p

---

### Post by kiki298 on 2011-01-23
No problem :) just mark this thread as solved so it can help others out

---

### Post by Chogsed10 on 2011-01-23
Hey guys, i was hoping someone on here could help me with my webcam problem.

I have a Logitech C500 webcam, and it works with skype, and cheese. but it doesnt work with firefox at all. Facebook doesnt pick the web cam up, its almost like its not plugged in.

im pretty new to ubuntu so there is probably something im missing...the webcam that i have (logitech C500) is compatible. 

Any ideas? Any solutions? Any help?

thanks in advance

- Christian

---

### Post by joe.w.fro on 2011-01-24
> **Chogsed10 said:**
> Hey guys, i was hoping someone on here could help me with my webcam problem.

I have a Logitech C500 webcam, and it works with skype, and cheese. but it doesnt work with firefox at all. Facebook doesnt pick the web cam up, its almost like its not plugged in.

im pretty new to ubuntu so there is probably something im missing...the webcam that i have (logitech C500) is compatible. 

Any ideas? Any solutions? Any help?

thanks in advance

- Christian

First off: Do you have javascript and flash installed (if you dont install ubuntu restricted extas)

If that is not the case type ```
firefox
``` in a terminal and print the output

---

