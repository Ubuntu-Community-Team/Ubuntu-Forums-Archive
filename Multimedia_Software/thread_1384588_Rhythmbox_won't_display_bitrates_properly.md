---
title: "Rhythmbox won't display bitrates properly"
date: 2010-01-18
forum: Multimedia Software
---

### Post by cmac_the_great on 2010-01-18
I've been using Rhythmbox since I got ubuntu in September, and this has never happened before. My music library is a mixture of CBR and VBR mp3, as well as FLAC files. CBR and FLAC display properly in the 'bitrate' column, but for some reason all new VBR files I add to my library recently display as being 48kbps instead of their actual respective bitrates. Any ideas?

---

### Post by cmac_the_great on 2010-01-18
Bump.

---

### Post by tns on 2010-10-18
I have the same problem. I verify with mediainfo than an entire album is encoded at v0, but Rhythmbox reports most tracks to be at 96kbps. I've verified that this is not a problem with gstreamer.

Rhythmbox 0.12.8 (is the version number a hint?)
Ubuntu 10.04 SMP i686

I posted a bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=632517](https://bugzilla.gnome.org/show_bug.cgi?id=632517)

I'm glad I caught on to this little pitfall before I got too far into my "PURGE THIS HUGE LIBRARY OF ALL LOW QUALITY ALBUMS! THEY MUST DIE! WHERE MY FLAC AT???" project... Whew.

[edit: sorry for bringing up an old topic, but this thread was at the top of Google.]

---

### Post by ozzman2 on 2010-10-19
Hey guys.

Don't know if this will help you, (I don't have any of the "lossy" formats in my machine).

Sometimes my FLAC files appear as "unknown" in the bitrate column in Rhythmbox.  Incidentally, I am unable to change any of the tag attributes when this happens (ie. right clicking, and going into properties, whatever I change reverts back to what it was originally moments later).

My workaround is this:
1.)  Edit the sound file with "EasyTAG" (it's in Ubuntu Software Centre).  Change some part of the tag information and save it.
2.)  Go back into Rhythmbox, right click and go to properties one more time.  Change some information and close the dialogue box.
----
Moments later, the bitrate shows up as "Lossless".

hope that helps.

---

### Post by tns on 2010-10-19
I actually modified the VBR album that I was testing with EasyTAG in the middle of my testing with no change. I found a reference to Rhythmbox having trouble with VBRI headers in certain situations, though, so I tried the replace/rebuild VBR data options in mp3diags. They didn't do anything to change how rhythmbox reports the bitrate.

I've never used mp3diags before, so maybe I'll find a combination of transformations that will serve as a workaround. I'll play with it a little more tomorrow and report back if it's good news.

---

