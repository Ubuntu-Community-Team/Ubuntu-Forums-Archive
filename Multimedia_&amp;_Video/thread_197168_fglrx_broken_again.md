---
title: "fglrx broken again"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2006-06-15
Thought I would start a new thread since I updated this morning and fglrx is broken again. I figured that if it's the update, I won't be the only one posting. I tried replacing libGL.so.1.2 again but it didn't work. I just got the huge list of errors that someone else posted [here]("http://www.ubuntuforums.org/showthread.php?t=185033&highlight=fglrx+openoffice"). It also broke OpenOffice.org so I switched back to the ati driver so that I can have functionality.

---

### Post by Slicedbread on 2006-06-15
[QUOTE=SteinbergerNate]Thought I would start a new thread since I updated this morning and fglrx is broken again. I figured that if it's the update, I won't be the only one posting. I tried replacing libGL.so.1.2 again but it didn't work. I just got the huge list of errors that someone else posted [here]("http://www.ubuntuforums.org/showthread.php?t=185033&highlight=fglrx+openoffice"). It also broke OpenOffice.org so I switched back to the ati driver so that I can have functionality.[/QUOTE]

Everything works fine here.

---

### Post by iZm on 2006-06-16
Still broken here too. 

I have a HP Pavilion dv8000 laptop with a "Radeon XPRESS 200M". Gdm loads up fine, but as it loads to the desktop, the gdm screen remains in the background, I get the top and bottom desktop bars and then it locks hard. :( I have switched back to the radeon driver again.

---

### Post by mochaspro on 2006-06-16
Same problem here... HP Pavilion dv8000, ATI RADEON XPRESS 200M, Dapper...

It loads slowly and freeze after i do almost every thing... :(

---

### Post by Galban on 2006-06-16
Just for your info. SteinbergerNate fixed his problem doing what is explained here:

[http://ubuntuforums.org/showthread.php?t=197471]("http://ubuntuforums.org/showthread.php?t=197471")

---

### Post by mochaspro on 2006-06-16
yeah but he doesnt have an Ati Radeon Xpress 200M he as another one... i just want to see ONE person with 3D with this card and WITHOUT getting problems with the slow things, scrolling, etc

but thanks for your suggestion anyways ;)

---

### Post by mochaspro on 2006-06-16
to be more specific i have the same problem as izm :confused:

---

### Post by tommohawk on 2006-06-16
mochaspro and izm,

I have a dv8000 aswell so I fully understand the problems you have both had.  

You need to make sure that you use the 8.24.8 ati proprietary drivers and not the 8.25.18.  There are issues with the new drivers and the xpress 200m card that have not yet been resolved.  You can downgrade the drivers using kpackage or some other package management program (kpackage works the best I found).  Once you have downgraded the drivers, you are on your own - I managed to get 3d working again but I am not 100% sure how I did it.  I know that I am using the 8.24.8 drivers and I know that I updated some of the packages to 8.25.18 but not all of them.  You need to run the ati installer from the command line and generate the separate Debian packages and then install them separately.

Hope that is of some use.

---

### Post by mochaspro on 2006-06-16
Thanks for your reply... i knew that 8.25 has problems with 200M but you're the first person i know that can use full 3D without problems... i've tried 8.24.8 drivers, 8.25, apt-get drivers, 99% of howto's but still can get my 3D :sad: 

The best i can get it's with fglrxinfo says the correct driver, i mean not mesa.... ATI RADEON, but it's almost unusable to me...

:-({|=

---

### Post by mochaspro on 2006-06-16
i just saw this thread [http://www.ubuntuforums.org/showthread.php?t=197992&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=197992&highlight=fglrx)
 so it means it's possible to do it... but im really starting to think that with xpress 200M amd 64 turion witu ubuntu dapper for 32 bits it's nearly imposible :confused:

---

### Post by mochaspro on 2006-06-19
Ok, i got it... just installed the ati drivers 8.24.8 in a fresh install with dapper 32 bits and please, dont update them to 8.25! :rolleyes:

---

