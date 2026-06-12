---
title: "Network Manager"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by untappedpilot2 on 2008-12-03
Hello 

I'm currently running Xubuntu 8.10 and I've just installed a wireless pci interface to my desktop. So I go to Applications > System > and I notice the Network Manager is missing.. as it turns out it's a listed bug for the Ubuntu 8.10 beta version.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/248163]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/248163")

 -Simple fix all you do is... 

```
sudo apt-get install gnome-network-admin
```

...and the Network Manager shows up again in Applications > System > Network

This may have been triggered by the installation of my wireless interface because I recall opening the Network Manager initially to setup my wired connection when my Xubuntu install was still fresh. Anyway I googled a little bit and didn't find any posts specific to Xubuntu for this bug(I had to look for Ubuntu), so I hope this post saves someone else a few minutes loL..

---

### Post by dextrome on 2009-03-06
Mission accomplished, you saved me time and confusion :) I installed madwifi for my Wifi card and Network Manager disappeared. Thanks!

---

