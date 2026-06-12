---
title: "blurry sound started recently, not the speakers' fault"
date: 2009-02-22
forum: Multimedia Software
---

### Post by v1nsai on 2009-02-22
So my sound playback all of a sudden has been horrible, completely full of static and almost unlistenable.  It hasn't always been this way and I can't think of anything that I might have changed to cause this, but I tested the speakers with my xbox and it's not their doing.

I've tried switching things around in Preferences > Sound but I'm not getting any positive response.  I was wondering if reinstalling my sound driver would work and how to go about this.  

I'm using a machspeed MSNV939 board with onboard sound, and I've been using the alsa sound driver, and though there is an Nvidia CK804 sound driver it has the same problem.

---

### Post by CaptainPatent on 2009-02-23
This sounds like the sound being turned way down for the card. Go into terminal and type 'alsamixer' this will pull up volume controls for your entire system.

Sometimes and for some unknown reason multimedia sounds get autoset too low. Try that out and let us know if it works

---

### Post by CaptainPatent on 2009-02-23
PS - there are some additional suggestions in this thread if you're still having trouble:

[http://ubuntuforums.org/showthread.php?t=987252&highlight=Hauppauge+1600+sound](http://ubuntuforums.org/showthread.php?t=987252&highlight=Hauppauge+1600+sound)

cheers!

---

### Post by v1nsai on 2009-02-23
cool thanks for the thread reference I didn't see that one, I'll post in there

---

