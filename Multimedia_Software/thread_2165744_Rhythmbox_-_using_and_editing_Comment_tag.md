---
title: "Rhythmbox - using and editing Comment tag"
date: 2013-08-06
forum: Multimedia Software
---

### Post by bugbear6502 on 2013-08-06
I am using a (sequence of) scripts to massage and tag some mp3 files
prior to adding them to rhythmbox.

In particular I am using eyeD3 to add tags, including comments.

But rhythmbox seems to behave very intermittently;
I created a blank mp3 file, added a comment to it:

 eyeD3 --remove-all eg.mp3 
 eyeD3 -c "eng::harry" eg.mp3

I then dropped this into an empty rhythmbox;

This display correct with a "harry" comment, on exit the rhythmdb.xml
showed  <comment>harry</comment>

So far, so good.

I then (in a restarted rhythmbox) edited the comment to be "harry2",
and confirmed (by re-opening the edit dialog) that this had "taken".

Exiting and checking, I found that rhythmdb.xml
showed  <comment>harry</comment>
and that running eyeD3 on the mp3 showed
Comment: [Description: Comment] [Lang: XXX]
harry2

All looking good.

But on re-starting rhythmbox, and opening the properties dialog
yet again, it shows NO COMMENT.

Worse, on exiting from this run of rhythmbox, the
rhythmdb.xml shows NO COMMENT.

Since I am presently using the comment box to hold episode
synopses of radio programs, this is "unfortunate".

Versions:

rhythmbox 2.97
eyeD3 6.18
Description:    Ubuntu 12.10
Release:        12.10
Codename:       quantal

   BugBear

---

