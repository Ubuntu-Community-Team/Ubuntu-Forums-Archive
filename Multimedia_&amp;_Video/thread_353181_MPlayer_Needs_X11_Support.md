---
title: "MPlayer Needs X11 Support"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by ktm5124 on 2007-02-04
I just installed mplayer without any configure options set and it installed fine. But then when I tried playing a .wmv I realized that I needed to enable the GUI in ./configure. So I entered ./configure --enable-gui and it said "Error: Needs x11 support". I've tried looking for all the x11 packages in my Synaptic Package Manager and by using apt-get install but none of them provide that "x11 support" that mplayer needs. I read in another post that you need x-window-system-dev, and when I tried apt-get'ing that it said it could not find it. 

My /etc/apt/sources.list file looks like this:

```

andrew@roflbirds:~/Desktop$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse
deb http://security.ubuntu.com/ubuntu/ dapper multiverse

```

Anyone have any ideas as to how I can get x11 support and ultimately get MPlayer working for windows media videos?

---

### Post by taurus on 2007-02-04
You know that mplayer is in the repos, right.

[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

---

