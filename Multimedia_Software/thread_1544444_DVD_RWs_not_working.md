---
title: "DVD RWs not working"
date: 2010-08-02
forum: Multimedia Software
---

### Post by lexiii on 2010-08-02
Hello, I'm using Lucid Lynx and my DVD Burner is unable to read DVD+RWs
When I insert a DVD+RW nothing happens. When I insert a DVD-R, the Burner starts to spin and Nautilus finds the DVD.

I've been trying to find a solution for ages, but I have no Idea what the Problem is. 

I've installed Windows XP in Virtual Box and Windows detects the DVD+RWs, so there is nothing wrong with my DVD Burner.

Hope anyone can help.
Thanks in advance.

---

### Post by _h_ on 2010-08-02
If you know they are blank (don't blank out cd/dvd if you suspect it has information you need on it), try this command in terminal:

```
dvd+rw-format -blank /pathto/cdromdevice
```An example of where my cd/dvd drive is located;

```
dvd+rw-format -blank /dev/sr0
```
The most likely reason why it can't be read is because of the filesystem on the specific cd/dvd (linux doesn't like the windows filesystems it uses on cd/dvd).

---

### Post by lexiii on 2010-08-02
thank you. 

Well, I know there are files on it. Backups, Videos (avi) etc.

I'm not sure, but I think I burned them with an older Ubuntu Version.

---

### Post by lexiii on 2010-08-02
> **_h_ said:**
> If you know they are blank (don't blank out cd/dvd if you suspect it has information you need on it), try this command in terminal:

```
dvd+rw-format -blank /pathto/cdromdevice
```An example of where my cd/dvd drive is located;

```
dvd+rw-format -blank /dev/sr0
```
The most likely reason why it can't be read is because of the filesystem on the specific cd/dvd (linux doesn't like the windows filesystems it uses on cd/dvd).

I get the following error Message with that command:

* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( mounted media doesn't appear to be DVD±RW, DVD-RAM or Blu-ray

---

