---
title: "different version of restricted and image in synaptic -FATAL: module nvidia not found"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by Stevko on 2006-07-22
When I tried to install nvidia drivers after restarting I got error "FATAL: module nvidia not found" and X did not start. I searched web and forums and found what was probably wrong (I am quite sure, since it works now). linux-restricted-modules was diferent version than linux-image. When I tried to run
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
I got error that package cannot be found. After I searched for correct package on the internet it worked. However, today I updated system (automatic updates) and linux-image was updated to linux-image-2.6.15-26-k7 and linux-restricted-modules were not. And again there was same error (FATAL...). I found restricted package on packages.ubuntu.com. However I had to download it again by hand, because apt-get did not find it. (everything works again). How can I prevent this happening in future? I do not want  to download restricted package after every update of linux-image.
(I think content of /etc/apt/sources.list can help you reply, so I attach it here.)
```


# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src http://sk.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://sk.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://sk.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://sk.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://sk.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper main universe restricted multiverse

deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

```

---

