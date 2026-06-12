---
title: "DVDs won't play"
date: 2009-08-14
forum: Multimedia Software
---

### Post by goldfish2 on 2009-08-14
Its seems that only about 1/3 of the DVDs I get from netflix will play on my computer.  I was not able to play Slumdog Millionaire or Wall-e.  I am running Ubuntu 8.10... are there packages outside the default install that I need to play these?

Thanks

---

### Post by sblunix on 2009-08-14
well of course! There are 2 packages you need to install, The [non-free-codecs]("apt:non-free-codecs") package, and the [libdvdcss2]("apt:libdvdcss2") package. After that, you should be able to play DVDs fine.

---

### Post by sblunix on 2009-08-14
By the way, just FYI you can just click the links in the post to download them, otherwise you should know the command:```
sudo aptitude install non-free-codecs libdvdcss2
``` will also work... :) have fun watching movies...

---

### Post by jerrrys on 2009-08-14
here's some information that may be helpful

[https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats)

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

[http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc](http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc)

---

### Post by goldfish2 on 2009-08-14
uh... I'm using Ubuntu 8.10... I have the Universe and the Multiverse enabled... what am I missing?

```
$ sudo apt-get install non-free-codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package non-free-codecs

$ sudo apt-get install  libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

Thanks

EDIT: Nevermind, I'll check out those guides that were posted.  Thanks guys!

---

### Post by jerrrys on 2009-08-14
"non-free-codecs"...there is no such package. my above post will supply you with needed packages.

---

