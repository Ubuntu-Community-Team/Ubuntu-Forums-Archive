---
title: "History"
date: 2011-07-11
forum: Multimedia Software
---

### Post by will453 on 2011-07-11
Is there any way to pull up deleted history with terminal and delete it permanently so that even a computer forensic couldn't pull it back up?

---

### Post by wolfen69 on 2011-07-11
```
sudo apt-get install secure-delete 
```

This has four tools:

srm - securely delete an existing file
smem - securely delete traces of a file from ram
sfill - wipe all the space marked as empty on your hard drive
sswap - wipe all the data from you swap space.

srm  is  designed to delete data on mediums in a secure manner which can not be recovered by thiefs, law enforce&#8208;ment or other threats.  The wipe algorythm is based on the paper "Secure  Deletion  of  Data  from  Magnetic  and Solid-State  Memory" presented at the 6th Usenix Security Symposium by Peter Gutmann, one of the leading civilian cryptographers.

The secure data deletion process of srm goes like this:

   The secure data deletion process of srm goes like this:

   *      1 pass with 0xff

   *      5 random passes. /dev/urandom is used for a secure RNG if available.

   *      27 passes with special values defined by Peter Gutmann.

   *      5 random passes. /dev/urandom is used for a secure RNG if available.

   *      Rename the file to a random value

   *      Truncate the file

As an additional measure of security, the file is opened in O_SYNC mode and after each pass an  fsync()  call  is done.   srm writes 32k blocks for the purpose of speed, filling buffers of disk caches to force them to flush and overwriting old data which belonged to the file.

---

### Post by will453 on 2011-07-12
thanks

---

