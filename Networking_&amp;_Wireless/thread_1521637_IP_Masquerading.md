---
title: "IP Masquerading"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by teonghan on 2010-07-01
Hi all,

I am setting up a computing cluster in my lab, as below. all the "eth0" IP addresses are static (for cluster communication) and the "eth1" of the front node is the only one connected to the internet through lab's DHCP server (which is connected to a centralized computer center in the university). The thing I wish to do is to do some sort of IP masquerading to enable all the nodes to have internet access. I actually google around and read some books. The similar things I came across is setting rules in iptables but I did not manage to get any of them working. Anyone here have an idea on how to do this? Would appreciate a step-by-step approach. I am using Ubuntu Lucid 64-bit on all machine.

---

### Post by pedro_orange on 2010-07-01
You'll need to configure the one attached to the Internet as a gateway.
You'll then need to tell the clients, that the machine connected to the Internet is their gateway.

Perhaps this will help you: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by capscrew on 2010-07-01
> **teonghan said:**
> Hi all,

I am setting up a computing cluster in my lab, as below. all the "eth0" IP addresses are static (for cluster communication) and the "eth1" of the front node is the only one connected to the internet through lab's DHCP server (which is connected to a centralized computer center in the university). The thing I wish to do is to do some sort of IP masquerading to enable all the nodes to have internet access. I actually google around and read some books. The similar things I came across is setting rules in iptables but I did not manage to get any of them working. Anyone here have an idea on how to do this? Would appreciate a step-by-step approach. I am using Ubuntu Lucid 64-bit on all machine.

I think you have 2 concepts here.  The first being the multiple hosts in a cluster configuration (ie. Beowolf, etc.).  I believe these hosts should be considered as one machine.  The master is the only host that needs to be connected to the wider world.

The second is IP masquerading.  This is now know as NAT.  It is used when running private addressed IP LAN's.  It provides a method for connecting numerous PC hosts to use 1 public IP address for connection to the internet.

If you are indeed creating a cluster then NAT is not needed, on the other hand if you are creating a LAN with private addressing through a gateway host then you do not really have a cluster situation.

Looking at you attachment it appears that you really are just constructing a LAN that will need a router/gateway to provide you a single connection to the Universities larger network.  See [**_here_**]("https://help.ubuntu.com/community/Router") for more information.

---

### Post by teonghan on 2010-07-01
> **pedro_orange said:**
> You'll need to configure the one attached to the Internet as a gateway.
You'll then need to tell the clients, that the machine connected to the Internet is their gateway.

Perhaps this will help you: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I have been checking out that one but I can not get it working.

---

### Post by teonghan on 2010-07-01
> **capscrew said:**
> I think you have 2 concepts here.  The first being the multiple hosts in a cluster configuration (ie. Beowolf, etc.).  I believe these hosts should be considered as one machine.  The master is the only host that needs to be connected to the wider world.

The second is IP masquerading.  This is now know as NAT.  It is used when running private addressed IP LAN's.  It provides a method for connecting numerous PC hosts to use 1 public IP address for connection to the internet.

If you are indeed creating a cluster then NAT is not needed, on the other hand if you are creating a LAN with private addressing through a gateway host then you do not really have a cluster situation.

Looking at you attachment it appears that you really are just constructing a LAN that will need a router/gateway to provide you a single connection to the Universities larger network.  See [**_here_**]("https://help.ubuntu.com/community/Router") for more information.

Yeah, you are right in a way. But the thing is my lab is that it sometimes will be used as a teaching lab/computer lab for students. The concept of my cluster is that it will be used when the computer-nodes are available (no class/during holidays). The nodes are all actually part of the computers available in the lab (around 25 of them). That is why, although I am using 4 of them to build a cluster but I need individual node to be able to connect to internet also.

p/s: will check out that link in a short time.

---

### Post by capscrew on 2010-07-01
> **teonghan said:**
> Yeah, you are right in a way. But the thing is my lab is that it sometimes will be used as a teaching lab/computer lab for students. The concept of my cluster is that it will be used when the computer-nodes are available (no class/during holidays). The nodes are all actually part of the computers available in the lab (around 25 of them). That is why, although I am using 4 of them to build a cluster but I need individual node to be able to connect to internet also.

p/s: will check out that link in a short time.

I think you will find that the cluster vs a LAN of individual hosts are mutually exclusive ideas.  You can have either one, but not both easily.  You would have to reconfigure the cluster each time you wanted to use it.  

[**_Here _**]("http://www.linuxjournal.com/article/5862")is an article on a 2 node cluster that might be fun to build.

---

### Post by teonghan on 2010-07-08
capscrew,

Thanks for the article. Anyway, I somehow get every node of my cluster to be able to connect to the internet in the following steps:

1. "cat /etc/resolv.conf" on the frontnode. Jot down the IP of nameserver, say 123.123.123.123

2. Say I have eth1 on my frontnode which has IP assigned by lab's server and eth0 which has static IP (192.168.0.1) connected to cluster's private LAN. "sudo nano /etc/network/interfaces" and add these lines:
    
    auto eth1
        [INDENT]iface eth1 inet dhcp[/INDENT]
    auto eth0
        [INDENT]iface eth0 inet static[/INDENT]
        [INDENT]address 192.168.0.1[/INDENT]
        [INDENT]netmask 255.255.255.0[/INDENT]
        [INDENT]broadcast 192.168.0.0[/INDENT]
        [INDENT]network 192.168.0.0[/INDENT]

3. "sudo gedit /etc/sysctl.conf" and set "net.ipv4.ip_forward=1".

4. "sudo gedit /etc/rc.local" and add

   sudo /sbin/iptables -P FORWARD ACCEPT
   sudo /sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE 
   exit 0

5. Reboot.

6. For each node/client, right click on the network connection, edit the eth0 connection -> IPv4 Settings -> Manual -> Add. Set IP as 192.168.0.2 (which is my 1st node's static IP), Netmask as 255.255.255.0, Gateway as 192.168.0.1. Set DNS server as 123.123.123.123. Disable and enable the network connection. Done.

---

