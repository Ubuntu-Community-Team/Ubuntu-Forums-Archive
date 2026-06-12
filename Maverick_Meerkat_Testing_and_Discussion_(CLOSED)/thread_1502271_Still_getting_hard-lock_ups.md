---
title: "Still getting hard-lock ups"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ELD on 2010-06-05
As per this very long topic -> [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

The hard lock up bug is still present for me in Maverick with the newer Kernel as well, is there anything else i can do to test since Maverick is the most up-to-date?

---

### Post by taavikko on 2010-06-05
Not wanting to sound too harsh, what's your problem?
/* didn't have the energy to read the long thread */

Is the system upgraded or fresh install?
tried with a different user?
what specs on a hardware?

---

### Post by ELD on 2010-06-05
Hadware is in my signature, and it's a hard lock-up, system freezes and mouse/keyboard etc nothing works. It's not harsh at all, you didn't read :P

---

### Post by ELD on 2010-06-05
Hadware is in my signature, and it's a hard lock-up, system freezes and mouse/keyboard etc nothing works. It's not harsh at all, you didn't read :P

---

### Post by ELD on 2010-06-05
The problem is outlined even in the first sentence of that topic, you should read before you send off a reply.

My hardware is also in my signature.

All installs.

---

### Post by ELD on 2010-06-05
The problem is outlined even in the first sentence of that topic, you should read before you send off a reply.

My hardware is also in my signature.

All installs.

---

### Post by VMC on 2010-06-05
> **ELD said:**
> The problem is outlined even in the first sentence of that topic, you should read before you send off a reply.

My hardware is also in my signature.

All installs.
Since that link is three weeks old and is for Lucid you should bring to Maverick what your experiencing. What you tried, etc. 

Try removing *quiet* from linux standza to see any noticable errors. Also have you checked var logs, home  ".xsession-errors" errors?

---

### Post by ELD on 2010-06-05
> **VMC said:**
> Since that link is three weeks old and is for Lucid you should bring to Maverick what your experiencing. What you tried, etc. 

Try removing *quiet* from linux standza to see any noticable errors. Also have you checked var logs, home  ".xsession-errors" errors?

The original post is old, it's the same issue and the topic is very active so it doesn't matter how old the original topic is since it's the issue.

---

### Post by 23meg on 2010-06-05
See if these help you debug:

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by ELD on 2010-06-05
> **23meg said:**
> See if these help you debug:

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Ah ha didn't even know where to begin before! Have now installed openssh-server.

Good job i have a non-freezing netbook i can ssh with next time and figure this one out!

---

### Post by 23meg on 2010-06-05
> **ELD said:**
> Ah ha didn't even know where to begin before! Have now installed openssh-server.

Good job i have a non-freezing netbook i can ssh with next time and figure this one out!

Glad it helped you. Here's the one URL you should resort to whenever you're stuck debugging a problem:

[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)

---

### Post by ELD on 2010-06-05
> **23meg said:**
> Glad it helped you. Here's the one URL you should resort to whenever you're stuck debugging a problem:

[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)

Thanks the main problem is that for this issue i am unsure as to what is the cause so that page pointing to all the packages isn't really much help at this point, all i know is that it is a wide-spread issue.

---

### Post by 23meg on 2010-06-05
> **ELD said:**
> Thanks the main problem is that for this issue i am unsure as to what is the cause so that page pointing to all the packages isn't really much help at this point, all i know is that it is a wide-spread issue.

I didn't post that link to help you with *this* particular issue; it's the general index of debugging instructions through which you could have reached the first links I posted, and can help you (and others) whenever you're faced with a malfunction and don't know how to troubleshoot / debug it. And yes, I want to advertise that lovely index; even on this forum, too few people know about it and that's a problem.

---

### Post by ranch hand on 2010-06-05
> **23meg said:**
> I didn't post that link to help you with *this* particular issue; it's the general index of debugging instructions through which you could have reached the first links I posted, and can help you (and others) whenever you're faced with a malfunction and don't know how to troubleshoot / debug it. And yes, I want to advertise that lovely index; even on this forum, too few people know about it and that's a problem.
I am actually going to have to have a separate folder for the real interesting links you provide if you don't quit this.

I have enough links to study up on from you to last me the rest of the year.

Thank you anyway.

---

### Post by Starks on 2010-06-05
I've been getting hard locks with fullscreened flash videos. Might xorg-edgers, haven't tried without.

---

