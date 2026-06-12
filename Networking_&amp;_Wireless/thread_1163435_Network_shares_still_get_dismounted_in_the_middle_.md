---
title: "Network shares still get dismounted in the middle of a transfer on Jaunty?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by nonoitall on 2009-05-18
Hi.  This is kind of a follow-up of an [thread=873424]old thread I started several months ago[/thread].  I ended up not using Ubuntu (at least not the default setup) for a while, so my need to solve the problem kind of dissolved.  But I recently installed Jaunty to find that this problem is still present.  Windows shares that are automatically mounted just unmount right in the middle of a file transfer, causing the transfer to hang, and the only way to cancel the transfer is to log out.  (The cancel button does not work.)  No logs are present in /var/log/samba.

I got the impression in my last thread that this is a somewhat common problem, and I'm just wondering if there's any real solution that doesn't require me to manually mount the share I want to use.  Has a bug report been filed for this yet?

---

### Post by nonoitall on 2009-05-19
Bump.

---

### Post by nonoitall on 2009-05-20
Bump.

---

### Post by nonoitall on 2009-05-27
Well I reported the bug [here]("https://bugs.launchpad.net/bugs/378873"), so if anyone else is experiencing the problem and has something to contribute, there's a place.

---

### Post by dbcoolio on 2009-05-27
How often does this occur for you?  This does happen for me every once in a while, but it is usually because the other device fails, and it is not very often or consistent.  (I have an ASUS wl520gu router with Oleg installed and set up as a NAS with 250gb external hd).  It usually is only when I'm trying to do multiple files at once.  Now that I think about it, it is much more common with FTP than SMB.  Can you still access other files after it has hung? (for me I often can)

---

### Post by dmizer on 2009-05-27
This has been a problem for a very long time. It's one of the several reasons I wrote the CIFS tutorial in my sig. However, you may have better success with this: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

