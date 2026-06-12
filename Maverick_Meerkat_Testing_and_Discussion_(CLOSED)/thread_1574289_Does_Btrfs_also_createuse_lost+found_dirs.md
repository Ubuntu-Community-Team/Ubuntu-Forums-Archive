---
title: "Does Btrfs also create/use lost+found dirs?"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-09-14
Hi,
if it doesn't that would be enough to sell me on it when Maverick is released.

I think it's a legacy way of backing up broken stuff and afaik Btrfs has built-in support for this, hackers and the likes are ok with it but I as a desktop user don't like having a folder (which is not even hidden!) in each partition or so which never served me for years except as a reminder that the filesystem doesn't have other means of treating broken stuff but to create visible folders and to put it there (oh yeah, of course, simplicity), again, not a big deal but such a solution is really somewhat gross for desktops and should be fixed, hopefully Btrfs addresses that.

---

### Post by antiram on 2010-09-14
btrfs has no /lost+found dir. But the btrfsck has also no ability to repair a btrfs, not yet.

---

### Post by kahumba on 2010-09-14
That's good news, thanks!

---

### Post by seeker5528 on 2010-09-15
> **kahumba said:**
> That's good news, thanks!

:confused::confused::confused:

Later, Seeker

---

### Post by cgroza on 2010-09-15
So you will switch to btrfs just because of a folder?

---

### Post by psusi on 2010-09-15
I think you are confused.  AFAIK, BTRFS has no ability to repair errors yet, period.  lost+found is where e2fsck puts files that otherwise appear to have been lost because of an error, but that you probably want to recover.  It is visible because you WANT to take a look at them and see if they were actually something you wanted to keep or not.

Of course, if you don't like seeing it there, you can delete it and I'm pretty sure e2fsck will recreate it if it needs to recover lost files.  That does beg the question as to why mke2fs still creates the directory when it isn't needed yet, and if all goes well, never will be.

---

