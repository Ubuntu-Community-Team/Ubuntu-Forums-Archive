---
title: "reformat playlists (m3u)"
date: 2010-12-13
forum: Multimedia Software
---

### Post by Azyx on 2010-12-13
Hi I have some playlist I want to keep the songorder, but I have the files in another file-structure.( I have the songs ordered in folder by artist and album, cos all songs are note tagged correctly or in the same way.) I want to use the playlist with the songs in copied to an another plays, for instance an usb-stick.
Is there an application who fix mass change of all links to the songs?

for instance I have in m3u-files:
#EXTM3U
#EXTINF:268,Salt Fare North Sea
./Hemma/280GB-D/Delat_D/MP3/Music/Chumbawamba/Readymades/Chumbawamba -01-Salt Fare, North Sea.mp3
......

to:
#EXTM3U
#EXTINF:268,Salt Fare North Sea
/media/16GB/music/Chumbawamba -01-Salt Fare, North Sea.mp3
.......

Or Is there a way in Amarok or another music-player that can make a copy of the playlists song order and use it with new links on a usb-memory?

Maybe there are a very easy way, but I don't now how sync to media-player and such things work.

/Cheers

---

### Post by StephenDavison on 2010-12-13
This ought not be too difficult with a few trusty old UNIX utilities.  Sed would be a good choice to modify the m3u playlist files.  Some combination of grep, xargs, and cp could handle copying the music files to the new location.

---

### Post by Azyx on 2010-12-13
you have probably right :)

find this but it way over my head. [http://ubuntuforums.org/showthread.php?t=519566](http://ubuntuforums.org/showthread.php?t=519566)

```
sed "s/#.*//g" < playlist.m3u | sed "/^$/d" | while read line; do cp "${line}" /path/to/drive/; done
```

....

---

### Post by StephenDavison on 2010-12-13
In that example, the first sed is removing all the lines beginning with #; effectively leaving the song file names and blank lines.  The output is being piped (|) into another sed command.  The second sed is removing the blank lines.  What is now left is just the song names listed.  Those are being piped into the while loop, which is copying each song file to /path/to/drive/

This is very applicable to what you are doing as it will copy your files while leaving the playlist file unmolested.  Now for the first part of what you were asking:  how to modify the playlist file to reflect the new location.  Try the following sed command on one of your m3u files AFTER MAKING A BACKUP COPY OF THE ORIGINAL:

sed -ri 's/^.+\/(.*mp3)$/\/path\/to\/drive\/\1/' playlist.m3u

The -i option to sed causes it to edit the input file in-place; hence the warning to back up first.  This is pretty rudimentary in that it assumes no whitespace between the file name extension and the end of the line.  What I'm trying to do is to match, starting at the beginning of the line, everything up to a /, identify an atom for what comes next, which should be anything from the last slash character to .mp3 at the end of the line.  Substitute everything matched with /path/to/drive/ followed by the file name.  \1 represents what was matched by (*.mp3)  

Edited to add better breakdown of the sed regular expression:
sed -ri    -- execute sed with extended regular expression and to edit in-place
s/   -- substitution expression
^.+\/      -- match from the beginning of the line to the last directory separator (/)
(*.mp3)$   -- following the slash, match the file name at the end of the line, saving the file name for replacement
/  -- done matching, now do the replacement expression
\/path\/to\/drive\/   -- the new location, escaping the directory separators to not treat them as special regex characters
\1  -- add the file name saved by (*.mp3)
/'  -- end the expression

I tried it on a simple test file and it seemed to do the job.

Good luck.

---

### Post by Azyx on 2010-12-14
Fantastic!!! Really great :) Thanks a lot Stephen :)

It work perfectlly. 

Now I can copy my  songs on the playlist and put them on an sd-memory, and then modyfie the playlist with sed. Really good :)

Thanx again Stephen

/Cheers

---

### Post by StephenDavison on 2010-12-15
You're welcome.

---

