---
title: "Multiple External IP addresses with single physical Ethernet card and virtualization"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by dc-spyder on 2010-02-15
Wasn´t sure if here or the Server forum was the best place for this query.

I recently installed Ubuntu Server 9.10 with the intent of using it as a platform for running a couple of Windows XP virtual machines along with Linux/Ubuntu.

I had no problems getting the server installed.  Had no problems getting the network up and running so that I had access to both my internal network as well as external connectivity to the internet.  Had no problems getting a VM installed and putting Windows XP inside of it.  Had no problems setting up a bridge between the WinXP virtual machine and the physical ethernet card (eth0).  

What I´m having trouble with is figuring out how to bridge from multiple VM´s AND Ubuntu natively through one physical ethernet card.  

When I set up the bridge, it knocks out the static IP address of the ethernet card that was set up initially with Ubuntu when first installed before the VM was created and installed.  Therefore, connectivity within Ubuntu natively is lost.  

Similarly, am having trouble figuring out how the second VM (also going to be running WinXP) is going to get its connectivity since it doesn´t seem to like me setting up 2 bridges to the same physical ethernet interface card.  

I need all 3 ¨machines¨ to have static IP addresses and be visible/accessible from the external network for either web/mail/dns/etc servers on the Ubuntu side and for remote PC control functionality on the VM side.

Any thoughts would be appreciated.  I have tried setting up ¨alias¨ ethernet interfaces (eth0:1, eth0:2, eth0:3) with static addresses which work fine from native Ubuntu in presenting multiple IP addressees, but it seems that I´m not permitted to bridge to these ¨alias¨ interfaces.

---

### Post by kiranmurari on 2010-02-16
Hi,

You can think of bridged mode like a switch connecting your host NIC and all guest NICs
to your network cable. Each guest will act like a dedicated physical machine.

Having said that, the network device(router) connected to ubuntu server, may not be
allowing multiple MAC addresses connected to one physical port (MAC spoofing).

If it is your home network, can you check the router configuration and see if there is
any configuration option to overcome this. If it is your corporate network, you can talk
to your IT admin guys.

---

### Post by dc-spyder on 2010-02-16
Assuming I can get the hardware issue resolved (home network), will this type of configuration in /etc/network/interfaces work?
 
iface eht0 inet static
 ...
 ...
 
iface br0 inet static
 address 192.168.2.6
 ...
 ...
 bridge_ports eth0
 
iface br1 inet static
 address 192.168.2.7
 ...
 ...
 bridge_ports eth0
 
iface br2 inet static
 address 192.168.2.8
 ...
 ...
 bridge_ports eth0

---

### Post by kiranmurari on 2010-02-17
Hi,
 
There is no necessity to create multiple bridges on your host. As there is only one physical interface, you just need to create one bridge. So your /etc/network/interfaces would be:
```
iface br0 inet static
address 192.168.xxx.xxx
...
...
bridge_ports eth0
```Assuming you are using KVM for virtualization and created the VM using libvirt, you need to specify the networking mode as "bridged". For this you can change the network mode to bridge by changing the corresponding VM's XML file located in /etc/libvirt/qemu/. You need to change the following lines:
```
<interface type='network'>
<source network='default'/>
</interface>
```to```
<interface type='bridge'>
<source bridge='br0'/>
</interface>
```For more information, please see: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

Hope this helps.

---

### Post by dc-spyder on 2010-02-17
Thanks for the link.

I understand how bridging the virtual machine through the physical ethernet card can bring a static, assigned address to the virtual machine, but it appears to be at the "expense" of the ethernet card itself having an address.  But what if I need Ubuntu to have a static IP address for purposes of running services (apache, smtp, dns, etc) but would like the VMs to also have a static address if I wanted to run some sort of service(s) on them accessible from the outside world?

---

### Post by kiranmurari on 2010-02-22
Hi,

You can access services running on the Ubuntu host machine with the IP address assigned to the bridge (br0). You can also access services running on individual VM by assigning static IP to the VM. But you need to allow the incoming connections through your gateway (router)

For example consider the following setup:
Assuming your internal network is in 192.168.1.168.xxx subnet;
192.168.1.1 is the LAN IP of the gateway and A.B.C.D is the WAN IP of
the gateway;
> Host (192.168.1.10) ----- GATEWAY ----- INTERNET ----- EXTERNAL MACHINE
VM1 (192.168.1.11)
VM2 (192.168.1.12)
VM3 (192.168.1.13)
VM4 (192.168.1.14)On the router, you need to forward an incoming request appropriately, something like - a request to A.B.C.D and port 80 should be forwarded to 192.168.1.11, if your apache server is running on VM1. Similarly, a request to A.B.C.D and port 25 should be forwarded to 192.168.1.10, if your SMTP server is running on the Host.

In case you have enough public IPs, so that you can assign one per VM, then you can use routing from the gateway to the VM or NATTing on the gateway.

Hope this helps.

---

