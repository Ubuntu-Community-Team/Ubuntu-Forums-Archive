---
title: "network-manager not starting on boot"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by percent20 on 2012-06-24
I recently installed 12.04 on my mac and it works AWESOME. Ran for a couple of days well no problems at all.

However, something changed after installing nfs-common. I installed virtualbox and vagrant which required nfs-common. Apprently somewhere in there it changed something, and I don't know what. 

Now when I boot it doesn't get network settings at all so it takes about 2 minutes to boot where it only took 13 seconds before (Love SSD). When it boots up at first I have no internet at all. 

However, once I run `sudo service network-manager start` all my network bits startup and I am on my way doing what I do. Is there a way to make sure this turns on, and I no longer have the odd boot issue?

EDIT SOLVED:
I solved the issue. My `/etc/network/interfaces` file was malformed. Once I fixed it wireless started working again.

---

