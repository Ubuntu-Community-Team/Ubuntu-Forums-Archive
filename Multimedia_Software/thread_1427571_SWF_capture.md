---
title: "SWF capture"
date: 2010-03-11
forum: Multimedia Software
---

### Post by kadaitcha on 2010-03-11
I'd appreciate information on any straightforward & reliable method of capturing / downloading SWF videos as used by MSN.  Whilst there are countless applications that claim to do the job, none that I've tried to date does what they promise. Other video formats like flv & mp4 invariably work fine but there is obviously a LOT more to capturing SWF than it appears. Some capture applications like Sothink 'appear' to be capable,however they give a very small file with SWF extension thats either damaged or corrupted regardless of the site.  Obviously I'd prefer to do this in Ubuntu / Firefox, but if its not viable then I'll use whatever is needed. Some sources suggest that Internet Explorer (cough cough splutter splutter) saves SWF videos by default in a chache, so if thats simpler than stuffing around ad infinitum with applications that don't work, then so be it. Nevertheless I'd prefer to use open source solutions ...... any suggestions that are tried and tested and which work properly ??

---

### Post by 2hot6ft2 on 2010-03-11
I guess it will be the same for msn videos. when you play it open places > home. Then go up > up then open the tmp folder and it should be there once it finishes downloading you can copy it to where you want to save it. There's also download helper addon for firefox here:
[http://www.downloadhelper.net/](http://www.downloadhelper.net/)

Here's a screenshot of one being downloaded into the tmp folder.

---

### Post by kadaitcha on 2010-03-13
'fraid not, there doesn't appear to be any relationship whatever between capturing SWF & capturing MP4 / FLV videos. There is no shortage of simple & straightforward systems which do the job with MP4 / FLV but I've yet to find any application that works with SWF, hence the post seeking feedback from folk who have actually succeeded. Download helper works for MP4 / FLV but is is USELESS for SWF. One suggestion that 'might' work is to look in the cache directory of Internet Explorer, so if that works I'll be happy. Haven't tried the /tmp directory but thats a good thought.

---

### Post by 2hot6ft2 on 2010-03-13
Link to one that you're talking about and we'll see. Otherwise there are too many add-ons and ways of doing things to try and figure out which will work for what you're trying to do.

---

### Post by kadaitcha on 2010-03-18
> **2hot6ft2 said:**
> Link to one that you're talking about and we'll see. Otherwise there are too many add-ons and ways of doing things to try and figure out which will work for what you're trying to do.

[http://video.au.msn.com/watch/video/queensland-police-leaving-state/xl420wz](http://video.au.msn.com/watch/video/queensland-police-leaving-state/xl420wz)
[http://video.au.msn.com/watch/video/queensland-police-setting-bad-example/xc1wqzw](http://video.au.msn.com/watch/video/queensland-police-setting-bad-example/xc1wqzw)
[http://video.au.msn.com/watch/video/allegations-grow-of-police-corruption/xqjmli2](http://video.au.msn.com/watch/video/allegations-grow-of-police-corruption/xqjmli2)
[http://video.au.msn.com/watch/video/calls-for-investigations-into-police/xbww1v0](http://video.au.msn.com/watch/video/calls-for-investigations-into-police/xbww1v0)
[http://video.au.msn.com/watch/video/police-quitting-over-paperwork/x4899fp](http://video.au.msn.com/watch/video/police-quitting-over-paperwork/x4899fp)

---

### Post by Chemical Imbalance on 2010-03-18
In Firefox, select 'Tools' then 'Page Info'.
Click on the media tab.

There will be a column labeled 'Type'.

Look for the one labeled 'Embed'.  It will be a .swf file.

Click on it and press "Save As".

Done!


If that doesn't work, then install and use 'gtk-recordmydesktop' in the repos to capture the video.

Gtk-recordmydesktop will capture anything you can watch in your browser.  Good quality captures too.

_

---

### Post by ron999 on 2010-03-18
@ kadaitcha
I can download those msn videos using a program called 'TubeMaster++'.
I use it to download clips from New York Times too.
It's not very user-friendly, but it works.

This is the website for TubeMaster:-[http://www.tubemaster.net/]("http://www.tubemaster.net/")

Attached is a screenshot showing the downloaded 'Queensland Police leaving state' video playing in VLC.

---

### Post by mocha on 2010-03-18
> **ron999 said:**
> @ kadaitcha
I can download those msn videos using a program called 'TubeMaster++'.
I use it to download clips from New York Times too.
It's not very user-friendly, but it works.

This is the website for TubeMaster:-[http://www.tubemaster.net/]("http://www.tubemaster.net/")

Attached is a screenshot showing the downloaded 'Queensland Police leaving state' video playing in VLC.

Wow, this sounds almost too good to be true.  Is it true that it handles RTMP streamed files??  I'm not at my Linux box right now to test, but will definitely try later!

---

### Post by mocha on 2010-03-19
I tried Tubemaster but it keeps crashing.  Something wrong with Java.

```
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb6f248ed, pid=26018, tid=1829288816
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Server VM (14.1-b02 mixed mode linux-x86 )
# Problematic frame:
# V  [libjvm.so+0x3988ed]
```

Are you running Karmic 32 bit?  I installed the sun-java6-jdk package, the jre and libpcap were already installed on my system.

---

### Post by ron999 on 2010-03-19
Hi
If I remember correctly...
When I installed TubeMaster I didn't have Java or libpcap installed. I installed everything that was recommended on the TubeMaster website. So everything was the correct versions for TubeMaster.
Later I had to sort out Java for Firefox too. For all I know, maybe I've got two versions installed, one used by TubeMaster and one used by Firefox.
I'm confused.:o

Edit. Yes my system is 32 bit.

---

### Post by mocha on 2010-03-19
Well according to the jcontrol program I only have one Java runtime environment installed.  I did need to play with the version of sun-java6 that were installed in the package manager since this box is a jaunty to karmic upgrade box, and there was some version mismatch stuff going on which I had to resolve in order to get the jdk package installed.  I'll play with it some more.

Can you tell me when you look in synaptic and search for "sun-java6" which packages you have installed?

---

### Post by ron999 on 2010-03-19
Hi
In Synaptic it shows installed:-
sun-java6-bin
sun-java6-jdk
sun-java6-jre

All are version 6-15-1

---

### Post by mocha on 2010-03-20
> **ron999 said:**
> Hi
In Synaptic it shows installed:-
sun-java6-bin
sun-java6-jdk
sun-java6-jre

All are version 6-15-1

Thanks very much.  I had sun-java6-fonts also installed, when I removed it the program stopped crashing.

---

