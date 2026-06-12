---
title: "Mac Ports + Darwin + Gnome"
date: 2008-02-16
forum: Mac OSX
---

### Post by DarkZyzx on 2008-02-16
I was wondering if anyone has tried or has seen the Mac OS X kernel (Darwin) used as the base for a UNIX system. I mean only Darwin. And then Mac Ports installed on it, using Gnome or KDE or Xfce or e17 as the DE / WM. Would this create some kind of new BSD or Linux type OS or distro? 

If anyone wants to try it please tell me how it goes.  :popcorn:
 I think I am going to try it.
:guitar:

---

### Post by hanzomon4 on 2008-02-16
MacPorts sucks.... 

Mostly everything fails to build so something like Gnome seems like a lost cause.

---

### Post by DarkZyzx on 2008-02-16
I found something called GNU-Darwin Distribution, and it seems to be something similar to what I am describing. I am going to download this now. If you have any info on this too, that would be even more helpful. Thanks. :popcorn:

---

### Post by DarkZyzx on 2008-02-16
bump

---

### Post by smartboyathome on 2008-02-17
I don't have info on it, but it looks interesting. I may try it out on my desktop. :)

---

### Post by handy on 2008-02-17
I have been wondering if anyone had done this yet.

I'm not personally interested in doing it, I can see the potential for a LOT of time to go in for an unacceptable result.

I hope I'm wrong too... :lolflag:

---

### Post by DarkZyzx on 2008-02-17
I have been looking for screenshots on this gnu-darwin project.....

Most of the screenshots I have discovered are hideous and cluttered.
I found one that closely resembled Ubuntu... I have no idea how this one looks ok, while the others look horrible...

Please someone tell me what it looks like.

---

### Post by pdusen on 2008-02-17
[http://upload.wikimedia.org/wikipedia/commons/b/bf/Distro-1.1-gnome.png](http://upload.wikimedia.org/wikipedia/commons/b/bf/Distro-1.1-gnome.png)

It just "looks like" whatever desktop environment you use... that one uses Gnome, for example.

---

### Post by handy on 2008-02-17
> **DarkZyzx said:**
> I have been looking for screenshots on this gnu-darwin project.....

Most of the screenshots I have discovered are hideous and cluttered.
I found one that closely resembled Ubuntu... I have no idea how this one looks ok, while the others look horrible...

Please someone tell me what it looks like.

Darwin, is like basically BSD.  So think of it as the kernel that you have to add a desktop & other software to if you desire.

BIG job actually.

Makes me think of installing Gentoo... but very likely more difficult in the extreme. :lolflag:

---

### Post by tgalati4 on 2008-02-17
I'm not sure of the benefit of doing this.  On the Mac, Darwin (a BSD derivative) runs on top of the Mach kernel.  The tasty bits of OSX are Cocoa, Aqua, and Quartz, proprietary graphical engine, themes, and compositing engine that make the totality of OSX.  Darwin is certainly rock-solid, as is BSD.  The Mach kernel is a carry-over from BEOS and the Next-Step computers.  I'm not sure how it stacks up against the Linux kernel.

You can run Gnome on top of OSX using XDarwin.  I do it all the time, and the perfomance is not bad.  So basically you have an untouched OSX running, and in a separate workspace you have Gnome and it's applications.  They run side-by-side just fine.  Haven't tried KDE yet.

---

### Post by handy on 2008-02-17
> **tgalati4 said:**
> I'm not sure of the benefit of doing this.  On the Mac, Darwin (a BSD derivative) runs on top of the Mach kernel.  The tasty bits of OSX are Cocoa, Aqua, and Quartz, proprietary graphical engine, themes, and compositing engine that make the totality of OSX.  Darwin is certainly rock-solid, as is BSD.  The Mach kernel is a carry-over from BEOS and the Next-Step computers.  I'm not sure how it stacks up against the Linux kernel.

You can run Gnome on top of OSX using XDarwin.  I do it all the time, and the perfomance is not bad.  So basically you have an untouched OSX running, and in a separate workspace you have Gnome and it's applications.  They run side-by-side just fine.  Haven't tried KDE yet.

That sounds like a sensible way to go about it.  I think building the system up from scratch would be only for those highly skilled who enjoy spending the days doing such a thing, & don't mind if it is useless in the end! :lolflag:

---

### Post by init1 on 2008-02-17
I tried the Darwin CD once. I'm not sure if it didn't recognize my hard drive, or if I wasn't doing it right.

---

### Post by handy on 2008-02-18
> **init1 said:**
> I tried the Darwin CD once. I'm not sure if it didn't recognize my hard drive, or if I wasn't doing it right.

At least Gentoo gives fantastic help for installation & other processes, on their web site.  Which is just as well... :lolflag:

---

### Post by DarkZyzx on 2008-02-23
So... GNU-Darwin is for people who want to build their own operating system....??
:confused:
Or what?

---

### Post by hanzomon4 on 2008-02-23
Try this [FaQ]("http://www.gnu-darwin.org/index.php?page=faq-general#1")

---

### Post by K.Mandla on 2008-02-23
Moved to Mac OSX subforum, which seemed like the best idea at the time.

---

### Post by smartboyathome on 2008-02-23
So, just wondering, but is there a way to port drivers from Linux to Darwin, like with (for example) e17? I would like to see if darwin would run on my laptop, but it requires the ipw3945 driver for internet.

Also, running darwin on a non-apple laptop is legal, right?

---

### Post by justin whitaker on 2008-02-24
> **smartboyathome said:**
> So, just wondering, but is there a way to port drivers from Linux to Darwin, like with (for example) e17? I would like to see if darwin would run on my laptop, but it requires the ipw3945 driver for internet.

I thought it was more like: linux>bsd>darwin. You can't just straight port Linux drivers to Darwin, because BSD and Linux are just different enough to make that difficult. There are also subtle differences between BSD and Darwin which amp up the difficulty a bit.

> Also, running darwin on a non-apple laptop is legal, right?

Yeah, it's open source isn't it? :)

---

### Post by LaRoza on 2008-02-24
> **justin whitaker said:**
> I thought it was more like: linux>bsd>darwin. You can't just straight port Linux drivers to Darwin, because BSD and Linux are just different enough to make that difficult. There are also subtle differences between BSD and Darwin which amp up the difficulty a bit.


Linux and BSD are separate, Linux was developed separately, and BSD has (at one point) some of the Unix code.

Linux was inspired by (but didn't use the code of) Minix, which was a ground up rewrite of Unix for learning purposes.

Darwin shares some code with FreeBSD and others. 

They are all Unix type operating systems, yet very separate. Which makes things fun...

[http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg](http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg)

---

### Post by DarkZyzx on 2008-02-24
This timeline thing is really cool, thanks LaRoza! > [http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg](http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg)

Has anyone installed it yet???

---

### Post by handy on 2008-02-24
> **DarkZyzx said:**
> 
Has anyone installed it yet???

We're waiting for you to tell us how it goes?

---

### Post by DarkZyzx on 2008-02-24
Oh, I am having trouble installing it....:( I'll let you know when I get it installed.:)

In the meantime, if any adventurous people want to try it, it wouldn't hurt.
:popcorn:

---

### Post by DarkZyzx on 2008-02-26
:lolflag:
Haha, I found out why I couldn't install the GNU-DARWIN distro.... it uses Darwin OS! Darwin has to be installed first... I have to download and install Darwin and then install the gnu-darwin project! Hope this helps anyone who is also trying this. :)

:popcorn:

---

### Post by molom on 2008-02-27
Does this mean you can use apps such as garage band and imovie on linux?

---

### Post by DarkZyzx on 2008-02-27
I'm not sure.... see the [website]("http://www.gnu-darwin.org")

It installs on Darwin 7 or 8, nothing higher... well maybe. Their website says installs on Darwin 7 or 8...

---

### Post by smartboyathome on 2008-02-28
I know you can install E17 on Mac (and similarly Darwin) using a modified install script based on Marlixus's script. I would think that you would be able to install other programs on there as well with modification.

---

### Post by hanzomon4 on 2008-03-01
> **DarkZyzx said:**
> I'm not sure.... see the [website]("http://www.gnu-darwin.org")

It installs on Darwin 7 or 8, nothing higher... well maybe. Their website says installs on Darwin 7 or 8...

I don't think so, AFAIK OSX is built on top of Darwin and all the OSX apps need the OSX proprietary bits to run. Not all apps but the iLife, professional, and proprietary apps will not run on just Darwin.

---

### Post by hanzomon4 on 2008-03-01
[QUOTE=molom]Does this mean you can use apps such as garage band and imovie on linux?[/QUOTE]

I don't think so, AFAIK OSX is built on top of Darwin and all the OSX apps need the OSX proprietary bits to run. Not all apps but the iLife, professional, and proprietary apps will not run on just Darwin.

Edit: Didn't see Linux in your post, thats a definite no. While both might be Unix like the two systems are very different. Think gui toolkits, the fact that OSX doesn't use X windows(sorta), certain UI elements like menubar... naw. You'd have to get Aqua to run on Linux if you had any hope of running software designed for the Mac OS

---

### Post by DarkZyzx on 2008-03-01
:KS OK, I was able to install Darwin on my PC.... but I cannot install the gnu-darwin project yet. :(

When I turn on Darwin, all it gives me is a console. I log in and the console says: Welcome to Darwin!

Is Darwin just a console??????? :confused:

I'm going to check the site for more help.... :(

---

### Post by molom on 2008-03-02
So if GNU Darwin doesn't work with mac apps. Why all of this discussion? Whats so good about GNU Darwin?

---

### Post by DarkZyzx on 2008-03-02
I don't know, I am just trying to discover how well this will work, and what benefits it might have.

---

### Post by smartboyathome on 2008-03-02
> **DarkZyzx said:**
> :KS OK, I was able to install Darwin on my PC.... but I cannot install the gnu-darwin project yet. :(

When I turn on Darwin, all it gives me is a console. I log in and the console says: Welcome to Darwin!

Is Darwin just a console??????? :confused:

I'm going to check the site for more help.... :(

I think it is just that (very minimal). You need to put it together yourself.

---

### Post by handy on 2008-03-02
Linux is really just a console too.

---

### Post by DarkZyzx on 2008-03-04
> **smartboyathome said:**
> I think it is just that (very minimal). You need to put it together yourself.

How do I "put it together myself"?:confused:

Thanks:popcorn:

---

### Post by smartboyathome on 2008-03-04
You have to compile everything, not sure how though. but I saw someone the other day on E17's IRC channel who compiled E onto Mac (Darwin is the same thing). I think you can use an edited version of Morlinxus' script (ask Rui Pais for a copy of the origional). Ask around on E17's IRC to see how you edit it. Also, check out gnu-darwin, I think some of the packages might be useful to you.

---

### Post by DarkZyzx on 2008-03-04
> **smartboyathome said:**
> You have to compile everything, not sure how though. but I saw someone the other day on E17's IRC channel who compiled E onto Mac (Darwin is the same thing). I think you can use an edited version of Morlinxus' script (ask Rui Pais for a copy of the origional). Ask around on E17's IRC to see how you edit it. Also, check out gnu-darwin, I think some of the packages might be useful to you.
:lolflag:
I started this thread basically about GNU-Darwin..... but thanks.:)

---

### Post by handy on 2008-03-05
> **DarkZyzx said:**
> :lolflag:
I started this thread basically about GNU-Darwin..... but thanks.:)

I would suggest that you would probably get the best help by following the [***_great install instructions for Gentoo_***]("http://www.gentoo.org/doc/en/index.xml?catid=install#doc_chap2").

After which you will have an in depth knowledge of the *nix OS structure, which will certainly make playing with GNU-Darwin somewhat easier, or even put you off the idea all together (as it has done me). ;-)

---

### Post by DarkZyzx on 2008-03-05
> **handy said:**
> I would suggest that you would probably get the best help by following the [***_great install instructions for Gentoo_***]("http://www.gentoo.org/doc/en/index.xml?catid=install#doc_chap2").

After which you will have an in depth knowledge of the *nix OS structure, which will certainly make playing with GNU-Darwin somewhat easier, or even put you off the idea all together (as it has done me). ;-)

Which install instructions? And why did it put you off the idea all together???

---

### Post by Oponium on 2008-03-06
If it's anything like a net install of FreeBSD 7.0, then it should be pretty fun to install.

FreeBSD was one of my happier experiences with a non Microsoft product (up next, my new Mac Mini!).

---

### Post by handy on 2008-03-07
> **DarkZyzx said:**
> Which install instructions? And why did it put you off the idea all together???

They are available [***_here_***]("http://gentoo-wiki.com/Index:HOWTO#Installation_Methods") & this is the [***_Gentoo Handbook_***]("http://www.gentoo.org/doc/en/handbook/index.xml").

If you do a Gentoo build, you may have an idea of what you are getting yourself into, & the Gentoo instructions are fabulous.

I am put off because I don't feel like spending a week building a Darwin system that won't be as good as the one I'm using now.

I could also be wrong! :lolflag:

No value judgment on you or anyone else doing it, go for it & have fun, learn heaps!

---

