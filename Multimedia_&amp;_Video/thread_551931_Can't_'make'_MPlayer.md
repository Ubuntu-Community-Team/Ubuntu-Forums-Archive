---
title: "Can't 'make' MPlayer"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by K3l3v on 2007-09-15
I downloaded MPlayer, the codecs, and the gui from mplayerhq.hu.  I followed the tutorial to ./configure MPlayer.  Downloaded all of the .dev files that aren't automatically installed.  Finally got the ./config to work.  But, I cannot 'make' or 'make install' MPlayer.

I have already searched through the Ubuntu forums for this problem.  Ran into a bunch of 'why didn't you just "apt-get" MPlayer' comments.  Tried getting MPlayer through 'apt-get', but could not.  Got:

caleb@Virchow:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

Made sure that I had all the universes, multiverses, and whatever else selected.  Got the same response.

Need help.

---

### Post by Bachstelze on 2007-09-15
Could you please paste your sources.list ?

---

### Post by K3l3v on 2007-09-15
> **HymnToLife said:**
> Could you please paste your sources.list ?

Gladly.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by Bachstelze on 2007-09-15
You don't have multiverse. Add multiverse at the end of those two lines :

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

Like this :

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Then

```
sudo apt-get update && sudo apt-get install mplayer
```

---

### Post by K3l3v on 2007-09-15
Thank you!  It is now installed.

As an aside, if the ./config had gone correctly, it should have made a make file, correct?

---

### Post by Bachstelze on 2007-09-15
> **K3l3v said:**
> 
As an aside, if the ./config had gone correctly, it should have made a make file, correct?

Correct.

---

### Post by K3l3v on 2007-09-15
Again, thank you very much!

I hate those darn, PEBKAC errors.

---

