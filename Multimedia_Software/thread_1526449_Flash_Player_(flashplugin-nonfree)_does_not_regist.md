---
title: "Flash Player (flashplugin-nonfree) does not register clicks in 10.04"
date: 2010-07-08
forum: Multimedia Software
---

### Post by WinstonChurchill on 2010-07-08
The Adobe Flash Player plugin for Firefox (packages "flashplugin-installer" and "flashplugin-nonfree") plays videos and other content absolutely fine, but it refuses to register any mouse clicks at all, even in the "settings" menu. This is obviously more than a little annoying - not only does it make YouTube and the like almost totally unusable, it also effectively breaks any website that uses SWF content as menus.

I've purged and reinstalled Firefox and the flash plugin multiple times to no avail - I had hoped that the recent update would fix this issue, but alas, it did not. I'm using SwfDec right now, which works, but is pretty terrible compared to the real thing. Gnash isn't any better...

So... has anybody else encountered this problem? Any help would be greatly appreciated.

---

### Post by lozt.again on 2010-07-08
I am having this problem too and have tried the same things as you. That's the limit of my knowledge. It works occasionally, but I have to click like 5/6 times in quick succession to register one click. Youtube work is just, well, a pain.

---

### Post by cchhrriiss121212 on 2010-07-08
It's a compiz problem, disable or remove it.

---

### Post by ias2 on 2010-07-08
Hi,

  most problems related to Flash and Firefox vanishes using Chrome or Opera. Anyone knows why?

---

### Post by WinstonChurchill on 2010-07-08
> **cchhrriiss121212 said:**
> It's a compiz problem, disable or remove it.
BRILLIANT! Thank you!

**EDIT: **Just to clarify what I removed:
```
$ sudo aptitude purge compiz
$ sudo aptitude purge compiz-gnome
$ sudo aptitude purge compiz-core
```Works just fine now. Removing those packages didn't effect anything else on the system.

---

### Post by lozt.again on 2010-07-09
I use desktop cube and various other compiz settings... surely this will get rid of those to?

---

### Post by unperson on 2010-07-09
I was also having the problem that flash would not register my mouse clicks, and I am not running compiz (Appearance->Visual Effects is set to none), so the above solution is not applicable.  However, I found a solution that does seem to work for me (and maybe it will help people use both flash and compiz simultaneously): [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html]("http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html")

---

### Post by cchhrriiss121212 on 2010-07-09
> **lozt.again said:**
> I use desktop cube and various other compiz settings... surely this will get rid of those to?
Yes. There should be ways to get around this (as unperson shows) but I don't remember exactly what settings cause the issue.

---

### Post by lovinglinux on 2010-07-09
> **unperson said:**
> I was also having the problem that flash would not register my mouse clicks, and I am not running compiz (Appearance->Visual Effects is set to none), so the above solution is not applicable.  However, I found a solution that does seem to work for me (and maybe it will help people use both flash and compiz simultaneously): [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html]("http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html")

This usually happens when you are using the 32bit plugin on a 64bit system. That fix solves the problem.

---

### Post by lozt.again on 2010-07-12
> **cchhrriiss121212 said:**
> Yes. There should be ways to get around this (as unperson shows) but I don't remember exactly what settings cause the issue.

Luckily for me I'm using 64bit, so, whoopy!!!! Solved!

Really didn't want to get rid of those compiz desktop effects and such.

---

