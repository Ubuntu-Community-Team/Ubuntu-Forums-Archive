---
title: "Inkscape 0.47 for Ubuntu 9.04"
date: 2009-12-15
forum: Multimedia Software
---

### Post by Joseph Schwenker on 2009-12-15
Where can I find a .deb of Inkscape 0.47 for Ubuntu 9.04?  I HATE Karmic, and am angry that applications like Gwibber and Inkscape are outdated in Ubuntu 9.04.  Is there any simple way to install Inkscape 0.47 in Ubuntu 9.04?  I AM NEVER UPGRADING to Karmic.  EVER.  Maybe 10.04 will be better, but 9.10 SUCKS.

---

### Post by Andrew_P on 2009-12-16
> **Joseph Schwenker said:**
> Where can I find a .deb of Inkscape 0.47 for Ubuntu 9.04?  ...  Is there any simple way to install Inkscape 0.47 in Ubuntu 9.04?

I found the package at [http://packages.debian.org/unstable/graphics/inkscape](http://packages.debian.org/unstable/graphics/inkscape).

I downloaded the i386 installer for Inkscape 0.47 and ran the package installer on it (right-click on the .deb file icon and select 'Open with "GDebi Package Installer"' from the context menu). Simple enough.

However ...

I'm running Ubuntu 8.10 (Intrepid Ibex) and the installation _failed_.:(  The installer reported that it was unable to satisfy dependencies for libgconf2-4.  I manually installed libgconf2-4 with the Synaptic Package Manager, but it's still no-go.  I'd like to see what was improved in Inkscape 0.47, but until this problem is resolved by the Inkscape team, it's not possible.  I reinstalled release 0.46.  I'm *not* going to change to another release of Ubuntu now or set up another instance on a spare hard drive just to test Inkscape 0.47; the Inkscape team needs to fix whatever is wrong with the package.  (It seems only every second or third release of Ubuntu works and the rest are duds, as was 9.04 and, from what I read, 9.10.)

If someone knows how to get around this problem so that Inkscape release 0.47 can run on Ubuntu 8.10, please chime in.

---

### Post by Andrew_P on 2009-12-16
> **Andrew_P said:**
> If someone knows how to get around this problem so that Inkscape release 0.47 can run on Ubuntu 8.10, please chime in.

My lack of experience is showing.](*,)

I read the fine print at the top of [http://packages.debian.org/sid/i386/libgconf2-4/download](http://packages.debian.org/sid/i386/libgconf2-4/download) regarding the suggestion that one use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via the website.  OK -- so, I ran the Software Sources tool under System -> Administration, and added ```
deb http://ftp.us.debian.org/debian sid main
``` to the list of sites, then ran System -> Administration -> Synaptic Package Manager.  Inkscape 0.47 has now replaced Inkscape 0.46 in the list of installable packages.  However, when the Package Manager examines the dependencies, it lists *dozens* of packages that need to be removed, installed or upgraded.  Over *four dozen* of the packages are categorized as "CANNOT BE AUTHENTICATED".  It looks like Inkscape 0.47 will probably install, should I proceed, but since I'm using my current installation for some serious work, there's a chance that I may seriously hose it.  If you feel game, Joseph, and can afford to jeopardize your system, go for it and let us know the outcome!:twisted:

---

### Post by Joseph Schwenker on 2009-12-17
It seems that none of your methods are easy at all.  Why doesn't Canonical keep their repositories updated?!  It makes it IMPOSSIBLE for users who actually want A STABLE SYSTEM to work productively.  Why wasn't 9.04 made an LTS?  It is the fastest and stablest yet!  9.10 sucks!

---

### Post by lukjad on 2009-12-17
> **Joseph Schwenker said:**
> It seems that none of your methods are easy at all.  

This is your opinion, I suppose depending what comfort level you have with Ubuntu, this may or may not be a valid comment.

> **Joseph Schwenker said:**
> Why doesn't Canonical keep their repositories updated?!  It makes it IMPOSSIBLE for users who actually want A STABLE SYSTEM to work productively.  

I haven't noticed anything wrong with the Jaunty Repositories. Every 30 days or so I get security updates. Now, I notice you mentioned something called a "stable system". Well, Debian is stable, let's look at them.

As per [this page]("http://packages.debian.org/search?keywords=inkscape"):

lenny (stable) (graphics): vector-based drawing program 
0.46-2.lenny2: alpha amd64 arm armel hppa i386 ia64 mips mipsel powerpc s390 sparc 

So the **stable** version of Debian is using the 0.46 version of inkscape... Interesting. So the stable releases use older software. 

The point I am trying to make is that if you want a simple stable system, there has to be a certain causion when pushing new software so as to not lose the stability.

> **Joseph Schwenker said:**
> Why wasn't 9.04 made an LTS?  It is the fastest and stablest yet!  

It was not made an LFS because it came out at the wrong time, 8.04 is the LFS.

> **Joseph Schwenker said:**
> 9.10 sucks!

Thank you for that review, I'll keep that in mind. But wait, that has new software, new file systems, and a new them. Maybe that's why it's not as stable as 9.04?

---

### Post by Joseph Schwenker on 2009-12-19
> **lukjad007 said:**
> This is your opinion, I suppose depending what comfort level you have with Ubuntu, this may or may not be a valid comment.



I haven't noticed anything wrong with the Jaunty Repositories. Every 30 days or so I get security updates. Now, I notice you mentioned something called a "stable system". Well, Debian is stable, let's look at them.

As per [this page]("http://packages.debian.org/search?keywords=inkscape"):

lenny (stable) (graphics): vector-based drawing program 
0.46-2.lenny2: alpha amd64 arm armel hppa i386 ia64 mips mipsel powerpc s390 sparc 

So the **stable** version of Debian is using the 0.46 version of inkscape... Interesting. So the stable releases use older software. 

The point I am trying to make is that if you want a simple stable system, there has to be a certain causion when pushing new software so as to not lose the stability.



It was not made an LFS because it came out at the wrong time, 8.04 is the LFS.



Thank you for that review, I'll keep that in mind. But wait, that has new software, new file systems, and a new them. Maybe that's why it's not as stable as 9.04?

Actually, it's because of the "faster shutdown time" which, combined with PulseAudio, leads to data loss, application loss, and overall frustration.  Inkscape 0.47 is stable, and Canonical is not updating the version for the last stable release.  9.10 is not stable.  9.04 is.

---

### Post by lukjad on 2009-12-20
My point is that 9.10 is trying new stuff. And something that may be stable in one environment may not be stable in others, or may not be as secure. 9.04 is older, so it will have older programs, that is a given.

---

### Post by Mazin on 2009-12-20
They're trying to point out the irony of you sticking to an older operating system while complaining about older software on said older operating system.

Anyways, add this PPA if you want cutting-edge Inkscape builds: [https://launchpad.net/~inkscape.testers/+archive/ppa](https://launchpad.net/~inkscape.testers/+archive/ppa)

---

### Post by lukjad on 2009-12-20
Thank you for putting it so well.

---

### Post by Joseph Schwenker on 2009-12-20
> **Mazin said:**
> They're trying to point out the irony of you sticking to an older operating system while complaining about older software on said older operating system.

Anyways, add this PPA if you want cutting-edge Inkscape builds: [https://launchpad.net/~inkscape.testers/+archive/ppa](https://launchpad.net/~inkscape.testers/+archive/ppa)

That's like saying that I'm complaining about older software on XP (old), and not Vista (new).  Karmic is like Vista; unstable.  Thanks for the PPA, though!  That solved my problem!

---

