---
title: "Switched Motherboards - No Network"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by fullmoonguru on 2010-11-24
I swapped mb's between 2 of our 'buntu machines & now I don't have a network connection on the one that I have got running again.  It's definitely a software issue because I can load a live cd & get a connection.  I assume that the NIC driver from the previous MB is there & needs to be removed or something but I'm not sure how to properly diagnose this issue.

---

### Post by CharlesA on 2010-11-24
What does this do:

```
sudo ifconfig eth0 up
```

---

### Post by fullmoonguru on 2010-11-24
Ran that.  No change.

---

### Post by CharlesA on 2010-11-25
If that's not working, can you post the output of this:

```
cat /etc/network/interfaces
```

Also look into [iftab]("http://linux.die.net/man/5/iftab"), since that is where the config for the network interfaces is stored.

---

### Post by fullmoonguru on 2010-11-25
Thanks for your help.  The eth1 listing below might point to the problem.  In Network Tools my NIC is listed as eth0.  I had a similar problem some time ago with this board when I got a switch to use with our router.  The network wouldn't work with the switch.  I remember seeing eth2 in the output of some file.  Somewhere along the line it went back to eth0 & then when i plugged it in to the switch it worked.

There's no iftab file in the directory shown at that link (I can see hidden files).

  	 	 	 	```
mammy@mammy:~$ cat /etc/network/interfaces  
 # This file describes the network interfaces available on your system  
 # and how to activate them. For more information, see interfaces(5).  
 

 # The loopback network interface  
 auto lo  
 iface lo inet loopback  
 

 # The primary network interface  
 auto eth1  
 iface eth1 inet dhcp  
 	address 192.168.0.194  
 	netmask 255.255.255.0  
 	network 192.168.0.0  
 	broadcast 192.168.0.255  
 	gateway 192.168.0.1  

```

---

### Post by CharlesA on 2010-11-25
Looks like iftab isn't on the desktop version of Ubuntu.

Try changing the entry in /etc/network/interfaces to eth0 instead of eth1 and reboot.

---

### Post by fullmoonguru on 2010-11-25
Alright so 70 persistent-net.rules is the new iftab.  I saw the eth1 in there (with a different mac address) & commented it out.  I think I the ifconfig eth0 up command again & restarted & it's up!

Thanks again for your help!

Edit: I almost became one of those people that fixes the problem at the end of the thread but never says how they did it!  Here it is:

In the terminal, run:

```
ifconfig
```

Look for the mac address of the NIC that's actually present.  In my case it was eth1:

```
eth1      Link encap:Ethernet  HWaddr 00:16:17:17:d5:b3  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe17:d5b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:982762 (982.7 KB)  TX bytes:398519 (398.5 KB)
          Interrupt:23 Base address:0xa400 

```
In the terminal:

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

In that file there will be lines for the old NIC card and the new one.  You can verify by check the mac address.  The old one will be eth0.  comment out that line by entering a # and a space at the beginning of the line, change "eth1" in the line for the new NIC to "eth0", save the file, restart.

---

### Post by CharlesA on 2010-11-25
Awesome. Thanks for the info on *70 persistent-net.rules*, I didn't know that.

Be sure to mark the thread as solved from thread tools :)

---

