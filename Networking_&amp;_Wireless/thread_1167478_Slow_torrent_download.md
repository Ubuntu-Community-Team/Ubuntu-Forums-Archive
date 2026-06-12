---
title: "Slow torrent download"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by thedarklaith on 2009-05-22
I just upgraded to ubuntu 8.04 recently (was running 7.10) and found that all my torrent downloads were really slow, averaging around 10kbps before i upgraded i was averaging 150kbps. I tried to search for a solution but all i found was this:
[http://languor.us/node/23](http://languor.us/node/23)
However i don't know if this would help since im running bittorrent and transmission (tried both).
Any help would be welcome

and btw i dont even know how to update Java through synaptic im a total noob in th linux world

---

### Post by konqueror7 on 2009-05-22
torrents are dependent on the seeds/downloaders ratio, so maybe its your torrent, try adding other trackers with more seeders...

also, i never really liked tranmission, connected way to long for me and seemed to not use my full internet bandwidth, try using Deluge, its in the Add/Remove... it has more settings which you could customize specific to your connection...

also about the java thing, vuze uses java, so that may be the problem, but if you just want to install java anyways, pop the terminal and execute the following,

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by thedarklaith on 2009-05-22
Maybe it is the number of seeds... i tried downloading a popular torrent and the speed was about 80kpbs (thats still not quick though, but its better than 10k)
anyway this is the response i got when i wrote the code you gave me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate

thanks for your help i appreciate it

---

### Post by superprash2003 on 2009-05-23
check to see if the required port is open , use this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by thedarklaith on 2009-05-23
I tried using deluge and i set it to connect to ports 6881-6889 however when i tested the port (using deluge) it told me it was closed how can i open it?
i tried entering some code into the terminal to edit the iptables so the port would open but it told only root user can do that (i dont even know how to login into root)

---

### Post by superprash2003 on 2009-05-24
just add a sudo to the command in the beginning

---

