---
title: "How to stop NFS from murdering my hard drive"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by avada on 2010-12-06
Hi there!
I set up an nfs server on my old machine. (SSH stuff didn't work well, because it didn't perserve the file dates. And was very slow)

Everything was fine until I wanted to copy files. I tried two a hundred something MB files. But I had to interrupt the process because the server was working the HDD like crazy. Judging by the speed the progress bar and the crazy hdd sounds, the server tried to copy the whole thing into the memory, of which the server doesn't have much, so started swapping in swapping out and writing the the file to the destination at the same time. How can I stop the nfs server doing that, and make it copy the files straight to the disk?

---

### Post by SeijiSensei on 2010-12-06
> **avada said:**
> memory, of which the server doesn't have much

How much is "not much?"  Are you running a GUI interface?  Log in using "console mode" instead so X Windows won't load.  Did you create a swap partition at installation?  How big was it?  In low-memory situations it should be at least 2-4X physical memory; say 512MB-1GB swap on a 256M machine.

Ubuntu Server runs in text mode by default.  Are you using that version or the desktop version?

My NFS server has 256M of memory with 512M of swap, but doesn't run a GUI.  It handles other tasks like mail as well without thrashing.

---

### Post by avada on 2010-12-06
> **SeijiSensei said:**
> How much is "not much?"  Are you running a GUI interface?  Log in using "console mode" instead so X Windows won't load.  Did you create a swap partition at installation?  How big was it?  In low-memory situations it should be at least 2-4X physical memory; say 512MB-1GB swap on a 256M machine.

Ubuntu Server runs in text mode by default.  Are you using that version or the desktop version?

My NFS server has 256M of memory with 512M of swap, but doesn't run a GUI.  It handles other tasks like mail as well without thrashing.
I have ubuntu server also, 256 ram with 4 gigs of swap.

---

### Post by avada on 2010-12-09
Well, I disabled the swap partition and it happened again after a while. So I guess NFS just sucks. I copied the stuff I wanted with an ssh connection, which didn't do anything of the sort, but I lost file dates and took a long time.

---

