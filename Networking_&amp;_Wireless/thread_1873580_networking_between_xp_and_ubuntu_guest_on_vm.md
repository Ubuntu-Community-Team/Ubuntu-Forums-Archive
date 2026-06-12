---
title: "networking between xp and ubuntu guest on vm"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by ohad.sadan on 2011-11-01
hello all 
(taking my first steps in linux looks well)
I have a problem trying to set up a network between my xp and my ubuntu which installed on vmware machine.
my xp is connecting to the web using modem.
I tried to define the connection in the vm seeting to use the bridge but then I had no connection to the web from my ubuntu 
Then I tried to set up network using the xp "machanism"
and changed my settings in the vm to bridge then I was able to reach the web from my ubuntu but when I tried to set up a connection from the xp it faile either way I didn't succeeded to see the xp machine in the ubuntu netwrking window and to see the ubuntu machine in my networking window in my xp .
little details

my modem is configured  wan(ppp/slip)

IP / Subnet Mask	89.138.253.156 / 255.255.255.255
Gateway	89.138.253.156
Hardware Address	00-53-45-00-00-00

my xp (LAN) is configured
IP / Subnet Mask	172.28.234.202 / 255.255.248.0
Gateway	172.28.232.1
DHCP	172.18.144.176
DNS	192.168.101.102
Hardware Address	00-19-D1-FC-DA-91

and my vm is configured


Hardware Address	00-50-56-C0-00-08
IP / Subnet Mask	192.168.0.1 / 255.255.255.0
DHCP	255.255.255.255

Regards

---

### Post by haqking on 2011-11-01
> **ohad.sadan said:**
> hello all 
(taking my first steps in linux looks well)
I have a problem trying to set up a network between my xp and my ubuntu which installed on vmware machine.
my xp is connecting to the web using modem.
I tried to define the connection in the vm seeting to use the bridge but then I had no connection to the web from my ubuntu 
Then I tried to set up network using the xp "machanism"
and changed my settings in the vm to bridge then I was able to reach the web from my ubuntu but when I tried to set up a connection from the xp it faile either way I didn't succeeded to see the xp machine in the ubuntu netwrking window and to see the ubuntu machine in my networking window in my xp .
little details

my modem is configured  wan(ppp/slip)

IP / Subnet Mask	89.138.253.171 / 255.255.255.255
Gateway	89.138.253.171
Hardware Address	00-53-45-00-00-00

my xp (LAN) is configured
IP / Subnet Mask	172.28.234.202 / 255.255.248.0
Gateway	172.28.232.1
DHCP	172.18.144.176
DNS	192.168.101.102
Hardware Address	00-19-D1-FC-DA-91

and my vm is configured


Hardware Address	00-50-56-C0-00-08
IP / Subnet Mask	192.168.0.1 / 255.255.255.0
DHCP	255.255.255.255

Regards

Just use NAT if you want the VM to access the internet and see the host.

If you want host to VM networking then you need bridged.

If you use bridged you need to change your guest IP as it is using a class C address

---

### Post by ohad.sadan on 2011-11-01
I want to use samba to share files so I will be able to remove all my development enviorment to linux.
How I can change my ip of the vm macine 
(besides give them static ips on the xp configuration window for network connetion)?

---

### Post by haqking on 2011-11-01
> **ohad.sadan said:**
> I want to use samba to share files so I will be able to remove all my development enviorment to linux.
How I can change my ip of the vm macine 
(besides give them static ips on the xp configuration window for network connetion)?

what version of Ubuntu is it ?

Use network manager or edit the

/etc/network/interfaces

and add or edit the following:

# The primary network interface
auto eth0
iface eth0 inet static
        address x.x.x.x
        netmask x.x.x.x
        network x.x.x.x
        broadcast x.x.x.x
        gateway x.x.x.x

with whatever entries you need, i cant tell you what they will be but need to be valid for your LAN, so in the 172.x.x.x range

When you say use smaba to share files you mean just to share files between the VM and the host ? if so just use shared folders.

NAT is easiest for VM's unless you really require bridged, im not saying you dont, i use bridged, but usually if you dont know what you are doing then NAT is the easiest choice

---

### Post by ohad.sadan on 2011-11-01
tnx for the quick replay
but I am complete dummy here
address I will change to 172.28.202.1
netmask to 255.255.248.0
gateway to 172.28.232.1
but what about 
network and broadcast (I don't have a clue)
and I want to shre files using samba so 
I dont now if I need NAT or not

---

### Post by ohad.sadan on 2011-11-01
> **ohad.sadan said:**
> tnx for the quick replay
but I am complete dummy here
address I will change to 172.28.202.1
netmask to 255.255.248.0
gateway to 172.28.232.1
but what about 
network and broadcast (I don't have a clue)
and I want to shre files using samba so 
I dont now if I need NAT or not

I am using the latest ubuntu(11.10) and the latest vm (4.0.0)

---

### Post by ohad.sadan on 2011-11-01
> **haqking said:**
> what version of Ubuntu is it ?

Use network manager or edit the

/etc/network/interfaces

and add or edit the following:

# The primary network interface
auto eth0
iface eth0 inet static
        address x.x.x.x
        netmask x.x.x.x
        network x.x.x.x
        broadcast x.x.x.x
        gateway x.x.x.x

with whatever entries you need, i cant tell you what they will be but need to be valid for your LAN, so in the Class B 172.28.x.x range

When you say use smaba to share files you mean just to share files between the VM and the host ? if so just use shared folders.

NAT is easiest for VM's unless you really require bridged, im not saying you dont, i use bridged, but usually if you dont know what you are doing then NAT is the easiest choice

I changed the address to 172.28.x.x
the netmask to 255.255.248.0
and the gateway to 172.28.232.1

I want to work on my xp and the files to be located on the ubuntu machine (to be able to read and write not just pass files betweent the machines)

---

### Post by haqking on 2011-11-01
> **ohad.sadan said:**
> I am using the latest ubuntu(11.10) and the latest vm (4.0.0)

the latest Virtual Box is 4.1.4

You can get it here [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

you also need the extensions pack

Well NAT works between VM and external, so if you want your VM to access windows files it can do, if you want to go back the other way then you need bridged, you could setup port forwarding but bridged is preferred.

Shared folders is for between VM and host both ways for file sharing between the 2.

---

### Post by ohad.sadan on 2011-11-01
I am using vmware 4.0.0

---

### Post by haqking on 2011-11-01
> **ohad.sadan said:**
> I am using vmware 4.0.0

ahh sorry i missed that bit, i stopped using VMware years ago.

The same terms apply with bridged, NAT, shared folders etc

---

### Post by ohad.sadan on 2011-11-01
> **ohad.sadan said:**
> I changed the address to 172.28.x.x
the netmask to 255.255.248.0
and the gateway to 172.28.232.1

I want to work on my xp and the files to be located on the ubuntu machine (to be able to read and write not just pass files betweent the machines)

I run  ifconfig etc0 down
and ifconfig etc0 up
but I still see the 192.168.x.x
address 

Is there a way to route it to the 172.28.x.x gateway ?

---

