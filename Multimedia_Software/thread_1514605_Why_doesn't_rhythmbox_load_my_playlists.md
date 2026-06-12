---
title: "Why doesn't rhythmbox load my playlists?"
date: 2010-06-21
forum: Multimedia Software
---

### Post by rdh61 on 2010-06-21
Ubuntu 9.10.
Rhythmbox 0.12.5.

I wanted to take my playlists from one computer and put them on another. In rhythmbox I did, on the first computer:

Music -> Playlist -> Save to file

And on the second: 

Music -> Playlist -> Load from file

A new playlist appears in rhythmbox with the right playlist name, but completely empty. However, I know that the playlist file is not empty as when I open it with gedit it has all my song titles in it. This happens with all playlists whether saved as .m3u, .pls, or .xspf files.

Thanks for any help.

---

### Post by SoFl W on 2010-06-21
Are the music files on both computers or are you accessing the files on the second computer over the network?
I think the problem is it can't find the music files.  If they are both locally stored then the file names/paths must be the same on each computer.

---

### Post by rdh61 on 2010-06-21
Thanks for your reply.

Exactly the same music files are on both computers in exactly the same directories with the same pathways.

---

### Post by rdh61 on 2010-06-22
OK, it *was* a problem of the path to the directory. I produced a test playlist on computer 2 to compare with those produced by computer 1.

The path in the playlists from computer nº1 was listed as: Music/song title.filetype

The path in the playlists from computer nº2 was listed as: ///home/my home folder/Music/song title.filetype

Adding the missing string to the playlist files in gedit (using Find & Replace) enabled the playlists to be loaded correctly.

---

