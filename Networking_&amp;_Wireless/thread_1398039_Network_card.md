---
title: "Network card"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by adeelm on 2010-02-04
hi everyone,

                 I am new to Ubuntu and I am using ubuntu 9.04. I have recently undated all the components using the following command

apt-get update
apt-get upgrade

After that I have noticed that I can browse and access my lan but can not see the network connection. It seems to be disconnected. the result of ifconfig is below
eth1      Link encap:Ethernet  [COLOR=Red]HWaddr aa:aa:aa:aa:aa:aa[/COLOR]  
          [COLOR=Red]inet addr:x.x.x.x  Bcast:y.y.y.y  Mask:x.x.x.x[/COLOR]
          inet6 addr: fe80::21b:78ff:fea5:3679/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4007837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1075560794 (1.0 GB)  TX bytes:8258132 (8.2 MB)
          Interrupt:16 Base address:0x4000 

Note: I have changed the Highlited part..



and the network in the GUI does not show it. I am attaching a screen shot of that.

Thank you all

Adeel

---

### Post by Iowan on 2010-02-04
I presume the masked information shows valid IP address? Which network connection cannot be seen (is there supposed to be an eth0?)

---

### Post by adeelm on 2010-02-05
Hi all,

Thanks for the reply. Yes there are two network cards. I am not using eth0.


Adeel

---

### Post by adeelm on 2010-02-05
hi all,

Yes the masked information is correct and it is about eth1, which I am using and it is seems to be disconnected. but I can browse the web. eth0 is not being used...

Adeel

---

### Post by Iowan on 2010-02-05
Is this a default, DHCP-addressed machine, or is interface configured via */etc/network/interfaces*? The "vmnet" designations seem unusual - is this a virtual machine?

---

### Post by adeelm on 2010-02-08
Hi all,

The interface is configured via */etc/network/interfaces. *and it is not a virtual machine. I am running 2 virtual machines on this OS.
[I]
Thanks

Adeel
[/I]

---

### Post by Iowan on 2010-02-08
Network Manager (the GUI) ordinarily won't touch (or acknowledge) interfaces defined in */etc/network/interfaces*.

---

### Post by adeelm on 2010-02-08
Thank you Iowan,

You are of great help. Can you guide me to a link or expalin me the cause of this behavior of Ubuntu that you mentioned in you reply. [SIZE=4][COLOR=Red](" [/COLOR][/SIZE][SIZE=4][COLOR=Red]		Network Manager (the GUI) ordinarily won't touch (or acknowledge) interfaces defined in */etc/network/interfaces*. 	")[/COLOR][/SIZE]

Thanks

Adeel

---

### Post by Iowan on 2010-02-09
[Here]("http://www.arachnoid.com/linux/NetworkManager/index.html") is some history. You can also search for "Network Manager". Earlier versions (pre-Hardy) used */etc/network/interfaces* for configuration. I could only speculate on the reasons for allowing the NM bypass.

---

### Post by adeelm on 2010-02-10
Thanks Iowan,

                     The info that you provided was of great help. it cleared doubts in my mind and I also got some good knowledge now.

Thanks again

Adeel

---

