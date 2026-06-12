---
title: "Persistent .mp3 ratings?"
date: 2010-12-09
forum: Multimedia Software
---

### Post by alanwalterthomas on 2010-12-09
I had rated (stars) a fair chunk of my music collection in rhythmbox. Then I clean installed 10.10, opened rhythmbox & banshee, & my ratings were all cleared.
I thought the rating out of 5 would be written to the .mp3 file's data section. Can that be done so that I don't lose track of what I like & don't like between installs?

---

### Post by samfuzz on 2010-12-11
i hope that you have saved your old rhythmbox database
in /home/user/.local/share/rhythmbox/rhythmdb.xml
if no , :(
because rhythmbox does not save ratings in metadata
there was a plug ins that saved ratings in metadata for rhythmbox :
[http://sites.google.com/site/airmind/rhythmboxplugins](http://sites.google.com/site/airmind/rhythmboxplugins)
usefull but import export only works for rhythmbox 
and it seems the plug ins doesn't work anymore with last version of rhythmbox.

a safe way to do that is to use the last freedesktop specification :
(FMPS, or Free Music Player Specs, an effort to have workable cross-player compatibility for difficult fields like rating and playcount)
[http://www.freedesktop.org/wiki/Specifications/free-media-player-specs](http://www.freedesktop.org/wiki/Specifications/free-media-player-specs)
[http://gitorious.org/xdg-specs/xdg-specs/blobs/master/specifications/FMPSpecs/specification.txt](http://gitorious.org/xdg-specs/xdg-specs/blobs/master/specifications/FMPSpecs/specification.txt)

few players support this specs at this moment, only one fully support them for all the know format (mp3, ogg, flac, mpc, m4a..)
it's gmusicbwroser with the devel version
[https://launchpad.net/~shimmerproject/+archive/ppa](https://launchpad.net/~shimmerproject/+archive/ppa)
(all my rated files are now tagged with FMPS field with gmusicbrowser)

but amarok will support this specs (jeff mitchell who wrote the specs is a dev from amarok), quodlibet will, clementine read the FMPS rating for mp3 id3 only, and perhaps banshee looks at this bug report :
[https://bugzilla.gnome.org/show_bug.cgi?id=532650](https://bugzilla.gnome.org/show_bug.cgi?id=532650)
[https://bugzilla.gnome.org/show_bug.cgi?id=602158](https://bugzilla.gnome.org/show_bug.cgi?id=602158)

---

### Post by utnubu(k) on 2011-01-31
Thank you Samfuzz, very helpful! I found out Amarok since version 2.4 has the option to read/write ratings and playcount as well :)

---

