---
title: "Wireless network - connected, got ip, but no packets through"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by nivwusquorum on 2012-06-25
Hi,

I have a really weird issue and I am not sure how to check whats wrong. Basically I connect to wireless network successfully. When running ipconfig I get 
```

          wlan0     Link encap:Ethernet  HWaddr 24:77:03:89:9e:6c  
          inet addr:192.168.2.112  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2677:3ff:fe89:9e6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2195 (2.1 KB)  TX bytes:10637 (10.6 KB)

```So I have ip assigned but when I try to ping router or google.com it doesn't work. 
My network card is intel centrino untimate-n 3000. 

Any suggestions what might be wrong?

Thanks,
Szymon

---

### Post by chili555 on 2012-06-25
Please try:```
lsmod | grep iwl
```See if your wireless driver is iwlagn or iwlwifi and then remove it and reload it with a parameter.```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

Any improvement? If so, we'll need to write one file to make it permanent.

---

### Post by nivwusquorum on 2012-06-26
Wow, what just happened? That works! Can you tell me why exactly that works? 

As far as adding this flag permanently is concerned, I will be able to do that :)

Thanks,
Szymon

---

### Post by chili555 on 2012-06-26
The iwlwifi driver is troubled with a bug wherein it doesn't handle N traffic at all well. It seems to clog and pass *NO* traffic at all. Fortunately,there is a fix; tell the driver to disable ts N capability. It's a compromise, I know, but there seem to be two choices: it works without N or it doesn't work at all.

Please open a terminal and do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Of course, use the actual name of your driver, if not iwlwifi. Write one line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. 

You might look for and add to an existing bug here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Finally, if it's now working well for you, please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by hawkingw on 2013-03-07
for my Realtek driver, the name is 'rtlwifi'

---

### Post by chili555 on 2013-03-07
> **hawkingw said:**
> for my Realtek driver, the name is 'rtlwifi'Is this a question? Are you having the same trouble? I suggest you start your own new thread and describe your issue fully and include this from the terminal:```
lspci -nn | grep 0280
```

---

