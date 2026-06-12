---
title: "ATI X1600 XT - Research - Did It work for you"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by alanrr_sr on 2006-05-31
I've tryed everything... and now I am almost going to buy a nvidia card...
Who did ANY ati driver work with dapper, dri enable??

HIS X1600 XT PCIX
kernel amd64 generic... everyone possible
dapper, every possible version
methods: restricted modules, ati with --buildpkg, and ati installer (I reinstalled dapper before everery try)
ASUS A8N-E


PS: By ATI Driver, I mean. ATI's driver
If you didn 't understand the question, I will repeat...
Did anyone got FGLRX driver working for a X1600 XT???

---

### Post by jon_z on 2006-05-31
before you shell out a large sum of money try [Here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")  and go down to the section that says "  ```
 Installing the new driver
```  "

---

### Post by disturbed1 on 2006-05-31
Dapper Flight 5, K7 Kernel, ATI driver from Repo (8.24). x1600 256mb AGP 8x.
3d performance worse than Nvidia fx5500 128 (time demo in UT2004 tested). Several 2d and 3d errors, including artifacting, and tearing. But man, the image quality was good ;) ATI has better looking 2d when compared to Nvidia ***imo***

The closed source ATI drivers are purely sub-standard when compared to Nvidia's offering. Linux gaming sites show an x1800 with much lower performance compared to an Nvidia 6600. ATI drivers are just not mature for linux at this point in time. There are getting better though :)

Of course the ati/radeon xorg driver doesn't work for the x1600 series, we're stuck with vesa.

Run out a buy a cheap $50 Nvidia card, you'll be happy.

---

### Post by jon_z on 2006-05-31
instead of using the ati or radeon driver for xorg, you should be using fglrx...

---

### Post by disturbed1 on 2006-05-31
[QUOTE=jon_z]instead of using the ati or radeon driver for xorg, you should be using fglrx...[/QUOTE]
Not when stability is a concern. Perhaps for older cards fglrx may work ok, but for the newer cards that were added since the 8.24 release (x1###), performance and stability are just bad. 

ATI has the VAR extentions disabled, which cause performance problems, and in worse cause stability problems.

---

### Post by mschievano on 2006-09-13
> **alanrr_sr said:**
> I've tryed everything... and now I am almost going to buy a nvidia card...
Who did ANY ati driver work with dapper, dri enable??

HIS X1600 XT PCIX
kernel amd64 generic... everyone possible
dapper, every possible version
methods: restricted modules, ati with --buildpkg, and ati installer (I reinstalled dapper before everery try)
ASUS A8N-E


PS: By ATI Driver, I mean. ATI's driver
If you didn 't understand the question, I will repeat...
Did anyone got FGLRX driver working for a X1600 XT???

some motherboard to me, same problem.
Ati Asus Eax1600PRO 512 Mb ram. fglrx load (I can write this post) but this error appear:
```

mschievano@mschievano-desktop:~$ fglrxinfo
Error: couldn't find RGB GLX visual!


```

---

