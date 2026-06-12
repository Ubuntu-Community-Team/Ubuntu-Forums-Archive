---
title: "Crummy File Sharing &amp; Networking"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by Bungo Pony on 2009-10-12
Is there some sort of Bug in Ubuntu when it comes to sharing folders over a network? I'm seriously frustrated.

I'm trying to share folders over the network. I want to access folders from my netbook (running Xubuntu 8.04) that are on my PC (running Ubuntu 8.04)

It is quite flakey

First of all, the folders on my Ubuntu PC will randomly unshare themselves. When I go to re-share them, I suddenly don't have permission to do so. The only workaround I have found for this is to re-name the folder. Once the folder quits sharing under a certain name, it will NEVER share under that name again.

Second, I have fuse AND pyNeighborhood installed on my netbook. Usually when one doesn't work, the other will. It's usually fuse that works.

I just had a little power blip while accessing files. Now, fuse and pyNeighborhood will not access anything.

But, I can still connect to the internet without any problem.

Does anyone have any kind of clue as to what's going on here?

---

### Post by Iowan on 2009-10-12
> **Bungo Pony said:**
>  Once the folder quits sharing under a certain name, it will NEVER share under that name again. Have you checked permissions when that happens?

---

### Post by ugm6hr on 2009-10-12
Honestly, if you don't use Windows, I'd suggest using ssh to share files rather than smb.

Or even nfs (although you will have to manually set this up).

---

### Post by arnold.pietersen on 2009-10-19
> **ugm6hr said:**
> Honestly, if you don't use Windows, I'd suggest using ssh to share files rather than smb.

Or even nfs (although you will have to manually set this up).

Using ssh will give others access to the whole hard drive.  You want them to only access a folder called say Public

How would one accomplish that with openSSH for example?

---

