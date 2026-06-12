---
title: "pymazon makes segmentation fault"
date: 2010-12-31
forum: Multimedia Software
---

### Post by waltersch on 2010-12-31
I'm using pymazon 0.9-2 for the download of multiple mp3 files from amazon. Sometimes it gets all of a big number of files at the first try, but sometimes it disappears (with segmentation fault) while downloading (e.g.) the first file. Here's the /var/log/messages from yesterday:

Dec 30 11:31:39 cardo2 kernel: [ 4589.257170] pymazon[2528]: segfault at 0 ip b74b67a0 sp bffe0398 error 4 in libc-2.11.1.so[b7443000+153000]
Dec 30 11:32:14 cardo2 kernel: [ 4624.260973] pymazon[2543]: segfault at 0 ip (null) sp bf87a63c error 14 in python2.6[8048000+1e0000]
Dec 30 11:33:37 cardo2 kernel: [ 4707.847638] pymazon[2554]: segfault at 0 ip b6a447e7 sp bfbe2b20 error 4 in libpango-1.0.so.0.2800.0[b6a2e000+40000]

Every line there stands for a new try to download the same two mp3 files. The behaviour was always the same: pymazon disappeared from the screen. But the time of disappearance was different. Just after beginning of the 1st file, just after end of the 1st file or beginning of the 2nd file, or somewhere while downloading a file.
I had to start pymazon a 4th time until these two mp3 files were correctly downloaded. At the end, I had the 1st file three times and the 2nd file one time.

I'm no system or python programmer, but it looks interesting that each of the three lines mentions a different system component.

My system is Ubuntu 10.04.1 with 4 GB RAM.
I installed pymazon by downloading Version 0.9-2 as a tar.gz package and (by alien) converting it into deb, then installed it by Synaptic.

Thanks for help!

---

