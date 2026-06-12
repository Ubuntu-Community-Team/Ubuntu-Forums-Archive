---
title: "XGL/Compiz in Ubuntu Dapper (ati, 64Bit)....problems"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by mwob on 2006-07-10
Hi,

I've been trying for a while to get my system setup to use XGL/Compix. I followed the "main" guide here:

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Anyway, I seem to have a few problems, and thought I would share them here in case anyone has similar issues/resolutions.

Problem 1)

> 
~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0


After installing everything this is the error I get when I try to load XGL and compiz. I have no idea what it means, or what to do.  Other posts suggets messed up "newer" mesa libraries, but their workarounds do not help.

Problem 2)

This is a recent problem. I am trying tp update my system in an attempt to fix things. But when I try to update compiz, it seems that there are broken packages:

> 
The following packages have unmet dependencies.
  compiz: Depends: libsvg-cairo (>= 0.1.6) but 0.1.5-0 is to be installed
E: Broken packages

I guess the answer for this one might be just to wait a while and see what happens in the next week or so....

Does anyone have any ideas that might help?

Thanks!

---

### Post by hazart on 2006-07-10
I can confirm, this happens for me as well with dapper drake and the following sources.

```
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://www.beerorkid.com/compiz dapper main
deb-src http://www.beerorkid.com/compiz dapper main

```

---

### Post by hazart on 2006-07-10
The sollution:

For the very recent AMD64 packages, use this source:

```
deb http://raof.dyndns.org/falcon/ dapper eyecandy flash misc multimedia mythtv all
```

Then remove any installed cvs version, apt-get update and upgrade

---

### Post by mwob on 2006-07-10
hazart,

Thanks a lot for the source hint. Sure enough adding that does let me update compiz without complaining about broken dependencies. 

But, alas no XGL goodness :( When I load my XGL session, I get a veyr unresponsive system with no effects at all, and the system just dies after a while. When I open a terminal and try to start gnome-window-decorator, I get this:

mattroberts@button:~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

Does this indicate a problem with my GFX card I wonder? I'm just to linux-lame to get much further.... any hints welcome..!

---

### Post by mwob on 2006-07-12
Whoops...

I tried to "remove the existing" compiz stuff to see if that would help, so I did this:

```

sudo apt-get **remove** compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

But it seems that I'm now without any UI at all apart from a nice terminal window... ermmmmm.... I think I feel a re-install coming on!

---

### Post by Gelupah on 2006-07-20
Hi,

After struggling with my ATI drivers on 64bit AMD, I was looking forward to using XGL/Compiz. Saddly I have the same problem. When I try installing compiz, I get the following:

> 
The following packages have unmet dependencies.
  compiz: Depends: libsvg-cairo (>= 0.1.6) but it is not going to be installed
E: Broken packages


I have tried changing the source to the suggested one, but I get a connection time-out.

I have tried a few clean installs and am getting this recurrent "broken package" problem, with or witout libsvg-cairo 0.1.5 installed.

Any ideas? I would be very grateful to anyone who has found a solution or has ideas on this problem! Thanks.

---

### Post by Gelupah on 2006-07-20
I found the solution to the problem. You can download the deb to the 1.0.6 version on the following site:

[HTML]
http://home.comcast.net/~psyberone/index.html
[/HTML]

Once this is done, compiz installs fine!

Thanks anyway!

---

### Post by mwob on 2006-07-21
I always found issues in 64bit that prevented me from using Xgl....it seems the ditro's are a bit behind the 32 bit version.

My solution was to install a 32-bit version, which sorted all out!

---

