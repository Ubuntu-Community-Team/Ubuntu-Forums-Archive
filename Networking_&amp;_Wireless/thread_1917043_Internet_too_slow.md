---
title: "Internet too slow"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by raja.genupula on 2012-01-29
OS : Ubuntu 11.10
Environment : Gnome 3 and Unity

Well , I am not a network expert . My problem is  network  too slow in Ubuntu . My internet connection is a 512kbps one (60 KBPS ) its downloading speed if its fine but now i am getting maximum 25KBPS .

   from the day when i have installed ([FONT="Arial Narrow"]recently i think from 3-4days back i switched to 11.10 before that 10.04& net fine with that[/FONT]) .At the day i have installed Ubuntu , i went for an update but its started with too slow speed  . I thought that server issue so i switched to best server option and choose the best one .but my problem not solved .

But i have observed by connecting to other laptop that its not with net , its with my ubuntu . I am not expert in networking to solve myself . so i came to here . 

I am ready to provide what ever the information you want. please Help me .

Thanks in advance .

---

### Post by vasa1 on 2012-01-29
Raja, is it slow only when updating from Ubuntu servers or even from other non-Ubuntu sites?

---

### Post by raja.genupula on 2012-01-29
> **vasa1 said:**
> Raja, is it slow only when updating from Ubuntu servers or even from other non-Ubuntu sites?

Hey thanks for replying but i have tried by downloading other data from internet . its same man , browsing also slow .

---

### Post by vasa1 on 2012-01-29
Raja, have you searched askubuntu.com for **slow internet speed**? There are a lot of hits but 
[here's one case]("http://askubuntu.com/a/96319/25656") in which updating / installing a driver helped.

(Please note that I'm not an expert either :D )

Also see [http://askubuntu.com/questions/43482/what-are-common-causes-for-greatly-decreased-internet-speeds](http://askubuntu.com/questions/43482/what-are-common-causes-for-greatly-decreased-internet-speeds)

---

### Post by raja.genupula on 2012-01-29
Thanks for replying man , i will look at them .

---

### Post by raja.genupula on 2012-01-29
> **vasa1 said:**
> Raja, have you searched askubuntu.com for **slow internet speed**? There are a lot of hits but 
[here's one case]("http://askubuntu.com/a/96319/25656") in which updating / installing a driver helped.

(Please note that I'm not an expert either :D )

Also see [http://askubuntu.com/questions/43482/what-are-common-causes-for-greatly-decreased-internet-speeds](http://askubuntu.com/questions/43482/what-are-common-causes-for-greatly-decreased-internet-speeds)

i  have seen them 
```
sudo apt-get install axel
sudo add-apt-repository ppa:tldm217/tahutek.net
sudo apt-get update
sudo apt-get install apt-fast


```

This one sounds good .

---

### Post by vasa1 on 2012-01-29
Raja, but will axel and apt-fast help in browsing or only in operations involving apt-get?

Edit: apparently, it can work with aria2c as well.

Edit 2: it does work with aria2c.

---

### Post by raja.genupula on 2012-01-30
> **vasa1 said:**
> Raja, but will axel and apt-fast help in browsing or only in operations involving apt-get?

Edit: apparently, it can work with aria2c as well.

Edit 2: it does work with aria2c.

Hi man , over the apt-get your suggestion really super. 
apt-fast is good . Now i am looking for synchronization apt-fast with software center .by this we can make speed installs from there .

---

