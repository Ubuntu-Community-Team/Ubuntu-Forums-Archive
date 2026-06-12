---
title: "Upgrade to 11.04 ? problems"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MadMonkey1966 on 2011-04-15
Today i upgraded to  Ubuntu 11.04 "Natty Narwhal" Beta 2 from Maverick. This is the first time i have ever tried to do it, but it seemed simple, in fact the whole process was....UNTIL

it finished upgrading, and rebooted. On starting up, it told me my hardware was not compatible with unity (i think) and i would have to use the old desktop.
Can anyone tell me what is incompatible, and if there is anything i can do about it ? OR at least find out what the problem is ?

Also (i am guessing its related) i just went into Thunderbird to check my email, and all my accounts, folders and mail have gone, although the address book is still there. Luckily i had only re-installed it last week, as my old email addy had been harvested, so i set up 3 new ones. So no major problem for me, BUT maybe others if there is a bug of some sort.

Thats 2 issues i have found in only a short time. Anyone any ideas..... ??

Still wont be going back to Windows ;)

---

### Post by nerdy_kid on 2011-04-15
Unity needs compositing (desktop effects) to run, unless you use the 2D version.  (You can download unity-2d from the software center)  To get the 3D version working:  first, what graphics card do you have?  To find this out, please run
```

lspci | grep VGA

```
and post the output

---

### Post by MadMonkey1966 on 2011-04-15
Thanks for the quick reply, done what you said and got this.

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by MadMonkey1966 on 2011-04-15
also just to add, Firefox now keeps crashing, and the graphics are very bitty (hard to explain really)

---

### Post by uRock on 2011-04-15
Moved to Natty Narwhal Testing & Discussion.

---

### Post by Duncan Williams on 2011-04-15
If anyone is wondering why I am posting this previous post excerpt is that some boot problems are video card driver related:

---------------------------------------

[I]No proprietory drivers after last install of natty.
I was advised in additional drivers of:
experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.[/I]

----------------------------------------

---

### Post by uRock on 2011-04-15
> **Duncan Williams said:**
> <snip>
The OP has an Intel, not nVidia, chip set.

---

### Post by Duncan Williams on 2011-04-15
As stated - it could be video card driver related.
as in/ may affect intel or ati etc.

---

### Post by kansasnoob on 2011-04-16
I don't think there is a "list" of supported hardware but you might want to read the release notes:

[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

But Compiz, which Unity relies on, is super demanding on resources!

Since Unity is not supported with your hardware you could try the package "unity-2d" and then select that DE option at login.

There is also a unity-2d ppa:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

Just be prepared for breakage ;)

---

### Post by MadMonkey1966 on 2011-04-16
Thanks everyone :D

Now i am more confused, i have only been using Ubuntu for 3 months, and this is a bit above me.

So, i am thinking that i have out of date hardware, and there is nothing i can do, apart from try some stuff they may or may not work.

And i guess the reason Firefox keeps crashing now, and i have lost everything in Thunderbird is all part of the same thing, though i dont know how graphics should effect my Thunderbird folders etc....

So, is here any easy way to go back to 10.10 and stay there, i had no problems with that.

---

### Post by dino99 on 2011-04-16
Dont worry

open synaptic (top menu: system admin synaptic) and:
- remove/purge (right click): ubuntu-desktop
- remove/purge compiz
- remove/purge unity

then reboot, you will get the "classic" gnome desktop

---

### Post by MadMonkey1966 on 2011-04-16
Yay, you are a star :D

So what will i have to do if i ever want to use unity etc... is it a new graphics card ?

Also all folders, emails etc.. have returned in Thunderbird...now that is weird, how could that be a graphic problem?

---

### Post by dino99 on 2011-04-16
about unity:
- as unity3d need compiz, which is actually too buggy, and your graphic card seems not able to run it, the solution is unity2d because it dont need compiz. So from synaptic you can try & install unity-2d.

- about thunderbird i cant answer as i dont use it

---

### Post by MadMonkey1966 on 2011-04-16
Thanks, i will give it a go and see :)

---

