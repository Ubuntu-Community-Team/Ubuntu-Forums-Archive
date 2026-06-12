---
title: "Skype Inverted Video Solution"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Tech226 on 2012-05-08
I used the following to correct the inverted video in Skype 2.2.0.35 (Beta) problem on my Asus UL30A notebook w/ Ubuntu 12.04 64bit.  This notebook shipped w/ a Suyin Corp. Asus Integrated Webcam [CN031B].  The video was not inverted in Cheese.

1.  Rename /usr/bin/skype to /usr/bin/skype.original.

```
sudo mv /usr/bin/skype /usr/bin/skype.original
```

2.  Create a new /user/bin/skype file.

```
sudo gedit /usr/bin/skype
```

3.  Paste the following:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype.original
```

4.  Save & exit gedit.

5.  Make /usr/bin/skype executable.

```
sudo chmod +x /usr/bin/skype
```

6.  Start Skype as you normally would.

I can't take credit for this solution.  I found it via google except the path to v4l1compat.so was incorrect in the other solutions I found.

Hope this works for you if you have a similar problem.  Comments welcome.

---

### Post by kimberley on 2012-06-06
Tech 226 - thank you so much - I tried your solution and it WORKED for me. I have been trying to fix the webcam problem on Skype for months.:p

---

### Post by Tech226 on 2012-06-06
> **kimberley said:**
> Tech 226 - thank you so much - I tried your solution and it WORKED for me. I have been trying to fix the webcam problem on Skype for months.:p

You're welcome!

---

### Post by kimberley on 2012-06-07
Your webcam solution works for me but only when I open from the terminal. Whilst it is great to now have video it is a bit frustrating to have to do this each time rather than just opening Skype.  

Any ideas on how to solve this?  By the way it wasn't a question of my video being inverted - I only had a black screen, so your solution might work for others with a similar problem.

Thanks again.:)

---

### Post by Tech226 on 2012-06-08
> **kimberley said:**
> Your webcam solution works for me but only when I open from the terminal. Whilst it is great to now have video it is a bit frustrating to have to do this each time rather than just opening Skype.  

Any ideas on how to solve this?  By the way it wasn't a question of my video being inverted - I only had a black screen, so your solution might work for others with a similar problem.

Thanks again.:)

Sorry, I don't know.  When I have some time I will try to figure it out and post back here.

---

### Post by alex36sd on 2012-06-24
Hi, 

The fix worked for my Asus U36SD. 
Thanks a lot!

Alex.

---

### Post by luc6 on 2012-08-14
thank you very very much!!! after many months I finally solved the upside down skype image!!! It worked with Ubuntu 12.04 and Skype 4.0.0.8 in Lenovo Ideapad Y510.
:D

---

### Post by Tech226 on 2012-08-14
Glad to hear others are having success with this. :)

---

### Post by Tech226 on 2012-08-14
> **kimberley said:**
> Your webcam solution works for me but only when I open from the terminal. Whilst it is great to now have video it is a bit frustrating to have to do this each time rather than just opening Skype.  

Any ideas on how to solve this?  By the way it wasn't a question of my video being inverted - I only had a black screen, so your solution might work for others with a similar problem.

Thanks again.:)


Kimberley,  any luck solving this yet?

---

### Post by aelex on 2012-10-27
This worked for me also on ASUS UL50AG with  Ubuntu 12.04.
Thanks !

---

### Post by muhh on 2012-10-28
Thank you! Worked excellent, now my webcam is fixed. Asus K70ID Ubuntu 12.04

---

### Post by sujit maharjan on 2012-10-31
thnx worked for asus u31f

---

### Post by leorolla on 2013-01-07
Worked perfectly on my asus too.

---

### Post by charlesopondo on 2013-04-16
My Asus B50A has been plagued by this problem since 2009 when I bought it. In that whole time I've tried lots of unsuccessful fixes. This one has worked like a charm. Thanks a mighty lot!

---

### Post by Tech226 on 2013-04-17
You're welcome.  Glad others are still having success with this yet puzzled as to why Skype, Asus, and/or Ubuntu have not resolved this issue yet.  Maybe it is and I am just not aware...?

---

### Post by blurrred on 2014-03-07
Hey man, I can't believe it but this actually worked almost perfectly with my Asus ul50vt running Linux Mint 16. The only thing left out was that I had to download the libv4l on my own

---

### Post by Ajidh on 2014-05-11
it worked for me also in my asus k50IN with ubuntu 14.04, after months of searching and trying solutions.

Thank you very much!!

---

