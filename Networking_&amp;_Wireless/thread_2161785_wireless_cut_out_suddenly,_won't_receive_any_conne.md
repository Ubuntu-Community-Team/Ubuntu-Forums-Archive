---
title: "wireless cut out suddenly, won't receive any connection even after restarting"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by krakket on 2013-07-11
I was browsing the web when suddenly my wireless stopped working . I checked using terminal commands I found on Google and the computer still recognizes my internal WiFi card . computer is a 2006 IBM ThinkPad . this has never happened before . I restarted it several times to no avail .also enabled and unenabled wireless several times . the computer isn't picking up any wireless connections at all although I am positive the network is running as I am using it now. my Xbox connects to the internet via a shared connection to my computer using an Ethernet cable so this is really annoying cause I can't play minecraft . I unplugged the Ethernet cable for all the troubleshooting so far . please ,any suggestions ?

---

### Post by kc1di on 2013-07-12
can you list the out put of this command in a terminal:
```
rfkill list all
```

note rfkill may not be install by default if you get a reply that says command not found. 
Install rfkill by this command ```
sudo apt-get install rfkill
```
and try again.

Also post the output of this command:
```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

---

### Post by krakket on 2013-07-12
thank you so much for responding . this is frustrating and weird but I woke up this morning and it was connected ...

---

### Post by kc1di on 2013-07-12
Well glad it's working for you 
Cheers!

---

