---
title: "Vlc 1.0.0"
date: 2008-10-14
forum: Multimedia Software
---

### Post by marshalldragon on 2008-10-14
Hi there folks,

Quite new to Linux etc but a quick learner I think.

Trying to install latest VLC via synaptic package manager and some dependancies not working:

 sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.0~git20081012-1) but it is not going to be installed
       Depends: libcaca0 (>= 0.99.beta15-1) but 0.99.beta13b-4 is to be installed
       Depends: libqtcore4 (>= 4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
       Depends: libqtgui4 (>= 4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
E: Broken packages


Does this mean that the repositories are not yet up to date with necessary info or is my Ubuntu setup broken in some way.

I guess its also a more general question about new packages and what one should expect in terms of dependencies.

cheers in advance.

---

### Post by xc3RnbFO8P on 2008-10-14
In Synaptic Package Manager:

Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all

---

### Post by marshalldragon on 2008-10-15
Thanks Ringi,

however I already have all options checked, except for the Gutsy Gibbon CDROM option which fails to find links anyway and makes no difference ( if 'links' is what you call them ) 
:confused:

---

### Post by mc4man on 2008-10-15
Looks like your trying to install a nightly build meant for Intrepid.  (8.10)
At this point if that's what you want (latest unstable) you'll need to compile the source yourself.

---

### Post by marshalldragon on 2008-10-16
Thanks mc4man,

I did not intend to do that. I was just going off of the VLC website instructions.
I am running 8.04 (Hardy Heron right ?) and I just wanted to run the latest stable version I guess.
Therfore should I remove the Nightly repository link from my package manager ?

Perhaps I should learn how to compile the source myself, but I do not wish to be too 'bleeding edge' just yet.

---

