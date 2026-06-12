---
title: "autofs and Nautilus replacing fstab - browsing?"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by robertmaynord on 2011-05-06
Because of NFS traffic congestion, I am trying to use autofs instead of fstab(NFS) to mount /home and /data directories on our system (from a NFS server). I have it up and running - users can log in and their /home directories work fine. However, when they need to save a file (openoffice or nautilus) they cannot see the directory tree to locate folders for saving. I have tried setting the --ghost option in auto.master, and I have tried commenting the BROWSE_MODE in /etc/default/autofs. But no luck. Using the terminal, I can go a folder and see subfolders using ls -la. They then appear in Nautilus, but later disappear. Since this is a school network, I can't expect teachers and students to use the terminal to save files. They are used to using Nautilus, with our regular NFS mounts.

Perhaps there is some other way of configuring the whole system. How can I reduce NFS bandwith traffic, and still allow users to "surf" files on the network?

---

### Post by dmizer on 2011-05-07
Can you post all relevant server and client configuration files please?

---

