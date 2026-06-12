---
title: "Wired Internet Connection only works for a few seconds"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by rdasilva451 on 2009-05-13
Greetings All,

I have a relatively new HP laptop running Intrepid Ibex. After working for months my wired internet is now giving me some headaches. I can get my wired connection to work for several seconds after I plug it in but then it goes dead. Any ideas? 

When I type ifconfig the output for the eth0 card is as follows:

eth0      Link encap:Ethernet  HWaddr 00:23:5a:2a:8b:4d  
          inet6 addr: fe80::223:5aff:fe2a:8b4d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3598 errors:0 dropped:736929217 overruns:0 frame:0
          TX packets:1174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:884701 (884.7 KB)  TX bytes:216033 (216.0 KB)
          Interrupt:251 Base address:0xe000 

I greatly appreciate any help you can give me.

As a side note, in the past I had dealt with a problem with the wired internet being put to sleep by windows whenever I logged into Windows, but that has been fixed (by changing the power saver settings in Windows), but I haven't logged into windows in a long time and I don't think this is the issue.

Thanks,
-rdasilva451

---

### Post by Peter09 on 2009-05-13
can you type the output of the route command

```
route
```
and
```
lshw -C network
```

---

### Post by rdasilva451 on 2009-05-13
Well it looks like this has been solved for me....

I decided to make sure my wired card actually worked by rebooting into windows. There it worked perfectly. 

As I mentioned before windows has the annoying habit of turning off my wired internet connection. The solution to this is to shutdown your computer and remove the battery and leave it sitting for a few minutes. When I went through this and booted back up the problem was gone... 

I thought they were unrelated since I hadn't used windows in months and it suddenly (this morning broke), but apparently not.

Thanks for all your help!

-rdasilva451

---

### Post by Iowan on 2009-05-13
Hmmm... I also have a new-ish HP laptop that quit playing nice with ethernet connection - I'll try the battery trick.

(update) Nope, still won't get an address via DHCP, but worth the attempt - thanks anyway.

---

