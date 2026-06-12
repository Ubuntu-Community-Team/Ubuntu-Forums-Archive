---
title: "Real PLayer 11 in Ubuntu 9.04 _64 bit"
date: 2009-06-23
forum: Multimedia Software
---

### Post by Matt.Rogers on 2009-06-23
As there does not appear to be an official 64 bit version of Realplayer 11 is there any way to use the 32 bit version?

I am somewhat stumped.

---

### Post by Arup on 2009-06-23
Mplayer handles RM format quite well but if you need real player for x64, you can also install Helix player which is the open source port of Real Player or you can download the Real [http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

---

### Post by sanumala on 2009-06-23
Add medibuntu repo and install realplayer i am using in the sameway
 
Here are the steps
 
```
 
Step 1: Add meibuntu repo
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
 
Step 2: Import GPG Key
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
 
Step 3: Install realplayer
sudo apt-get install realplayer

```
 
Hope this helps :)

---

