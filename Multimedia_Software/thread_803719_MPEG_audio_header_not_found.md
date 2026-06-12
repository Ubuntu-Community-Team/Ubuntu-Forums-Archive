---
title: "MPEG audio header not found"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Paul_G on 2008-05-22
I recently installed Banshee 0.99 onto my AMD64 Hardy machine, in the process I removed my old version of Banshee 0.13.

When I came to import my music collection of some 1400songs only 300 are being imported with the rest being reported as errors with the report saying

'MPEG audio header not found.' this is obviously a large part of my collection. When I reinstalled the old Banshee through synaptic again the same amount of music (about 1100 songs) didn't import.

What is odd, is that all my music imports and plays in Rhythmbox, I have nothing against Rhythmbox it seems like a good player, but I really like the fact that Banshee still plays from the icon tray and I don't have to the program open tucked away on another desktop.

The error report on banshee doesn't give any help on this issue at all.
Has anyone else come across this at all and have any suggestions. 

'Please refrain from the why don't you just use rhythmbox ones, thanks'

---

### Post by juicyoner on 2009-03-08
Long time reader, first time poster.

I had the same exact problem, and realized that the songs that were causing it had the album artwork in the mp3 tags somehow. I was able to delete the album art associated w/ the songs in easytag - in the ID3 TAG area, Picture tag.

This made the files import into banshee w/o problem.

---

