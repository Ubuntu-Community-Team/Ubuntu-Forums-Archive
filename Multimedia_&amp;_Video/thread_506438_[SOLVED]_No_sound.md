---
title: "[SOLVED] No sound"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by upthelum on 2007-07-21
I have no sound when using any media player but i do get system sounds and instant messaging sounds. I use an Audiopci sound card which is quite old but works fine and like i said i get sound through my monitor and speakers with other os's. I need my music so can anyone shed any light on this? Thanks...

---

### Post by jimbob on 2007-07-21
Try entering *[COLOR="Blue"]alsamixer[/COLOR]* in a terminal window and making sure everything applicable has the volume turned up and is unmuted.

Use the up/down arrows to change volume and the left/right arrows to move between outputs.  Use the letter "m" to mute/unmute.  There are additional selections to the right (off screen) so don't neglect them.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by upthelum on 2007-07-21
Thanks again...

---

### Post by upthelum on 2007-07-23
That helped but it seems to be getting intermittent now, sometimes it's fine with system sounds but none of my media players play sound.

---

### Post by noodleboy on 2007-07-23
Check your system>preferences>sound>devices tabs to make sure the os is using the proper outputs per events/apps.
Hope that helps.

Noodleboy.
:)

---

### Post by upthelum on 2007-08-03
After a few re-installs and upgrades it's working fine now. Thanks...

---

