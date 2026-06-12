---
title: "dir2ogg cross-partitions"
date: 2011-08-31
forum: Multimedia Software
---

### Post by tudor117 on 2011-08-31
Hi, I'm trying to convert a massive amount of audio files (specifically wav and wma) to ogg.
I figured that dir2ogg is the best option because it can recurse through directories, making my life easier.
However, all my music is on a different ext3 partition.

Here is the output:
```


dir2ogg 0.11.8 (2009-08-04), converts audio files into ogg vorbis.

INFO: Converting "/media/other partition/song.wma" (using mplayer as decoder)...
mplayer: could not connect to socket
mplayer: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/dir2ogg", line 673, in <module>
    main()
  File "/usr/bin/dir2ogg", line 665, in main
    ConvertDirectory(conf, directory, files)
  File "/usr/bin/dir2ogg", line 618, in __init__
    Convert(directory + song, conf)
  File "/usr/bin/dir2ogg", line 352, in __init__
    self.convert()
  File "/usr/bin/dir2ogg", line 427, in convert
    success, dec = self.decode()
  File "/usr/bin/dir2ogg", line 414, in decode
    os.rename(tempwav, self.songwav)
OSError: [Errno 18] Invalid cross-device link

```
I've read that the OSError is because the /tmp directory is on a different partition. I've tried exporting TMPDIR to a folder on that same partition with no avail. I'm also not sure what to make of the mplayer issues. 
Any help is appreciated.

---

### Post by dniMretsaM on 2011-08-31
I'm sure the partition is mounted when your trying this?

---

### Post by tudor117 on 2011-08-31
LOL yes it is mounted.
I mounted it with nautilus.
It can be accessed fine, except dir2ogg doesn't work on the files.

---

### Post by dniMretsaM on 2011-08-31
> **tudor117 said:**
> LOL yes it is mounted.
I mounted it with nautilus.
It can be accessed fine, except dir2ogg doesn't work on the files.

Yeah I just figured I'd ask. Could you maybe symlink the folder with the music on the other partition to a folder on the same partition as the program? That might just have the same affect as copying the files over though, I don't have much experience with this type of thing. Just throwing out ideas. Cue, someone smart.

---

### Post by tudor117 on 2011-09-01
Symlinking didn't work. See next post.
I never thought of that though! (didn't even know you could cross-partition symlink)

---

### Post by tudor117 on 2011-09-01
OOOPS. Nevermind. The symlink made dir2ogg start from a different directory. 
Thus, it converted some wav files before the wma's.
Turns out only the wma's cause problems.
At least I can convert HALF the music for now.
...still unsolved though...

I hear it's a python problem.

**EDIT:**
I have come to the conclusion that the wma's are DRM'd. I can't play them with any open-sourced audio player on linux. Though the error doesn't say so, I'll consider that to be the problem.
Thanks for your help.

---

