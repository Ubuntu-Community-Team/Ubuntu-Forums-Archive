---
title: "[SOLVED] Copying playlists to your flash-based MP3 Player"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Shampyon on 2007-04-17
My problem is simple: I have a flash-based MP3 player. When I plug it into my computer, Ubuntu Edgy recognises it as an MP3 player. Under Dapper it, like my old MP3 player, was simply recognised as a thumb drive.

One of the handiest features of iTunes was the ability to drag and drop a playlist onto any flash drive to start copying to relevant music files over. I realise it may be a bit much to ask for the drag-and-drop, but is there any way to make transferring my music onto my player any easier than having to hunt through the thousands upon thousands of folders and files and copy and past them piece by piece?

Currently I use Rhythmbox for all my pc-based MP3 playing needs, so a plugin for that, or an app that can read it's playlists, would be especially helpful.

---

### Post by hiazle on 2007-06-01
**BUMP**

I am also interested in something like a script that parses the contents of a m3u playlist and copies each file to a directory on the flash drive. I have a WM5 Pocket PC phone with a 1GB flash drive. It would be nice to be able copy a playlist in a few clicks. any ideas?

---

### Post by robinl on 2007-08-10
Googling around and I have came up with this little script:

```

sed "s/#.*//g" < playlist.m3u | sed "/^$/d"[FONT=verdana, arial, geneva, sans-serif][SIZE=-1]* |*[/SIZE][/FONT] while read line; do cp "${line}" /path/to/drive/; done

```
Works reasonably fine, with space and other messy characters.

---

### Post by Shampyon on 2008-02-17
Just in case anyone stumbles on this thread, Rhythmbox currently alows for a simple drag-n-drop of your music onto removable media.

---

