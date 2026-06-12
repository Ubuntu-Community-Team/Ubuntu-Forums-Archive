---
title: "New Netgear network adapter troubles"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Bill Dubinski on 2011-04-02
Good Evening Ubuntu family. 
   I am very new to Ubuntu, with in the past 2 months, firing Winblows all together. So, yes......I am a rookie. Go easy on me, and stop laughing. Lol. 

Here is my rookie dilemma. I installed a Netgear GA311 PCI 10/100/1000 network adapter. It is physically installed into my PC. I have an integrated network card that came with my Dell computer that still works, but I wanted to upgrade, the original is a little on the old side. 

After install, and firing up Ubuntu 10.10 Maverick, the system recognizes the card being there, eth0 (original Intel) eth1 (the new Netgear) but when the ethernet cable is plugged in to the Netgear card, the system recognizes the connection via the dialog box that pops up in the upper right corner, but no internet connection. 

I have tried pinging myself, pinging my router, google.com and 8.8.8.8 with the terminal telling me "no net access". 

Running ifconfig results:
sovereign420@sovereign420:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:9d:18:f1  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe9d:18f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:372317217 (372.3 MB)  TX bytes:12983400 (12.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:1b:2f:28:50:0c  
          inet6 addr: fe80::21b:2fff:fe28:500c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16775 (16.7 KB)  TX bytes:42630 (42.6 KB)
          Interrupt:22 Base address:0xcf00

When I installed Ubuntu 2 months ago, every thing worked with no configuration what so ever. So I expected the new card to be the same result. 
I did run the Ubuntu Live disk to see if it would work there, and still no result. 
I can't fathom that a Netgear product wouldnt work with Ubuntu, so that has been ruled out in my head. But I also know that with my lack of  Linux experience, I know either I could be doing something wrong, or have left things out. 
Other than plugging it in, discovering it has not worked, and doing some pinging in the terminal, that is all Ive done. 
So if anybody has any suggestions, please help me out.
Thank you so much,

---

### Post by mads65 on 2011-04-02
I am not sure, but try
sudo ifdown eth0
followed by
sudo ifup eth1

---

### Post by Bill Dubinski on 2011-04-02
I tried those commands, Im not sure what they did, here is the out put: 

 sovereign420@sovereign420:~$ sudo ifdown eth0
[sudo] password for sovereign420: 
Ignoring unknown interface eth0=eth0.
sovereign420@sovereign420:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.

But still the same result.
Thank you so much for your effort.

---

