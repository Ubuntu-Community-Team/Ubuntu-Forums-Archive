---
title: "NTFS files turning to 0 bytes.  What's the deal?"
date: 2009-06-13
forum: Multimedia Software
---

### Post by myk02k on 2009-06-13
I've noticed a few movies/music on my NTFS partition being 0 bytes.  It's possible that they got corrupted upon transfer, but I'm a little concerned that this may be from Ubuntu's NTFS reader.  Any comments?  Will it be probable that this will stop if I switch over that partition to ext3?  If useful, I'm running 2 Western Digital 500 GB x 5400 RPM notebook SATA hard drives that are less than 7 months old.

---

### Post by expelledboy on 2009-06-14
Make sure that it is just not nautilus reporting incorrectly.
```
cd /path/to/media/folder/
ls -hl
```
Have you tried playing the files? They arent corrupted if they work! :)

I suggest that you move to a linux partition format though, if you arent dual booting that is and want to share media.

---

### Post by myk02k on 2009-06-15
> **expelledboy said:**
> Make sure that it is just not nautilus reporting incorrectly.
```
cd /path/to/media/folder/
ls -hl
```
Have you tried playing the files? They arent corrupted if they work! :)

I suggest that you move to a linux partition format though, if you arent dual booting that is and want to share media.

Everything seems OK with the path.  The files do not work.  I also have a dual-boot setup, but I do not use Windows for anything but Assassins Creed and Crysis nowadays.  Therefore, a shared NTFS partition is becoming less necessary.  It's just a pain to have to reformat.

---

### Post by expelledboy on 2009-06-15
Ya it is abit.. but its worth it. :)

---

### Post by myk02k on 2009-06-16
> **expelledboy said:**
> Ya it is abit.. but its worth it. :)

Hmm.  I think I'll wait till Ubuntu 9.10 comes out and switch it to EXT4.  That way I won't have to reformat twice.

---

