---
title: "Multithreading with acidrip"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by damu on 2007-02-15
I've been using acidrip for quite a while now, and feel it works really well. I use the x264 codec (available with synaptic) and the end result is really good.

But Acidrip doesn't seem to offer  an smp option for dual core systems like mine. X264 encoding is already not  fast, so doing it on just one core is a bit of a pain. 

I would like to keep the possibility to rip and encode directly from DVD (no rip on HD first) .I didn't see find any solution, even in command line  which allows to rip and encode from the DVD.

I've been through many threads, and found the options used for multithreading with x264 from command line :
threads=auto:
or 
threads 2

I tried to add one or the other in the misc option of acidrip with no results.

What would be the solution for a  multithreaded rip&encode from DVD in x264 on Ubuntu if acidrip can't do it?

thanks

---

### Post by damu on 2007-02-19
Does anyone how to benefit of multithreading when ripping a DVD?

---

### Post by mercutio on 2007-03-16
I have the same issue, haven't been able to get acidrip to use both cores, and its driving me crazy.

---

### Post by hotani on 2007-05-07
It uses both cores. First it uses 100% of the first one, then 100% of the second one!

Sorry, I'm no help. :D

---

### Post by kefurd06 on 2008-01-05
bump.

---

### Post by jdmpike on 2008-01-08
I have been trying to do some research on this as well...

This page seems to offer some suggestions about making x264 a little faster [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options-speedvquality](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options-speedvquality)

The thing I am eager to try when I get home tonight is messing with the threads setting in the x264encopts

> **threads:** This option allows to spawn threads to encode in parallel on multiple CPUs. You can manually select the number of threads to be created or, better, set threads=auto and let x264 detect how many CPUs are available and pick an appropriate number of threads. If you have a multi-processor machine, you should really consider using it as it can to increase encoding speed linearly with the number of CPU cores (about 94% per CPU core), with very little quality reduction (about 0.005dB for dual processor, about 0.01dB for a quad processor machine).

The page has a lot of other options you can tweak, I just wish that acidrip would incorporate more of the options available for the x264 codec. I don't even know how to make it do two pass...

Regards,

JDM

---

### Post by neltnerb on 2008-01-14
Hi.

I randomly found your note.

I wrote patches over a year ago to fix the x264 support. I wasn't sure how to submit them, but here they are for your use.

The patches should be run on two files in /usr/share/perl5/AcidRip/ (acidrip.pm and signals.pm)

After patching, it'll probably rename them to acidrip-updated.pm and signals-updated.pm.

You'll have to rename them to the original names (acidrip.pm and signals.pm) in order to get the program to work, but after you do that x264 options should be all set up and ready to go (although the defaults I built in a year or so ago are quite possibly obsolete).

Sorry for the delay, hope it's of some use.
-Brian Neltner

---

