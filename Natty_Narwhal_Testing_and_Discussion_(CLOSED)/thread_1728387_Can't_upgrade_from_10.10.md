---
title: "Can't upgrade from 10.10"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aenemic on 2011-04-13
I get the error: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb) 404  Not Found after fetching new software packages. Being the beginner that I am, this doesnt tell me much!
Anyone care to explain why the upgrade fails?

---

### Post by wilee-nilee on 2011-04-13
You shouldn't be upgrading at this time anyway, especially if you're a beginner, install it in a partition separately, and ask for help there if needed.

If you trying to upgrade a wubi your asking for problems.

---

### Post by aenemic on 2011-04-13
It's mostly in hopes that it could solve some of the troubles I'm having with 10.10, constant freezing and ****. And I don't have a USB stick at the moment, so trying different distros is kind of difficult.

---

### Post by wilee-nilee on 2011-04-13
> **aenemic said:**
> It's mostly in hopes that it could solve some of the troubles I'm having with 10.10, constant freezing and ****. And I don't have a USB stick at the moment, so trying different distros is kind of difficult.

But as the last post suggests in your other thread upgrading may bring its own problems.

One thing missing here is your type of install, is this a wubi, did you install Ubuntu from a live windows system. If you did this type of install does run slightly slower.

Also missing is a description of the ram usage and programs and browser tabs open when you have problems. You have a netbook atom 1.6 chip and 2 gigs ram stock, I have basically the same set up in a netbook it has its limitations, and has frozen on occasion, but I was driving it to use to much of the resources.

---

### Post by aenemic on 2011-04-13
This was a clean install from live-cd on a USB-stick.

It freezes anytime i download torrents, most times i view flash, although at random times it seems. Freezes if I stream video through sopcast with VLC as player at higher rates than 800kbs. So quite a few different scenarios. Also froze when downloading a file through Chromium.

---

### Post by nilarimogard on 2011-04-13
The error seems to be caused by a missing package for the mirror you're using so it will probably work if you switch to the main server.

To switch to the main server: in Ubuntu Software Center select Edit > Software Sources and then under "Download from" select "Main server".

---

