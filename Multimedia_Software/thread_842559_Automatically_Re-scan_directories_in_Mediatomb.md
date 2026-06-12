---
title: "Automatically Re-scan directories in Mediatomb"
date: 2008-06-27
forum: Multimedia Software
---

### Post by earthmeLon on 2008-06-27
It took me a while to figure out how to have my Mediatomb server automatically rescan directories, so I wanted to share what I found.

Mostly, I had a hard time figuring out *where* to put the info in the config file.

If you open your config file **~/.mediatomb/config.xml**


```

  [COLOR="Red"]</scripting>[/COLOR]
    <autoscan use-inotify="auto">
        <directory location="/media" mode="timed" interval="3600"
                level="full" recursive="yes" hidden-files="no"/>
        <directory location="/home/xxx/_in/" mode="inotify"
                recursive="yes" hidden-files="no"/>
    </autoscan>
  [COLOR="Red"]<mappings>[/COLOR]

```

The [COLOR="Red"]red[/COLOR] represents the existing part of the file.  The black represents what you will be adding to it.

**Explanation:**

I have two directory entries that will be scanned.
 The first will be scanned using a TIMED method every 3600s.  It will use FULL level scanning, which means it will scan every file for any changes.  It will also do a recursive search through all the sub directories, while skipping hidden files.
 The second is set up not to scan, but learn of new files whenever the OS/Kernel/Whatever tells Mediatomb that a file has been created/modified.  This is called "inotify", which your system must support to use.  It will also do a recursive search, skipping hidden files.

Another level of scanning other than FULL is BASIC, which means Mediatomb will only scan for NEW files, not MODIFIED files.  Sounds faster.  BASIC is the default.

All of this information is found at the [documentation page]("http://mediatomb.cc/pages/documentation") of Mediatomb, but it might not be clear for ever user.

I hope this clarifies some things.

---

### Post by dannyboy1121 on 2009-05-13
Excellent .. just what I was looking for. Thanks for sharing.

---

### Post by ephraste on 2011-06-04
Great ! thanks for sharing:):):)

---

