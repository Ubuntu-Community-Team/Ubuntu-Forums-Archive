---
title: "configure Ubuntu 12.04 as a host to access from W7 (remote desktop) from outside LAN"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by dvb24 on 2013-07-19
Hi all, I'm new to Ubuntu and have tried several things to connect to ubuntu from W7 outside the lan. I have done the following:

1. I have installed the xrdp #


sudo apt-get install xrdp
2. I have registered to obtain a dynamic ip-address on no-ip so i have myname.no-ip.org

3. I have used the network manager to set a manual ip address and dns server name

4. I have opened port 80 in my router for the static ip that I have set

When I try to connect through the ip directly (inside my home lan) it works, however if I try myname.no-ip.org it doesn't.

Also, testing port 80 [http://www.canyouseeme.org/](http://www.canyouseeme.org/) doesn't work either.

Many thanks for helping!

---

### Post by steeldriver on 2013-07-19
Hello and welcome to the forum

Port 80 is typically only used for webservers, the standard port for RDP is 3389 so you will need to forward that port on your router to the W7 machine instead of 80, I think

You may also need to check the W7 machine's firewall setup as it may be allowing incoming connections only from the LAN

---

### Post by dvb24 on 2013-07-19
Thanks for replying! I changed to the 3389 and now it works, I have a second pc but my router doesn't allow me to use the same port is there any other that I can use? I tried 3388 an 13389 but didn't work

EDIT: I get the error 'xrdp_mm_process_login response login failed' when trying to connect from outside LAN (inside LAN is ok). It seems that there are lots of people having the same problem but haven't found any solution for this.

---

### Post by ogenrwot on 2013-12-01
I'm having the same issue. It seems like this is very common and yet there isn't much as to a fix.

---

### Post by mkmanifesto on 2013-12-01
> **dvb24 said:**
> Thanks for replying! I changed to the 3389 and now it works, I have a second pc but my router doesn't allow me to use the same port is there any other that I can use? I tried 3388 an 13389 but didn't work

EDIT: I get the error 'xrdp_mm_process_login response login failed' when trying to connect from outside LAN (inside LAN is ok). It seems that there are lots of people having the same problem but haven't found any solution for this.

Try using port 3390 on the 2nd computer. You are going to have to edit the xrdp.ini for this to work as well.

```
sudo nano /etc/xrdp/xrdp.ini
```

about half way down you will a section with the heading [xrdp5]

change port=ask3389 to port=ask3390

now when you go to connect to this specific computer you will also need to specify the port for example "myname.no-ip.org:3390"

---

### Post by mkmanifesto on 2013-12-01
Forgot to tell you to restart xrdp once you make that change.

```
sudo service xrdp restart
```

---

