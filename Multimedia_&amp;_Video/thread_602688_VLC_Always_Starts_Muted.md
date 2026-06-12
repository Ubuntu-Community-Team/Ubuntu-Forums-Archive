---
title: "VLC Always Starts Muted?"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by NoVista on 2007-11-04
Starting about a month ago, everytime I start VLC to watch TV, it always starts with the volume control in the muted position.
I've tried closing it with the volume un-muted, and have triple checked the VLC audio prefernces, yet I can't seem to make it start un-muted.

Any VLC guru's out there?

---

### Post by A-dogg on 2008-01-10
Having the exact same problem. It's not muted out of my speakers since even when VLC is muted, as my system volume is up I can still hear audio (which I don't quite understand, but whatever). But it seems to make the audio harsher when it plays with VLC is "muted".

---

### Post by NoVista on 2008-01-10
The problem eventually cleared up for me. I have no idea what caused or corrected it.
One day I just went to start VLC and it was un-muted and has stayed that way ever since.

---

### Post by AndrooUK on 2008-07-19
Resetting the settings will work... if you go to Settings/Preferences, Audio tab, check Enable audio checkbox, and ensure that default audio volume is 512 or less (512 being 100 % volume), then Save (or just use the Reset All button if you aren't bothered about settings you may have configured, or haven't changed the default settings for anything else).

For some reason, it does a weird scaling... 1024 is not full volume, it is a value that VLC interprets as higher than full volume, so it starts muted.

Don't know why this is, but there you go!  :)

---

### Post by A-dogg on 2008-07-21
Bro, you are a GOD. That fixed it. Permanently. Thank you!

---

