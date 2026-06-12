---
title: "Converting to mp4"
date: 2008-07-16
forum: Multimedia Software
---

### Post by abuakel on 2008-07-16
I've got a variety of music videos in various formats ranging from mpg to avi to mkv to mpeg. However, I'd like to convert them to a smaller mp4 iPhone format

I found this site with a walk through, although I don't think it was directed at Hardy:
[http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html](http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html)

I followed their instructions, but kept coming out with this out put:

```
$ mp4ize Danie_ Powter_Bad_day.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Danie_: I/O error occured
Usually that means that input file is truncated and/or corrupted.
Couldn't figure out aspect ratio.

```

If anyone knows how to fix the above problem, or knows a better, easier way to convert videos, I'm all ears. :)

---

### Post by chicken101 on 2008-07-16
I think that perhaps you are not using the script properly.  I think what you want to do is:```
mp4ize /home/name/blah/file.mpg
```

---

### Post by abuakel on 2008-07-16
thanks, but I tried that, and it didn't workd :/

---

### Post by chicken101 on 2008-07-16
I've used mp4ize before, and with some files it is a bit testy.  Have you gotten it to work at all?  Try some other videos and see if it works.

---

### Post by abuakel on 2008-07-16
> **chicken101 said:**
> I've used mp4ize before, and with some files it is a bit testy.  Have you gotten it to work at all?  Try some other videos and see if it works.

I've tried four different videos with the same result. I'm not too picky about using mp4ize, I'd just like an easy way to convert my videos.

---

### Post by chicken101 on 2008-07-16
Ahhh ok, I remember when I got mp4ize to work correctly I had to configure ffmpeg with certain options (options which are not included by default).  Instructions to set this up can be found [here]("http://thomer.com/howtos/ipod_video.html").  It's sort of a pain, but I have done it with success in the past.:KS

---

### Post by abuakel on 2008-07-16
> **chicken101 said:**
> Ahhh ok, I remember when I got mp4ize to work correctly I had to configure ffmpeg with certain options (options which are not included by default).  Instructions to set this up can be found [here]("http://thomer.com/howtos/ipod_video.html").  It's sort of a pain, but I have done it with success in the past.:KS

Thanks, but I get stuck at this point:
```
You need to configure and install the latest version of ffmpeg as follows:
(this worked for ffmpeg-0.cvs20070307)

./configure --enable-gpl --enable-pp --enable-pthreads \
            --enable-libvorbis --enable-libogg --enable-liba52 \
            --enable-libdts --enable-libgsm --enable-dc1394 \
            --disable-debug --enable-shared --enable-xvid \
            --enable-libfaac --prefix=/usr/local
make
sudo make install

```

What I receive is this:

```
$ ./configure --enable-gpl --enable-pp --enable-pthreads \
>             --enable-libvorbis --enable-libogg --enable-liba52 \
>             --enable-libdts --enable-libgsm --enable-dc1394 \
>             --disable-debug --enable-shared --enable-xvid \
>             --enable-libfaac --prefix=/usr/local
bash: ./configure: No such file or directory
geries@home-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
geries@home-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

---

### Post by chicken101 on 2008-07-16
Yeah, the guide misses a step (sorry about that), you need to download ffmpeg with ```
sudo svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

If you get an error about not having svn just run apt-get ```
sudo apt-get install subversion
```

This will create a folder call ffmpeg in your home directory, next run ```
cd /home/yourname/ffmpeg
```.  This will tell the terminal to run things from within that folder.  Now just continue with the ./configure procedure from that tutorial.  

That tutorial is a little confusing, sorry about that!:KS

---

### Post by abuakel on 2008-07-16
> **chicken101 said:**
> 
That tutorial is a little confusing, sorry about that!:KS

not a problem, I've gone through a little more confusing commands, but this is kinda inching it's way to the top of the most confusing :)

When I try to run 'make' I get this:
```
/ffmpeg$ make
Makefile:1: config.mak: No such file or directory
libavdevice/Makefile:1: libavdevice/../config.mak: No such file or directory
libavformat/Makefile:1: libavformat/../config.mak: No such file or directory
libavcodec/Makefile:1: libavcodec/../config.mak: No such file or directory
libavutil/Makefile:1: libavutil/../config.mak: No such file or directory
make: *** No rule to make target `libavutil/../config.mak'.  Stop.

```

---

### Post by fenian on 2008-07-16
get the medibuntu version of ffmpeg open a terminal and enter...

> sudo apt-get remove ffmpeg

then enter...

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then enter...
> 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then enter...

> sudo apt-get install ffmpeg

---

### Post by abuakel on 2008-07-16
hmm, when I punch in:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
```
everything seems to work, but when I go and look at the results more closely, I get this error somewhere in the middle:
```
W: GPG error: http://ftp.debian-unofficial.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 394D199524C52AC3
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

I again 'apt-get update', but I get the same results.

---

### Post by fenian on 2008-07-16
run them seperately...

> sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update

---

### Post by abuakel on 2008-07-16
> **fenian said:**
> run them seperately...

each time I run 'sudo apt-get update' I get the same error:

```
W: GPG error: http://ftp.debian-unofficial.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 394D199524C52AC3
W: You may want to run apt-get update to correct these problems

```

Just out of curiosity, doesn't '&&' mean to run the command after only if the first command succeeds?

---

### Post by chicken101 on 2008-07-16
You have to run that ./configure command first, which creates that make file you are trying to run.

---

### Post by abuakel on 2008-07-16
> **chicken101 said:**
> You have to run that ./configure command first, which creates that make file you are trying to run.

yes, I know.. which I have.
these are the results when I get to the --enable-pp part:

```
ffmpeg$ sudo ./configure --enable-pp
Unknown option "--enable-pp".
See ./configure --help for available options.

```

Let's backtrack for a moment.. should the source "http://packages.medibuntu.org/" in Software Sources be marked?

---

### Post by fenian on 2008-07-16
> **abuakel said:**
> 
Let's backtrack for a moment.. should the source "http://packages.medibuntu.org/" in Software Sources be marked?

Yes but you appear to have a problem with another repository missing a gpg key.

---

### Post by abuakel on 2008-07-16
> **fenian said:**
> Yes but you appear to have a problem with another repository missing a gpg key.

when I mark it and reload the repos, I get the same error:

```
W: GPG error: http://ftp.debian-unofficial.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 394D199524C52AC3
```

---

### Post by chitowner2 on 2009-03-07
8 months later I am interested in a solution to this. I am trying to install winff thru synaptic and get that same GPG err about the public key.

I get this:
The following packages have unmet dependencies:
  winff: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
         Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
E: Broken packages

which led me to focus on libgtk2 which in turn led to the GPG error.

Can anyone untangle this??   :(

thanks!

---

### Post by paul.gevers on 2009-03-09
> **abuakel said:**
> 
```
$ mp4ize Danie_ Powter_Bad_day.mpg

```

If anyone knows how to fix the above problem, or knows a better, easier way to convert videos, I'm all ears. :)

The problem you encounter is the space in the name of the file. If you type
```
$ mp4ize Danie_\ Powter_Bad_day.mpg

```
or
```
$ mp4ize "Danie_ Powter_Bad_day.mpg"

```
everything should be fine.

---

### Post by paul.gevers on 2009-03-09
> **chitowner2 said:**
> 
I get this:
The following packages have unmet dependencies:
  winff: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
         Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
E: Broken packages

The problem here is that you should probably also activate the ubuntu-updates section of the repositories.

---

### Post by chitowner2 on 2009-03-09
> **pa:confused::confused:ul.gevers said:**
> The problem here is that you should probably also activate the ubuntu-updates section of the repositories.

Paul- thanks for the help, but if i open synaptic>settings>repositories>updates/ubuntu updates  everything is already checked. 
From this page I find the lib:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.12.9-3ubuntu5](https://launchpad.net/ubuntu/+source/gtk+2.0/2.12.9-3ubuntu5)
 but it is already installed.
Maybe i should be looking for "libpango1.20.5-0ubuntu1"?  That apeears to also be unsatisfied.
:confused:

---

### Post by mc4man on 2009-03-09
Your main problem is your trying to install a winff package meant for intrepid. Also that version (0.45) is possibly not compatible with hardy anyway.

You could try to build it or look here for a hardy version (reverted back to 0.43

[https://launchpad.net/~paul-climbing/+archive/ppa](https://launchpad.net/~paul-climbing/+archive/ppa)

If you want to download directly (without adding the ppa then expand the first winff listing and scroll down to "package files"

---

### Post by chitowner2 on 2009-03-10
> **mc4man said:**
> Your main problem is your trying to install a winff package meant for intrepid. Also that version (0.45) is possibly not compatible with hardy anyway.

You could try to build it or look here for a hardy version (reverted back to 0.43

[https://launchpad.net/~paul-climbing/+archive/ppa](https://launchpad.net/~paul-climbing/+archive/ppa)

If you want to download directly (without adding the ppa then expand the first winff listing and scroll down to "package files"



mc4man: Do you hear that knocking sound? That's me banging my head against the wall. I never realized it was an ibex package!  ](*,)

But from what I've seen, Ibex with KDE4 is nuts. I actually tried it, and i simply don't grok the whole "widgits" thing. But that's another story for another day.

Thanks for the pointer. I'll see what I can do with it... meanwhile I'm gonna have a run at ubuntustudio and maybe mint.

Ibex? I'm waiting for either KDE3.5 to get backported reliably or for KDE4 to get more user-friendly. Those developers are on Mars!   :P

---

### Post by mc4man on 2009-03-10
> But from what I've seen, Ibex with KDE4 is nuts. I actually tried it, and i simply don't grok the whole "widgits" thing. But that's another story for another day.

If you are referring to kubuntu, I agree, somewhat 'restrictive' atm to say the least.
You could install ubuntu 8.10 and with just a little effort set it up very well AV wise with current versions of anything you wish. (not confined to intrepid versions, including your winff.

---

### Post by chitowner2 on 2009-04-03
Well, based on some things I've learned recently, I went ahead and upgraded right to jaunty, then installed kde3.5 on it.

I have mixed impressions about the results tho- see my new post: "kde3 in jaunty: apps don't run"

I wanted to run Mint and UbuntuStudio on VirtualBox-OSE but I can't get that to run with this setup either.

:-(

---

### Post by syb0rz on 2010-09-12
Ubuntu 10.04 update for the 'Couldn't figure out aspect ratio' problem for mp4ize and details for ffmpeg 0.6.

1) I followed the instructions here:
[http://thomer.com/howtos/ipod_video.html](http://thomer.com/howtos/ipod_video.html)

1.a) EXCEPT, I used ffmpeg 0.6 instead of 0.5:
[http://ffmpeg.org/releases/ffmpeg-0.6.tar.bz2](http://ffmpeg.org/releases/ffmpeg-0.6.tar.bz2)

1.b) Also, libamrnb-dev and libamrwb-dev have been replaced by libopencore-amrnb-dev and libopencore-amrwb-dev. So you need to change your ./configure flags when you setup ffmepg 0.6.

2) Then I setup the mp4ize ruby script from here:
[http://thomer.com/howtos/mp4ize](http://thomer.com/howtos/mp4ize)

2.a) For ffmpeg 0.6 you need to replace all '/usr/bin/ffmpeg' with just 'ffmpeg'. 


Hope this helps!

---

### Post by syb0rz on 2010-09-12
Also, I made a quick bash script so you can right-click the file in Nautilus in Ubuntu 10.04 and conveniently convert it to MP4:

1) Make a bash file called Convert-to-MP4
```

#!/bin/bash
gnome-terminal -x mp4ize "$1"

```

1.a) Move it to /usr/local/bin then:
1.b) sudo chmod +x /usr/local/bin/Convert-to-MP4

2) Add it to the right-click menu in Nautilus
2.a) Open your videos folder, right-click a video go to Properties.
2.b) Go to 'Open with' tab, click Add
2.c) Click 'Use a custom command' type Convert-to-MP4, click Add

Now you should be able to right click any of that file type and it will run mp4ize in terminal. You need to repeat this for each filetype (.avi, .mpg, etc).

---

