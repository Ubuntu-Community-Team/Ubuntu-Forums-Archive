---
title: "Music library managment on a headless Ubuntu server"
date: 2015-11-11
forum: Multimedia Software
---

### Post by alasdair3 on 2015-11-11
Quick question:

I'm running an Ubuntu media server with subsonic and Plex. 

Can anyone recommend a good App for music library management - i.e. tag editing, meta-data look-up, file renaming, possibly transcoding - that can be run headless? 
Some kind of UI - e.g. web-based - would be helpful.

Many thanks in advance for your suggestions.

---

### Post by TheFu on 2015-11-11
Why not use **sshfs** to mount the storage do a desktop and manage the media that way?
Then just tell PlexMS to refresh.  You don't need to sshfs, nfs would work just as well, but an sshfs mount can be created by any userid with ssh access.

Don't know about transcoding, but I use Clementine for tag management. It has a mode that will use directory structures to create tags.  I find that very handy,  genre/artist/album/##-title.ext  is my collection layout.

If you want a CLI solution, id3tag and **id3ren** are what I've wrapped scripts around.  
For transcoding,  **ffmpeg** is THE tool, assuming **lame** isn't sufficient.

The business-end of my script:
 ```
  nice id3ren -tag -tagonly -genre=79 -comment="$COMMENT" \
          -song="$SONG" -artist="$ARTIST" -album="$ALBUM" -year="$YEAR"\
          -track="$TRACK" -template='%n-%s' -space=_ "$MP3"
```

---

