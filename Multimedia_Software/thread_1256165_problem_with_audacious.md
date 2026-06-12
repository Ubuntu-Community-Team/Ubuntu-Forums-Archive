---
title: "problem with audacious"
date: 2009-09-02
forum: Multimedia Software
---

### Post by bubsy100 on 2009-09-02
hi all 

i have problem with my audacious  

i can not play any media or file at all after i load my flies into list player its not play and can not listen on it 

please help me because its my favorite player 

my current os ubuntu hardy 8.04  and my audacious 1.5 version 

thanks in advanced

---

### Post by mdmarmer on 2009-09-02
Does it work as root or as a different user?
What happens if you enter audacious in terminal?
Try
sudo apt-get install --reinstall audacious
(probably the above won't help, but try first -- then this solution will probably work):
Probably it can be fixed by deleting configuration files
Audacious has configuration files in 2 places:
/home/username/.config/audacious 
/home/username/.audacious
(may want to delete 1 at a time)
Mike

---

### Post by bubsy100 on 2009-09-03
thank u 

i put command in terminal and this message appeared ,
[B]
gogo@gogo-desktop:~$ sudo apt-get install --reinstall audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of audacious is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  libservlet2.3-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/B]

How can you help me ?
anybody could help me for this problem ????

---

### Post by bubsy100 on 2009-09-14
plz help me ???

---

### Post by kelvin spratt on 2009-09-14
Try this 1st
sudo apt-get update then sudo apt-get install --reinstall audacious

---

