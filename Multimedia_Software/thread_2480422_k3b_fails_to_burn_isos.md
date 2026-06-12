---
title: "k3b fails to burn isos"
date: 2022-10-29
forum: Multimedia Software
---

### Post by tjcw on 2022-10-29
I tried to use k3b to burn and then verify an ISO file (which had been created by asking k3b to create an image). It got to 98% burned but then hung, requiring me to reboot my machine to recover. I presume the DVD was incompletely burned therefore worthless.
After the reboot (I forced all file systems to be fsck-ed by adding fsck.mode=force to the kernel command line) I tried again, with the same result.
After another reboot, I used nautilus to burn and verify the ISO; this ran to completion and indicated that the DVD was good.

Is this a bug with k3b or one of the libraries that it uses ? Does anyone else have the same problem ?

I am running with VERSION="22.04.1 LTS (Jammy Jellyfish)" , recently updated. Kernel is 5.15.0-52-generic .

The DVD is open source software, so I can drop a copy in the mail to anyone who is prepared to investigate the problem; you could presumably use k3b to make a file system image from the iso and then try burning it again; or I could upload it to a server if someone gives me access to a suitable machine. I do not have the requisite 4GB of space on an Internet-facing machine to upload the file to somewhere of mine that an investigator could download it from.

---

### Post by tjcw on 2022-10-29
Looks like this is a known bug [https://bugs.launchpad.net/debian/+source/dvd+rw-tools/+bug/1945585](https://bugs.launchpad.net/debian/+source/dvd+rw-tools/+bug/1945585)

---

