---
title: "Cinelerra on 64-bit Edgy"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by The Aa of Ron on 2006-10-25
Has anyone had any luck installing Cinelerra on 64-bit Edgy?  If so, I could use some help.    



Thanks!

---

### Post by pressman57 on 2006-10-25
I got the i386 flavor of cinelerra version 2.0-2 (older version) to install on edgy by going to Rpmfind.net, downloading the RPM, using alien to make a .deb file and installing that.

---

### Post by pressman57 on 2006-10-25
And they do have a 64 bit RPM

---

### Post by The Aa of Ron on 2006-10-25
Thanks!

I'll have to see how that works for me.  Is alien included in the default load of Edgy?  I've never used it.

---

### Post by pressman57 on 2006-10-26
Nosir, you have to sudo apt-get alien, then:

sudo alien cinelerra-2.0-1.whatever.rpm -d

then

sudo dpkg -i cinelerra_2.0-2_whatever.deb

Like I said, it's not the newest version, there's no rpm on their website.

Now that I have cinelerra I'm trying to learn how to use it.

Good luck

---

### Post by The Aa of Ron on 2006-10-26
Thanks!

I'll give it a whirl!

---

### Post by dna_media on 2006-11-02
I have followed these instructions for a very fresh (like 25 minute old) install of Dapper64 (after a week of failure with edgy, I figured I would give dapper a go again.) One of the main reasons I am even using linux is cinelerra. I get the following error when trying to run cinelerra:

cinelerra: error while loading shared libraries: libmp3lame.so.0: cannot open shared object file: No such file or directory

Thoughts. The only thing I apt-get was alien, so I am sure I am missing a bunch of stuff in this fresh install. I have never installed via a deb before, so I didn't even know where I to begin. I decided to just do this install and let the errors lead me to the things I am missing.

Just to clarify, I am running Dapper64 on an Athlon64, fresh install. The only things i have done prior to this install are:

nano xorg.conf for resolution
nano sources.list to enable repos
apt-get update
apt-get alien
and the above instructions.

I use the .rpm seen here: [http://zod.freshrpms.net/rpm.html?id=583](http://zod.freshrpms.net/rpm.html?id=583). It is a week old .rpm for FC6_64 (which I have been attempting to dual boot, but can't get that to work either.) This is the 5th time I have attempted to install cinelerra, 3rd on Ubuntu.

---

### Post by dna_media on 2006-11-02
Ok, I am a relative newbie, and it has been awhile since my last attempt at this. I figured out the lame problem. I changed the following two lines /etc/apt/sources.list from:

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

to:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

```

and then just used synaptic and added all the lame and lame libraries I could find. This fixed my initial problem, but as expected, it brought up another library that I missing. I will keep looking to these errors until I have everything installed that I need. I feel like this should work...

---

### Post by dna_media on 2006-11-02
Well, after finding libfaad and libfaac and installing via Synaptic, I am at a loss trying to find libx264.so.54. I have tried installing via synaptic and by following these howto's:

[http://www.ubuntuforums.org/showthread.php?t=215252](http://www.ubuntuforums.org/showthread.php?t=215252)

The battle continues...

---

### Post by dna_media on 2006-11-02
Success! I found an rpm for x86_64 for x264.so.54. I aliened it up and I have advanced to:

liba52

If I EVER get this to work, I may just wipe my hard drive, do another fresh install and document the process exactly in a post. If anyone ever does get cinelerra to work on 64 bit, they generally disapear into video editing nirvana, or at least never fully explain what voodoo they used...

---

### Post by tuxcantfly on 2006-11-10
if you're having issues with binaries, you could always compile it
[http://ubuntuforums.org/showthread.php?t=215252](http://ubuntuforums.org/showthread.php?t=215252)

---

### Post by fsnk on 2006-11-18
I combined directions and had no problem getting it working, so this might help fixing the missing library issues?

My sources.list looks like this:
```
## MAIN
deb http://se.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

## UPDATES
deb http://se.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS
deb http://se.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

```

Then I did apt-get as specified [here]("http://ubuntuforums.org/showthread.php?t=215252") ( + alien):
```
sudo apt-get install build-essential alien automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

Next, I downloaded the [Cinelerra x86_64 .rpm]("http://downloads.sourceforge.net/heroines/cinelerra-2.0-1.x86_64.rpm?modtime=1128461027&big_mirror=1") from SourceForge. (It's not the most current version, but I didn't want to mess around with compiling it.)

Then I followed pressman57's directions:
```
fs@cthulhu:~$ sudo alien cinelerra-2.0-1.x86_64.rpm -d

fs@cthulhu:~$ sudo dpkg -i cinelerra_2.0-2_amd64.deb
```

That got it working for me on 64-bit Edgy. (Some of the stuff in the apt-get list isn't necessary. I installed it since I wasn't sure if I was going to need to compile it anyway.)

---

### Post by Amurko on 2007-02-10
> **fsnk said:**
> I combined directions and had no problem getting it working, so this might help fixing the missing library issues?

My sources.list looks like this:
```
## MAIN
deb http://se.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

## UPDATES
deb http://se.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS
deb http://se.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

```

Then I did apt-get as specified [here]("http://ubuntuforums.org/showthread.php?t=215252") ( + alien):
```
sudo apt-get install build-essential alien automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

Next, I downloaded the [Cinelerra x86_64 .rpm]("http://downloads.sourceforge.net/heroines/cinelerra-2.0-1.x86_64.rpm?modtime=1128461027&big_mirror=1") from SourceForge. (It's not the most current version, but I didn't want to mess around with compiling it.)

Then I followed pressman57's directions:
```
fs@cthulhu:~$ sudo alien cinelerra-2.0-1.x86_64.rpm -d

fs@cthulhu:~$ sudo dpkg -i cinelerra_2.0-2_amd64.deb
```

That got it working for me on 64-bit Edgy. (Some of the stuff in the apt-get list isn't necessary. I installed it since I wasn't sure if I was going to need to compile it anyway.)

THANK YOU!!!!!

I've struggled for weeks trying to compile Cinelerra 2.1 and even some other alternatives like KDEnlive to no avail..  although it's ver 2.0, doesn't matter..  as long as I can edit video on my 64 bit system I'm cool..

---

### Post by cesera on 2007-04-09
Has anyone tried this:
> Ubuntu packages
    ...
    #ubuntu edgy amd64
    deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
    deb-src [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
from [http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

I am installing it at the moment, will let you know how it works.

---

