---
title: "Natty Install"
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by grubdude on 2011-01-18
Ok,
 
I know that this has been covered before in the Partial Updates thread but I am a bit confused. I am installing Natty in a virtual machine. I selected download updates while installing one time and not to download another time. Each time after the install is done, I get a error regarding update manager.
 
What is the best (read easiest) way to get all the latest updates without continually hosing the install? I tried sudo apt-get install -f but that creates either an error or depenency issues. When trying to fix the broken packages, it says successful but it reverta back again.
 
Any ideas? I don't recall the Maverick Alpha being as flakey when I installed it......
 
Thanks!

---

### Post by cariboo on 2011-01-18
Daily builds fluctuate as far as usability goes, one day they work, and they next day they fail.

To solve your problem use the broken packages filter in synaptic to get rid of partially installed packages.

---

### Post by nm_geo on 2011-01-18
> **grubdude said:**
> Ok,
 
I know that this has been covered before in the Partial Updates thread but I am a bit confused. I am installing Natty in a virtual machine. I selected download updates while installing one time and not to download another time. Each time after the install is done, I get a error regarding update manager.
 
What is the best (read easiest) way to get all the latest updates without continually hosing the install? I tried sudo apt-get install -f but that creates either an error or depenency issues. When trying to fix the broken packages, it says successful but it reverta back again.
 
Any ideas? I don't recall the Maverick Alpha being as flakey when I installed it......
 
Thanks!

I think you will find most of us are updating with Synaptic.  Custom Filters/ Upgradable (upstream)  I typically hit the reload button first then you can read about each selected upgrade. 

 The other option is aptitude which keeps up with what you choose to download for easier removal.  
```
sudo aptitude update && sudo aptitude safe-upgrade
```I prefer the Synaptic route for now.

---

### Post by grubdude on 2011-01-18
Thanks...Actually I did use the broken package filter. It said that it repaired them but then told me that there are 587 packages that need to be upgraded. When I do that it goes until the end of the install and fails again.....
 
After I reboot from fresh install what is the best way to install the updates at this point? Thanks.

---

### Post by cariboo on 2011-01-18
If it needs that many updates, you may want to try a daily live image available [here]("http://cdimage.ubuntu.com/daily-live/current/"), it may work for you, it isn`t recognizing my partitions today.

---

### Post by grubdude on 2011-01-18
sorry for double post

---

### Post by grubdude on 2011-01-18
So will sudo aptitude update safely update? I tried the synaptic route the first time and it really hosed things. So you have to go through all 500 plus updates and manually approve them?

---

### Post by grubdude on 2011-01-18
Thanks I will try that..Is it safe to choose install updates while doing install or better to wait? My iso was old so maybe you are right. I will try the 1/18.11 build.....

---

### Post by nm_geo on 2011-01-18
> **cariboo907 said:**
> If it needs that many updates, you may want to try a daily live image available [here]("http://cdimage.ubuntu.com/daily-live/current/"), it may work for you, it isn`t recognizing my partitions today.

cariboo, 

Are you installing a new current daily iso everyday a major change is made or using a stick for testing the daily too?  Seems like my daily downloads had no changes from 1/12 until today.

---

### Post by cariboo on 2011-01-18
> **nm_geo said:**
> cariboo, 

Are you installing a new current daily iso everyday a major change is made or using a stick for testing the daily too?  Seems like my daily downloads had no changes from 1/12 until today.

No my gnome-desktop-environment/ gnome 3/gnome shell is a failure so far :( , so I was going to do a fresh Natty/Unity install. I do test daily builds fairly often, and usually on a usb stick, I hadn't updated the iso since last week. I also test in vbox on occasion.

---

### Post by grubdude on 2011-01-19
Just teried installing the 1/18/11 build but now it will not recognize the partition table running virtualbox. The earlier build worked fine in that regard.
 
Anyone else see this problem?

---

### Post by grubdude on 2011-01-19
Trying 1/19/11 but probably won't help....
 
I guess that I was wrong 1/19/11 seems to be installing fine-------so far :-)

---

