---
title: "dont recognize wireless network"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by shanto_eee on 2010-11-03
hello,
I have installed ubuntu 10.10 beside my windows 7 in dell studio 15 (core i7). but after installing ubuntu does not recognize any wireless network. But I find wireless network from my windows 7.
I installed ubuntu 2 times to solve the prblem but :(

For your information, I installed ubunto 10.10 from this CD before when it was my only OS. in that time it could recognize the wireless network.

what shud i do?

---

### Post by Peter09 on 2010-11-03
Can you post the output of the terminal command
 
```
lshw -C network
```
 
also ensure that you have done 
 
```
sudo apt-get update && sudo apt-get upgrade
```
 
and reboot.
 
Also
 
Check
 
System->Admin->Hardware to see if any drivers need to be enabled.
 
(If you are new to Linux the above code can be cut and pasted into a terminal)
 
To get a terminal do Applications->Terminal

---

