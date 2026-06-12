---
title: "Any way to get MythRename to work?"
date: 2010-08-11
forum: Mythbuntu
---

### Post by toddk111 on 2010-08-11
Is there any way to get MythRename to work again?

I previously used it to rename all of my recordings but have since re-installed the OS and it no longer works.  I would occasionally use it to rename the recordings and then remove my full recordings drive (for archiving) and put in a fresh blank drive for new recordings.  Renaming the files made it easy so that I could know what file a show is even when hooking up the archived drive to another OS.

I understand that Mythlink replaced MythRename because people had problems when files were renamed based on guide data.  This was never a problem for me because I always do manual timers (I don't use a guide).

Please help me, my drive is getting full and I'd really like to rename the recordings before removing the drive.

Thanks,
Todd

---

### Post by nickrout on 2010-08-11
No

Use the intended replacement, mythlink

---

### Post by toddk111 on 2010-08-12
> **nickrout said:**
> No

Use the intended replacement, mythlink

Is it possible to make Mythlink rename files instead of just make links?

---

### Post by nickrout on 2010-08-12
(I have deleted my original answer after checking by running 

> mythlink.pl --help

which I assume you can do too :)

---

### Post by toddk111 on 2010-08-13
> **nickrout said:**
> (I have deleted my original answer after checking by running 



which I assume you can do too :)

I don't have Mythlink installed but I found the help file on the Wiki and found: 

> Renaming the recording files is no longer supported. 

Ugh! So the answer is no.  I thought open source was supposed to be about choice...not lack of it.  If anyone has an idea of how to rename these files, I'd really appreciate it.

Thanks,
Todd

---

### Post by nickrout on 2010-08-13
it is no longer supported BECAUSE IT BREAKS THINGS to rename your files rather than create a link to them.

If you have mythtv-backend installed, you have mythlink.

Here's what mine tells me:

> --rename

    Rename the recording files back to their default names.  If you had
    previously used mythrename.pl to rename files (rather than creating links
    to the files), use this option to restore the file names to their default
    format.

    Renaming the recording files is no longer supported.  Instead, use
    contrib/exports/mythfs.py to create a FUSE file system that represents
    recordings using human-readable file names or use mythlink.pl to create links with human-readable names to the recording files.


For your purpose, what is wrong with making a link on the drive, then removing it for archiving? The link will have a human readable name, and will point to the file with the cryptic name.

---

### Post by toddk111 on 2010-08-14
> **nickrout said:**
> it is no longer supported BECAUSE IT BREAKS THINGS 

It never broke anything for me because I don't use the guide.

> **nickrout said:**
> For your purpose, what is wrong with making a link on the drive, then removing it for archiving? The link will have a human readable name, and will point to the file with the cryptic name.

From my understanding symlinks are OS specific.  So, if I wanted to hook up the drive to a WinXP machine, I'm out of luck.  Is this correct?

---

### Post by nickrout on 2010-08-15
Don't know, what if you are suing ext3 then there is a free ext2/3 driver for windows, whether it copes with symlinks I dunno

---

