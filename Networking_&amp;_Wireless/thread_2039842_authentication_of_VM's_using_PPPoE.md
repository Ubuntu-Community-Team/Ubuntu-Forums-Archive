---
title: "authentication of VM's using PPPoE"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by liv2hak on 2012-08-09
I have two VM's running on Ubuntu box.Their name and IP addresses are give below.

nas                      192.168.129.153
home_user                192.168.129.152 

I establish a ppp connection between the two machines

    #nas (server)
    sudo pppd noauth local lock defaultroute persist nodetach 10.1.1.2:10.1.1.3 pty “nc -l 3333”
    
    #home_user(client)
    sudo pppd noauth local lock nodetach passive pty “nc 192.168.129.153 3333”


Once I do the above I can see a ppp connection established between the two machines (from ifconfig )

    #nas (server)
    
    ppp0  	Link encap:Point-to-Point Protocol  
          	inet addr:10.1.1.2  P-t-P:10.1.1.3  Mask:255.255.255.255
          	UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          	RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          	TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          	collisions:0 txqueuelen:3
          	RX bytes:78 (78.0 B)  TX bytes:72 (72.0 B)
    
    #home_user (client)
    
    ppp0  	Link encap:Point-to-Point Protocol  
          	inet addr:10.1.1.3  P-t-P:10.1.1.2  Mask:255.255.255.255
          	UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          	RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          	TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          	collisions:0 txqueuelen:3
          	RX bytes:72 (72.0 B)  TX bytes:78 (78.0 B)


My next aim is to use PPPoE for transport.I install pppoe package on the server 

sudo apt-get install pppoe

sudo pppoe-server -I eth0 -L 192.168.129.153 -R 192.168.129.152 -O /etc/ppp/options

I have edited the options file to enable chap and pap authentication.I have also edited chap and pap secret files.

Now my question how do I use the ppp daemon pppd to connect to the server above?
It seems that I have to use the /usr/lib/ppp/version/rp-pppoe.so (part of ppp daemon).How do I make the ppp daemon act as a pppoe client that supports authentication?Any help is appreciated.

---

