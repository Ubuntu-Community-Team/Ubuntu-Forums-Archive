---
title: "Dual boot, no connection in Ubuntu"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by djk628 on 2009-06-16
I just installed Ubuntu 9.04 on an old desktop and I am dual booting it with XP. I have a wired connection that works perfectly in XP, but in Ubuntu it doesn't recognize any connection at all. I am completely new to Ubuntu so it could possibly be a very simple fix. Thanks for any help.

---

### Post by Iowan on 2009-06-16
Are you getting (or trying to get) address via DHCP? Though it doesn't seem as helpful as I'd hoped, [this]("http://ubuntuforums.org/showthread.php?t=1156441") solved my (wired) DHCP problem. 
Beyond that, please post results of **ifconfig -a**, and **lshw -C netowrk**.  If what I'm asking doesn't make sense, I (or someone else) can provide more detailed instructions. :p

---

