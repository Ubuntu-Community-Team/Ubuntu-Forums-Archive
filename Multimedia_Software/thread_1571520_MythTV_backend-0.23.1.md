---
title: "MythTV backend-0.23.1?"
date: 2010-09-09
forum: Multimedia Software
---

### Post by MarkKnecht on 2010-09-09
Hi,
   First forum post. 

   I'm a long-time Linux user but new to Ubuntu. I have an old PowerPC MacMini that I used previously as a MythTV backend running Gentoo but got tired of building code so looking around I found a supported Ubuntu 10.04 LTS for the PowerPC and decided to try it. The install was painless and I was able to bring up an older version of the Myth backend (0.23) but I'd like to using 0.23.1 if possible.

   Can anyone explain how I find a newer version? I assume it's in some repository somewhere but I don't know how to search for it and assuming I find it how to get the software installer to us it.

Thanks,
Mark

---

### Post by andrewc6l on 2010-09-10
I'm not sure if this is exactly what you want, but take a look here:
[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

This lets you select which stream you're on, and where you're getting fixes from.

---

### Post by MarkKnecht on 2010-09-10
Andrew,
   Thanks for the response.

   It's the right idea but (I think) the wrong processor architecture. As best I can tell so far Mythbuntu only supports x86 and since my MacMini is PowerPC the binaries won't run. I would have loved to use Mythbuntu but AFAICT it won't work on this machine. That's why I was so happy to find the 10.04 LTS setup for the PowerPC because at least I could boot the machine and get going with Myth because they have the older 0.23 version.

   As a newbie to Ubuntu I'm having a hard time understanding where my machine is getting it's updates. I am guessing that the 'Ubuntu Software Center' app just points at some default vanilla repository or something but I haven't found docs that tell me how to change that in any intelligent way. I mean I've found the list of 'Software Sources' in the Edit menu for the app, but it's just a list of repositories (I guess) and as a newbie I've no idea why I should choose one vs another.

   Is there a good document to read about the setup of the machine in terms of what repositories are available or how to search the repositories out there to see if there is one that has the version of the app I'm interested in? Gentoo has a tool for searching all the portage overlays to figure out which ones are supporting specific apps and what versions they support. Is there anything like that for Ubuntu, specifically ensuring that it's searching repositories that support my PowerPC machine?

Thanks,
Mark

---

### Post by andrewc6l on 2010-09-15
Sorry, I missed the "Mac Mini" in your message :-)

General info about repositories is here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I don't think there is a "master list" of repositories - anyone with a machine on the net can set one up. The ones that have only a few things on them frequently disappear.

As for architecture, the only way I know of to get it is with
```
aptitude -v show packagename
```
That will also show you which repository a particular package is coming from.

---

### Post by lystor on 2010-09-15
> **MarkKnecht said:**
> 
   Can anyone explain how I find a newer version?
The latest available version of [mythtv-backend is 0.23.0+fixes24158-0ubuntu2_i386]("http://pkgs.org/ubuntu-10.04-i386/ubuntu-multiverse/mythtv-backend_0.23.0+fixes24158-0ubuntu2_i386.deb.html") for [Ubuntu 10.04 LTS]("http://pkgs.org/ubuntu-10.04-i386/ubuntu-multiverse/").

---

