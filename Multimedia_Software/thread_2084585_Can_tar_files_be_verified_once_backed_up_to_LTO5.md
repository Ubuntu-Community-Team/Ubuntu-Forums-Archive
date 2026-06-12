---
title: "Can tar files be verified once backed up to LTO5"
date: 2012-11-15
forum: Multimedia Software
---

### Post by linuxgabe on 2012-11-15
I am trying to find a terminal command to verify tar LTO backup files.  I am backing up large media files using Ubuntu and LTO5 drives. I would like to be able to verify "file sizes" or even "number of items" on the backed up tapes. I don't know if you can even do that. Just wondering because I am fearful of losing an media. Any help would be appreciated.
Thanks:)

---

### Post by cjhabs on 2012-11-15
"tar tvf device_name" will list the files in tar archive without restoring them

---

### Post by linuxgabe on 2012-11-15
> **cjhabs said:**
> "tar tvf device_name" will list the files in tar archive without restoring them

What i'm mainly looking for are the File Sizes or number of items in the Files

Any cmd for that?

---

### Post by cjhabs on 2012-11-18
the tar command gives you the file size of every file.
tar tvf tarfile | wc -l 
returns the total number of files in the archive

---

