---
title: "Xsane can't find wireless scanner"
date: 2012-09-21
forum: Networking &amp; Wireless
---

### Post by Bhakti108 on 2012-09-21
Hi,
I have a Canon Pixma MG6250 multifunction. I have installed the relevant drivers and scan-gear-mp finds and can use the scanner. However I want to use xsane preferably, and it can't see the scanner. 

I have followed this tutorial 
[https://help.ubuntu.com/community/sane.d%20tutorial#Test_if_the_server_can_reach_its_own_saned_on_localhost](https://help.ubuntu.com/community/sane.d%20tutorial#Test_if_the_server_can_reach_its_own_saned_on_localhost)  

But to no avail.

I really prefer xsane as it has a multi page function for scanning that I find very useful. 

Any ideas greatly appreciated. Thanks

some details of the printer

IP address 192.168.0.14
default gateway 192.168.0.1
subnet mask 255.255.255.0

Printer name B8039B000000
Primary server 211.29.152.116
Secondary server 198.142.0.51

---

### Post by Bhakti108 on 2012-09-21
Bump

---

### Post by pdc on 2012-09-22
xsane is the GUI for ..........sane.........

if you look at this page, 

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

you will see that many of this MG series of printers are untested;

........so if you want to do the testing for it, you can; 

you would need to download a usb sniffing programme that runs on xp...

.......you could make a great contribution............

...........much of linux is volunteers etc

---

### Post by NHellFire on 2012-11-06
It's not supported in sane-backends older than 1.0.23. It's working in the latest (currently 1.0.23).
You  can either build the quantal package yourself, or use the builds in my  PPA.
[https://launchpad.net/~nathan-renniewaldock/+archive/sane](https://launchpad.net/~nathan-renniewaldock/+archive/sane)

---

### Post by Bhakti108 on 2012-11-29
Thanks guys, not sure what is going on, but it stopped completely, so I am trying to re load the drivers and running into problems because the install script returns an error of "package missing or in wrong location" 

I am lost.

---

