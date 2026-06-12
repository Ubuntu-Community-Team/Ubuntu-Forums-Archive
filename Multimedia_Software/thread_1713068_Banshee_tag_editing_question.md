---
title: "Banshee tag editing question"
date: 2011-03-23
forum: Multimedia Software
---

### Post by MikeyDL on 2011-03-23
I've been using Banshee and love it.  I spent some time editing song tags in Banshee to get compilation albums to group and such.  I keep my music on a dropbox so it's linked to to multiple computers.  I noticed that when I installed banshee on a new computer that the albums weren't grouping after I had fixed up the tags on another system.  I'm guessing that banshee must have some sort of database for the library and that some of those tags aren't coded into the actual song file but a library database.  Is it possible to move the library database over to dropbox and then have all my albums tag edits work on any system with Banshee?

---

### Post by jettjunker on 2011-05-24
I'm not sure if it'll work, but banshee has a db (and other files) in ~/.config/banshee-1/ ; you could try copying that over.

If you want banshee to 'write metadata to files', there's a checkbox for that in Edit -> Preferences. (I'm also not sure that works perfectly, for all fields).

---

### Post by MikeyDL on 2011-05-27
Thanks!  I'll give those a shot!

Just wish there was an option to define where the db goes then I could stuff it in dropbox!

---

### Post by nutznboltz on 2011-10-29
Look on the "Edit" menu for "Preferences".

Under "General Preferences" set the checkbox by "Write Metadata to Files".

---

