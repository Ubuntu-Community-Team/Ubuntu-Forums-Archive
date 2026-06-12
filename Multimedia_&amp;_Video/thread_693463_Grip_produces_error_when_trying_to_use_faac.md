---
title: "Grip produces error when trying to use faac"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by pepclub on 2008-02-11
Hi, 

I'm trying to rip AAC audio using Grip, following the advice on[ this thread]("http://ubuntuforums.org/showthread.php?t=473212&highlight=ripping+AAC+audio"), I installed all the faac related stuff(see below) from synaptic, selected faac in the Grip encoder settings, but when I try to rip it gives me this error: "Invalid encoder excutable, check your encoder config..."

Any ideas?

Stuff I installed: 
Ubuntu Restricted Extras
All Gstreamer packages
faac
faad

---

### Post by logos34 on 2008-02-11
But that thread is about SoundJuicer (?).

You may have the path wrong.  It should be (default)

> /usr/bin/faac

check to verify that it is in fact there.

My encoder command line looks like this:

> -w -q 125 --writer %a --artist %A --album %d --title %n --track %t --year %y --genre %G %w

---

### Post by pepclub on 2008-02-11
> **logos34 said:**
> But that thread is about SoundJuicer (?).
Opps, I didn't link it to the right post, it should be this post, it recommends using Grip: [http://ubuntuforums.org/showpost.php?p=3023986&postcount=8](http://ubuntuforums.org/showpost.php?p=3023986&postcount=8)

> 
You may have the path wrong.  It should be (default)



check to verify that it is in fact there.

My encoder command line looks like this:

I got the path wrong, the default was just "faac" instead of "/usr/bin/faac". Everything is working great now, guess I won't be going to Windows anytime soon :). Thanks for your help!

---

