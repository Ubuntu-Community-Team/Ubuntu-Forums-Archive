---
title: "SSH over local DHCP"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by barrel_master on 2009-04-07
I've been trying to use WINscp to transfer files onto my ubuntu laptop on my local network. Unfortunately WINscp can't seem to connect to my private ip 192.168.1.105. My router uses DHCP and I am able to ping my ubuntu laptop from my windows machine. What am I doing wrong?

---

### Post by bhaverkamp on 2009-04-07
Your email says you want to use ssh. ssh is not installed by default. you will need to add it using

sudo apt-get install openssh-client openssh-server

---

### Post by barrel_master on 2009-04-07
> **bhaverkamp said:**
> Your email says you want to use ssh. ssh is not installed by default. you will need to add it using

sudo apt-get install openssh-client openssh-server

Thanks for the feedback. I actually already have ssh installed (I should have mentioned that). In tests I've been able to ssh onto external machines outside my network. I don't have any test machines in my local network to test the functionality of my ubuntu laptop.

---

### Post by andrewc6l on 2009-04-08
It sounds as if your Ubuntu machine has the ssh client installed, but possibly not the ssh server? If you go to the Ubuntu machine's shell prompt and type:
  ```
ssh localhost
```
are you able to log in?

---

### Post by barrel_master on 2009-04-09
> **andrewc6l said:**
> It sounds as if your Ubuntu machine has the ssh client installed, but possibly not the ssh server? If you go to the Ubuntu machine's shell prompt and type:
  ```
ssh localhost
```
are you able to log in?

I feel like such a newb. I just assumed that being able to ssh out meant that the ssh server had been installed. My bad. Your solution totally worked. You guys are the best ever.

---

