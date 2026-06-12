---
title: "[SOLVED] mplayer issue"
date: 2008-12-21
forum: Multimedia Software
---

### Post by davidself1001 on 2008-12-21
I downloaded mplayer source (svn) from this site [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) in an attempt to get a stable mplayer.  I compiled/built per linux.com instructions.

./configure --enable-gui (really just wanted cli version but this option gives both - at least that was my understanding)
make
sudo make install

Now I get the following error when executing mplayer from the cli.


MPlayer dev-SVN-r28173-4.2.4 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1400MHz (Family: 15, Model: 0, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Two questions: 1) what version do I need and 2) how do I remove the version that I compiled so that I can install the correct version?

---

### Post by ajgreeny on 2008-12-21
I'm pretty sure you can remove it using apt-get remove, or purge.  Also I think using synaptic, which is very good at getting rid of things, even if that is not the way they were installed.
As to the version you need, I have no idea, I'm afraid.

---

### Post by Jose Catre-Vandis on 2008-12-21
What was the problem with mplayer from the repos? I use mplayer for just about everything, admittedly I enable medibuntu before installing, but never have problems with mplayer. As suggested a bit of purging and removing then try:

Assuming you are on intrepid, put this in your /etc/apt/sources.list
```
#medibuntu
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
```
then
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install mplayer mencoder
```

---

### Post by shirilover on 2008-12-21
> **davidself1001 said:**
> Now I get the following error when executing mplayer from the cli.


MPlayer dev-SVN-r28173-4.2.4 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1400MHz (Family: 15, Model: 0, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Two questions: 1) what version do I need and 2) how do I remove the version that I compiled so that I can install the correct version?

I don't see any error report in the above quoted text.
I assume you actually tried to play a file, but you for got to include the rest of the text output.

If you want to remove the version you compiled, cd into the source directory and issue sudo make uninstall.

---

### Post by davidself1001 on 2008-12-21
I was trying to play a file and this was all that I get out.  No video.  It is strange because I can use smplayer which supposedly uses mplayer and it works (although all of the transport buttons - play, stop, rewind, etc are greyed out, but that's another problem I have yet to fix).  I am on 8.04 as indicated in my signature so can I just substitute the word Hardy where it says Intreped?

---

### Post by laceration on 2008-12-21
if mplayer does not get something proper to open or play you will not see anything.  Those were not errors.  Mplayer will display a lot of messages about what its doing.  To suppress some of them you can use -quiet or -really-quiet on the command line.  To open the graphical mplayer:
```
gmplayer
```
Mplayer is generally stable and I don't think anyone should bother downloading from svn and compiling for that purpose.

---

### Post by davidself1001 on 2008-12-21
I managed to find out that I had two different versions on my PC.  One was the svn and the other was the standard version.  I deleted the svn version and now I can play videos.  Now I am having performance issues with slow video (HD) and no audio in cli mode on HD videos.  I have started another thread to discuss those issues.  I will mark this one as solved.

---

### Post by rvm4000 on 2008-12-21
If you prefer to use a recent version from svn (which may be a good idea as 1.0rc2 is very old and with many bugs), you can get deb packages here (for hardy and intrepid):
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

---

