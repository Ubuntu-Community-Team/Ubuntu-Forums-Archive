---
title: "jaunty upgrade - ping yes, ftp yes, browse / web no"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by enrite on 2009-05-10
Hi All,

I am having a similar problem as others and have tried several solutions suggested in other threads to resolve the issue, but have not been successful.

I can ping successfully and log into FTP sites, but cannot browse to web sites using Opera or Firefox - the browser cannot connect.  I have a wired network that worked fine under intrepid.  

Any suggestions would be very much appreciated!

Thanks,

Ian

---

### Post by superprash2003 on 2009-05-11
are you able to open [http://74.125.45.100](http://74.125.45.100)

---

### Post by enrite on 2009-05-11
Hi,

Thanks for your note and sorry for the delay in getting back to you.  Tough to get to the computer during the week...

I cannot connect to Google with Opera or Firefox.

---

### Post by superprash2003 on 2009-05-12
it didnt even open via ip?.. post output of **ifconfig** from the terminal.

---

### Post by enrite on 2009-05-12
Here's the output.  Thanks for taking a look!

Ian

eth0
      Link encap:Ethernet  HWaddr 00:40:ca:90:65:08  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe90:6508/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29640497 (29.6 MB)  TX bytes:2243921 (2.2 MB)
          Interrupt:20 Base address:0xa000 

lo
        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:850120 (850.1 KB)  TX bytes:850120 (850.1

---

### Post by coutts99 on 2009-05-12
Does dns resolve stuff?

If you ping [www.google.com](www.google.com), does it resolve to an ip address?

---

### Post by enrite on 2009-05-12
Hi, 

Yes, if I use the network tool I can ping [www.google.com](www.google.com) - it returns packets.

Thanks for the suggestion!

Ian

---

### Post by superprash2003 on 2009-05-13
have you tried disabling ipv6?? [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by enrite on 2009-05-14
Thanks for the suggestion, but that didn't work either.

I decided to try to boot from cd with jaunty to see if I was able to browse.  That worked, so I just reinstalled from scratch.

Thanks for all the help, though!

Ian

---

