---
title: "Why the deuce does dssi-vst require wine 1.3 in Oneiric?"
date: 2011-11-16
forum: Multimedia Software
---

### Post by immerohnegott on 2011-11-16
Just wondering if anyone could shed a little insight into this. DSSI-VST requires wine 1.3 as a dependency, but wine 1.3 has no jack support. This pretty much breaks the whole purpose of the program, and I've been without success in getting any plugins to output sound with this setup. Is this just a packaging bug, or was a conscious decision made to change this dependency?

This is not the case in previous versions (11.04 had wine 1.2).

---

### Post by Trinley on 2011-11-29
Yes, this is something I'd like to know, too!

---

### Post by immerohnegott on 2011-11-29
Glad to see someone else wondering what's going on here. In the interim, it seems the version of LMMS in the repo (4.10) plays a lot more nicely with my Windows VST instruments than it did in the past - which is to say they actually run this time around. The GUI can be a bit buggy sometimes, but the plugins seem to be fully functional and qutie responsive.

Still, it'd be nice to have dssi-vst around anyway to allow direct MIDI control without the overhead of another host app, or to use something other than LMMS as a host/sequencer.

---

