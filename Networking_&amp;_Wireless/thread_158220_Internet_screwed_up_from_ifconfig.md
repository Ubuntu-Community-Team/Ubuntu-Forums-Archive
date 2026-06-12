---
title: "Internet screwed up from ifconfig"
date: 2006-04-10
forum: Networking &amp; Wireless
---

### Post by ctkroeker on 2006-04-10
I did something like this just a little while ago to change my IP address
```
sudo ifconfig eth0 192.168.0.120 netmask 255.255.255.0 up
```
and now I can´t connect to the internet at all. It was really stupid to just do it like that, but I didn´t know how to get a static IP address otherwise (I´m running Xubuntu). I´d apreciate any help at the moment (I´m writing this from another machine on the network) and hope to get this resolved fast.
BTW, when I open Firefox, it pops up an error saying that it couldn´t connect to  the internet.
Here´s kinda what iconfig says.
```
# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:80:C8:F8:4A:53  
          inet addr:192.168.0.120  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x5000 
```
I´ll have to fix this from the command line.
here is my network info that I want to be static:
IP: 192.168.0.120 (router is default 192.168.0.1)
Mask: 255.255.255.0
Any help will be greatly appreciated and I apologize if this has been asked before (I searched a lot).

---

### Post by ctkroeker on 2006-04-10
```
 pljvaldez said:

http://textsnippets.com/posts/show/319

Just use sudo nano /etc/network/interfaces and use the address 192.168.0.120 instead of 192.168.0.100 in the link above...

Then you should just have to do sudo ifdown eth0 and sudo ifup eth0 to restart the network.

Or use /etc/init.d/networking restart (I just found this command)...
```
I did that and I got this:

~$ sudo ifconfig -a eth0      

Link encap:Ethernet  HWaddr 00:08:54:22:0F:32
BROADCAST MULTICAST  MTU:1500  Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0        
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)          
Interrupt:17 Base address:0xec00  

lo        
Link encap:Local Loopback          
inet addr:127.0.0.1  Mask:255.0.0.0          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:402 errors:0 dropped:0 overruns:0 frame:0         
TX packets:402 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:0          
RX bytes:14461 (14.1 KiB)  TX bytes:14461 (14.1 KiB)

---

### Post by patricku on 2006-04-11
Do you get a reply by pinging : gateway & dns ?
If not, there is your problem.

---

### Post by s7eam on 2006-04-11
```
sudo nano /etc/resolv.conf
```
Write dns information you've got from your ISP like this:
```

nameserver [nameserver IP #1]
nameserver [nameserver IP #2]

```

```
sudo ifconfig eth0 192.168.0.120 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1
```
**ping 192.168.0.1** to see if you can reach your gateway

---

### Post by ctkroeker on 2006-04-11
Thank you s7seam! It worked! I gotta bookmark this thread so I can remember it if it happens again.

---

