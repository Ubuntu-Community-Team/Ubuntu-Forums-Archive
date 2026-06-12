---
title: "Zombie Internet Connection With Broken Network Manager"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by 1ntel on 2013-01-29
Hi,

I've been having a heck of a time. 2 weeks ago I was having VPN issues, so I tried upgrading network manager. Apt suggested that I run apt-get autoremove, which I did and it uninstalled tons of critical dependencies that broke network manager. Further, when it rebooted it could not boot Linux and was stuck on a very weird screen.

My college Linux Users Group troubleshot it with me for almost 2 weeks and we FINALLY got it running a few days ago. I have an internal wlan0, exerternal wlan3, and a wired eth0. network manager wasn't working on the Ubuntu/Debian host but I have many virtual machines, all of which had Internet. I tried to make them share the internet with the host but it never worked. I tried using USB to get some downloaded .deb's of network-manager and the dependancies, but I still got error messages when trying to replace/upgrade network manager.

Then today, mysteriously, the host suddenly has the internet!!!!!!!!!! Yay! But what the heck???? Network Manager is still broken and I still can't fix it. I've tried everything. 

Thoughts?

Thanks in advance!

---

