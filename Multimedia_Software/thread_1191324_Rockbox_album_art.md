---
title: "Rockbox album art"
date: 2009-06-18
forum: Multimedia Software
---

### Post by jonnich90 on 2009-06-18
I am using Rockbox on my Sansa e280, and I was wondering if there was an easy way to get all the album art I already have with the music (imbedded and not imbedded) to show up in rockbox.  Maybe a script or program?

---

### Post by enigmaniac23 on 2009-07-02
I use Amarok 1.4 to listen and organize my music and this site has the instructions for what I did to get all of the Album art copied over to each music folder.
[http://www.64bitjungle.com/ubuntu/batch-export-amarok-album-art-to-the-albums-containing-directory/]("http://www.64bitjungle.com/ubuntu/batch-export-amarok-album-art-to-the-albums-containing-directory/")
This will save the album art as "cover.png" in each folder.  Rockbox, however requires that the album art be a .bmp, so I found a quick script to find all of the cover.png files and convert them to cover.bmp. I run this from my Music directory.
```
find . -name cover.png > covers.txt
while read current
do
 convert -resize 100x100! "$current" "$(dirname "$current")/cover.bmp"
done < covers.txt
```

All of this of course depends on using Amarok as my music player, since it stores it's album art in a specific way.  I also have a script that uses rsync to keep my Music folder on my computer synced with the Music folder on my MP3 player, so that any changes to the music, such as genre, name, added music, playlists, cover art, etc will get synced between my computer and MP3 player.

---

