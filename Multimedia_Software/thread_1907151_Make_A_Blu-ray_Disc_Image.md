---
title: "Make A Blu-ray Disc Image"
date: 2012-01-10
forum: Multimedia Software
---

### Post by R0BiN on 2012-01-10
I'm sorry if I've missed something that actually deals with this, but I'm trying to sort out if there's any way for me to pack a BDMV folder into a .iso file (like toast) that would essentially be a virtual Blu-ray.

Is there an Ubuntu program that will allow me to do this?
EDIT & BUMPED:

I just finally switched my server from CentOS to Ubuntu 11 on my server.

Couldn't decide if this was gonna be rezzing a thread or just avoiding  clutter.  If I made the wrong call, let me know and I'll start a new  thread instead.

_**What I Don't Want/Need**_
DumpHD as well as the few other options I've seen are all about letting   me take files from my Blu-ray Disc and dump them/convert them to watch   on the computer.

Just a utility/option that will let me mount the BDMV folder-group-thing  as if it/they were a Blu-ray Disc.  I'm really looking to convert the  thing into a sold disk image.

_**What I Do Want/Need**_
What I have is a BDMV folder, and I'd like to turn it into a UDF Disk  Image (like a ".toast" file on Macs, and I think just normal ".iso" for  Windows that can do this).

_**Things I'm Aware Of That Might Be (Close To Being) Able To Do What I Want**_
UDFTools looks like it has to at least be close to being able to do what  I'm talking about, but if it can do this, I can't for the life of me  figure out how...

Thanks!
Robin

---

### Post by wolfen69 on 2012-01-10
The info [here]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") is a bit dated, but DumpHD may help you.

---

### Post by BicyclerBoy on 2012-01-11
AFAIK
Be aware that an ISO image of a BD is not necessarily playable because it does not contain the MKB or the VUK.
Making an ISO of a BD is not problematic like DVDs because decrypting occurs at playback or rip/transcoding.

The ISO image of a BD does not/can not contain special data areas of a BD ..see AACS.

If you have the VUK keys then you could play the ISO.
You need the real BD disc & optical drive to extract the VUK (or the internet)..

---

### Post by R0BiN on 2012-04-01
I just finally switched my server from CentOS to Ubuntu 11 on my server.

Couldn't decide if this was gonna be rezzing a thread or just avoiding clutter.  If I made the wrong call, let me know and I'll start a new thread instead.

_**What I Don't Want/Need**_
DumpHD as well as the few other options I've seen are all about letting  me take files from my Blu-ray Disc and dump them/convert them to watch  on the computer.

Just a utility/option that will let me mount the BDMV folder-group-thing as if it/they were a Blu-ray Disc.  I'm really looking to convert the thing into a sold disk image.

_**What I Do Want/Need**_
What I have is a BDMV folder, and I'd like to turn it into a UDF Disk Image (like a ".toast" file on Macs, and I think just normal ".iso" for Windows that can do this).

_**Things I'm Aware Of That Might Be (Close To Being) Able To Do What I Want**_
UDFTools looks like it has to at least be close to being able to do what I'm talking about, but if it can do this, I can't for the life of me figure out how...

Thanks!
Robin

---

### Post by BicyclerBoy on 2012-04-02
Have you found this?

[http://irishjesus.wordpress.com/2010/10/17/blu-ray-movie-authoring-in-linux/](http://irishjesus.wordpress.com/2010/10/17/blu-ray-movie-authoring-in-linux/)

k3b states bluray support..

Note: dumpHD has other uses apart from ripping the BD..

---

### Post by R0BiN on 2012-04-05
I didn't mean to imply DumpHD wasn't a capable app or anything (sorry if it came across otherwise).  Only that it isn't (at least that I can tell) even attempting to be an application for creating UDF disk images from BDMV folders.

Yes, that blog seems to come up (even as #1 often for Google) a lot when searching for information about this.

That said, it isn't really up to date, and the OP is actually attempting to encode a stream into a disc (so could likely come up with a solution that wouldn't work for me).

NeroLinux seems to come up, but the Nero site is VERY bizzarre about it and I can't really figure out what the deal is there.  (Especially since I'm running Ubuntu on a server, so I'm looking for something with command-line capability).

K3B comes up often too, but the only actual information I've found about K3B's capability is that it DOESN'T allow you to create actual UDF 2.50 disk images (the requirement for actual Blu-ray Discs--even if not all players require the standard all the time).

It seems something has to be able to do this (or somewhere should be explaining what it is about linux/Ubuntu/whatever that is responsible for the limitation--what do I know, I'm a complete ******* idiot about things like this).

Anyway, I still haven't been able to find something to let me make a complete 1:1 copy of my BDMV on a disk image with UDF 2.50 (Blu-ray standard).

Any help, explanation, knowledge from the community would be fantastic!

---

