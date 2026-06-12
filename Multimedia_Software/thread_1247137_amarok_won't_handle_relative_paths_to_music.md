---
title: "amarok won't handle relative paths to music"
date: 2009-08-22
forum: Multimedia Software
---

### Post by Hudy on 2009-08-22
Ubuntu 8.04.3, Amarok 1.4.9.1.

I have my own library of music, organized into 0-9, and subdirs A-Z. Then Artist, then album. I build my own play list files (.pls) and I've had them work with WinAmp and with XMMS.

Now XMMS is dead (as far as I'm concerned), and rhythmbox completely fubars my file tree by trying to be too darn smart (95% of my music is "artist unknown, album unknown" :-/ .  I've tried a few others (banshee trashes my collection, just as "smart" as rhythmbox), and can't find anything that will just play my already-organized collection of files.

Amarok seems like my next-best-last-chance. I CAN change my playlists to use absolute path; but while program settings claim to support relative paths for "manually-built playlists" it does not work.  I'm giving relative paths in each playlist to each file, but none of the files play unless I navigate to the specific music file and play it. 

That may be a gotcha, I have no idea 'manually-built playlists' means to an Amarok developer.

Example: a file appears in more than one playlist, such as Beethoven-5th.mp3 --- it would appear as 'Beethoven-5th.mp3' in 'c/Classical/Classical.pls' and as 'c/Classical/Beethoven-5th.mp3' in 'AllFiles.pls' (a large list at the top of the directory tree).

This is the only way to do it portably (if you use absolute paths, every user must mount the partition at the /same/ path on every computer. Ugh!).

Does anyone have any hints, tips, or advice? It's been painful trying to play music under Linux for a few years now (since XMMS self-destructed), and I've just about reached my limit, today, August 22, 2009!

Many thanks

/Bill

---

### Post by Hudy on 2009-08-22
Ah well - answered my own question.  It happens.

First clue was the bug created at [http://bugs.kde.org/show_bug.cgi?id=91053](http://bugs.kde.org/show_bug.cgi?id=91053) that was "fixed".  That tells me there is some way that it works.

For whatever reason, flipping from .pls to .m3u format activated support for relative pathing.

Go figure.  As someone said in 2007, "it's buggy as hell, but it's also amazing" and worth keeping......([http://ubuntuforums.org/showthread.php?t=492156](http://ubuntuforums.org/showthread.php?t=492156)).

Thanks (to me :-D )

Maybe this will help someone else...

/Bill

---

