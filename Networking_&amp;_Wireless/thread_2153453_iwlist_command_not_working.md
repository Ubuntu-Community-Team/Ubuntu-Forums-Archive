---
title: "iwlist command not working"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by overcast on 2013-06-11
I tried running iwlist command but getting message of following

> 
iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


I am not sure if this is the message that is supposed to be returned.

---

### Post by Hadaka on 2013-06-11
Hi, you were close!
the command is..
```
iwlist <DEV> scan
```
DEV=wlan0..wlan1..eth1..ethx
to find your DEV....do..
```
iwconfig
```
hope that helps.
if you are satisfied with this answer then please mark this solved

How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

