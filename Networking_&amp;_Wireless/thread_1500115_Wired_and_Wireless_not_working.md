---
title: "Wired and Wireless not working"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by bschertzing on 2010-06-02
Please Help!

I am very new to Ubuntu. I installed lucid lynx on my HP DV6000 series laptop today. I'm dual booting with win 7 and Ubuntu 10.04. I cannot connect to the internet via wireless or wired connections. My indicator light on the front of the laptop for wireless connection stays orange when it should be blue.

Wireless and wired connections work fine when booting to Win 7.

My network adapter is Broadcom 802.11 Multiband netowkr Adpater and a NVidia nforce Networking Controller.

Any help would be greatly appreciated.

---

### Post by Iowan on 2010-06-02
Post results (from a terminal) of **sudo lshw -C network** to see if interfaces are being configured. **ifconfig -a** (also from a terminal) will show if neither/either/both have an IP address.

---

### Post by bschertzing on 2010-06-02
Iowan,

Thanks for your help. fortunately I was able to get this issue fixed. I used the fix that involves installing the .deb file from my original install USB key. It was in directory pool/restricted/b/bcmwl. I had do install some other things in order to get that to work, but eventually I got onto the internets.

wish I remembered the original post so I can give some credit and better instructions.

Thanks again!

---

### Post by Iowan on 2010-06-02
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :)

---

