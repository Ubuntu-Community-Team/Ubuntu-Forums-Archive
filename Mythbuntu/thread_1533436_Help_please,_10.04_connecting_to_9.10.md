---
title: "Help please, 10.04 connecting to 9.10"
date: 2010-07-18
forum: Mythbuntu
---

### Post by dardack on 2010-07-18
I upgraded my 9.10 server/frontends with mythbuntu debs (auto-builds).  On my laptop with 10.04, i did the same.  However:

Server displays this:

Please attach all output as a file in bug reports.
MythTV Version   : 25366
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.201000710-1
QT Version       : 4.5.2


My laptop displays this:
Please attach all output as a file in bug reports.
MythTV Version   : 25356
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.201000617-1
QT Version       : 4.6.2

So they don't match, can anyone help.  There is no update in the update-manager for my laptop.

---

### Post by tgm4883 on 2010-07-18
Check for updates again. I can see that fixes25368 is the latest version in both karmic and lucid

---

### Post by ian dobson on 2010-07-18
Hi,

Looks as if something is really screwed up on the server (Network Protocol : 23056), the current protocol version for 0.23 is 56, so try running an update.

Regards
Ian Dobson

---

### Post by ron!b on 2010-07-18
I can confirm the same problem.  I have a separate backend/frontend and frontend-only setup.  The frontend works on the combined system but doesn't on the frontend only system.  

I have updated and rebooted both systems.

---

### Post by dardack on 2010-07-18
> **ron!b said:**
> I can confirm the same problem.  I have a separate backend/frontend and frontend-only setup.  The frontend works on the combined system but doesn't on the frontend only system.  

I have updated and rebooted both systems.

yea my laptop only has a frontend, there are no updates for either.

---

### Post by ian dobson on 2010-07-18
Hi,

Can everyone with problems check what mirrors they're using.

I'm running the auto-builds on my systems and am not seeing any problems (using the CH - Swiss mirrors).

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-18
yea, everyone post their /etc/apt/sources.list.d/mythbuntu-repos.list

---

### Post by Singing Dwarf on 2010-07-18
I can confirm the same problem, after upgrading my frontend/backend combination this afternoon.

Contents of /etc/apt/sources.list.d/mythbuntu-repos.list on the FE/BE:

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23 ubuntu lucid main
```My BE only has the same entries, but trunk-0.22 in all instances instead of 0.23, HOWEVER, all three lines are commented out 
```
# disabled on upgrade to lucid

```

---

### Post by dardack on 2010-07-18
Ok, for my 9.10 machines (1 master BE, 2 frontend's only):

sources is:

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu karmic main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu karmic main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu karmic main
```

on my laptop that can not connect:

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
```

EDIT:
I just updated my laptop, now my version is:

Please attach all output as a file in bug reports.
MythTV Version   : 25368
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.201000710-1
QT Version       : 4.6.2


so somehow the network protocol finally updated correctly, before it was just saying 56, not 23056, which all my other mythtv machines where saying.  So can be marked as fixed for me.

---

### Post by ian dobson on 2010-07-18
Hi,

There's something wrong here. Mythtv 0.23 use the protocol version 56 for some reason your system is adding 230 to the front of the protocol version.

On my system I see:-
```

mythfrontend.real --version
Please attach all output as a file in bug reports.
MythTV Version   : 25368
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.201000710-1
QT Version       : 4.6.2

mythbackend --version
Please include all output in bug reports.
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2

```

Frontend using mythbuntu/auto-builds, backend is normal ubuntu standard repositries, and have no problems with mythtv.

Regards
Ian Dobson

---

### Post by dardack on 2010-07-18
> **ian dobson said:**
> Hi,

There's something wrong here. Mythtv 0.23 use the protocol version 56 for some reason your system is adding 230 to the front of the protocol version.

On my system I see:-
```

mythfrontend.real --version
Please attach all output as a file in bug reports.
MythTV Version   : 25368
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.201000710-1
QT Version       : 4.6.2

mythbackend --version
Please include all output in bug reports.
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2

```

Frontend using mythbuntu/auto-builds, backend is normal ubuntu standard repositries, and have no problems with mythtv.

Regards
Ian Dobson

Your frontend shows 230 also, so don't understand.  Before my laptops frontend was showing 56, but my backend (and other mythtv dedicated frontends) were showing 23056.  Now my laptop shows 23056 for the network protocol.  But just straight 56 wouldn't connect to 23056.  Yours is backwards from mine.  Your from what mine was.  Your backend is 56, but frontend is 23056, where as my original backend was 23056, but laptop frontend was just 56.  The update last nite from autobuilds fixed this for me.

---

### Post by tgm4883 on 2010-07-18
> **Singing Dwarf said:**
> I can confirm the same problem, after upgrading my frontend/backend combination this afternoon.

Contents of /etc/apt/sources.list.d/mythbuntu-repos.list on the FE/BE:

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23 ubuntu lucid main
```My BE only has the same entries, but trunk-0.22 in all instances instead of 0.23, HOWEVER, all three lines are commented out 
```
# disabled on upgrade to lucid

```

Sounds like you have auto-builds disabled on your backend then. (It gets completely disabled on a distro upgrade. I would run 'dpkg-reconfigure mythbuntu-repos' then do another upgrade

---

### Post by ian dobson on 2010-07-18
Hi,

Just restarted my frontend this morning and I'm getting the same error that the backend is using protocol 56 and the frontend is using 23056 and are not compatible with each other.

Note my frontend is using auto-builds, my backend isn't.

This appears to have just happened with the newest updates to mythfrontend.

Here's a dump of my repos file:-
```

cat  /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main

```

Something is screwed up with the auto-builds. Even trunk doesn't have such a high protocol version.

It appears to be related to this [http://www.gossamer-threads.com/lists/mythtv/users/443645](http://www.gossamer-threads.com/lists/mythtv/users/443645)

I was under the impression that mythtv that The Frontend/Backend can communicate with each other as long as they're running the same version (I have 0.23 on the backend and Frontend). I don't really want to go over to auto-builds on my backend if I can avoid it, the backend is used for other things and stability is more important than anything else.
  
Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-19
> **ian dobson said:**
> Hi,

Just restarted my frontend this morning and I'm getting the same error that the backend is using protocol 56 and the frontend is using 23056 and are not compatible with each other.

Note my frontend is using auto-builds, my backend isn't.

This appears to have just happened with the newest updates to mythfrontend.

Here's a dump of my repos file:-
```

cat  /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main

```

Something is screwed up with the auto-builds. Even trunk doesn't have such a high protocol version.

It appears to be related to this [http://www.gossamer-threads.com/lists/mythtv/users/443645](http://www.gossamer-threads.com/lists/mythtv/users/443645)

I was under the impression that mythtv that The Frontend/Backend can communicate with each other as long as they're running the same version (I have 0.23 on the backend and Frontend). I don't really want to go over to auto-builds on my backend if I can avoid it, the backend is used for other things and stability is more important than anything else.
  
Regards
Ian Dobson

Yea that appears to be exactly what happened. Usually there isn't  a change in a release branch that would require a change in the protocol version, so I'm not sure why upstream changed it. To resolve that, you will either need to upgrade the backend, or downgrade the frontend to a version that works.

---

### Post by jamesarbrown on 2010-08-19
Ack..... yes it would seem they have pushed a protocol change, inbetween major releases.

I known things must progress.... but what a stupid thing to do. Its ok for yum or apt-get.... but for those that have had to compile for various reasons this is a real pain.

Like my minimyth is a compiled version due to regression in openchrome. 

James

---

### Post by tgm4883 on 2010-08-19
> **jamesarbrown said:**
> Ack..... yes it would seem they have pushed a protocol change, inbetween major releases.

I known things must progress.... but what a stupid thing to do. Its ok for yum or apt-get.... but for those that have had to compile for various reasons this is a real pain.

Like my minimyth is a compiled version due to regression in openchrome. 

James

I pushed a fix for this today, so the latest auto-builds for 0.23.0 for karmic and lucid should be using protocol version 56.

You should see that in version 0.23.0++fixes25362-0ubuntu0++mythbuntu1

---

### Post by Thomas.Husemann on 2010-08-20
> **tgm4883 said:**
> I pushed a fix for this today, so the latest auto-builds for 0.23.0 for karmic and lucid should be using protocol version 56.

You should see that in version 0.23.0++fixes25362-0ubuntu0++mythbuntu1
Hi TGM4883,

this update grilled my setup at home. All other clients are using the branch proto #. Please go back to proto 23056.

Thanks in advance

Regards, Thomas

---

### Post by tgm4883 on 2010-08-20
> **Thomas.Husemann said:**
> Hi TGM4883,

this update grilled my setup at home. All other clients are using the branch proto #. Please go back to proto 23056.

Thanks in advance

Regards, Thomas

There isn't a way to go back to proto 23056 on 0.23.0 because protocol version 23056 isn't on 0.23.0, it's on 0.23.1. You can do a reconfigure on mythbuntu-repos and select 0.23.1 and then update. That should resolve it for you.

Reconfigure it by either going into MCC or by doing a dpkg-reconfigure mythbuntu-repos

PS. I've always hated thanks in advance, as it basically means you are too lazy to confirm I have fixed the issue. This hurts twofold, as other users might have the same issue don't know if it was resolved either.

---

### Post by Thomas.Husemann on 2010-08-20
> **tgm4883 said:**
> There isn't a way to go back to proto 23056 on 0.23.0 because protocol version 23056 isn't on 0.23.0, it's on 0.23.1. You can do a reconfigure on mythbuntu-repos and select 0.23.1 and then update. That should resolve it for you.

Reconfigure it by either going into MCC or by doing a dpkg-reconfigure mythbuntu-repos

PS. I've always hated thanks in advance, as it basically means you are too lazy to confirm I have fixed the issue. This hurts twofold, as other users might have the same issue don't know if it was resolved either.

You fixed the issue.. ;-) the last update pulled .23.0 . I was on 23.1. The reconfigure solved my problem.

Thanks, Thomas

---

### Post by jtree on 2010-08-24
tgm4883, 

Reconfiguring to use 0.23.1 fixed my version problem.  However, the US repository does not include "0.23.1".  I had to use the PPA repository to access version "0.23.1".

Thank You!
Joshua

---

### Post by tgm4883 on 2010-08-24
> **jtree said:**
> tgm4883, 

Reconfiguring to use 0.23.1 fixed my version problem.  However, the US repository does not include "0.23.1".  I had to use the PPA repository to access version "0.23.1".

Thank You!
Joshua

Yep. Trying to work out why US, UK and FR don't have 0.23.1. Thanks

---

### Post by raid996 on 2011-01-07
Hi all, I'm having the same problem with my installation on top of a regular Ubuntu installation I have:
[LIST]
[*]PC with frontend/backend with 10.04 and protocol 56 (v. 0.23.0)
[*]Laptop with frontend with 10.10 and protocol 23056 (v. 0.23.1)
[/LIST]

What can I do to solve the problem?
Is it safe to use the PPA repos for my server (it has other functions so I really need it to be stable) and will it solve the problem or do I have to downgrade my frontend?
And how do I do that....??

---

### Post by thatguruguy on 2011-01-07
> **raid996 said:**
> Hi all, I'm having the same problem with my installation on top of a regular Ubuntu installation I have:
[LIST]
[*]PC with frontend/backend with 10.04 and protocol 56 (v. 0.23.0)
[*]Laptop with frontend with 10.10 and protocol 23056 (v. 0.23.1)
[/LIST]

What can I do to solve the problem?
Is it safe to use the PPA repos for my server (it has other functions so I really need it to be stable) and will it solve the problem or do I have to downgrade my frontend?
And how do I do that....??

I'm not sure what you mean by "other functions."  However, you can update the mythtv package on your box running 10.04 without changing anything else on that box, if that's what you're asking.  Just update the repo through the mythbuntu control center.  In fact, you can update both boxes to run myth .24, if you'd like, without otherwise changing the OS on either box.

---

### Post by raid996 on 2011-01-07
> **thatguruguy said:**
> I'm not sure what you mean by "other functions."  However, you can update the mythtv package on your box running 10.04 without changing anything else on that box, if that's what you're asking.  Just update the repo through the mythbuntu control center.  In fact, you can update both boxes to run myth .24, if you'd like, without otherwise changing the OS on either box.

I meant that my ubuntu box has other functions, I use it as a backup server, mail server, lamp server and file server.
Basically I now have all my media shared in a NAS that has an automatic redundant copy, since it's not the fastest device on earth I wanted to port all my media to the server and have 1 working copy of everything + 2 backups of everything with daily and weekly incremental backups.
I wanted to achieve this also by sharing the TV signal and have a complete setup, thus the backend/frontend needs.

What you propose though poses a problem for me since I would like to avoid installing a whole load of stuff that I will not need (I already have plenty of stuff working on that box right now as it is), installing the mythbuntu-center package would install me the whole mythbuntu stuff right?
Do i really need this, isn't it posible to fix the problem by avoiding mythbuntu stuff?

---

### Post by thatguruguy on 2011-01-07
> **raid996 said:**
> installing the mythbuntu-center package would install me the whole mythbuntu stuff right?
No.

> **raid996 said:**
> Do i really need this, isn't it posible to fix the problem by avoiding mythbuntu stuff?

I think you can install the repos from the mythtv website.

---

### Post by tgm4883 on 2011-01-07
> **thatguruguy said:**
> No.



I think you can install the repos from the mythtv website.

[http://mythbuntu.org/repos](http://mythbuntu.org/repos)

You don't need to install the control center, it's configurable via debconf.

---

### Post by raid996 on 2011-01-07
Awesome thx! sorry to be such a bother but I really don't like installing useless stuff, I am now updating my laptop to 0.24 will do the same for backend, thx!

EDIT: I talked too soon, couldn't even try if it works because it all just went awall... now the frontend that used to work doesnt work anymore, it doesn't lock to a single channel (before it did and pretty well too), I've been trying to sync again the channels but it was all useless... it doesnt grab the listings, it doesnt sync the channels, it doesnt see the videos specified in the path, music is jittery...
a total mess... and now the dvb-t card stopped working also with other sw as vlc or kaffeine... it's a total mess... I'm just gonna erase every trace of mythtv...

---

### Post by raid996 on 2011-01-09
Ok, now this is weird... when I had myhttv installed i tried to use w_scan to scan the channels and feed myth with a channel.conf... didn't work... vlc wouldn't work, kaffeine wouldn't work.

Now I removed everything related to myh and guess what... w_scan, kaffeine and vlc work... I'll try one more time next week to get it up & running... let's hope it'll work this time.... I'll let you know

---

### Post by newlinux on 2011-01-09
You may have conflicts if you have tuners being used by mythbackend (even if you aren't watching them - if they are just configured in mythbackend and mythbackend is running) and other external programs at the same time. You will probably want to stop mythbackend before using the tuners in other programs, if you didn't already.

---

### Post by raid996 on 2011-01-14
> **newlinux said:**
> You may have conflicts if you have tuners being used by mythbackend (even if you aren't watching them - if they are just configured in mythbackend and mythbackend is running) and other external programs at the same time. You will probably want to stop mythbackend before using the tuners in other programs, if you didn't already.

Yeah I figured that out... fact is the dvb-t adapter works great with other software, I just scanned th whole thingy with w_scan and I can watch all my channel with vlc at an exceptional quality...
I'll try to set a vls now to see if I can access the dvb through web interface or somthing like that, if it doesnt work I'll be trying myht once more...

---

