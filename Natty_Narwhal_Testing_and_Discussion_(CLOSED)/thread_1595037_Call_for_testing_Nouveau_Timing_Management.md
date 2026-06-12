---
title: "Call for testing: Nouveau Timing Management"
date: 2010-10-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-10-12
I found this call for testing on Phoronix ([http://www.phoronix.com/scan.php?page=news_item&px=ODY2Nw):](http://www.phoronix.com/scan.php?page=news_item&px=ODY2Nw):)
[QUOTE=Martin Peres]Hi,

Roy Spliet, Emil Velikov and I are working on getting memory timing 
support to nouveau ([http://en.wikipedia.org/wiki/Memory_timings](http://en.wikipedia.org/wiki/Memory_timings)).

We badly need your help as the vbios timing table (that stores the 
timings that should be set when we up/down-clock the memory clocks) 
contains a lot of magic.

If you want to help us, please follow this link:
[http://github.com/pathscale/pscnv/wiki/TestingTimings](http://github.com/pathscale/pscnv/wiki/TestingTimings)

For those who already sent us your info and had a bios table containing 
timing values, please re-read the page, we now also need the strap 
register now (sorry).

Thanking you by advance.

Cheers,

Martin[/QUOTE]

The [_instructions_](http://github.com/pathscale/pscnv/wiki/TestingTimings) are pretty straightforward, you just need to compile a couple of tools (envytools, pgtest, vbtracetool - see the tools' README files for build instructions or just run 'make' if there is no README).

Packages you might need to install for compiling the tools: ```
sudo apt-get install git libpci-dev libpciaccess-dev libxml2-dev cmake flex bison
```

---

### Post by lsmobrian on 2010-10-12
I was missing libxml2-dev which caused errors when compiling envytools

---

### Post by MacUntu on 2010-10-12
Thanks, added it. It's difficult to find out which packages are needed if you already have lots of -dev packages installed.

---

### Post by efflandt on 2010-11-26
It would help if pasted links did not have asterisks in them, for example:

```
git clone git://github.com/pathscale/envytools.git
```

See the README in envytools/ because you first need to use cmake before you can make.  I had to install **cmake**, **flex**, and **bison**.

I sent them the peeks and vbios dumps of my GT 430 = GF108 = NVC1 which is so new that lspci does not show a model for it:

01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)

---

### Post by MacUntu on 2010-11-26
What the heck?

h*******
gith*******
*******

That spam protection (or whatever it is) wasn't there when I wrote the post (I promise).

Anyways, it's:

**git****hub****.com**

> **efflandt said:**
> 
See the README in envytools/ because you first need to use cmake before you can make.

Yeah, seems they moved to cmake in the meantime.

---

### Post by efflandt on 2010-11-27
Who is cariboo907 and why do they break things by inserting astericks?

---

### Post by cariboo on 2010-11-27
> **efflandt said:**
> Who is cariboo907 and why do they break things by inserting astericks?

I'm a moderator, and I was trying to fix your link, which I have done now. The admins have set up word filtering in the hopes of slowing spammers from inundating the forum.

github.com

The problem has been fixed

---

### Post by VMC on 2010-11-27
Yes and I remember when "MacUntu" name was asterisked out. It got fixed somewhere along the line.

---

