---
title: "WiFi Networking"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by gerardgillan on 2006-06-26
Hi,

I've been using Ubuntu 5.04 on my HP NX6110 Laptop for a while now and find it fantastic. It found 99% of my hardware 1st time.

My only real problem is my internet connection, via eth0 (IPW2200). Sometimes I just can't get it to connect to my wifi AP (DHCP), then sometimes when I do I can't get connected to the Internet. I receive a "www.xxx.com could not be found" error. I have checked DNS settings etc and everything is OK.

Can anyone suggest anything else?

Thanks,  Gerard

---

### Post by x64Jimbo on 2006-06-26
It would help if you could include the commands you've used to bring up your interface and configure it on your router. Also, are you using DHCP or assigning a static IP?

---

### Post by gerardgillan on 2006-06-26
My wifi AP is also set as a DHCP server allocating IP addresses. I have turned off all security features of the AP including mac address filtering, encryption keys etc.

I have tried using "ifconfig eth0 down --> ifconfig eth0 up" and also using the GUI tool included in Ubuntu to configure the interface including DNS settings etc.

The thing that puzzles me is that it is intermittent.

---

### Post by x64Jimbo on 2006-06-27
what kind of intermittent? days at a time, hours, minutes? Have you tried configuring the wireless interface with iwconfig at the command line?

---

### Post by gerardgillan on 2006-06-28
Intermittent as in occurring at irregular intervals, there is no sequence to it. It may work fine for a couple of days then stop for 5 minutes, a day etc.  

When the problems have occurred I have checked the wifi network via a Win XP machine and everything works fine.  

I will look into the iwconfig command. 

Thank’s

---

