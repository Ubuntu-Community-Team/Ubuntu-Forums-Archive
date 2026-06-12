---
title: "ID3 tags not transferring with the MP3 file via FTP"
date: 2009-08-07
forum: Multimedia Software
---

### Post by madnessjack on 2009-08-07
Hi people,

I've had a look around and I can't see many people noticing this issue. Maybe I'm doing something wrong.

In Ubuntu Studio Jaunty I've added ID3 tags to an MP3 file using Audacity and tried with Easytag. All seems fine and the data is showing in Rhythmbox etc. When I upload the MP3 via FTP the tags don't go with it. Downloading it on another computer looses the information.

Is this to do with journaling/ext3 that Jaunty uses, or should I do something before uploading it?

Cheers all

---

### Post by madnessjack on 2009-08-10
Quick bump.

Tried and still can't fix it. When I copy mp3 files via FTP, the ID3 tags don't show. It's as if they get left behind on the file system or something.

Can anyone help?

---

### Post by megamania on 2009-08-10
I don't think FTP cares about *what* you're transferring (it is supposed to transfer a stream of bytes, regardless of what the file actually "is"), so I don't understand how ID3 tags are removed in the transfer process.

Check the size of the file on both the sender and the target machines, and see if there's a difference.

---

### Post by Stochastic on 2009-08-10
Moved to Multimedia & Video.

---

