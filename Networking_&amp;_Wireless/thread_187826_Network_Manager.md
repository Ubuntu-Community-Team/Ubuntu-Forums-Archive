---
title: "Network Manager"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by siofwolves on 2006-06-03
After installing 6.06 3 times hoping it would run on wi-fi straight out of the box, I later find out through a research you need a live internet connection during/after installation.
The problem I have is getting WPA-PSK to work ! I've installed the 4th time using a live internet connection and all is good. But I still cannot set up my WPA-PSK.
Network Manager installs using the Add/Remove app, it says after installation its in the Applications/Internet pull down menu, but its not ?
I get a Network Manager icon up by the clock, but there's not much I can do with it ?

---

### Post by s31523 on 2006-06-03
Did you edit your /etc/network/interfaces file?  If not, that is probably the issue.  You need to edit that file and comment out (or delete) the entries for eht0 and eth1 if you want Network Manager to manage those interfaces.  Do not mess with lo.

---

### Post by siofwolves on 2006-06-03
Yep, I've commented out everything apart from the first two lines (lo).

I can see more people are having this problem in the irc chan, but getting no answers :???:

---

