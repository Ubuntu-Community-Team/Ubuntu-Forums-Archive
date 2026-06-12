---
title: "separate login for TV out"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by machs_fuel42 on 2007-09-10
I'm on my way to setting up my 'buntu box to act as a media player.  I've got freevo installed and working, lirc works now and tv out works (twinview clone) thanks to Envy

I've got a separate user for freevo which logs in after 55 seconds. I've followed this guys guide

[http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)

So i can have two separate X Layouts. One for my desktop use and one for freevo. I've got a small script to setup the python path for lirc and start freevo using the tv layout.

```
#script to import pylirc and then start freevo!
#
export PYTHONPATH=/usr/lib/python2.3/site-packages:$PYTHONPATH
/usr/bin/xinit /usr/bin/freevo -- /usr/bin/X :1 -layout tv
```

The scripts works fine when ran from a terminal;  X starts and freevo begins on TVout.  However when i login as my freevo user (which runs this script) X crashes and burns.  i'm not sure what the problem is.. my .xsession-errors isn't helping out right now..

```
freevo@electric-monk:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "freevo"
/etc/gdm/Xsession: Beginning session setup...
```

---

### Post by machs_fuel42 on 2007-10-15
nothing eh?
I've been messing about with GDM configs and different layouts.  i've hit a bit of a wall...
my layouts work, and i can start freevo on the tv fine, but doing so disables my desktop.

maybe i should restate what i'd like to achieve.

I'd like to have my LCD as my standard gnome desktop.  gdm would take care of this and allow multiple users to login.  normal keyboard and mouse inputs. 

I'd like my tv to display freevo - all of the time. I'm using a remote for freevo, so keyboard and mouse need to be ignored.  It would be nice if loaded user prefs for my freevo user...

How can i configure X / gdm to work like this?

---

