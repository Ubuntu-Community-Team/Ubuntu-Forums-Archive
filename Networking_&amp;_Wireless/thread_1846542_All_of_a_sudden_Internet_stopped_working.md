---
title: "All of a sudden Internet stopped working"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by garg.anoop@gmail.com on 2011-09-19
All,

I am using Ubuntu 11.04 and it's working well for me so far until I got into Internet connectivity issue. My internet connection is secured and hence, before I can surf internet, I have to login into my internet provider's site. Basically first time i search/open any site, i'll be redirected to my service provider's site where i can login to authenticate myself.

From last couple of days my browser (firefox/chrome) is not redirecting me to the service provider's site so I am not able to surf/connect. 

I tried loading the previous linux version(kernel) but did not work. Any suggestions?
Do i need to reinstall?

---

### Post by varunendra on 2011-09-19
Are you sure you are connected to your ISP? Have you talked to your ISP to make sure the problem is not at his end or in the cable connection? Ask him the IP address of his DNS/Gateway and try to ping them:
```
ping <the IP of your ISP's DNS>
ping <the IP of your ISP's Gateway>
```
See if ping gets replies or not

You may also try creating a DSL connection in Network Manager entering the ID/Password there.

By the way, who is your ISP?

---

### Post by garg.anoop@gmail.com on 2011-09-20
I forgot to mention in my post that, I am able to connect to Internet on Windows. My system is dual boot and in Windows vista, it connects fine. My ISP is Hathway.

---

### Post by varunendra on 2011-09-20
Right-click on the network manager icon (at the right side of upper panel) and make sure "Enable Networking" is checked. If it is already checked, please post the errors message that firefox or chrome return when you try to browse.

Additionally, output of these commands:
```
ifconfig -a
sudo lshw -C network
route -n
cat /etc/resolv.conf
```

---

### Post by garg.anoop@gmail.com on 2011-09-20
Sure, thanks!!

The firefox or Chrome never return and continue in an infinte loop. I'll try again. I'll also share the output of these commands.

---

