---
title: "Problem connecting to internet after starting apparmor."
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by newhere_m on 2011-10-08
I am using os ubuntu 10.04 LTS and adsl modem to connect to internet. The problem is ever since I kept firefox profile in apparmor enforce mode, I have problem connecting to internet. (I kept some other profiles in enforce mode but later removed those and also brought back firefox to complain mode.) I use these commands to connect to internet:
```

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf

``` and the follow the instructions. Before the current problem started, I had set the network connection using the above commands and then in order to connect to the net, used the commad: "sudo pon dsl-provider" but now a days if I use this command, I get response like: Timeout waiting for PADS packets, Unable to complete PPPoE Discovery, Terminating on signal 15 etc (sometimes even "network is down"). I repeat the sudo comands as in the code above again (though this is no required to be done each time I try to connect to net, only the command "sudo pon dsl-provider" is supposed to be used each time) and then finally the net can be connected. The response this time is like:
> Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Why am I required to set up network connections everytime? This was not so earlier. Can anybody please explain? I am giving below the result of ifconfig -a:
> 
eth0      Link encap:Ethernet  HWaddr x.x.x.x  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.255.0
          inet6 addr: x.x.x.x/x Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1031728 (1.0 MB)  TX bytes:160778 (160.7 KB)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63856 (63.8 KB)  TX bytes:63856 (63.8 KB)

ppp0      Link encap point-to-Point Protocol  
          inet addr-x.x.x.x  P-t-P-x.x.x.x  Mask-x.x.x.x
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:1316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:953063 (953.0 KB)  TX bytes:133787 (133.7 KB)
 (Here I have replaced numbers in addresses by x, being unwilling to expose my exact network parameters to open world, thus reducing chances of hacking.) Any suggestions will be appreciated. Thanks.

---

