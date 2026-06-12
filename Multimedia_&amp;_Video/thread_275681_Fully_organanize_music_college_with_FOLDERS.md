---
title: "Fully organanize music college with FOLDERS"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by michael117 on 2006-10-11
I wasn't sure where else to ask this, so I am asking here since it seemd the most appropriate. Anyway, I have a rather large music collection that is on a home nfs debian server in my closet. I have been using EasyTag to correctly tag all of my music and rename it to my preferred format. Although, I've run into a bit of a problem. I also like my music to be organized in sub-folders, first by the artist, then by the album. So lets say I like artist ABC and their album was 123, the folders would be like this /Music/ABC/123 with the songs from that album in there. However, I have been unable to find any program that would automate this sort of task and organize it all. Is there any GTK application or even a terminal program that I could run to do this? Could I maybe make a small script or something to use a terminal program and arrange everything? Thanks in advance.

---

### Post by kidders on 2006-10-11
Hi there,

If it were me, I'd just do it from a terminal window with mp3info, or a similar tool. Something like this ought to do the trick...

[B]
for i in `find /path/to/unsorted -iname *.mp3 -print 2>/dev/null`; do mv $i "/path/to/sorted/`mp3info $i -p '%a/%l'`"; done
[/B]

I *think* I have the quoting right! :-k If memory serves, passing **-p "%a/%l"** to mp3info will have it stick a '/' between the artist and album names of a song, so you'd wind up with all your music moved into **/path/to/sorted/artist/album/whatever.mp3**.

---

### Post by michael117 on 2006-10-15
Hmm... I got some errors. It doesn't seem to read the spaces right and doesn't want to copy over. The errors were just scrolling down the screen and  here's some of what I got:

```
Error opening MP3: /disk2/Music/consumed: No such file or directory
cp: cannot stat `/disk2/Music/consumed': No such file or directory
Error opening MP3: by: No such file or directory
cp: cannot stat `by': No such file or directory
Error opening MP3: your: No such file or directory
cp: cannot stat `your': No such file or directory
Error opening MP3: poison/10.Despise: No such file or directory
cp: cannot stat `poison/10.Despise': No such file or directory
Error opening MP3: the: No such file or directory
cp: cannot stat `the': No such file or directory
Error opening MP3: Icons.mp3: No such file or directory
cp: cannot stat `Icons.mp3': No such file or directory

```

Anyone else have any suggestions? I would really appreciate it!

---

### Post by kuja on 2006-10-15
Well, it's not a gtk app, or even a terminal app, buuuuuutttt back when I did this I did it with Amarok :)

---

### Post by sp4rd on 2006-10-16
The Scanner in EasyTAG will do this for you.  Go to this thread
[http://ubuntuforums.org/showthread.php?t=276255]("http://ubuntuforums.org/showthread.php?t=276255")

---

### Post by kidders on 2006-10-16
> **michael117 said:**
> Hmm... I got some errors. It doesn't seem to read the spaces right and doesn't want to copy over. The errors were just scrolling down the screen and  here's some of what I got:

```
Error opening MP3: /disk2/Music/consumed: No such file or directory
cp: cannot stat `/disk2/Music/consumed': No such file or directory
Error opening MP3: by: No such file or directory
cp: cannot stat `by': No such file or directory
Error opening MP3: your: No such file or directory
cp: cannot stat `your': No such file or directory
Error opening MP3: poison/10.Despise: No such file or directory
cp: cannot stat `poison/10.Despise': No such file or directory
Error opening MP3: the: No such file or directory
cp: cannot stat `the': No such file or directory
Error opening MP3: Icons.mp3: No such file or directory
cp: cannot stat `Icons.mp3': No such file or directory

```

Anyone else have any suggestions? I would really appreciate it!
Eeep ... I didn't really intend for that line to be blindly copied & pasted!! (It appears to need additional quotes around the $i in "mv $i", for instance.) As mentioned, Amarok/etc. will do this quite nicely, but simply copying files around seems like a silly reason to install it.

If you already have a media manager app installed, use that :-) otherwise, moving files about the place is a job best done with a terminal imo.

---

