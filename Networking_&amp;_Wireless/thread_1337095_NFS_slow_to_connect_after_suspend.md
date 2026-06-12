---
title: "NFS slow to connect after suspend"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by bertmanphx on 2009-11-25
Hello,
My 9.10 desktop suspends to ram and resumes nicely.  However, I've noticed since the install of 9.10, my NFS shares don't reconnect quickly.  If I access them through Nautilus, or start a program requiring them, the program, or the panel will just hang for about 2 whole minutes.  After that time, it works.  My fstab is attached, unchanged from the 9.04 installation.  Also, the server, running 9.04 has not changed.  It's setup has remained the same.

Any help is appreciated.

bertmanphx

---

### Post by Wizzu on 2010-01-02
I seem to have the same issue, though I haven't tried this prior to 9.10. I use autofs, and the NFS mounted directory is really slow coming up - takes two mins.

My /var/log/messages has eg. this:

```
Jan  2 10:43:29 carrell kernel: [332515.880026] nfs: server newcastle not responding, still trying
Jan  2 10:45:29 carrell kernel: [332635.880826] nfs: server newcastle OK
```The pattern is always the same, exactly 2 minutes between those two messages. During the period I can ping the server, so it's not a network issue. The network does come up pretty quickly when waking up (a few seconds) but I don't know whether it was up at the time of the first message.

(edit:) There's a bug report about this at [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594)

---

### Post by bertmanphx on 2010-01-04
Hello,
Good reply.  I'm dealing with the problem here, but just being patient..:)  My NFS shares DO come up, they just take a while.
I'd like to try a fresh install, and see if that clears things up, but no time for that right now.

bertmanphx

---

### Post by arbrandes on 2010-03-16
This is a known bug in the kernel:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379385](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379385)

If you read through the report, you'll see that there are two patches in the kernel bugzilla.  One of them has been applied to mainline (and thus, Karmic's kernel), but not the second.  If you apply the second to the Karmic kernel, you will se the problem go away.

Adolfo

---

### Post by bertmanphx on 2010-03-16
Interesting.
Actually, I had though this was better, but am still having the problem with the latest Karmic kernel.  I'll keep an eye on it.

bertmanphx

---

