---
title: "What is cinerella doing in my /etc/rc folders?"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by Arthur Archnix on 2008-03-17
I just installed Cinerella and this was in the terminal output during install:

> Setting up cinelerra-generic (1:2.1.0-1svn20080222akirad1) ...
Description:    Ubuntu 7.10
 Adding system startup for /etc/init.d/cinestart ...
   /etc/rc0.d/K20cinestart -> ../init.d/cinestart
   /etc/rc1.d/K20cinestart -> ../init.d/cinestart
   /etc/rc6.d/K20cinestart -> ../init.d/cinestart
   /etc/rc2.d/S20cinestart -> ../init.d/cinestart
   /etc/rc3.d/S20cinestart -> ../init.d/cinestart
   /etc/rc4.d/S20cinestart -> ../init.d/cinestart
   /etc/rc5.d/S20cinestart -> ../init.d/cinestart

What the heck is it doing there? I've removed all those entries, but still, that's at a minimum bad form, if not downright malicious. It also installed this akiranews thing, which is essentially spam/spyware! Here's the full output:

```
arthur@archnix:~$ sudo aptitude install cinelerra-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  akiradnews fftw3 libguicast-generic libmpeg3hv-generic 
  libquicktimehv-generic 
The following NEW packages will be installed:
  akiradnews cinelerra-generic fftw3 libguicast-generic libmpeg3hv-generic 
  libquicktimehv-generic 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6MB of archives. After unpacking 31.6MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://fi.archive.ubuntu.com gutsy/main fftw3 3.1.2-2ubuntu2 [1030kB]
Get:2 http://repository.akirad.net akirad-gutsy/main akiradnews 20080222 [3496B]
Get:3 http://repository.akirad.net akirad-gutsy/main libguicast-generic 1:2.1.0-1svn20080222akirad1 [330kB]
Get:4 http://repository.akirad.net akirad-gutsy/main libmpeg3hv-generic 1:2.1.0-1svn20080222akirad1 [118kB]
Get:5 http://repository.akirad.net akirad-gutsy/main libquicktimehv-generic 1:2.1.0-1svn20080222akirad1 [1632kB]
Get:6 http://repository.akirad.net akirad-gutsy/main cinelerra-generic 1:2.1.0-1svn20080222akirad1 [11.5MB]
Fetched 14.6MB in 2m20s (104kB/s)                                               
Selecting previously deselected package akiradnews.
(Reading database ... 79790 files and directories currently installed.)
Unpacking akiradnews (from .../akiradnews_20080222_all.deb) ...
Selecting previously deselected package fftw3.
Unpacking fftw3 (from .../fftw3_3.1.2-2ubuntu2_i386.deb) ...
Selecting previously deselected package libguicast-generic.
Unpacking libguicast-generic (from .../libguicast-generic_1%3a2.1.0-1svn20080222akirad1_i386.deb) ...
Selecting previously deselected package libmpeg3hv-generic.
Unpacking libmpeg3hv-generic (from .../libmpeg3hv-generic_1%3a2.1.0-1svn20080222akirad1_i386.deb) ...
Selecting previously deselected package libquicktimehv-generic.
Unpacking libquicktimehv-generic (from .../libquicktimehv-generic_1%3a2.1.0-1svn20080222akirad1_i386.deb) ...
Selecting previously deselected package cinelerra-generic.
Unpacking cinelerra-generic (from .../cinelerra-generic_1%3a2.1.0-1svn20080222akirad1_i386.deb) ...
Setting up akiradnews (20080222) ...

Setting up fftw3 (3.1.2-2ubuntu2) ...

Setting up libguicast-generic (1:2.1.0-1svn20080222akirad1) ...

Setting up libmpeg3hv-generic (1:2.1.0-1svn20080222akirad1) ...

Setting up libquicktimehv-generic (1:2.1.0-1svn20080222akirad1) ...

Setting up cinelerra-generic (1:2.1.0-1svn20080222akirad1) ...
Description:    Ubuntu 7.10
 Adding system startup for /etc/init.d/cinestart ...
   /etc/rc0.d/K20cinestart -> ../init.d/cinestart
   /etc/rc1.d/K20cinestart -> ../init.d/cinestart
   /etc/rc6.d/K20cinestart -> ../init.d/cinestart
   /etc/rc2.d/S20cinestart -> ../init.d/cinestart
   /etc/rc3.d/S20cinestart -> ../init.d/cinestart
   /etc/rc4.d/S20cinestart -> ../init.d/cinestart
   /etc/rc5.d/S20cinestart -> ../init.d/cinestart

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done    
```

---

### Post by tlink on 2008-03-17
The company that makes it is called 

"Heroine Virtual Ltd"

..... yeah... um... that could be part of it.

---

### Post by akir4d on 2008-05-03
I'm the maintainer of akirad project... my repository is fully signed and akiradnews is not an addware as you can read here:

[http://www.akiradproject.net/repository]("http://www.akiradproject.net/repository")

and specially here:
[http://akiradproject.net/disable_akiradnews]("http://akiradproject.net/disable_akiradnews")

but the problem is that you never try to read package description on synaptic:

[I]An audio/video authoring tool
Cinelerra is a complete audio and video authoring
tool. It understands a lot of multimedia formats
(quicktime, avi, ogg) and audio/video compression
codecs (divx, xvid, mpeg1/2, ...)

This is a special ubuntu rebuild from akirad.net that include some variants:

- cinelerra (all x86 and x86_64 without opengl 2.0 video card)
- cinelerra-generic (all x86 and x86_64 with opengl 2.0 video card)
- cinelerra-k7 (all amd32 without opengl 2.0 video card)
- cinelerra-k7gl (all amd32 with opengl 2.0 video card)
- cinelerra-k8 (all amd64 with opengl 2.0 video card)

add also:
- /usr/bin/Cinelerra scripts that fix traslation problem on ubuntu
- /etc/init.d/cinestart that set shmmax to 0x7fffffff ( you can edit this script to not do that ). 
[/I]

byez 

Paolo Rampino

---

