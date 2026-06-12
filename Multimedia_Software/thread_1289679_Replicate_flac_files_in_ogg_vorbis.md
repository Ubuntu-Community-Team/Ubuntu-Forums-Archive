---
title: "Replicate flac files in ogg vorbis?"
date: 2009-10-12
forum: Multimedia Software
---

### Post by jmidgley on 2009-10-12
Hi

I've had a search for this and I can't find quite what I'm looking for. I have a load of flac files on an Ubuntu server, and I'd like to replicate them in ogg format. I've got as far as using the 'name' command to replicate the structure under a different directory. I did this in the 'flac' directory from which all the other directories hang: 

find ./ -type d ! -name . -exec mkdir "../ogg/{}" \;

which worked a treat and I've successfully converted a file with oggenc.

What I'd ideally like is a script that traverses the flac directories, creating ogg files as it goes in the matching ogg directories. Even more ideally, a script that on a second pass would only convert newly added files...

Can anyone give me some pointers? 

Many thanks
John

---

