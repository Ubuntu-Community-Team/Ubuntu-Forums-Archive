---
title: "Flash Player in FireFox28?"
date: 2014-05-12
forum: Multimedia Software
---

### Post by frank18 on 2014-05-12
Hi guys: anybody knows if Flash player in Ubuntu 14.04 Has been fixed to work right in firefox28,i'm using Google Chrome which flashplayer works good, but i realy would like to use FF instead,

---

### Post by Yellow Pasque on 2014-05-13
Be more specific. Why does/did it not work for you?

---

### Post by Slopsbucket on 2014-05-13
Hi frank18,

There's nothing wrong with your Ubuntu or with Firefox here.

The problem is the company that makes Flash have decided to play a very nasty little game and they are no longer making new versions of FlashPlugin for Linux.

The only real reason I can see is that Macintosh, Microsoft and Google Chrome are all huge supporters of Big Brother as ALL of their software comes with built in spyware to report what you do when and where. Linux respects and protects your privacy and this upsets Adobe so we don't get flash no more. Your Google Chrome uses Flash13 but the latest version you can get for Linux is 11.2

On the bright side - there's a new open source plugin for all web browsers called Shumway that's utilizing the new Html5 protocols to play flash videos without Adobe's software being required. Unfortunately it's still under development and doesn't work with many videos yet but it's moving ahead in leaps and bounds.

I really hope this comes together soon, I like to see recalcitrant companies relegated to the side lines like they deserve. No fancy marketing strategy will save them when this comes through.

Cheers,

Andrew.

---

### Post by Yellow Pasque on 2014-05-13
> **Slopsbucket said:**
> The problem is the company that makes Flash have decided to play a very nasty little game and they are no longer making new versions of FlashPlugin for Linux.

The 11.2.x version still receives security updates and it still works fine on the websites I use, so that's not really a "problem" per se. Again, OP needs to be more specific on what doesn't work.

---

### Post by frank18 on 2014-05-13
> **Slopsbucket said:**
> Hi frank18,

There's nothing wrong with your Ubuntu or with Firefox here.

The problem is the company that makes Flash have decided to play a very nasty little game and they are no longer making new versions of FlashPlugin for Linux.

The only real reason I can see is that Macintosh, Microsoft and Google Chrome are all huge supporters of Big Brother as ALL of their software comes with built in spyware to report what you do when and where. Linux respects and protects your privacy and this upsets Adobe so we don't get flash no more. Your Google Chrome uses Flash13 but the latest version you can get for Linux is 11.2

On the bright side - there's a new open source plugin for all web browsers called Shumway that's utilizing the new Html5 protocols to play flash videos without Adobe's software being required. Unfortunately it's still under development and doesn't work with many videos yet but it's moving ahead in leaps and bounds.

I really hope this comes together soon, I like to see recalcitrant companies relegated to the side lines like they deserve. No fancy marketing strategy will save them when this comes through.

Cheers,

Andrew.


Thanks Andrew; for the great explaintion,i knew something is not right,what i can't understand is only happen after Ubuntu 14.04Long Time Support edition april 17 official release, before that it was OK,i notice this problem on ESPN3,
is there a way of downgrading ffox28 to other lower version that works or this happens now on all versions of firefox?
and if so why the Heck Ubuntu 14.04LTS comes with FIREFOX in it from the Box?.It doesn't make sence to have some browser that doesn't work right.

Also want to add i have Xubuntu 14.04 on an  old Dell Pentium 4 and firefox works great no problem with firefox, that's why i don't understand,is is not  Xubuntu 14.04 from the Linux Ubuntu same software support,

---

### Post by Yellow Pasque on 2014-05-13
> OK,i notice this problem on ESPN3,
**What is the problem?**

---

### Post by frank18 on 2014-05-13
> **Temüjin said:**
> The 11.2.x version still receives security updates and it still works fine on the websites I use, so that's not really a "problem" per se. Again, OP needs to be more specific on what doesn't work.

Thanks Temujin: what doen't work right is just  Video in ESPN3 and some other video streamers sites which video lags every 2  seconds plays and stops,i already reinstalled system and no change,but it's as stated  only on firefox and after 17th ubuntu Long Time Support,

If you want to know my Desktop system is A Lenovo Intel core(tm) I5 2400 CPU  3.10ghz  ,3.8Gib Mem
It has Intel integrated HD 2000 but i've got and run  an ATI AMD 6450 Video Card with fglrx video drivers

---

### Post by Yellow Pasque on 2014-05-13
Have you tried disabling Flash hardware acceleration? (right-click a Flash object and select Settings).

---

### Post by frank18 on 2014-05-13
> **Temüjin said:**
> Have you tried disabling Flash hardware acceleration? (right-click a Flash object and select Settings).

Thanks man i did that on Espn3 but samething, but i've noticed  now  it does lag  after i go with  full screen only

---

### Post by monkeybrain20122 on 2014-05-13
Well it is the same version of flash whatever version of FF you install, and the current version is 29, not 28. I doubt that it has anything to do with it. Maybe you want to try a clean FF profile.

Close all instances of FF. Go to your home, press ctrl+h or choose "show hidden files" and locate the folder .mozilla, rename it to something like .mozilla-old, then start FF and see if it makes a difference. To revert back to the original profile, close FF, go to your home and show hidden files again, delete .mozila and rename .mozilla-old  back to .mozilla

You can also test other versions of FF, download any version from [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/) (or go to parents and find the betas or nightly)
extract the tar ball, go to the extracted folder and click firefox, that's it. You may want to do it with a clean profile as described above (close all Firefox instances and rename .mozilla before you click)

---

### Post by frank18 on 2014-05-13
> **monkeybrain20122 said:**
> Well it is the same version of flash whatever version of FF you install, and the current version is 29, not 28. I doubt that it has anything to do with it. Maybe you want to try a clean FF profile.

Close all instances of FF. Go to your home, press ctrl+h or choose "show hidden files" and locate the folder .mozilla, rename it to something like .mozilla-old, then start FF and see if it makes a difference. To revert back to the original profile, close FF, go to your home and show hidden files again, delete .mozila and rename .mozilla-old  back to .mozilla

You can also test other versions of FF, download any version from [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/) (or go to parents and find the betas or nightly)
extract the tar ball, go to the extracted folder and click firefox, that's it. You may want to do it with a clean profile as described above (close all Firefox instances and rename .mozilla before you click)

Thanks Bro: that seems to be a lot of work and i like the easy way,so i keep Chrome instead,what i wonder is that this crap with fire fox only happen after Ubuntu Lts 17th April,before that i've run on same computer ubuntu 12.04, then 13.10,then 14.04 thar and none of these  ever happened,only when they made Ubuntu14.04 official release,i have xubuntu 14.04 and never had this either.I still believe Ubuntu people trying to fix other stuff that  have messed big time,it's not only me complaining there are other people saying there  are big bugs,what is pretty shame, this is primitive stuff

---

### Post by Yellow Pasque on 2014-05-13
So have you tried running a different desktop on the problematic system? (You can use lxde if you want something light/small). It's possible that it something specific to Unity/Compiz.

---

### Post by frank18 on 2014-05-13
> **Temüjin said:**
> So have you tried running a different desktop on the problematic system? (You can use lxde if you want something light/small). It's possible that it something specific to Unity/Compiz.

Thanks Temujin: i run desktop gnome2 flashback (metacity) but also get the same issue with Unity
unless i remove Unity and only run Gnome2 flashback! is that possible in ubuntu 14.04?

---

### Post by frank18 on 2014-05-14
Hi guys: today i installed xubuntu in this intel I5  machine and you know what i don't have the lagging problem now;
i guess the problem is Ubuntu 14.04 for sure,so i keep this xubuntu for now

---

