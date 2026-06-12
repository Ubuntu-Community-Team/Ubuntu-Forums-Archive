---
title: "trouble installing vlc (kubuntu)"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by ziploc67 on 2008-02-22
Just today, I installed Kubuntu. Everything worked fine until I needed to install vlc. In the Adept Package Manager, I searched for the package vlc, but to no avail. I also tried installing it via the Konsole, by typing "sudo apt-get install vlc" but that did not work either. What am I doing wrong, and is there a way to fix it?

---

### Post by kaens on 2008-02-22
Could you post the file /etc/apt/sources.list?

---

### Post by ziploc67 on 2008-02-22
Alright, I attached the file using the Manage Attachments, but, in case that didn't work, here is what my sources.list says:

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by kaens on 2008-02-22
remove the #s from all the lines that start with deb (not necessarily deb-src) with

```
 sudo nano /etc/apt/sources.list
``` 

you'll probably want to add a # at the first line that says deb cdrom

then run:

```

sudo apt-get update
sudo apt-get install vlc

```

what probably happened here is that you installed without being connected to the internet. this file is used by apt and synaptic, aptitude etc. to tell them where to look for for packages. a # means "ignore the rest of this line"

---

### Post by ziploc67 on 2008-02-22
thank you so much!

---

### Post by ziploc67 on 2008-02-22
by the way, what is the difference between "deb" and "deb-src"?

---

### Post by kaens on 2008-02-22
the deb-src packages contain the source code for the programs. If you want to modify a program in the repository, or compile it optimized for use on your machine you could get packages from the deb-src repositories.

---

### Post by ziploc67 on 2008-02-22
thanks again! where do you learn all of these things about kubuntu and linux in general, or does it come with experience, or both?

---

### Post by kaens on 2008-02-23
My pleasure!

I'm no guru - it's a constant learning process. I've been using linux for around 5 years now, and I'm a programmer.

When I first started out, I found [RUTE]("http://rute.2038bug.com/index.html.gz") to be of a great help. Also, [tldp]("http://tldp.org/"). I couldn't get X to work for a long time, and got comfortable with the bash shell as a result - which I reccommend.

The command "apropos" is your best friend. "apropos x" will give you commands related to x. Then "man" for looking up documentation, e.g. "man apropos" will give you documentation for apropos. 

"man bash" sometime - it's a lot of info to absorb, but some of it is simply amazing.

I hosed my computer a few times. If you look at my recent posts, I somehow managed to cause a very strange audio / video glitch that I've never seen before.

All in all, it's a matter of exploration, searching, fiddling around, and asking fo (and giving) help. The ubuntu IRC channels are highly recommended.

On the other hand, if you don't want to spend a lot of time learning all kinds of esoteric stuff, linux is rapidly becoming usable without such knowledge. I'd practically argue that it's there now, especially compared to how it was 5 years ago. When I started using linux, ubuntu barely existed, and if you weren't a coder, you would probably have no luck at all.

But yeah. Constant learning. Taking notes helps too.

---

### Post by ziploc67 on 2008-02-24
thanks yet again, i will be taking notes! i ditched windows about 2 months ago because i was tired of having to deal with all of the anti-malware. i would like to become proficient in linux, and you have helped me lots.

---

### Post by TE7 on 2008-02-25
Couldn't get totem to play DVDs in gutsy with anything I tried. This post solved my problem. Thanks a heap! VLC works great.

---

