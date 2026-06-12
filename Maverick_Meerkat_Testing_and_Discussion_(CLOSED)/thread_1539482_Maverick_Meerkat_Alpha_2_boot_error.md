---
title: "Maverick Meerkat Alpha 2 boot error"
date: 2010-07-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JackNocturne on 2010-07-26
Hi,
I've been trying for whole two days to test **Ubuntu 10.10 Alpha 2** to no avail:(
I have been using only Ubuntu for the past 5 years till now so my knowledge of linux is average.

Ok so i download the ISO image and i check MD5 hash, all is good. 
1)I tried first **Startup Disk Creator(0.2.22)** to create live USB , when i restart my computer ,and then USB boots i get the following "error"

```
[COLOR=#000000][FONT=dejavu sans][LEFT][FONT=sans-serif]SYSLINUX 3.63 Debian-2008-07-15 EBIOS (C) 1994-2008 H. Peter Halvin
Unknown keyword in configuration file.
boot:[/FONT][/LEFT]
[/FONT][/COLOR]
```Then it hangs there forever.
I tried editing my syslinux.cfg more than 3 times,no progress.

2)Then i decided to use **unetbootin(408-1ubuntu0.10.04.1) **to create new live USB,
when i boot i get the following error 

```
FATAL: Error inserting ramzswap (/lib/modules/2.6.35-10-generic/kernel/drivers/sswap.ko)  Unknown symbol in module, or unknown parameter (see dmesg)
No init found. Try passing init=bootarg

BusyBox ......(some stuff)
(initramfs) 
```I don't know what these "errors" are or what i'm doing wrong.

Any help will be appreciated,Thanks in Advance.

---

### Post by JackNocturne on 2010-07-26
](*,) I have found the solution in this thread **[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)  **

Strangely this thread didn't come in the search tool, i had to find it manually page-by-page.

But its good that it works now :p

---

### Post by DevHead on 2010-07-29
> **JackNocturne said:**
> ](*,) I have found the solution in this thread **[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)  **

Strangely this thread didn't come in the search tool, i had to find it manually page-by-page.

But its good that it works now :p

Thanks for this!  I've been having this boot error issue myself.  I will try this now.

---

