---
title: "wired connection drops randomly"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by atactionpark on 2012-01-12
Hello, very green ubuntu/linux user here. Running 11.10 on a HP pavilion a6228x. I have a wired connection set up manually. It is connected upon start up, but after some time browsing the web or when I've tried to fetch additional drivers, the connection simply disappears -- however, Ubuntu still shows that the connection is working. The only way to get it back is to restart. I believe all the network settings are appropriate judging from previous posts.

I've attached images for information that was requested in previous posts:
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/resolv.conf

Thanks

---

### Post by spacecheck on 2012-01-12
Any other devices on the local subnet? If so and if one of them happened to have the same IP and occasionally tried to access the network, it could repeatedly ruin your connection on the pavilion.

You are also apparently connected to the FAU network and FAU may have set individual bandwidth and/or data load (upload/download) limits for its users. You might want to check with the network admin or FAU advisories to find out if that is the case.

If your problem is resolved by the foregoing suggestions, please remember to mark the thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  

Good luck!

---

### Post by tastro on 2012-01-13
i have the same issue.

i have 3 computers which all use the same out-going ip.

what can i do to fix this? so that i won't get dropped anymore? :(

---

