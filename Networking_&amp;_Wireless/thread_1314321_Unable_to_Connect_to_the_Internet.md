---
title: "Unable to Connect to the Internet"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by nlindz2065 on 2009-11-04
Hello, I need some serious help!!!!  I have somehow managed to reconfigure my computer and now it no longer recognizes my internet connection.  My modem/router shows that it has a connection to the internet but when I try to log into a site I get the message that firefox can not find the server.  I tried to reinstall ubuntu to see if that would fix the problem but it did not.  I have tried using the help feature for ubuntu...  tired all suggestions with not success.  I need some help I've been with the internet at home for a month.

---

### Post by djyoung4 on 2009-11-04
click on your network connections icon in the notification area.  are there any available networks there.

---

### Post by undecim on 2009-11-04
If you reinstalled Ubuntu and the problem persisted, then it is either a problem with your BIOS settings, or your router/modem.

After reinstalling, did you make sure that you had all your restricted drivers installed? If you are using wireless, you will need to connect to the internet with an ethernet cable in order to download those drivers.

---

### Post by nlindz2065 on 2009-11-04
Are you refering to the icon next to the date and time?  If so, I don't know if they are available but it shows that I am connected to a wirered network.

---

### Post by nlindz2065 on 2009-11-04
> **undecim said:**
> If you reinstalled Ubuntu and the problem persisted, then it is either a problem with your BIOS settings, or your router/modem.

After reinstalling, did you make sure that you had all your restricted drivers installed? If you are using wireless, you will need to connect to the internet with an ethernet cable in order to download those drivers.
How would I download drivers?  I can't do anything on the internet?

---

### Post by ukripper on 2009-11-04
> **nlindz2065 said:**
> Are you refering to the icon next to the date and time?  If so, I don't know if they are available but it shows that I am connected to a wirered network.

Can you go to Applications-->Accessories-->terminal and type following command and post output here:
```
ifconfig
```

---

### Post by LewRockwell on 2009-11-04
what happened when you reset your network devices?

.

---

### Post by djyoung4 on 2009-11-04
yeah.  first check if you have the drivers installed.  system>administration>hardware drivers.  if they aren't plug in your ethernet cable and see if you can download the drivers.

---

### Post by tom.gobel on 2009-11-04
Sometimes my Ubuntu box has trouble with DNS, for whatever reason (probably my setup and limited knowledge of routing), but I am able to connect to internet with ip addresses.

GOOgle = 64.233.169.147

You could try pinging that or through a browser.  I turned DHCP off on my routers and configured static ip addresses on each box, and the problems go away.

---

### Post by nlindz2065 on 2009-11-05
> **tom.gobel said:**
> Sometimes my Ubuntu box has trouble with DNS, for whatever reason (probably my setup and limited knowledge of routing), but I am able to connect to internet with ip addresses.

GOOgle = 64.233.169.147

You could try pinging that or through a browser.  I turned DHCP off on my routers and configured static ip addresses on each box, and the problems go away.
Hi, I tried the google IP address last night and I was able to see some results and when I type in google.com it takes me to their home page.  However, if I try to surf to another site from there, I get the same message....firefox can not find the server at (whatever site).

---

### Post by nlindz2065 on 2009-11-05
> **djyoung4 said:**
> yeah.  first check if you have the drivers installed.  system>administration>hardware drivers.  if they aren't plug in your ethernet cable and see if you can download the drivers.
My system says that there are no papritary drivers installed.  I also checked the first install of ubuntu that started all of this and it did not have any drivers listed either.  When I reloaded the ubuntu operating system, I partitioned the hard drive so I still have my original.

---

### Post by nlindz2065 on 2009-11-05
> **ukripper said:**
> Can you go to Applications-->Accessories-->terminal and type following command and post output here:
```
ifconfig
```
Since I am at work trying to fix my pc at home, I can't copy and paste but I did print it out and will try to retype what it said.  

eth0   Link encap:Ethernet HWaddr 00:1d:7d:26:31:d7
       inet addr:192.168.1.64 Bcast:192.168.1.255 Mask:255.255.255.0
       inet6 addr: fe80::21d:7dff:fe26:31d/64 Scope:link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:20099 errors:0 dropped:0 overruns:0 frame:0
       TX packets:6758 errors:0 dropped:0 overrunns:0 carrier:0
       colisions:0 txqueulen:1000
       RX bytes:1210396 (1.1 mb) TX bytes:410340 (400.7 KB)
       Interrupt:18 Base address:0xd800

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:1846 errors:0 dropped:0 overruns:0 frame:0
       TX packets:1846 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:92300 (90.1KB) TX Bytes:92300 (90.1 KB)

---

### Post by ukripper on 2009-11-06
can you ping your router? In terminal run below command and tell me if it is returning packets..or post output here
```
ping -c 5 192.168.1.1
```

---

### Post by nlindz2065 on 2009-11-06
> **ukripper said:**
> can you ping your router? In terminal run below command and tell me if it is returning packets..or post output here
```
ping -c 5 192.168.1.1
```
I have tried to ping the router and I get no results.  I think that it says that I'm not connected to the internet or that there is no connection.
I did try a google IP add that another poster on this site gave me and I get some results but when I try google.com i get the same firefox cannot fing the server at google.com.

---

