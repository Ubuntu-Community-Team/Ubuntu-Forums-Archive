---
title: "Easy Question; how to find the device name of my wireless adapter?"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by jostafew on 2010-08-13
Hello everyone, I'm working on a stubborn wirelss networking issure and attempting to get my wireless adapter running in monitor/promiscuous mode to capture 802.11 management packets. I've been following some tutorials on the matter, but I'm not nearly as practiced with Ubuntu (or Linux in general) as I am with Windows, and I'm having a hard time nailing down the device name of my wireless adapter. 
 
I'm trying to run the command "sudo ifconfig XXX promisc" where XXX is my adapter name, but of course this is my problem.
 
I've loaded the "Device Manager" application and run "lspci -vv" from the terminal and not been able to come up with a solid answer.
 
Thank you in advance for your assistance
 
- Justin

---

### Post by wannadumpwindows on 2010-08-13
Just run:

```
ifconfig
```
or
```
iwconfig
```
in a terminal, it should give you all the info you need.

---

### Post by jostafew on 2010-08-13
Hahah wow, the answer was in front of me the whole time. It just wasn't obvious until I ran iwconfig! I've run ifconfig and reviewed the information, but I was looking for something like "RTL-8185" or something that refered to the make and model of the adapter, not something simple like "wlan0".... Thanks!

---

### Post by Iowan on 2010-08-13
Having contributed SOOO... much to this thread, 
I *almost* hesitate to suggest marking it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

