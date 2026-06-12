---
title: "Can't ping my windows 7 while connected by ethernet cable"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by Nablet on 2012-07-18
Hello

First of all - I am noob, either in windows and ubuntu.

I wanted to transfer 200 gb of data to my computer [Windows 7] from my workstation [ubuntu 10.04]. I connected them with crossover ethernet cable. Windows see [COLOR=Black]_unidentified _lan and theres some received and sent data [in status of this lan].

I gave ipv4 adresses either on ubuntu and windows 7.
I modified hosts on both computers [etc/hosts].

When I ping ubuntu - time limit

When I ping windows - ping: sendmsg: Operation not permitted


I have read many threads about that and I do not know what to do now. Please help me.
[/COLOR]

---

### Post by Sergius14 on 2012-07-18
Please, attach Full configurations that you use either at Win7 and Ubuntu.


Also remember to fully disable Windows Firewall.

---

### Post by rukiaEnix on 2012-07-18
Please post result of ipconfig in windows and ifconfig in ubuntu

---

### Post by Nablet on 2012-07-18
Thanks for replies.
 
Problems seems solved for me in some way: I can connect and share files [and obviously ping other computer] WHEN I disable my wireless connection to the internet. Also my network is very slow [10 mb/s] but it might be case of slow hard disk.

---

### Post by rukiaEnix on 2012-07-19
...If  you say that's solved... 

Maybe it has something to do with which of your interfaces is the  main one.

In windows there's a way of setting your primary interface. I'm just saying that *may be* the problem.

---

