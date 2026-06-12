---
title: "internet connectivity problem"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by Asmaa R A.Aziz on 2011-04-23
Hi all, 

I do have a problem with my internet connection at home, I've a Huawei router and ubuntu 10. When I connect to the internet whether wireless or wired I become able to surf the internet for less than 10 min then it cuts off! and to be able to surf it again I need to restart the whole system!
I used this command to restart the networking but in vain
```
sudo /etc/init.d/networking restart
```

 On windows I do not face this problem with the same internet connection.

I do not face it either when I'm using my campus wireless connections using ubuntu/windows!, so the problem is related to my home connection+ my OS. 

How can I solve this ?

---

### Post by varunendra on 2011-04-24
After browsing for a while (before cut-off), run and post output of:
```
ifconfig
```

Also these (after the cut-off)
```
sudo lshw -C network
``````
dmesg | grep net
```When you run sudo /etc/init.d/networking restart, do you get any error message?

I initially doubted a driver issue, but you said it is same for both wired or wireless connection, so I now suspect it to be an issue of packet/frame size. After the 'cut-off', can you ping the router or does it (your network interface) get completely disabled?

Have you tried up/down with ifconfig? (**sudo ifconfig eth0 down**, then **up**, then check configuration with **ifconfig**)

---

### Post by dineshs on 2011-04-25
> sudo /etc/init.d/networking restartIf your network devices are managed by Network manager , you should try
```
sudo service network-manager restart
```
I have seen an option `Maximum idle time=....seconds' in router/modem settings.Can you try making it to `Always ON'.

---

