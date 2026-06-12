---
title: "File Sharing Not Working"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by Bungo Pony on 2009-08-19
I've been trying to share files between my HP 2140 netbook and my Ubuntu PC in the other room. I've had no problems with other laptops (and OSes) but this netbook just doesn't seem to like seeing anything across the network.

I've tried setting up sharing in Thunar with fusesmb. It would work for a while, and I could see all my files. After a reboot, it would quit working and I could see nothing.

Next, I decided to try setting up pyneighborhood and I'm getting the same results. After a reboot, I can see the folders fine, but I cannot see any of the files inside the folder, and I get an error that says "failed to mount".

This is extremely frustrating

---

### Post by stinger30au on 2009-08-19
are both machine using ubuntu 9.04???

if so use giver

sudo apt-get install giver

lets u share stuff across a lan with no config or setup needed, it does the lot for u

---

### Post by Bungo Pony on 2009-08-19
Both are running 8.04, the PC running UbuntuStudio, the netbook running Xubuntu. Not sure if the pyNeighborhood log file will help...

```
mount error: could not find target server. TCP name LINUX/shared not found
No ip address specified and hostname not found
[Unix] Server=[Samba 3.0.28a]
Domain=[LINUX] OS=[Unix] Server=[Samba 3.0.28a]

```

---

### Post by Bungo Pony on 2009-08-19
I think the problem is from the Ubuntu end. I noticed that the folder is not staying shared. When I run Nautilus from the terminal and try to share the folder, this is what I get:

```
** (nautilus:29503): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/was (not was) is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/recorded is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```

---

### Post by Bungo Pony on 2009-08-19
Allright, I figured it out. Here's the stupid, dumb, retarded solution.

The shared directory wouldn't share on the Ubuntu pc. So, I renamed the folder and then shared it, which successfully worked. Then I renamed it back to "shared" and it remained shared.

I WASTED AN EVENING for a dumb hack like that :P

---

### Post by dmizer on 2009-08-19
What was the previous share name?

---

