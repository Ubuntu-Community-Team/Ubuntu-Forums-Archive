---
title: "ffmpeg troubles in Lucid"
date: 2011-12-30
forum: Multimedia Software
---

### Post by ray field on 2011-12-30
I can't seem to upgrade my FFmpeg:

```
sudo apt-get -f install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/767kB of archives.
After this operation, 2,191kB of additional disk space will be used.
(Reading database ... 349394 files and directories currently installed.)
Unpacking ffmpeg (from .../ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-ipod640.ffpreset', which is also in package libavcodec-extra-52 4:0.5.1-1ubuntu1.2+medibuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried following the directions at 

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

but somehow yasm wasn't installed or something so it fails.  isn't there some easier way than having to recompile ffmpeg?

---

### Post by ron999 on 2011-12-30
> **ray field said:**
> I can't seem to upgrade my FFmpeg:

```
sudo apt-get -f install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/767kB of archives.
After this operation, 2,191kB of additional disk space will be used.
(Reading database ... 349394 files and directories currently installed.)
Unpacking ffmpeg (from .../ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/[COLOR="Red"]ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb[/COLOR] (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-ipod640.ffpreset', which is also in package libavcodec-extra-52 4:0.5.1-1ubuntu1.2+medibuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Looks like you're trying to install FFmpeg from a PPA?

---

### Post by ray field on 2011-12-30
well 

```
raphael@Swann-ubuntu:~$ sudo rm /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb
raphael@Swann-ubuntu:~$ sudo apt-get install ffmpegReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 767kB of archives.
After this operation, 2,191kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/ lucid/main ffmpeg 4:0.9-0ubuntu1~jon5~lucid1 [767kB]
Fetched 767kB in 1s (479kB/s) 
(Reading database ... 349394 files and directories currently installed.)
Unpacking ffmpeg (from .../ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-ipod640.ffpreset', which is also in package libavcodec-extra-52 4:0.5.1-1ubuntu1.2+medibuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_4%3a0.9-0ubuntu1~jon5~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ray field on 2011-12-30
a little background: I've been trying to upgrade to the latest version of DeVeDe.  when I try to install the downloaded deb package, GDebi reports: 

Error: Dependency is not satisfiable: ffmpeg (>= 4:0.7.2)

this thread 

[http://ubuntuforums.org/showthread.php?p=11537675](http://ubuntuforums.org/showthread.php?p=11537675)

suggests installing this PPA for "the latest ffmpeg"

```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg && sudo apt-get update
```

which leads to the error (because I am on Lucid?).  if I uncheck the repo in Synaptic, installing ffmpeg works just fine.

looking through Jon Severinnsson's FFmpeg PPA page, I see he says "On Ubuntu 10.04 (Lucid Lynx) this PPA depends on the official backports repository." should I add this?

---

### Post by Mia1990 on 2011-12-31
You may be able to grab a deb from the Debian multimedia package website [here]("http://debian-multimedia.org/pool/main/") but i would install ffmpeg from Git as the guide says thats what the guide is for.Best of luck.

---

### Post by stuartcnz on 2012-01-01
If it were me trying to do this, I would be inclined to install fresh copy of Lucid in a VirtualBox, and experiment on how to do this in there. 

I suspect that adding all the newer versions of stuff that you are trying to do, could break other parts of your system, so it might be adviseable to test in the expendable environment of a virtual machine. If you can get it to work there, then duplicate the process on your existing setup.

And by all means follow the instructions to the letter, and install the backports, in the virtual machine, it will probably make all the difference.

---

### Post by ray field on 2012-01-01
> **stuartcnz said:**
> ...I suspect that adding all the newer versions of stuff that you are trying to do, could break other parts of your system, so it might be adviseable to test in the expendable environment of a virtual machine.

this is one of my fears.  the truth is, it's not going to kill me if I can't get DeVeDe running. but as far as going to trouble, there is probably a windoze port of it and I could run XP in virtualbox and run it from there.

the other thing is, as much as I love the idea of being able to compile things, it's just one step too far for me.  I love Ubuntu, but between my curiosity leading me someplace where I'll just waste three hours trying to figure out why some subroutine won't complete, and my simple lack of competence, I can't afford to waste the time -- a year and a half ago I spent three hours trying to recompile mc so it could use network shares & I couldn't even manage that.  

which is, I'm afraid, just my way of complaining that no one has/can compile(d) an ffmpeg version that I know will work. worse things have happened.

---

### Post by stuartcnz on 2012-01-01
I guess that is the great dilema of stable versus newest in an OS. The way I get around that is to have a multi-boot system and also use virtual machines as well.

I have installed on my computer Ubuntu Lucid 10.04 LTS, Debian Squeeze 6(stable with backports), Debian Wheezy 7(testing), and CentOS 5.7. Between them, I have the benefits of stable through to new. CentOS and Squeeze are both rock solid for stability, but their software is certainly not the newest. Lucid is not a bad compromize, but with the shear amount of stuff I have loaded onto it, is not as stable as it could be (I even have Cinepaint running on it).

At this stage Wheezy appears to be at least as stable as my installation of Lucid, but has surprisingly current versions of stuff.

I can access the home folders of both Debian and the Ubuntu installation from any of them, which is convenient, though CentOS sits in complete isolation from the others.

I also have VirtualBox set up in all except for CentOS and use all sorts of other stuff in them.

---

### Post by ray field on 2012-01-06
thankfully I came across this thread:

[http://ubuntuforums.org/showthread.php?t=1557846](http://ubuntuforums.org/showthread.php?t=1557846)

(the fix (#9) was to add a bleeding-edge PPA.)

not sure yet if DeVeDe is working like I want it to but the newest version starts successfully anyway.

---

