---
title: "Fall back Host Name?"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Kickboy on 2011-02-13
**Basic Problem**

I have a service setup to use a local hostname **'source1'**, which is not always available. I want it to automatically fallback to hostname **'source2'** in this case.

**Detailed Explanation**

I setup a local debmirror on my network, in order to speed up ubuntu updates on my network. I have 4+ machines running Ubuntu, and got tired to downloading the same file 4 times whenever there is an update. The debmirror works flawlessly for my Desktops, but not so good for my laptop. Why? Well... If I'm not at home I can't do updates (without changing apt/sources.list), since it relies on hostname **apthost** which is mapped in my hosts file to **192.168.1.201** (local IP).

Simply put, I want my local hostname **apthost** to fallback to **mirrors.kernel.org** when I'm not on my home network.

I have failed to find any way of doing this thus far. I would appreciate any help you guys can offer!

Thanks!

[If this is the wrong category, I would appreciate if you could point me in the right direction]

---

