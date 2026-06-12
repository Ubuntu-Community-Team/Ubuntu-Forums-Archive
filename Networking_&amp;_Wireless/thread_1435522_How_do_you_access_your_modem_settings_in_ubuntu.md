---
title: "How do you access your modem settings in ubuntu"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by supoerangrymonkey on 2010-03-21
I'm a total noob apparently and have no idea how to configure my modem or even access it via ubuntu to chance the settings to a wireless connection.

---

### Post by alexfish on 2010-03-21
> **supoerangrymonkey said:**
> I'm a total noob apparently and have no idea how to configure my modem or even access it via ubuntu to chance the settings to a wireless connection.

hi

Which version of Ubuntu are you using

can you post details about the type of modem 

is it

usb , serial or pci ,also the manufacture details look at the box and the modem it's self

in the meantime try this code from the terminal and post the results if possible

Code:

dmesg | grep -e "modem" -e "tty" 

for finding a built in modem which could be almost anywhere in the dmesg  output

then from a second terminal

Code:

tail -f /var/log/syslog

**tail** is a command which outputs the last 10 lines of a file, with  the -f option it continues to monitor the file and keeps outputing any  further additions appended to the file in real time.

thanks in advance

alexfish

---

### Post by 26venger on 2010-03-21
first you need to find your gateway...
what i do is i type 

netstat -nr
this brings up your kernel ip routing table

and under the column labeled gateway it will show something like 192.168.0.1

then open firefox and type 192.168.0.1 (or whatever your gateway is) in the URL
and press enter

---

