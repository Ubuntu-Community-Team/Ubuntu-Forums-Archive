---
title: "K3b and Brasero blu-ray burning problems."
date: 2014-04-25
forum: Multimedia Software
---

### Post by alex189 on 2014-04-25
Hi, I have recently been trying to write blu-ray discs in ubuntu 12.04 LTS, I am looking for a way to not only write data onto the discs, I am also looking for a way to automatically have an md5 checksum file generated.
I have had some success - Brasero ***can ***do what I want but not fully, Brasero *does *make an md5 checksum file but it can only burn data (even when it is completely crammed up into the disc *I made sure that there was as less space as possible left before it started burning as a test, and it worked) onto re-writeable blu-ray discs (ones that are like a usb flash drive), unless I am trying to burn data onto re-writeable discs it doesnt work at the very first thing - simulation. Is there a way to disable this??? BTW, I am using 2.0x speed.

In K3b can burn standard blu-ray discs, but it doesn't make an md5 checksum file, at least everything else works :roll:  - anyway, is there a way to automatically generate md5 checksum files in the newest version of K3b(doesn't have to be the newest vesion, just so long as it supports blu-ray and makes the checksum file)??
I ***_have added the cdrtools repository and installed cdrecord - If anyone has problems with ubuntu "choosing" wodim instead of cdrecord during installation, do:_*** sudo apt-get update **- really helps ;) and install afterwards.**

Can someone please tell me why Brasero stop at simulation and how do I turn it off, and how/can K3b generate a checksum md5 file?

Thanks :D !

---

### Post by SeijiSensei on 2014-04-25
You can generate an md5 checksum from the command line like this:
```
md5sum < /path/to/some/file
```
So you could use k3b to generate an ISO image, use md5sum against that, then burn the image to disk if it is intact.

---

