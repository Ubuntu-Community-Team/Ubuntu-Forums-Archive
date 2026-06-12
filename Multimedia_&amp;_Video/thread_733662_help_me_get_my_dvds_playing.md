---
title: "help me get my dvds playing"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by timetoballj on 2008-03-24
i can not figure out how to get my dvds to play i am new to gusty and i cant figure it out i have tried doing what some other post says do and don't get it i need a lot of help please

---

### Post by wolfen69 on 2008-03-24
open terminal and copy and paste in:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
vlc is a great video player
```
sudo apt-get install vlc
```

---

### Post by timetoballj on 2008-03-25
its says error not found i working off a acer laptop if the helps please some one help me

---

