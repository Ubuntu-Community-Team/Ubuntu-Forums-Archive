---
title: "is there a way"
date: 2010-04-20
forum: Mythbuntu
---

### Post by TheMiz on 2010-04-20
Is there a way to use mythtv to convert an ISO file saved on the hard drive to a VOB file?

In OSX, you can "mount" an iso file and it acts for all intents and purposes like a disk.  I need to do that then make mythtv rip it into a vob file.

Is that possible?

---

### Post by prince_sabin on 2010-04-20
I like Furius iso mount for Ubuntu.

I've never tried it with MythTV though.

```
sudo apt-get install furiusisomount
```

---

### Post by TheMiz on 2010-04-20
thanks I'll give it a try!

---

### Post by Lindsay.Mathieson on 2010-04-21
> **TheMiz said:**
> Is there a way to use mythtv to convert an ISO file saved on the hard drive to a VOB file?

In OSX, you can "mount" an iso file and it acts for all intents and purposes like a disk.  I need to do that then make mythtv rip it into a vob file.

Is that possible?

From the command line
```
sudo mount -o loop <filename>.iso <mount dir>
```

e.g.
```
sudo mount -o loop my.iso /cdrom
```

---

