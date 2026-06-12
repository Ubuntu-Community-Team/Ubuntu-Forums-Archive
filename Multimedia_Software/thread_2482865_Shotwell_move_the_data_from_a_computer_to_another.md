---
title: "Shotwell: move the data from a computer to another"
date: 2023-01-12
forum: Multimedia Software
---

### Post by raphael-bastide on 2023-01-12
Hi! I am trying to move the local/share/shotwell/data from a computer to another in order to keep my shotwell config (events, metadata&#8230;), but I am facing this error when I open shotwell:

```
ERROR:src/shotwell.p/db/VersionTable.c:133:version_table_construct: assertion failed: (res == Sqlite.OK)
Bail out! ERROR:src/shotwell.p/db/VerstonTable.c:133:version_table_construct: assertton failed: (res == Sqlite.OK)
Abandon (core dumped)

```

Do you know how can I fix that?

---

### Post by TheFu on 2023-01-12
I don't use any photo management software that doesn't keep data directly inside the image files and honors my organized directory structure.  I've been burned a few times over the decades with software that only stored metadata about the photos inside their proprietary DB. Never again.

Are the versions of shotwell identical on both systems?
Did you use rsync to move the entire directory tree, retaining file and directory permissions?

This is from 2011: [https://ubuntuforums.org/showthread.php?t=1834800](https://ubuntuforums.org/showthread.php?t=1834800)
[https://wiki.gnome.org/Apps/Shotwell/FAQ](https://wiki.gnome.org/Apps/Shotwell/FAQ) has suggestions for moving everything to a new directory.  There's a section "How can I copy my Shotwell library to a new computer?" that probably has the steps to follow.

---

### Post by raphael-bastide on 2023-01-15
THank you TheFu, both versions are the same, that is what bothers me. I will take an extra look at the FAQ.

---

### Post by raphael-bastide on 2023-01-27
I solved it, apparently it was an issue related to the file structure or permissions: moving the whole local/share/shotwell folder instead of its content only, worked. Thank you again TheFu!

---

