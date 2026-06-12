---
title: "Avidemux splits AVI at 4gb regardless of settings"
date: 2008-12-12
forum: Multimedia Software
---

### Post by phenest on 2008-12-12
I'm saving a video as an AVI with uncompressed video and uncompressed audio and the file size exceeds 7gb. Avidemux splits the file at 4gb regardless of what I set it to in AVI Demux Options. I tried setting it to 8192Mb but it still splits at 4Gb. Why would this be?

---

### Post by phenest on 2008-12-12
In fact, it will start to split at random sizes: 808.1, 98.1, etc. I'd rather it didn't split at all.

---

### Post by rsambuca on 2008-12-12
Perhaps you should have a look at the Avidmux wiki!

> [SIZE="4"]How do I disable automatic AVI file splitting (create AVI files larger than 4 GB)?[/SIZE]

By default, Avidemux creates standard AVI files, which imposes a 4 GB file size limit. OpenDML files do not have this limitation. You can enable OpenDML output in Avidemux by checking Edit->Preferences->Output->Create OpenDML files. 

---

### Post by phenest on 2008-12-12
Perhaps, but even then the file limit is 9000Mb.

---

### Post by rsambuca on 2008-12-12
So what is the problem?  You said your file was over 7GB, and that you were trying to set max file size at 8192MB.  You just trying to be difficult now, or are you always so snippy with people that try to help?

---

### Post by phenest on 2008-12-13
> **rsambuca said:**
> ... You just trying to be difficult now, or are you always so snippy ...

Do you always speak to people like that? I was only asking a question. I just happened to find the answer the same time time as you.

---

