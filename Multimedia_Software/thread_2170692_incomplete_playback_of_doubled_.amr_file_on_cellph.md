---
title: "incomplete playback of doubled .amr file on cellphone"
date: 2013-08-27
forum: Multimedia Software
---

### Post by blesbok on 2013-08-27
The following code produces a copy of an amr file that's double the length; the file seems to be played twice:
```

cp original.amr copy.amr
cat copy.amr >>original.amr
```

The workstation's media player plays what sounds like the original being played twice, which is the desired result. However, the *Samsung GT-C3053* cellphone plays for the time of the original file and then stops with a **FAILED** message. This happens whether the original's length is 3 s or 3 minutes. Is there a way to tweak the amr file so that it's acceptable to the cell's media player and not only that of the Ubuntu box?

---

### Post by tgalati4 on 2013-08-27
The amr file format probably has a file header with the file length (in time or bytes) that the Samsung phone respects.   It generates an error when the file time or size doesn't match what is in the header.  So perhaps edit the amr header?  A quick search for amr in the repositories brings up *fadecut*.  Perhaps it can tag your files correctly.  Otherwise *sox* or *audacity*.

---

### Post by blesbok on 2013-08-27
Thanks for the handy tip, tgalati4. 

Some searching led me to the suggestion that the first 6 bytes be removed from copy.amr before concatenation with original.amr and how to remove those undesired bytes. (If curious, see [http://stackoverflow.com/questions/17447508/android-get-duration-of-amr-audio-file-programatically?rq=1]("http://stackoverflow.com/questions/17447508/android-get-duration-of-amr-audio-file-programatically?rq=1") and [http://unix.stackexchange.com/questions/6852/best-way-to-remove-bytes-from-the-start-of-a-file]("http://unix.stackexchange.com/questions/6852/best-way-to-remove-bytes-from-the-start-of-a-file"))

Conclusion: modify #1's code to this

```

dd bs=6 skip=1 if=original.amr of=copy.amr
cat copy.amr >>original.amr
```

Play original .amr on the cell and it works!    :popcorn:

---

### Post by tgalati4 on 2013-08-27
The best fixes are the ones you discover yourself.  Thanks for sharing.

---

