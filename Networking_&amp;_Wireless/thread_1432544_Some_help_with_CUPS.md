---
title: "Some help with CUPS"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by a.walker on 2010-03-17
I am a bit of a newbie when it comes to linux/ubuntu. 

Question 1:

I run a windows XP VM in virtualbox (Not OSE) to print coupons from coupons.com for my wife. I tried to set up the USB in the VM so that I could print directly to the printer. This didn't work out too well and so I set up XP so that it printed directly to CUPS in Ubuntu, which worked perfectly. Unfortunately, I've reformatted / reinstalled Ubuntu since then and I forgot how I set it up. I have done the following:

0) set the XP VM's networking so that it operates in bridged mode.
1) installed the printer drivers in Ubuntu
2) installed the printer drivers in Windows XP
3) disabled UFW in ubuntu
4) entered the Windows XP dialog to print to networked printer and set it up to print as follows "http://<ip address of Ubuntu Box>:631/printers/Brother (my printer's name)"

At this point it when I click on "Okay" XP pops up an error messages saying something along the lines of "Could not find the printer".

Is there additional configuration that I need to do for CUPS? Is there an easier/better way to do this?

QUESTION 2:

When I run
```
netstat -ntulp
```I receive the following output 


```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:38568           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -       
```
Are those two entries for cups normal?

---

### Post by johnson.d on 2010-03-18
The cause may be you didn't share the printer in CUPS. For sharing the printer in CUPS you can use the following command:

$ sudo cupsctl --share-printers

Now try connecting from windows again.

The above command makes CUPS listen requests from other machines.

---

### Post by a.walker on 2010-03-18
Thanks. That's exactly what it was. The printer is working perfectly now.

---

