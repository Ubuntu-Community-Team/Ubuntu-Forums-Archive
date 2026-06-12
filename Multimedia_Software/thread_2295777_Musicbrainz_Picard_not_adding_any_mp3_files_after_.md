---
title: "Musicbrainz Picard not adding any mp3 files after &quot;Add Folder&quot; done"
date: 2015-09-21
forum: Multimedia Software
---

### Post by drunkmatador on 2015-09-21
Hello everyone. So i just went and installed Musicbrainz Picard. Install went fine, no issues. Also it's only been a week or so since I did a fresh install of latest Ubuntu.

I open up the program, and have tried either clicking the Add Folder button, or doing the same thing through the File menu.

Each time, it will bring up a dialog and let me choose the folder I'd like to add. In my case, all of my music is kept in my /Downloads folder... so i highlight that, and click Open. Pretty basic right?

Nothing happens. Have waited quite some time in case it was processing (have a very large library). But, when I chose Add Files, went into a specific folder with mp3's, they showed up right  away.

[SIZE=5]EDIT.[/SIZE]....... I just opened picard in terminal so that I could look at if it was giving me any errors. This is what it does as soon as i try to add my directory full of other directoreis:

```
AsdfkjlpoiwerEeinglknb123@Notebook-PC:~$ picard
E: 140716851824448 07:13:44 Traceback (most recent call last):
  File "/usr/lib/picard/picard/util/thread.py", line 58, in run_item
    result = func()
  File "/usr/lib/picard/picard/tagger.py", line 377, in get_files
    root, dirs, files = walk.next()
  File "/usr/lib/python2.7/os.py", line 284, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.7/posixpath.py", line 80, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xf6 in position 2: ordinal not in range(128)
```

Is there something I need to enable for it to scan subdirectories? I can't imagine it would come like that as d\efault, but who knows.Most of my files are located in folders that would be like: /Downloads/Band-Album/song.mp3

Is there something i'm missing? Or is this some kind of bug  that I shouldn't be experiencing?

Thank you, hope I can get this figured out.

drunkmatador

---

### Post by Yellow Pasque on 2015-09-21
[http://tickets.musicbrainz.org/browse/PICARD-644](http://tickets.musicbrainz.org/browse/PICARD-644)

---

