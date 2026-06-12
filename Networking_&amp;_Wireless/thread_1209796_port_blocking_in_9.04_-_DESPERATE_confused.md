---
title: "port blocking in 9.04 - DESPERATE :confused:"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by francisco2007 on 2009-07-10
Hi all, 

After upgrading to 9.04 my ubuntu suddenly has a problem with opening ports. I declared static IP using Wicd, made sure UFW and MOBLOCK is off and still I cannot open ports for utorrent or any other applications. 
I also got firestarter, opened the specific port, and tried when the firewall is on or off. 
The most frustrating part is that I'm able to open the same port easily on Vista, so I'm pretty sure it has nothing to do with my router configuration. So the problem is isolated to ubuntu.

My ifconfig eth output is attached.

eth2      Link encap:Ethernet  HWaddr ..:..:..:..:..:..  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe4e:c0e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108837980 (108.8 MB)  TX bytes:6465440 (6.4 MB)
          Interrupt:219 Base address:0x2000 


Thanks.

---

### Post by gombadi on 2009-07-10
It looks like you are using a private ip range so you are behind some sort of router. 

To see what ports are open on the machine you can -
```
sudo netstat -plntu
```

and to see what you firewall is blocking you can use -
```
sudo iptables -vnL
```
If the firewall is not blocking ports and your system is listening on those ports then I would guess that you are not forwarding those ports to the correct address i.e. 10.0.0.3
You say you are able to open the ports easily on Vista - is that the same ip address that Ubuntu is using?

---

### Post by francisco2007 on 2009-07-11
> **gombadi said:**
> It looks like you are using a private ip range so you are behind some sort of router. 

To see what ports are open on the machine you can -
```
sudo netstat -plntu
```

and to see what you firewall is blocking you can use -
```
sudo iptables -vnL
```
If the firewall is not blocking ports and your system is listening on those ports then I would guess that you are not forwarding those ports to the correct address i.e. 10.0.0.3
You say you are able to open the ports easily on Vista - is that the same ip address that Ubuntu is using?


Indeed, I'm using a router. I defined 10.0.0.3 as the static IP of ubuntu and 10.0.0.4 as the static IP of vista (same computer - dual boot). 

The relevant part of ```
sudo netstat -plntu
``` is as follows (I listed only the 10.0.0.3 parts): 
udp        0      0 10.0.0.3:137            0.0.0.0:*                           5712/nmbd       
udp        0      0 10.0.0.3:138            0.0.0.0:*                           5712/nmbd       
udp        0      0 10.0.0.3:123            0.0.0.0:*                           6124/ntpd       


I tried opening port 12345, so does that mean that this port is closed? 

The output of ```
sudo iptables -vnL
``` gives:
Chain INPUT (policy ACCEPT 164K packets, 206M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 139K packets, 17M bytes)
 pkts bytes target     prot opt in     out     source               destination         

What do you make of it?

Many thanks for your help.

---

### Post by superprash2003 on 2009-07-11
you could try flushing your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

### Post by francisco2007 on 2009-07-11
> **superprash2003 said:**
> you could try flushing your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

Didn't help :confused:. Port is still blocked. 
I even tried 
```
 netstat -an | grep "LISTEN "
```

and found:
tcp        0      0 0.0.0.0:12345      0.0.0.0:*           LISTEN

12345 is the port Deluge/uTorrent try to listen to. I declared my PC with static IP (10.0.0.3). Does the 0.0.0.0 means something?

---

### Post by gombadi on 2009-07-11
> 
Indeed, I'm using a router. I defined 10.0.0.3 as the static IP of ubuntu and 10.0.0.4 as the static IP of vista (same computer - dual boot).


I think the above is your problem.

You say that you have no trouble using the torrents in Vista but can not use them in Ubuntu.
From the above I guess you have port forwarding set up on the router to forward port 12345 ip 10.0.0.4 with Vista. When you dual boot to Ubuntu, with 10.0.0.3, the router is still sending the torrent connections to 10.0.0.4. Ubuntu is not listening on that ip address so torrents do not work with it.

You either need to change the port forwarding ip address each time you reboot into a different operating system or configure it so both Ubuntu and Vista use the same ip address.


> 
12345 is the port Deluge/uTorrent try to listen to. I declared my PC with static IP (10.0.0.3). Does the 0.0.0.0 means something?


The 0.0.0.0 means it is listening on all interfaces - in your case 127.0.0.1 and 10.0.0.3. If you only show netstat output for things listening on 10.0.0.3 then you will miss other programs that are also listening on that ip address.

---

### Post by francisco2007 on 2009-07-12
> **gombadi said:**
> 
You say that you have no trouble using the torrents in Vista but can not use them in Ubuntu.
From the above I guess you have port forwarding set up on the router to forward port 12345 ip 10.0.0.4 with Vista. When you dual boot to Ubuntu, with 10.0.0.3, the router is still sending the torrent connections to 10.0.0.4. Ubuntu is not listening on that ip address so torrents do not work with it.

You either need to change the port forwarding ip address each time you reboot into a different operating system or configure it so both Ubuntu and Vista use the same ip address.


Already tried this and it still doesn't work. 
This is not it.

---

### Post by gombadi on 2009-07-12
> 
Already tried this and it still doesn't work.
This is not it. 


Right so with ubuntu on 10.0.0.3 and the router configured to send port 12345 to 10.0.0.3 the system is not working.

In that case you may want to see what packets the system is receiving, if any. Use tcpdump to display all packets going to/from that port -
```

sudo tcpdump -tnl -c 1000 tcp port 12345

```

---

### Post by francisco2007 on 2009-07-12
> **gombadi said:**
> play all packets going to/from that port -
```

sudo tcpdump -tnl -c 1000 tcp port 12345

```

I saw no packets, so just for sanity check I used port 80 and still nothing. Anyway I can check it otherwise?

---

