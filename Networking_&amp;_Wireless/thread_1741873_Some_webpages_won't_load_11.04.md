---
title: "Some webpages won't load 11.04"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by ozooner on 2011-04-28
Hi,

I had actually the same problem in 10.10, but I was patiently hoping that 11.04 will fix it for me.
At the moment it's facebook(nothing will load) and lifehacker(mainpage will load,but further on no news will load)
First of it loads facebook after fresh install, but when i closed firefox, and reopened it, it won't load.
I pinged facebook.com and it's working:S
Chrome for instance loaded facebook atm, but didnt load lifehacker news aswell. Altho Windows on same machine will do it perfectly.
Please, I would like to use 100% ubuntu, but its not possible if some essential webpages won't load:(

---

### Post by uncaspi on 2011-04-28
To see if you have any intruders, trojans etc. open a terminal and issue this command: sudo /sbin/tcpdump -i wlan0
I assume your card is wlan0
If there is havy traffic through your interface while all internet app is turnrd off, you have intruders.

---

### Post by dineshs on 2011-04-29
May be [MTU]("http://ubuntuforums.org/showthread.php?t=872346") issue.
I suggest you try to set a different MTU (default is 1500)
Rightclick network manager icon - edit connections - select the tab wired/DSL depending on the connection you use - select the connection from the list - edit - set MTU as 1492 - apply.
Run```
sudo service network-manager restart
```and see if pages are loading
Note :You may findout optimum MTU value as given in the link or do a trial and error with 1492,1482 etc

---

### Post by ozooner on 2011-04-30
Thank you! 
Indeed it was MTU issue, unexpectedly easy fix.

---

### Post by fisch246 on 2011-10-06
I believe the correct command is this. You put a dash after service.
```
sudo service network-manager restart
```

---

### Post by dineshs on 2011-10-07
> **fisch246 said:**
> I believe the correct command is this. You put a dash after service.
```
sudo service network-manager restart
```
You are right.Sorry for the mistake.I have edited my post.

---

### Post by vsraul on 2011-11-12
> **dineshs said:**
> May be [MTU]("http://ubuntuforums.org/showthread.php?t=872346") issue.
I suggest you try to set a different MTU (default is 1500)
Rightclick network manager icon - edit connections - select the tab wired/DSL depending on the connection you use - select the connection from the list - edit - set MTU as 1492 - apply.
Run```
sudo service network-manager restart
```and see if pages are loading
Note :You may findout optimum MTU value as given in the link or do a trial and error with 1492,1482 etc

**[SIZE="3"]Thanks to this post and the tutorial of [[COLOR="Blue"]_MTU_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=872346") I can finally use my browser at full speed and it runs smoothly.[/SIZE]** :KS

---

