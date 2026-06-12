---
title: "[SOLVED] Flash again, it doesn't work now"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by hutxubix on 2007-12-31
Hello!

I know there are hundreds of threads about installing Flash, Me Myself I have got it installed many times, but I have done a brand new install of Ubuntu 7.10 32 bits on a AMD64 Athlon X2 and I do not get it to work! Neither in FF, nor in Opera. I installed it first when FF tells you it needs more plugins but nothing. Then, through Synaptic, then through the download from the Adobe webpage, but IT DOES NOT WORK!!!!!!

Any idea, please?

---

### Post by Old Jimma on 2007-12-31
Hi:

I had this same problem yesterday with my 64 bit AMD. 

I tried so many things to get it working, I'm not sure what eventually worked. Try this first: look at the ubuntu page on web browsing at 

[https://help.ubuntu.com/7.10/internet/C/web-browsing.html](https://help.ubuntu.com/7.10/internet/C/web-browsing.html)

Try following some of the directions there.

Then have a look at the other options you've got, just in case you can't get Flash to work.

Also, what I did was to download flash and move the .so file into the firefox32 plugins folder.


Phil Smith
Duluth, GA

---

### Post by Seisen on 2007-12-31
You need to download the tar.gz file from the Adobe website and install it that way. There is a bug that is supposed to be fixed but for some reason some poeple are still having problems.

---

### Post by hutxubix on 2007-12-31
Thanks!!

That list gave me the clue: Is Java installed? NO

I think that, when FF installs flash-plugin it should also install java but, for any reason, it doesn't so, install sun-java6 and that's is.

Thanks.

---

