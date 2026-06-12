---
title: "WPA2-Enterprise AES PEAP wireless server certificate problem"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by yoobin.jeong on 2010-05-28
My university recently did a complete rehash of its wireless system and decided to abandon

UTN user first hardware certificate (which was easily obtainable from /usr/share/ca-certificates/mozilla)

and introduce server certificate. Since then, wireless connection to 'uniwide' has been incredibly unstable.

I can still connect to uniwide by not choosing certificate but I get disconnected every 2 minutes or so.

Even more infuriating because Windows and Mac are thriving in this new wireless setting and linux is left for dead.

IT (part-time uni students) guys at the university keep on saying 'oh, just leave the certificate empty, it's ok'.

Well, it's not ok because I CAN'T DO JACKSHIT ON UNIWIDE!

Anyways, I decided to take this matter to you guys for your wisdoms.

[https://www.it.unsw.edu.au/students/uniwide/index.html](https://www.it.unsw.edu.au/students/uniwide/index.html) -> this website has pdf setup guides for windows, mac os and linux.

DISREGARD LINUX SETUP GUIDE! It's way out of date.

If I could somehow get the server certificate on my hard drive and choose that certificate during setup,

would it solve the problem?

---

### Post by yoobin.jeong on 2010-05-28
Bump

---

### Post by ashwyn on 2010-07-20
Not much help perhaps, but I'm also just starting at UNSW and an ubuntu user.  I was experiencing the same problem.  Just a few minutes ago, as a result of a google search, I downloaded the security certificate:
[https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=87](https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=87)
and then selected it as the CA for uniwide.

I saw someone else suggesting it for the UNSW network.  Haven't disconnected since adding it, not sure if it is just luck so far though.

Worth a try.

---

### Post by shrinux on 2010-09-06
yoobin.jeong, thank you for posting this problem, because I have the same issue at unsw.

ashwyn, i will try your suggested certificate. :D

---

### Post by shrinux on 2010-09-08
sorry.
but it didn't work :(

---

### Post by dcaffeine8d on 2010-09-16
Try the instructions here: 
[http://www.engin.umich.edu/caen/network/wireless/docs/linux.html](http://www.engin.umich.edu/caen/network/wireless/docs/linux.html)

---

