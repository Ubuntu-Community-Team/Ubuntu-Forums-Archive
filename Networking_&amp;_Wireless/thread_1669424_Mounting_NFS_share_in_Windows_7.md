---
title: "Mounting NFS share in Windows 7"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by covisp on 2011-01-17
I have an NFS share setup on my Unbuntu 10.04 machine. I can mount it on my mac with the command

mount -o noowners 10.0.0.99:/home/bbu/Share /Users/bbu/Share

When I try to mount it in Windows 7, I can do it from the command line:

mount -o anon \\10.0.0.99\home\bbu\Share

but that doesn't remount it at startup, so I try to mount it via the GUI. After reading these forums, I see that in the GUI I am supposed to use the format

server:/path/to/share

(but those posts are 1) about XP and 2) from 2006) So I try:

10.0.0.99:/home/bbu/Share

but it fails with an unexpected error.

So, I try the same path as I use from the commandline, but that doesn't work either (sam unexpected error). At present, I am simply having to manually mount the NFS share at every reboot from the command line in Windows 7 (less than ideal)

I do have the UNIX-Appplication support installed in W7 and, obviously, the NFS admin tools and client tools.

Also, while I'm here, how do I make sure the NFS share is seen as writable? It is setup as writable on the ubuntu side, but Win7 sees it as Read Only. Or do i have to use a user/pass to connect with r/w access?

---

