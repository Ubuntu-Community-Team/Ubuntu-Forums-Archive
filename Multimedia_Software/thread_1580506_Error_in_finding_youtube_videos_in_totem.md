---
title: "Error in finding youtube videos in totem"
date: 2010-09-23
forum: Multimedia Software
---

### Post by Praveen30 on 2010-09-23
i am getting this error when i am trying to search for youtube videos on movie player.

error:
The response from the server could not be understood. Please check you are running the latest version of libgdata.

i have updated my ubuntu.but error is still coming..why???

---

### Post by Praveen30 on 2010-09-23
> **Praveen30 said:**
> i am getting this error when i am trying to search for youtube videos on movie player.

error:
The response from the server could not be understood. Please check you are running the latest version of libgdata.

i have updated my ubuntu.but error is still coming..why???

pleaseee reply!!!!!

---

### Post by lkjoel on 2010-09-23
> **Praveen30 said:**
> i am getting this error when i am trying to search for youtube videos on movie player.

error:
The response from the server could not be understood. Please check you are running the latest version of libgdata.

i have updated my ubuntu.but error is still coming..why???
Open up a Terminal window and type in it:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install libgdata6 libgdata-common
```

---

### Post by Praveen30 on 2010-09-25
> **lkjoel said:**
> Open up a Terminal window and type in it:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install libgdata6 libgdata-common
```
 
i am  getting this error--

~$ sudo apt-get install libgdata6 libgdata-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgdata6

---

