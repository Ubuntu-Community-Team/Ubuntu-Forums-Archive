---
title: "ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/...."
date: 2009-03-01
forum: Mythbuntu
---

### Post by Markus72 on 2009-03-01
Hi,

I use MythBuntu 8.04 and lots of errors in my backend log.

```

2009-03-01 18:30:19.011 Expiring 14 MBytes for 18418 @ Sa Jan 24 10:45:00 2009 => SPIEGEL TV Thema
2009-03-01 18:30:19.013 Expiring 10 MBytes for 2267 @ Sa Jan 24 11:05:00 2009 => Das Igelkomitee
2009-03-01 18:30:19.039 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/barebone/18418_20090124104500.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-01 18:30:19.045 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/barebone/2267_20090124110500.mpg. File doesn't exist.  Database metadata will not be removed.

```

That's annoying and as far as I understand the problem will never be fixed.

I have two questions:

1) what is the reason and how can I prevent from it?
2) how can I fix that particular problem?

Thanks
Markus

---

### Post by klc5555 on 2009-03-01
> **Markus72 said:**
> Hi,

I use MythBuntu 8.04 and lots of errors in my backend log.

```

2009-03-01 18:30:19.011 Expiring 14 MBytes for 18418 @ Sa Jan 24 10:45:00 2009 => SPIEGEL TV Thema
2009-03-01 18:30:19.013 Expiring 10 MBytes for 2267 @ Sa Jan 24 11:05:00 2009 => Das Igelkomitee
2009-03-01 18:30:19.039 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/barebone/18418_20090124104500.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-01 18:30:19.045 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/barebone/2267_20090124110500.mpg. File doesn't exist.  Database metadata will not be removed.

```

That's annoying and as far as I understand the problem will never be fixed.

I have two questions:

1) what is the reason and how can I prevent from it?
2) how can I fix that particular problem?

Thanks
Markus

A few Autoexpire metadata phantoms can be corrected (in the System Information screen) by moving the phantom shows to the default recordings group. Then delete them as regular recordings. Mythtv still can't find the file, but now offers to delete the database entry.

For a large number of metadata phantoms, the myth.find_orphans.pl script is usually to be preferred.

---

### Post by Markus72 on 2009-03-06
Thanks, that helped

---

### Post by ripleyberlin on 2010-11-14
I have a similar problem since I updated my Mythbuntu machine from 9.04 (Jaunty) to 9.10 (Karmic).

Previously I had no trouble deleting recordings after archiving them (I regularily copy them to external hard drives on
another machine using rsync).  The update was necessary though, due to errors in getting EPG data for all channels.

Since the update, deleting old recordings does not always work.  I have found the reason for that now.

Before I copy the files, I run "mythrename.pl" to get proper names.  Apparently I cannot delete recordings where
the show's name contains an Umlaut.  I just checked this with some recent recordings.

Of two episodes shown one has an Umlaut in its episode title and the other didn't.  To confirm my theory I recorded
some random show with Umlaut in its name.  I had no trouble deleting it when I did not run mythrename.pl

The mythbackend.log has many entries with badly encoded UTF-8 for Umlaut characters in it.

So I guess I have to find out how to make mythrename.pl change the filename entries in the database
so the mythbackend can handle them correctly.

---

