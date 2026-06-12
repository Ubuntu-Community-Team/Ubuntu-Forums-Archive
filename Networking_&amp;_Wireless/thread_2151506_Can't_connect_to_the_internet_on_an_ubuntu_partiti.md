---
title: "Can't connect to the internet on an ubuntu partition"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by Tinker1972 on 2013-06-04
Computer: Mac mini
Processor: 2.26 GHz intel core 2 duo
Memory: 4GB 1067 MHz DDR3


Operating system: Dual booting Mac os x 10.6.8 and Ubuntu: 12.04.1 LTS 


Internet: BT broadband


Problem: Auto ethernet connection has not worked in eight months and the wireless network only works for a few seconds.


Error message: Authentication required by wireless network 


Entering the password connects it to the internet. However after a few seconds it requires a new password. 


(I have no trouble running wireless on any other machine (and it works fine in the main partition which is mac).

What options (if any) do I have please?

---

### Post by Hadaka on 2013-06-04
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
lsusb
rfkill list
```
thanks.

---

### Post by Tinker1972 on 2013-06-04
Solved thanks :)

---

### Post by Hadaka on 2013-06-04
Great ! glad you got it sorted out..
please mark this thead solved.
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2013-06-04
Glad you got it solved but it is forum etiquette to share with us how (a chance to help other users). ;)

---

### Post by Tinker1972 on 2013-06-05
Sorry I tried to mark it as solved last night but couldn't find it. Didn't realise it had been moved. (Turned out the problem was with the ethernet cable).

---

