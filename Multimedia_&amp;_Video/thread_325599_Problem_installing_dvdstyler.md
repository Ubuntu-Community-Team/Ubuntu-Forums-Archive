---
title: "Problem installing dvdstyler"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by SBFC on 2006-12-26
Hello all, I'm having a problem installing dvdstyler from the repos. When I perform 'sudo apt-get install dvdstyler' I receive the following error:

```

  dvdstyler: Depends: mjpegtools but it is not installable
E: Broken packages

```

An "apt-cache search mjpegtools" listed "libmjpegtools0c2a" and I installed it but I still receive the same error when trying to install dvdstyler.

Any ideas?

Thanks.

---

### Post by IanW on 2006-12-26
mjpegtools is in the Multiverse repository.

---

### Post by SBFC on 2006-12-26
In my sources file I have the Multiverse lines uncommented...

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

```

Unless there are additional lines I don't have in my sources file.

Also, as mentioned before an apt search for 'mjpegtools' yields 'libmjpegtools0c2a', and I have it installed but I still receive the error.

---

### Post by DarkN00b on 2006-12-26
> **SBFC said:**
> Hello all, I'm having a problem installing dvdstyler from the repos. When I perform 'sudo apt-get install dvdstyler' I receive the following error:

```

  dvdstyler: Depends: mjpegtools but it is not installable
E: Broken packages

```

An "apt-cache search mjpegtools" listed "libmjpegtools0c2a" and I installed it but I still receive the same error when trying to install dvdstyler.

Any ideas?

Thanks.

Open Synaptic and click Edit=>Fix Broken Packages. That should fix your problems.

---

### Post by SBFC on 2006-12-26
> **DarkN00b said:**
> Open Synaptic and click Edit=>Fix Broken Packages. That should fix your problems.

Isn't that the same as performing an "apt-get -f install"?

---

### Post by DarkN00b on 2006-12-26
Honestly I don't know. I haven't used "apt-get -f install" before. I just know that the Synaptic repair thing fixes broken packages if it can.

---

### Post by SBFC on 2006-12-26
I did an 'apt-get -f install' and it didn't seem to help. I'll try the Synaptic method when I get home and see if that affects anything.

---

### Post by SBFC on 2006-12-26
I just downloaded the 'mjpegtools' package from the 'Ubuntu Packages' page...and used dpkg to install it. After that dvdstyler installed fine.

What I can't figure out is why the mjpegtools package wouldn't show up when I searched Synaptic/apt-get for it.

*shrugs*

---

### Post by DarkN00b on 2006-12-26
I don't know why either. When I searched Synaptic I found it no problem.

Anyway, I'm glad you got it to work!

---

### Post by SBFC on 2006-12-26
Would you mind posting your sources.list file so I can compare?

---

### Post by DarkN00b on 2006-12-27
Sure, here it is:

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.lupine.me.uk edgy main
deb http://beryl-mirror.pricechild.co.uk edgy main

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

#AUTOMATIX REPOS END

```

---

### Post by SBFC on 2006-12-27
Thanks man, the repo I didn't have that includes mjpegtools is

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

```

Where'd you get the AUTOMATIX repos? Or find out about them I guess. Somewhere on the forum?

---

### Post by DarkN00b on 2006-12-27
I got them from the Automatix website. I followed a link (to the wiki I think - its been a while :) ) from there. Update manager keeps me up to date on the latest version. Same with Beryl.

---

