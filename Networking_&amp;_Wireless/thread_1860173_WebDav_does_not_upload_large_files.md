---
title: "WebDav does not upload large files"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by natomb on 2011-10-14
Hello,

I want to use WebDav (1&1 SmartDrive, 115 GByte capacity) for online backup. To keep my data private, I want to put the backup into a truecrypt container.

I can mount the WebDav, read from it, (partially) write to it and create the TC container. Yet, whenever I try to write a "large" file, it does not appear online. I wrote a file with few kilobytes which also appeared online. However, when I try place the TC container with 30 GByte online, it appears in the davfs2 cache, but not online. I also tested with a TC container with a few megabytes. It appears in the local cache but not online. Even after waiting a couple of days, it did not appear online.

My uplink capacity is something like 400 kbit (poor line)


Did you experience something similar? Did you came across some solution?

According to several posts, I set the if_match_bug option to 1. I also tried to increase cache_size as well as using use_locks .


Thank you for any hints
  Bjoern

---

