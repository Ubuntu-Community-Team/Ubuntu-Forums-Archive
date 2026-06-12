---
title: "how to use VLC &amp; LIRC in Edgy?"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by mageus on 2007-03-10
I've got the latest Edgy repository version of VLC (0.8.6) and the latest LIRC.  I want to use my remote control to control VLC.

Using irexec, vlc doesn't respond to any of the lirc commands.
   - I have 'infrared remote' checked off in Prefs -> Interface -> Control Interfaces
   - When running 'vlc -I lirc' it says 'lirc interface error: lirc initialisation failed'
   - Do I have to recompile vlc to enable lirc support?

If I can't get vlc to respond to lirc directly, I heard I can do it using the rc interface for vlc (command shell).  How would I go about setting this up?


I've got working vlc and lirc installs.  I know irexec works because I use it to control Rhythmbox.


TIA

---

### Post by mageus on 2007-03-11
The Ubuntu repository version of vlc _does_ work with lirc.  I was using the information from a couple of peoples' posts to set up the the config key bindings for my .lircrc file.

I used vlc --longhelp, grepped for '--key-' and found the correct flags.

---

