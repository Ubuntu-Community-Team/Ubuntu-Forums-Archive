---
title: "Leadtek WinFast TV2000 XP Deluxe on Ubuntu?"
date: 2010-01-02
forum: Multimedia Software
---

### Post by gabe17 on 2010-01-02
Hi! I am thinking about buying this TV card, but I don't know, whether it is possible to run this card under ubuntu and work with it or not, because I don't see any drivers and software on the official site.

If someone has this card, please let me know. 

Thanks.

---

### Post by TaTaE on 2010-01-03
yes, it is working here without too much configuring. IR remote is working too.

---

### Post by gabe17 on 2010-01-03
Is there any software for Ubuntu to watch TV with TV card?

---

### Post by TaTaE on 2010-01-03
yes, the best one is called "tvtime".

---

### Post by gabe17 on 2010-01-06
Thanks. :)

---

### Post by 0dd1 on 2012-02-25
I have the Expert version, but I can't seem to make it work. I tried tvtime but i get a blue screen and no channels. On Zapping Tv viewer it works but without any sound. I am new to ubuntu, and I have no clue what I have to do..Thanx

---

### Post by TaTaE on 2012-02-27
Install tvtime using the ubuntu software-center.

Then you should run this command in the Terminal:

```
tvtime-scanner
```

It will do the scanning and storing of all channels available.

Then you may start tvtime and do more configuring by hand.

All the configuration files are here :

```
/home/youusernamehere/.tvtime
```

For example, these are mine:

```
$ ls -ls .tvtime/
total 48
 0 -rw-r--r-- 1 tatae tatae     0 nov 12 08:02 listings.xml
 0 -rw-r--r-- 1 tatae tatae     0 ian 18 20:10 listings.xml.backup
20 -rw-r--r-- 1 tatae tatae 17858 feb 25 15:09 stationlist.xml
20 -rw-r--r-- 1 tatae tatae 17858 ian 18 20:10 stationlist.xml.backup
 4 -rw-r--r-- 1 tatae tatae  1685 feb 25 15:36 tvtime.xml
 4 -rw-r--r-- 1 tatae tatae  1685 ian 18 20:10 tvtime.xml.backup
```

Of course, the *.backup files are made by me before some major changes I made in settings.


Cheers,

---

### Post by 0dd1 on 2012-02-28
Thanks TaTaE, I will try it out tonight.

---

### Post by 0dd1 on 2012-02-29
I installed tv time, and I selected PAL and Europe and scanned for the channels, but I still don't have any sound. And I can't acces the .tvtime folder, it says I don't have permission. Any suggestions what I should do next? :) Thanks.

---

