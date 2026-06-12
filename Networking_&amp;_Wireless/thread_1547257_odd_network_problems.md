---
title: "odd network problems"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by james.king@4act.com on 2010-08-06
I am having (seemingly) random trouble with my wired network ever since I installed Lucid. I have no problem getting an ip address from dhcp. However, randomly the computer will boot and although I have an ip address I do not receive any responses for pings on the network nor can I browse the web. If I sudo /etc/init.d/networking restart a few times (or reboot) it will start working. However, restarting the networking services (as mentioned above) again will cause me to no longer receive responses for pings or browse the web. 

Furthermore, I have never been able to successfully ping if I manually set an ip address. 

I have un-installed network manager and I am using /etc/network/interfaces to configure the network. 


Using Lucid Lynx 64bit on a Dell Precision. I have pasted below the output of a few helpful commands. When I switch between static ip and dhcp I am commenting/uncommenting the lines shown in /etc/network/interfaces. 

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:99:4a:85
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5754-v3.24 ip=10.200.147.153 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:78 memory:f7cf0000-f7cfffff



cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1

auto eth0
#iface eth0 inet static
#address 10.200.147.56
#netmask 255.255.255.0
#broadcast 10.200.147.255
#gateway 10.200.147.1

iface eth0 inet dhcp

---

### Post by james.king@4act.com on 2010-08-06
Here is a post of the output of the same commands above when I attempt to use static configuration. Perhaps I am doing something wrong.




ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:99:4a:85  
          inet addr:10.200.147.56  Bcast:10.200.147.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2912 (2.9 KB)  TX bytes:2961 (2.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)



cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1

auto eth0
iface eth0 inet static
address 10.200.147.56
netmask 255.255.255.0
broadcast 10.200.147.255
gateway 10.200.147.1


#iface eth0 inet dhcp



ping 10.200.147.1
PING 10.200.147.1 (10.200.147.1) 56(84) bytes of data.
^C
--- 10.200.147.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9008ms

---

### Post by cgb on 2010-08-06
Seems like everything is setup correctly from what I can see..  Just a thought, have you tried another cable?  I have seen strange behavior such as this from slightly faulty cables before.

---

### Post by james.king@4act.com on 2010-08-06
I don't really have another cable long enough (10 ft). 

The thing is, if I reboot my computer into my old distro (Hardy) everything works great.

---

### Post by james.king@4act.com on 2010-08-06
> **cgb said:**
> Seems like everything is setup correctly from what I can see..  Just a thought, have you tried another cable?  I have seen strange behavior such as this from slightly faulty cables before.

okay, I found another cable. Problem still exists.

---

### Post by dineshs on 2010-08-07
> I have un-installed network manager and I am using /etc/network/interfaces to configure the network. Did you do it using
```
sudo apt-get remove --purge network-manager*
```?

---

### Post by rcchume on 2010-08-07
[FONT="Arial"][SIZE="1"]Comment out "gateway 10.200.147.1" in /etc/network/interfaces[/SIZE][/FONT]

---

### Post by james.king@4act.com on 2010-08-09
> **dineshs said:**
> Did you do it using
```
sudo apt-get remove --purge network-manager*
```?

Wow Dinesh! Either that did the trick or one other thing I did which was get my network administer to have the dhcp server always give me the static ip I was setting up! Either way I have set up static to work now. I am a little confused at why though. Especially considering that ifconfig was correctly giving me the same info it is giving now.

Any ideas?

Cheers,

James

---

### Post by james.king@4act.com on 2010-08-09
oops. Sorry Dineshs, I take that back. After rebooting the machine nothing worked. I ran "sudo /etc/init.d/networking restart" about 3 times and still nothing. I then switched back to using dhcp and restarted the network a few times and still nothing. Then I rebooted again and still nothing worked. 
Then I ran dhclient manually and everything finally kicked up again.

So weird.

---

