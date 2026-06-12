---
title: "Install i386 mplayer in 64bit Ubuntu"
date: 2011-05-01
forum: Multimedia Software
---

### Post by etrek64 on 2011-05-01
Hello, could someone explain how to do the following (step-by-step)::confused:

"NOTE: the w32codecs can be used on amd64 ubuntu (hardy, intrepid) 
with the i386 mplayer, but it requires manual installation and 
forcing the install. The i386 mplayer executable can be extracted 
(and moved or renamed to mplayer32 to keep it separate from the 64 
bit version), and will use the ia32 /usr/lib32 entries and w32 codecs - 
but updated libraries (e.g. libx264.so.59 v.s .57) may also be required."

I found the above paragraph here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
And not sure the steps involved in doing it.
Very much appreciate help :)

---

### Post by potiphera on 2011-08-11
(bump)

This interests me, as I haven't found a guide for installing 32-bit mplayer (keeping it separate from the 64-bit version of the program) in 64-bit Ubuntu 10.04 that has worked for me yet.  Can anyone explain how to do this?

---

### Post by BicyclerBoy on 2011-08-12
To install a 32bit deb package on 64 bit system you use the
[sudo] dpkg --install --force-architecture blah.deb

You need the ia32 32bit runtime libraries.

For example..The nVidia 64 bit graphics driver builds a 32 bit component if you have the ia32 libraries installed. (needed for Wine etc)

To build 32 bit apps on 64bit system some other 32 bit libraries are needed ( I think).

---

### Post by potiphera on 2011-08-12
Thanks so much! Will that overwrite the 64-bit version I have installed?  Because I'd like to keep that and install 32-bit mplayer as mplayer32 or something similar.

---

### Post by BicyclerBoy on 2011-08-12
Good question that..I don't know the answer..
I suspect it will if the application name is the same.

You could just install the 32 bit package & rename the binary then install the 64 bit over the top..
Could cause some trouble...
I think the installed shared 32 & 64 bit libraries are stored separately.

I have only had multiple copies of the same program when one of them was **outside** of the package management system. i.e. compiled from source.

The debian package contains very complete/complex setup info install/removal scripts pre-run scripts dependency stuff etc etc.
I guess it could be hacked but I wouldn't try...much easier to compile from source code.


But is all this trouble just to get the i386 w32codecs ??
Just install the x86-64 (em64T amd64) w64codecs..

---

### Post by potiphera on 2011-08-12
Was trying to get WMV3 videos to play in 64-bit Ubuntu (it works in 32-bit).  Are there codecs that work for 64-bit that don't require installing 32-bit mplayer?  I've been trying to compile it from source and it keeps telling me

```
Error: The GUI requires libavcodec with PNG support (needs zlib)
```

and I'm not sure how to satisfy that dependency.

---

### Post by BicyclerBoy on 2011-08-12
Which libav* libraries have you installed..
The default *buntu ones are stripped..

The problem may not be solved by compiling mplayer as it will still use your ffmpeg (libav*) libraries.
It is possible to build mplayer against your  private builds of libav* but...

From the medibunti repos..
should get
w64codecs
non-free-codecs
libav*extra-*  (7 items)

This may solve the problem..

---

### Post by mc4man on 2011-08-12
The library in question is zlib1g-dev.
If you're building mplayer then you/it should be building off of internal (statically linked) ffmpeg libraires in the mplayer source.

As far as w64codecs - worthless, there is only a few codecs included and only 1 that provides support not already available.

Here's 1 way to build a fairly full featured 32 bit mplayer on a 64 bit 10.04 install. The post is over a year old so possible some adjustment is needed. The one current difference is an mplayer checkout no longer includes ffmpeg sources, when you 1st run the ./configure .... it should prompt you about that and download for you.

If trying and unclear ask 1st., any errors ect. post completely, as said it's over a year ago.
post 4, other option in post 2
[http://ubuntuforums.org/showthread.php?p=9338517](http://ubuntuforums.org/showthread.php?p=9338517)

---

### Post by potiphera on 2011-08-13
Awesome, thanks! Does that install 32-bit mplayer as a separate program from the 64-bit version?  If those instructions will compile/install it as a separate program, I'll try that, but if not, the smplayer through Wine option sounds good, as I'd rather not overwrite the mplayer I have installed.

---

### Post by mc4man on 2011-08-13
> **potiphera said:**
> Awesome, thanks! Does that install 32-bit mplayer as a separate program from the 64-bit version?  If those instructions will compile/install it as a separate program, I'll try that, but if not, the smplayer through Wine option sounds good, as I'd rather not overwrite the mplayer I have installed.

It's been quite a while, and when reviewing the post i see I did it on a live cd so my memory is a bit vague
(also to keep in mind that starting in 11.04 somewhat and definitely in 11.10 ubuntu has gone to multiarch which could be a factor

Anyway - I'm fairly sure that will it shouldn't 'overwrite' an existing mplayer  but it will certainly trump it in terms of the mplayer command
(the 32 bit build is installed to /usr/local/bin

**Edit:** actually it will remove an existing mplayer package if it's the same name - I guess you could get around that by altering the checkinstall command and name it a bit differently or just use a sudo make install instead of creating/installing from checkinstall
(i probably would test the new mplayer itself and w/ a frontend if desired and if good not keep the 64 bit package 

I guess you could keep a typical repo or ppa install (/usr/bin ) and if need be call it directly as in 
/usr/bin/mplayer <whatever>

I've got an 11.10 install I may redo tonight w/ the latest daily, maybe before that I'll throw in a quick 10.04 64 bit and d. check those instr.'s

Otherwise if you try post up any issues **if** they occur, maybe can figure out

---

