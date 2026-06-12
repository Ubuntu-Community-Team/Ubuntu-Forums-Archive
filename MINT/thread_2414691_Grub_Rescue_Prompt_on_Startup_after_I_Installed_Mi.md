---
title: "Grub Rescue Prompt on Startup after I Installed Mint on USB Drive"
date: 2019-03-13
forum: MINT
---

### Post by shai3 on 2019-03-13
I followed the boot repair instructions but the repair didn't work. Here is the pastebin:

[https://paste.ubuntu.com/p/7nGsyXk8Kr/](https://paste.ubuntu.com/p/7nGsyXk8Kr/)

---

### Post by wildmanne39 on 2019-03-13
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by oldfred on 2019-03-14
It looks like your install is Ubuntu using LVM & full drive encryption.
Better to run Boot-Repair from Ubuntu live installer, so it uses correct repositories.
For Boot-Repair to run correctly you have to decrypted your install first.

Can you manually boot with?
       configfile (hd0,1)/boot/grub/grub.cfg

---

