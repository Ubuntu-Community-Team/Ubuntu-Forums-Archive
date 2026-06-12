---
title: "TV OUT ATI Mobility Radeon M6 LY"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by red1916 on 2007-03-04
Hi all,

how can I do to use the TV out with my ATI Mobility Radeon M6 LY? 

I installed ubuntu edgy and used the drivers that comes in it. 3D works ok now and I installed beryl that works ok too. So drivers don't seems to be a problem.  

Am I missing anything?
whick is the equivalent for ATI to the program NvTV TV out I found for nvidia?  

thanks very much

---

### Post by chenoille on 2007-03-27
Hi, 

That is what I'm trying to do as well... I tried this method

[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

not succesfully. 

For sure it is possible to make it working with linux, since it is working with the geexbox. But how? 

Please help!!

---

### Post by chenoille on 2007-03-27
try atitvout it's working by me for a single TV output

---

### Post by stieltjes on 2007-06-28
> **chenoille said:**
> try atitvout it's working by me for a single TV output

Great. I have used atitvout on my Dell Latitude 610 with the M6 chipset. I have used the test program along with a combination of command line options and have nothing working yet.

Since it has worked for you, what cmdline options have you used? Anybody?

---

### Post by stefanst on 2007-12-25
Sorry- I don't have the solution for your problem- I am struggling with the same issue.

Running Gutsy on a Dell Inspiron 4100 that I want to use as a MythTV frontend on my TV, so TV Out is crucial for me.

No matter what I do, I always find the following in my xorg.0.log:

```

(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768

```

Even though the S-Video is certainly connected and it worked when I was using WinXP.

Here's the bump :-)

STS

---

### Post by www.rzr.online.fr on 2008-01-20
If it helps
It works on debian and not hardy ...

[http://rzr.online.fr/q/TvOut](http://rzr.online.fr/q/TvOut)

---

