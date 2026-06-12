---
title: "installing ipwraw driver error"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by pannam on 2009-08-17
hi all,
i am trying to install ipwraw driver but i am having problems. this thing is new to me.. hope some one could help me out.
my error 
```
pannam@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
pannam@ubuntu:~$ 


```
my driver adapter is Intel PRO/Wireless 3945ABG ..

---

### Post by cariboo on 2009-08-17
Before installing drivers from third party sources, I would suggest you check and see if your device is already detectged and the drivers loaded. Open a terminal and type:

```
lshw -C network
```

The above command will list all your network devices and tell you whether the driver has been loaded.

---

### Post by pannam on 2009-08-18
sorry...being very new i wasn't aware to intall the 'build-essential' first.
now, i can get it to work.
```
sudo apt-get install build-essential
```

---

