---
title: "FTP - Incomplete file when not Binary mode"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by luvshines on 2010-10-16
I have setup FTP Server on my Windows machine with Filezilla server.
Now, if I try to copy files from it using Ubuntu 10.04, Lucid, it downloads incomplete files if I don't switch to binary mode.

Is there some config issue from Ubuntu client or something needs to be changed from Windows Client.

---

### Post by DavePlummer on 2010-10-16
Personally, I use binary mode for all transfers. If I happen to run into a line-ending problem in text files, I can convert, using the appropriate tool for the OS I'm running. Most current Linux text editors can handle Windows line-endings transparently, anyway.

---

### Post by luvshines on 2010-10-16
> **DavePlummer said:**
> Personally, I use binary mode for all transfers. If I happen to run into a line-ending problem in text files, I can convert, using the appropriate tool for the OS I'm running. Most current Linux text editors can handle Windows line-endings transparently, anyway.

The files I am copying are movies and its subtitles and the file content that is being lost is too much.
I can't play the movie and srt has been cut short :confused:

Neways, how can I set 'bin' as default for FTP client ?

---

### Post by DavePlummer on 2010-10-16
I recommend setting the server to transfer in binary mode by default Then the Linux command line client will use binary mode.The gFTP client can be set tue binary mode by default.

---

### Post by luvshines on 2010-10-16
> **DavePlummer said:**
> I recommend setting the server to transfer in binary mode by default Then the Linux command line client will use binary mode.The gFTP client can be set tue binary mode by default.

I guess I'll have to switch the mode from client side only.

Filezilla server won't set binary as default
[http://forum.filezilla-project.org/viewtopic.php?f=6&t=15434](http://forum.filezilla-project.org/viewtopic.php?f=6&t=15434)

They are already at War with this:lolflag:

---

