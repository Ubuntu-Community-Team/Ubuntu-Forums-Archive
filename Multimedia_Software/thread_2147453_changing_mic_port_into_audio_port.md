---
title: "changing mic port into audio port"
date: 2013-05-22
forum: Multimedia Software
---

### Post by luckygrox on 2013-05-22
I would like to use the mic in port with my speakers (i.e switch it to be line out). The middle default line out port is somewhat damaged (Confirmed even in windows xp) However when i use the realtek HD audio panel on XP to set the mic in (pink) port to line out, i get awesome sound. Was wondering if the same could be done from ubuntu.I use ubuntu 10.04 desktop version. Any assist will greatly be appreciated.

---

### Post by papibe on 2013-05-22
Hi luckygrox.

Before open the application you want to use to record or reproduce audio, open 'Sound Settings' on the drop menu under the volume, or 'Sound' on the dashboard.

There you can setup which input and output to use as a default.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by luckygrox on 2013-05-22
Hi.
 Thank you for your suggestions..
 But sorry to say that it didn't work.
 In my desktop pc, there are 3 audio ports on the rear panel pink,gree,and blue. Green one doesn't work as I mentioned before.So I have pluged my speakers to pink port. How ever there are two ports in the front panel pink and green. I have pluged my headphones to the green one.When I choose &#8220;analog output&#8221; as output connector in sound preferences, the headphone works.when I choose &#8220;analog headphons&#8221;,none of them work.So i can't hear any sound from my speakers.  
 Regards.

---

### Post by luckygrox on 2013-05-22
can anybody help me? :confused:

---

### Post by luckygrox on 2013-05-24
couldn't you find the reason for my problem?? :-(

---

### Post by papibe on 2013-05-24
Check that the input and output you want to use are not muted.

Open  a terminal and run:
```
alsamixer
```
Regards.

---

### Post by Yellow Pasque on 2013-05-26
[http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by gordintoronto on 2013-05-26
Also, the version of Ubuntu you are using has expired, which makes it harder for people to help you: the people who have answers are not running 10.04.

---

