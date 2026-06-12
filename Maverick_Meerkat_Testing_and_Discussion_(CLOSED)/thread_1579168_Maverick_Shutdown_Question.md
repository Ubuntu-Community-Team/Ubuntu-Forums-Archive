---
title: "Maverick Shutdown Question"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by A_Nonny_Moose on 2010-09-21
This may be a silly question, but I haven't really been following the development history.  When I shut down my Maverick test bed there is a remark about dismounting 'weak' file systems?  What is that all about, please?  Is there a new file system on Maverick?

---

### Post by cariboo on 2010-09-21
I've seen that too, I meant to create a thread about, but you've done it now.

---

### Post by FatAngus on 2010-09-21
I have seen this too - anyone??

---

### Post by VMC on 2010-09-21
I wonder if it occurs when you leave a file system mounted during shutdown. Also some searching said about security issues.

I have seen it in the past but not recently. Need to check some logs to see if in fact it has stopped for me.

---

### Post by cariboo on 2010-09-21
I just tried shutting down with an nfs share still mounted, and saw the weak file system message, but haven't been able to find anything in the logs yet.

---

### Post by ktp on 2010-09-21
it definitely not new.  I don't what it really means but did find [this bug]("https://bugs.launchpad.net/ubuntu/+bug/616287")

Note: the bug is not for "unmounting weak filesystems", but just using it as reference.

---

### Post by VMC on 2010-09-21
I read several articles regarding "weak file systems", and they tend to point to Windows as having a weak file system, because it can become fragmented and is not journaled.

So maybe you have a Fat or NTFS mounted on shutdown.

---

### Post by ktp on 2010-09-21
that is what my search also came up as...it be nice to be someone close to the code clear this up.

Even someone asked "What are 'weak filesystems?'" on following Kernel Q+A:

[https://wiki.ubuntu.com/MeetingLogs/openweekLucid/KernelQA](https://wiki.ubuntu.com/MeetingLogs/openweekLucid/KernelQA)

Answer was:
> (11:08:52 AM) apw: that sounds like a userspace message, not a designation i have seen used in the kernel before
(11:09:05 AM) apw: we'll have to look into that and try and get back to you

---

### Post by cariboo on 2010-09-21
I don't think it has anything to do with NTFS, as I see it on a Ubuntu only system, no windows partitions and shares are only mounted using nfs.

---

### Post by A_Nonny_Moose on 2010-09-25
> **VMC said:**
> I read several articles regarding "weak file systems", and they tend to point to Windows as having a weak file system, because it can become fragmented and is not journaled.

So maybe you have a Fat or NTFS mounted on shutdown.

Nope.  All my file systems are ext4.  So what is considered 'weak'?

---

