---
title: "internet connections"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by meghama on 2010-03-10
I would appreciate any help and advice with getting the wired internet connection working under ubuntu
he problem is that under Ubuntu 9.04 , when I plug in an ethernet cable to the pc the network icon in the taskbar rotates briefly, then promptly notifies me that the network connection is disconnected ("wired network: disconnected, you are now offline"). This happens repeatedly. It never successfully connects.


when i go to /etc/network/interfaces  the interfaces file contain
  auto l0
iface lo inet loopback 
what is loop back  i think i have etherent card 
i can connect using xp

please help me

---

### Post by Iowan on 2010-03-10
Loopback ("lo") is an internal interface - your */etc/network/interfaces* file looks normal for a Network Manager-controlled machine. [Here]("http://ubuntuforums.org/showthread.php?t=1156441") is a problem/solution I had with wired on Jaunty.

---

