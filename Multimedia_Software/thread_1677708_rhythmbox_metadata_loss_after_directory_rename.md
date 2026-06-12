---
title: "rhythmbox metadata loss after directory rename"
date: 2011-01-29
forum: Multimedia Software
---

### Post by InspiredIndividual on 2011-01-29
Rhythmbox seems unable to handle a directory rename. My problem is the following:

1. Create a playlist in Rhythmbox with some songs in it.
2. Close Rhythmbox.
3. Rename the directory with the songs in it.
4. Open Rhythmbox.
5. The songs are gone from Rhythmbox' index and can be found under "Missing Files". New versions of the songs show up, but this is not very helpful, as the playlist is empty.

I searched the web and found a known bug which occurs if step 2 is left out (that is, a directory rename with Rhythmbox open). However, in my case, even changing a directory name without Rhythmbox running breaks its file index.

This is highly annoying. Does anyone have an idea what's going on?

---

### Post by InspiredIndividual on 2011-01-29
I've still got no clue how to solve this particular problem, but I did manage to come up with a crude hack that mimics the desired behavior. For the sake of those struggling with the same problem, below a description of what I did to restore my playlists.

First, I located the xml-file containing my playlists with

```
find ~ | fgrep rhythm | fgrep playlist
```

I opened the file rhythmbox/playlists.xml with a text editor and replaced all instances of OLD_DIR_NAME with NEW_DIR_NAME. Very crude, but at least I think it works as it should.

---

