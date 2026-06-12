---
title: "Hipo iPod management"
date: 2009-09-27
forum: Multimedia Software
---

### Post by edxabbey on 2009-09-27
Didn't really seem like there is anything on the forums about how great this app is.  I tried Amorak, was not pleased, felt pretty good about Rythmbox.  Rythmbox is the best out of the music players I've tried, but there was no management for iPod, in true opensource form I knew there had to be somthing to support this.  I found Hipo.

What it does:
-Allows you to edit all file properties
-Update album artwork
-Input files/folders
-Essentially everything you could do in iTunes

The greatest thing about this is I feel like it is quicker, easier and more efficient then iTunes.  I am not just saying this, try it yourself if you are not already using this.

It is located in add/remove, search: hipo

---

### Post by edxabbey on 2009-09-27
On second thought it just deleted all 56g of my music, wiped the entire iPod clean.  At least the infastructure, my settings and extras are all still the same.  Weird, I was trying to upload many folders at once, as it seemed to be fine doing a few at a time.  

Looks like it's buggy.

---

### Post by BCW142 on 2010-02-03
Hipo iPod Management Tool under Ubuntu 8.04 LTS, came up with little work, but under 9.10 it won't do anything! What are You using it under and how much work was it to setup. I haven't found anything that really works well. The default under Ubuntu is to load iPod as /media/IPOD which it seems Hipo hates, also no option or way to make it work (Preferences won't start). So I renamed it to what Hipo seems to want and still nothing:

/dev/sdb2             39003792   1134960  37868832   3% /media/IPOD
bcw@Livingroom:~$ umount /media/IPOD
bcw@Livingroom:~$ sudo mkdir /media/Hipod
bcw@Livingroom:~$ sudo mount /dev/sdb2 /media/Hipod
bcw@Livingroom:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             51398644  22681568  26106116  47% /
udev                    509216       264    508952   1% /dev
none                    509216      1108    508108   1% /dev/shm
none                    509216       284    508932   1% /var/run
none                    509216         0    509216   0% /var/lock
none                    509216         0    509216   0% /lib/init/rw
/dev/sdb2             39003792   1134960  37868832   3% /media/Hipod

Still totally dead. :mad::lolflag:

---

