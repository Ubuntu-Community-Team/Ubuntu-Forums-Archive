---
title: "Daap server and Windows Client"
date: 2013-03-09
forum: Multimedia Software
---

### Post by Stephen_at on 2013-03-09
I used to have a nicely working mt-daap server which my old laptop (connected to my amp) running an old version of itunes could connect to and I could listen to music.

I upgraded to 12.0.4 and the replacement forked-daapd is pretty much total junk. I get disconnects (it just stops playing music which is apparently a known bug that has been outstanding for over a year), I get buffering errors. If I stop and start the forked-daapd daemon it hammers my hard drives for over 45 minutes during which time its pretyt much unrepsonsive to connections. It would seem that forked-daapd is a basically as dead as mt-daapd.

I looked at putting tangerine on their (despite my dis-like of mono) but it looks like that it is as broken when it comes to itunes.

Installed Amarok on my old laptop... no go. 

So does anyone have a solution for a Windows XP laptop streaming music from a 12.0.4 server in terms of server and client software?

---

### Post by tgalati4 on 2013-03-09
Have you tried running rhythmbox on the server with the daap plug-in enabled?  Is the Ubuntu machine a desktop being used as a server?  Or is it a true server with no desktop environment?

Rhythmbox does not explicitly use the forked-daapd framework, but I don't know what the plug-in daap functionality is based on.  So only testing will tell if it works in your environment.

---

### Post by Stephen_at on 2013-03-09
The server is headless with no GUI on it at all. 

Mt-daap had its fauilts but in so many ways forked-daap is a huge leap backwards, and is more broken than mt-daap was

---

### Post by tgalati4 on 2013-03-09
If the rhymbox daap plug-in was based on the older mt-daap code, then you might get back that functionality.  You can still install rhythmbox on your headless server and run it through an ssh -2 -Y session with a display switch:

       --display=DISPLAY
              X display to use

*env* or *$DISPLAY* to get your DISPLAY setting.  Yes, it will pull in a bunch of xorg libraries and will be running the xorg server (but without an actual display) but then you have access to a lot more multimedia clients (via ssh).

An alternative is to install mt-daap by pulling in a deb package from an older Ubuntu distro from [http://packages.ubuntu.com](http://packages.ubuntu.com) .  There may be some breakage, but it also might work!

Lucid looks like the latest distro to have it.  [http://packages.ubuntu.com/lucid/mt-daapd](http://packages.ubuntu.com/lucid/mt-daapd)  That's an old release for sure.

Perhaps you could provide a list of broken things (and regressions) in forked-daap so that they can be worked on by developers.

I run a freenas server that runs mt-daap ([http://nas4free.org](http://nas4free.org)), so I haven't experienced forked-daap behavior--yet.

---

### Post by Stephen_at on 2013-03-10
The problems with forked-daapd are well know if you browse its gitbun repository  - there are even some partial patches, some of them submitted over a year ago,  but they've not been properly pulled and the developer of forked-daap is, as I undertstand it, the maintainer of the application in the ubuntu builds and he seems to be on extended leave so nothing is getting pulled back into the builds.

I could pull and rebuild mt-daap. I'd actually fixed it for one of the problems with itunes but I think I junked it when I upgraded, and digging round in other people's source code trying to fix odd things is not really the most fun thing to do.

Running a gui app on the server just to provide a music share seems extremely wrong....

I wonder how freenas are getting round the problems with mt-daap? Either they're maintaining it or its not going to work with itunes or some versions of rhythmbox.

---

### Post by Stephen_at on 2013-03-10
It gets worse..:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=688538](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=688538)

From: Ana Guerrero <ana@debian.org>
To: [email]submit@bugs.debian.org[/email]
Subject: O: forked-daapd -- media server with support for RSP, DAAP, DACP and
 AirTunes
Date: Sun, 23 Sep 2012 16:57:18 +0200

Package: wnpp
Severity: normal

The current maintainer of forked-daapd, Julien BLACHE <jblache@debian.org>,
has retired.  Therefore, I orphan this package now.


So there is NO daap server package in Ubuntu that is maintained....

---

### Post by tgalati4 on 2013-03-10
Time for you to step up to the plate.  The freenas version is probably the Hardy or Lucid version, and it works on my older powerbook with an old version of iTunes, and it works with older versions of Rhythmbox, so as long as you have old equipment and software you are OK.  If you want the newer stuff, then it sounds like there is some debugging to do.

---

### Post by Stephen_at on 2013-03-10
Well I got a version of forked-daapd on my laptop to support itunes 10, which is fine for what I need. Wont work with 11 - just disconnects immediately. So I'll push that over to my server and recompile there and see if its reliable against a much larger library of tunes.

The problem is I am not a C programmer....

---

