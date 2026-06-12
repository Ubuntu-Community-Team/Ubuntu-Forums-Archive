---
title: "Rhythmbox not playing anything?"
date: 2010-12-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ScislaC on 2010-12-27
It's been a couple weeks here now that Rhythmbox won't play anything for me (regardless of format). It shows the Play icon but the bar doesn't move and it's not reading audio from the files (it still reads tags and everything fine). Am I the only one this is currently happening to?

---

### Post by efflandt on 2010-12-27
I just use rythmbox for internet radio (background music), and that works fine.  I did see something some time ago when opening rythmbox that Ubuntu music store or something crashed (maybe when libs were being changed), but it is no longer on the list of stores, so no more errors about it.

Does **aplay -l** (small L) show audio devices and does **alsamixer** show necessary things unmuted (without MM)?  Does Sound Preferences show Outputs, and do any of them work with other audio applications (like any video players).  Flash actually uses default alsa audio, if for some reason alsa is not coordinated with pulse front end.

---

### Post by susema on 2010-12-27
Run it in terminal, what's error? Paste here please;

```
rhythmbox
```

---

### Post by foxmulder881 on 2010-12-27
Are you sure you've installed the gstreamer codecs?

---

### Post by ScislaC on 2010-12-27
aplay and alsamixer both report back everything as expected.

No terminal errors per-se... the only output is:
(rhythmbox:29260): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

Gstreamer should all be rockin' as this install has seen numerous dist-upgrades w/o issues (meaning it hadn't asked me to remove anything necessary) and Totem is still working fine.

---

### Post by mc4man on 2010-12-27
you may get some info from running rhythmbox in debug mode.
Some of the various choices would be this which will produce voluminous output (so much that I'd either output the terminal to file or in terminal - Edit - Profile Pref.'s - Scrolling, set the scrollback to 'unlimited'

rhythmbox --debug

Or much smaller - possibly nothing of use

rhythmbox-client --debug --enqueue --play /path/to/an/audiofile

I'd probably first create a new user, login to it and see if rhythmbox works there. Can point to or eliminate a setting(s) in your home dir.

---

### Post by Harry33 on 2010-12-28
Yes Rhythmbox work just fine in Natty.
You could also purge it and then clean home dir rhythmbox folders too:
  .cache/rhythmbox
 . gconf/apps/rhythmbox
 . local/share/thythmbox

So no need to create a new user then.

---

### Post by ScislaC on 2010-12-28
Tried with another user, all is well there.

Tried cleaning out all of the RB related settings in the user profile with the issue and after it scans to get everything back in, it still doesn't work.

Wow that debug mode outputs a ton of info. The only two things that seem possibly of interest are:

(09:03:52) [0x9978e68] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:841: No username set

(09:03:53) [0x9978e68] [slider_moved_callback] rb-header.c:676: slider is not dragging

---

### Post by mc4man on 2010-12-28
Maybe try deleting this file (assuming you deleted all that Harry mentioned
~/.gstreamer-0.10/registry.i686.bin
The only other one I see is this but don't think it matters
~/.gnome2/accels/rhythmbox

Otherwise it may be something not specific to rhythmbox, though possibly disable all the plugins and work back.
Does totem play back tracks?

---

### Post by ScislaC on 2010-12-28
Neither of those helped either. I'm guess the easiest "fix" at this point is to backup/move my homedir and start bringing stuff back in slowly.

---

