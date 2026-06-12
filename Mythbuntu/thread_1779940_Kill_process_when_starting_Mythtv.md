---
title: "Kill process when starting Mythtv"
date: 2011-06-11
forum: Mythbuntu
---

### Post by Derek Karpinski on 2011-06-11
I'm running mythtv in Ubuntu 11.04, and I'm also running redshift. [http://jonls.dk/redshift/](http://jonls.dk/redshift/) I'd like to kill redshift when starting mythtv.  Is there a way in the myth front end setup that will let me?  Or should I write a script to kill it, then start mythtv?

The command to temp. toggle redshift is:
killall -USR1 redshift

and the same command turns it back on, which I'd like to do when I exit mythtv.

MODS: If this is the wrong section to post in since I'm using Ubuntu, feel free to move it.  Just thought I'd get more reads here.

---

### Post by klc5555 on 2011-06-11
> **Derek Karpinski said:**
> I'm running mythtv in Ubuntu 11.04, and I'm also running redshift. [http://jonls.dk/redshift/](http://jonls.dk/redshift/) I'd like to kill redshift when starting mythtv.  Is there a way in the myth front end setup that will let me?  Or should I write a script to kill it, then start mythtv?

The command to temp. toggle redshift is:
killall -USR1 redshift

and the same command turns it back on, which I'd like to do when I exit mythtv.

MODS: If this is the wrong section to post in since I'm using Ubuntu, feel free to move it.  Just thought I'd get more reads here.

How are you "starting mythtv" in general? I assume that what you're referring to is starting mythfrontend, since even in Ubuntu proper the backend is normally started automatically at boot somewhere toward the end of the upstart scripts. mythbackend therefore ought to be already running before you have the opportunity to issue a command to kill anything.

So if this is just killing a userspace app prior to starting mythfrontend, I'd go with a three-line bash script: first line toggles off your app, second line runs mythfrontend, third line (which shouldn't run until after mythfrontend exits) toggles redshift back on.

---

