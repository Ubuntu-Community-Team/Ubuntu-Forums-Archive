---
title: "ubuntu wireless network connection"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by drteeth1978 on 2012-06-11
I have:
HP All-In-One 200 5220A
Windows 7 64 bit
Wireless broadband with WPA2 encryption. 
 
Recently,  having got tired of Windows, I have installed Ubuntu 12.04.  Ubuntu  loads fine and all seems well in the world, but I have having problems connecting to the wireless  connection.

 
I am able to see my connection as well as the  neighbours, but I am repeatedly asked for the WPA2 encryption key.  It  is definitely the right key, but I am unable to connect. 



I have also taken off the WPA2 encryption to no avail.  The connection just continues as pending and eventually will time out.  

 
I  have read in various posts online that there may be chipset issues or a  new driver required for Ubuntu and this particular machine, but I can  not find a straight answer in relation to this particular problem. 
 
Any advice?

---

### Post by wildmanne39 on 2012-06-23
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

