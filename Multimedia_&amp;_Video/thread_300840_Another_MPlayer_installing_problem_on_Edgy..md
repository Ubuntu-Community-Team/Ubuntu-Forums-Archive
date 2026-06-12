---
title: "Another MPlayer installing problem on Edgy."
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by rich.bae on 2006-11-16
Hi, there.
Yes, I know there are so many posts about mplayer problem.
But, there is no any post can help me.

Please, help me. I need mplayer now.
My error message and source.list likes below.

> 
root@rich-desktop:~# apt-get install mplayer
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
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libungif4g (>= 4.1.3) but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages


> #deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
#deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-updates main universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-updates main universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-backports main universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy-backports main universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main universe multiverse

#deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
#deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
#deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
#deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy

#deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm

# for csh
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
      


---

### Post by rich.bae on 2006-11-16
Oops!, sorry. I was a fool.

I made comment first two lines having edgy main repos.

> #deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

They were mandatory, whatever I do.
After uncomment them, Everything goes alright. :KS

---

