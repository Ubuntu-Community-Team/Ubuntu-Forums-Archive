---
title: "Requirements for a good classical music player"
date: 2022-03-01
forum: Multimedia Software
---

### Post by pwabrahams2 on 2022-03-01
As far as I know, there are no music  players in Ubuntu-world that are even nearly adequate for playing classical music. To prove my point, I will set out four design requirements:

1. **The ability  to handle recursive playlists. **The classical repertoire has a deeply nested structure.  For example, we have Beethoven / String Quartets/ Early, Middle, and Late Quartets /  Individual Quartets / Movements.  The movements are "songs" in  the lingo of music players. The shuffle operation should be  able to operate at any level, or a combination of levels.

2. **The ability to define new genres. **None of the existing music players even come close to recognizing the genres of classical music.  The solution is to enable a collector to define her own genres, or even better, a hierarchy of genres; merely adding a fixed set of genres is not adequate.

3. [B]The ability to utilize an existing music database. 

4. The ability to access an open-ended set of online streams.

[/B]It wouldn't be very hard to enhance one of the existing players such as Clementine or Elisa to meet these requirements.  I would have done it myself, but at age 86 my programming abilities are not what they used to be.

---

### Post by QIII on 2022-03-01
This might be a subject better addressed with the developers of those applications.  This is a humble peer-to-peer end-user support forum.

---

### Post by pwabrahams2 on 2022-03-01
I had several reasons for writing this post.  Most of the existing players have  no one interested in maintaining or enhancing them, so there's no user community to draw on. Elisa seems to have a few people interested in it, but their interest is very limited.  The documentation is sketchy, and I couldn't find anything that would help me adjust the font sizes nor anyone to ask about it.  

I don't think the authors of any of the the existing players care much about classical music, so they  have  no motivation to make enhancements in that direction.  I'm hoping that  someone in the not-tiny Ubuntu community has the right combination of interest and skill, and this forum was the best place  I could find to post bout it.

---

### Post by TheFu on 2022-03-01
I use a bash script that uses '**find**' to create playlists on the fly for **mpv** or **mpd** to use.  To me, a file system layout **is** a hierarchical database. No need for anything else.

With mpd, we can use any mpd-client GUI we like. There is a specific playlist directory and all playlists (m3u) just need to be relative from the top music directory.  As for Genres, I make up my own all the time and haven't noticed any issues with any players, but I haven't looked too hard, since my directory layout is typically:
TOP/<genre>/<artist>/<album>/<trk#>-<title>

So, I have a "Lounge" genre ... for music I've only heard in famous lounge acts, usually from the 50-70s.

The "shuffle" part is hard.  Either I play albums in order to hear the story or I live with the mix, which is a little painful when the wrong track plays following.  That problem exists in albums outside of classical too, BTW.  *You Really Got Me* can only follow *Eruption*. Can't happen any other way.

---

### Post by pwabrahams2 on 2022-03-02
Your approach of using **mpd** and a bash script clearly works for you, but how can other people utilize it easily?  I wasn't familiar with **mpd **at all; I've learned what it is, but it seems one has to know it pretty well even to get started.

Yes, the Linux filesystem provides a hierarchical structure, but I don't know how to put that information to use.

---

### Post by TheFu on 2022-03-02
Not all solutions fit all needs. What is your true interest level in having a little bash script that plays music and keeps a list of playlists in a DB (a DB is just a text file in this case).

---

