---
title: "Issues connecting to some servers in 9.10"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Kimm on 2009-11-11
Basically what the title says (I am posting for my friend). After my friend upgraded from 9.04 to 9.10 he can no longer connect to some online services. Including Spotify, the Medibuntu repositories (which he added after the upgrade), the Wine repositories (same thing there) (appears that apt complaints about a sourceforge server in both the Wine and Medibuntu cases). Beside from these irregularities his internet works fine, he can visit any website for example.

His system is pretty much completely unmodified (no extra repositories, besides the ones he added after the upgrade), and he has no router that could be causing it.

I'm going to have a look at his system tomorrow, to see if there is some service running that could be blocking his connection attempts, does anyone have any ideas as to what could be behind this?

---

### Post by dmizer on 2009-11-11
DNS errors are the most common cause of this. You'll probably have to manually configure DNS addresses in network-manager. Here's how: [http://ubuntuforums.org/showpost.php?p=8291606&postcount=2](http://ubuntuforums.org/showpost.php?p=8291606&postcount=2)

---

### Post by Kimm on 2009-11-11
> **dmizer said:**
> DNS errors are the most common cause of this. You'll probably have to manually configure DNS addresses in network-manager. Here's how: [http://ubuntuforums.org/showpost.php?p=8291606&postcount=2](http://ubuntuforums.org/showpost.php?p=8291606&postcount=2)

Great, thanks for your tip, we'll see if that fixes it tomorrow :)

---

