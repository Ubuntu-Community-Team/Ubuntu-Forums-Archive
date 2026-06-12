---
title: "cdrecord has no permission......"
date: 2011-07-23
forum: Multimedia Software
---

### Post by frabato56 on 2011-07-23
Hi All,

First, let me apologize for starting a new thread for such and old topic. I got this message when I was using archlinux with k3b and I couldn't fix it. I switched to xubuntu and, "it's a miracle! It's been healed" After the last update (within the last few days) this nasty problem has surfaced on my xubuntu installation. I've seen threads on this that date back to 2008 with a lot of possible solutions. But, before I start aimlessly hacking away, I thought I would ask if anyone else has had this happen recently and what would be the most likely solution. I use k3b quite a bit so this is a real problem for me. Any suggestions would be greatly appreciated.

Thanks!

---

### Post by eathrock on 2011-09-22
Bump

---

### Post by perspectoff on 2011-09-22
It depends on your version.

The old problem/solution was:

Cdrecord has no permission to open the device error

If you receive the "cdrecord has no permission to open the device" error while burning using K3B, open a terminal and type:

 sudo chmod 777 /dev/scd0

        Note: replace /dev/scd0 with your own device, e.g. /dev/sr0. 

        Note: chmod 777 is the universal option for granting full permission to a folder. The 777 mask indicates that read, write, and execute permission is given to all users. 

Lately (Natty, I think), the permissions for your device needs to be set internally in K3b:

K3b -> Devices -> Modify Permissions ... (for your specific device)

I just do both. I see little harm in giving full permissions to my CD/DVD device (unlike my USB device), at least on my personal (non-business) computers.

---

