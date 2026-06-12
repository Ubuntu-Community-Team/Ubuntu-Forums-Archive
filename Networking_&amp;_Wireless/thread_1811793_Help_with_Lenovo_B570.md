---
title: "Help with Lenovo B570"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by crazedsquirlz on 2011-07-25
Hello, I recently installed Ubuntu 11.04 on my laptop.
every time I boot up my computer it turns off my wireless switch
i go to the networking panel at the top and i enable my wireless and for a second it shows the wireless networks in range, but then it just displays. Device not ready.

i go to additional drivers. none needed.

this is weird because it knows the wireless connections are there. 

can someone please help?:(

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands in a terminal please
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by crazedsquirlz on 2011-07-27
The problem is resolved

---

### Post by wildmanne39 on 2011-07-27
Hi, I am happy to hear it if you do not mind you can share with the community how you fixed it.
Thank you

---

### Post by sefs on 2011-12-26
Friend, you really should follow up with how you resolved your problem.

---

### Post by esteban1uy on 2011-12-29
Wow... what an impolite guy.
Whatever, here you can find the solution: [http://ubuntuforums.org/showthread.php?t=1867367]("http://ubuntuforums.org/showthread.php?t=1867367&highlight=lenovo+b570")
I have a B570 and that trick works like a charm.
I also use the "battery drain" fix described in that post.

---

