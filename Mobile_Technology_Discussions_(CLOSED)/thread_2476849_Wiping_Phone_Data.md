---
title: "Wiping Phone Data"
date: 2022-07-09
forum: Mobile Technology Discussions (CLOSED)
---

### Post by bilkay on 2022-07-09
I have an android phone that I had to take out of service. After  deleting files, etc., since android doesn't actually delete stuff, I  wanted to overwrite the "unused" space with zeroes (dd if=/dev/zero...).  After connecting via usb to my laptop, I was able to use nautilus to  copy an all-zero file I'd created to the phone. What I wasn't able to do  was write directly to the phone from my laptop's command line (mounted  at /run/user/1000/gvfs/mtp*).

After searching the internet, I came across jmtpfs. After installing it from repository, I created mountpoint mtp in my home directory, then with the phone connected (and unmounted), the command jmtpfs ~/mtp mounted the phone and I was able to write directly to it.

Who needs bleachbit?

---

