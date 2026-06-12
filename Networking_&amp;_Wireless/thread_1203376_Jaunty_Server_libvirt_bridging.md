---
title: "Jaunty Server libvirt bridging"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by patryk77 on 2009-07-03
Hey,

I need a networking guru's help.

I am trying to setup a bridge and use virtual machines, but am having lots of troubles.

I am working remotely on my server through SSH, and as it is 3800 KMs away, I have no physical access.


This is my interfaces file (obviously, X and Y are valid numbers):
```
# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address X.Y.61.18
	network X.Y.61.0
	netmask 255.255.255.224
	broadcast X.Y.61.31
	gateway X.Y.61.1
	bridge_ports eth0
	bridge_stp off
	bridge_maxwait 5

auto br0:0
iface br0:0 inet static
	address X.Y.62.118
	netmask 255.255.255.248
	gateway X.Y.62.118

```

As it is, I can't access the server at all. It doesn't reply to ping, and logging in by SSH times out. Luckily, I wrote a script to change the interfaces file and reboot, so I can work with it some more.

If I comment out br0:0, it works fine.

Now, the data center where the server is located has given me the information which I used, with secondary IP addresses:

X.Y.62.113-118

As I only have a gateway for the primary address, I need to fix the bridge to get it running.

Any suggestions? Thanks

---

### Post by patryk77 on 2009-07-03
```

bridge name	bridge id		STP enabled	interfaces
br0		8000.00221598371a	no		eth0
							vnet0

```

Ok, I assigned the secondary IP to vnet0 and now that works fine.

I have X.Y.61.18 and X.Y.62.118 working on the machine, and they both answer to ping from the internet.

I also have a VPS running under libvirt/kvm as per the server guide's instructions.

I am unable to ping or access the VPS from both the internet and the local machine however.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
X.Y.62.112      *               255.255.255.248 U     0      0        0 vnet0
X.Y.61.0        *               255.255.255.224 U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         *               0.0.0.0         UG    100    0        0 br0

```

```

sudo vmbuilder kvm ubuntu -d /mnt/second/Virtual/XXX -m 3072 --cpus=2 --rootsize=307200\
 --ip=X.Y.62.113 --gw=X.Y.62.118 --mask=255.255.255.248 -a amd64 --hostname=ruv \
--flavour=virtual --user=patryk --name="Patryk" --libvirt=qemu:///system \
--domain=aaa.bbb --firstboot ssh-boot-install.sh --bridge=br0 -o

```


```

PING X.Y.62.113 (X.Y.62.113) 56(84) bytes of data.
From X.Y.62.118 icmp_seq=1 Destination Host Unreachable
From X.Y.62.118 icmp_seq=2 Destination Host Unreachable
From X.Y.62.118 icmp_seq=3 Destination Host Unreachable

```

---

### Post by patryk77 on 2009-07-04
Ok, here is all the progress I have so far:

```
$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:X.Y.61.18  Bcast:X.Y.61.31  Mask:255.255.255.224
vnet0     Link encap:Ethernet  HWaddr 16:ee:9a:43:ba:da  
          inet addr:X.Y.62.118  Bcast:X.Y.62.119  Mask:255.255.255.248

```

I now have a second (virtual) interface.

```
$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.00221598371a    no        eth0
                            vnet0

```

Bridge is setup between the two interfaces.

IP forwarding is enabled in sysctl.conf ...

Yet I am not sure what to do now.

Pinging gives me a "Destination Host Unreachable"

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
X.Y.62.112      *               255.255.255.248 U     0      0        0 vnet0
X.Y.61.0        *               255.255.255.224 U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         *               0.0.0.0         UG    100    0        0 br0

```

Routing seems correct, but I am no expert.

I tried setting my gateway on the virtual machine to the address of vnet0 (X.Y.62.118 ), and to the address I assigned it (X.Y.62.114). Nothing seems to work.

I also tried setting the VPS to the same IP address (.118 ). When I SSH'd into it, I was connected to the host and not the guest.

Any ideas, anyone? I hope there are a few networking gurus here, because I am really at a loss.

IPTables is set to accept all by default. Is there something I have to set to get it to forward?

Is there a setting I have to change on the VPS itself?

Thanks

---

### Post by patryk77 on 2009-07-05
I tried adding another route to my network, with X.Y.62.118 as the gateway, which also didn't work.

EDIT: Maybe what I actually need is a TUN device, not a bridge?

---

### Post by patryk77 on 2009-07-06
Virtual server is running... I can mount its disk image with nbd-client and read its contents, including all configuration files and log files.

According to *Advanced Linux Networking*, all I need to do for routing to work is to enable IP Forwarding and add the route, both of which I have done.

I really hope someone can help, because I have a feeling I'm talking to myself here.

```
brctl showmacs br0 | grep 52
  3	52:54:00:12:84:aa	no		   0.02
```

I added a script to dump ifconfig to a file on first boot for my VPS.

Its MAC address shows up in the bridge and the IP is set properly.

---

### Post by bodhi.zazen on 2009-07-12
Sorry , was away for the last week.

I can not tell from your post exactly what you are trying to do exactly and yes networking with KVM can be difficult.

Typically when you bridge your network card you add a tap (tunctl).

Typically you make a bridge (give your bridge your public ip adress) , then add your eth0 to the bridge.

Then with the guests you add a tap to the bridge. You then assign an ip address to the guests.

Take care, if you do not have physical access, you typically loose access as you bring down eth0 , bring up a bridge, and then add eth0 back in.

Also, how are you using KVM ? Do you have a wewb interface ? If so, what ? If not, are you using KVM directly or what ? 

See if this helps at all :

[http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/](http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/)

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

---

### Post by patryk77 on 2009-07-13
> **bodhi.zazen said:**
> Sorry , was away for the last week.


No problem. Hope you had a great time, and thanks for answering :)

I am trying to setup my VPSs in such a way that they are accessible to the outside world, so I can run services on them (Postfix, Apache, MySQL, FTP, etc.) 

Also, I have to bridge two subnets, as the datacenter provided me an IP of X.Y.61.18, with a gateway and the IP range X.Y.62.112-118, for the other network, for which I have to set the gateway myself.

> **bodhi.zazen said:**
> 
Typically when you bridge your network card you add a tap (tunctl).


Yeah, I read all your stickies, and your blog. The best link I found so far was **[The BRIDGE section from the qemu wiki](http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/bridge)**

I am using vm-builder to create the guests with the correct IP addresses.

I am unsure of the settings for the gateway. Should I use the Primary address? The one which is assigned to br0?

> **bodhi.zazen said:**
> Also, how are you using KVM ? Do you have a wewb interface ? If so, what ? If not, are you using KVM directly or what ? 

I am using libvirt (virsh).

I can access the servers by VNC, but not directly. Can't ping, or SSH or anything.

> **bodhi.zazen said:**
> 
[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)


Both links taught me quite a bit, but I haven't managed to solve the problem yet.

Finally, here is all my config (or at least the relevant parts):

This is the kvm-ifup script. I added the tunctl line to it.
```
patryk@RU-Ca:/etc/kvm$ cat kvm-ifup
#!/bin/sh

# NOTE: For this script to operate properly, it is expected that
#       you have a br0

BRIDGE=br0

/usr/bin/sudo /usr/sbin/tunctl -u `whoami` -t $1

/sbin/ifconfig $1 0.0.0.0 up
/usr/sbin/brctl addif $BRIDGE $1

```


```
patryk@RU-Ca:/etc/kvm$ ifconfig 
br0       Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:X.Y.61.18  Bcast:X.Y.61.31  Mask:255.255.255.224
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17823 (17.8 KB)  TX bytes:12230 (12.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21265 (21.2 KB)  TX bytes:12716 (12.7 KB)
          Interrupt:252 Base address:0xa000 


# I used to have a tap0 which was not an actual tap device... I just set it to X.Y.62.118 and tried to use it as the default gateway.


```

```
$ brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.00221598371a	no		eth0
virbr0		8000.000000000000	yes		

```

Then once I start a virtual machine:

```
patryk@RU-Ca:~$ virsh start pato
Connecting to uri: qemu:///system
Domain pato started

patryk@RU-Ca:~$ brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.00221598371a	no		eth0
							vnet0
virbr0		8000.000000000000	yes		

```

```
patryk@RU-Ca:~$ ifconfig 
vnet0     Link encap:Ethernet  HWaddr 22:97:ed:ae:27:0d  
          inet6 addr: fe80::2097:edff:feae:270d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1980 (1.9 KB)  TX bytes:14447 (14.4 KB)

```

```
$ brctl showmacs br0
port no	mac addr		is local?	ageing timer
  1	00:22:15:98:37:1a	yes		   0.00
  2	22:97:ed:ae:27:0d	yes		   0.00
  2	52:54:00:aa:ec:c1	no		   1.97

```

52:54:00:aa:ec:c1 is the MAC address of the eth0 on the virtual machine.

```
$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
X.Y.61.1                 ether   00:00:0c:07:ac:01   C                     br0

```

```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
X.Y.61.0        0.0.0.0         255.255.255.224 U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         X.Y.61.1        0.0.0.0         UG    100    0        0 br0

```

Lastly, here is the startup command.
```
patryk@RU-Ca:/var/log/libvirt/qemu$ sudo cat pato.log
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin /usr/bin/kvm -S -M pc -m 512 -smp 1 -name pato -uuid 43d9a815-246d-c883-04a9-499b15faae46 -monitor pty -pidfile /var/run/libvirt/qemu//pato.pid -boot c -drive file=/mnt/second/Virtual/pato/disk0.qcow2,if=ide,index=0,boot=on -net nic,macaddr=52:54:00:aa:ec:c1,vlan=0,model=virtio -net tap,fd=16,script=,vlan=0,ifname=vnet0 -serial none -parallel none -usb -vnc X.Y.61.18:0 

```

Thanks again for taking the time to look at this :)
Let me know if you need anything else.

---

### Post by bodhi.zazen on 2009-07-13
You are getting tripped up in a few issues.

1. It appears your bridge is working and eth0 is bridged ? Assign your "primary" ip to this , ie "X.Y.61.18" .

2. You then simply bring up a tap device and add it to the bridge.

3. You then assign an IP address to the guest as you would any other (physical) machine. There is no need to be messing around with iptables or the route on the host at all.

The way you bring up a tap varies, for virsh See :

 [https://help.ubuntu.com/community/KVM/Networking#Configuring%20ubuntu-vm-builder%20to%20create%20bridged%20guests%20by%20default](https://help.ubuntu.com/community/KVM/Networking#Configuring%20ubuntu-vm-builder%20to%20create%20bridged%20guests%20by%20default)

For the guest use the same network defaults (netmask, nameserver, and gateway) as you do for your host. If the second set of ip addresses, X.Y.62.112-118, are not on the same network as the host (which I doubt) you will need to ask of a set of IP addresses on the same network.

So you do not need to change routing or gateways or any such thing on the host, simply edit your guest config (xml) file.

Post the network section of you have problems (should look like)

> [FONT=Verdana]<interface type='bridge'>
      <mac address='00:11:22:33:44:55'/>
      <source bridge='br0'/>[/FONT]
    </interface>[FONT=Verdana]where your mac address is a unique random number for each guest.[/FONT]

---

### Post by patryk77 on 2009-07-13
> **bodhi.zazen said:**
> 1. It appears your bridge is working and eth0 is bridged ? Assign your "primary" ip to this , ie "X.Y.61.18" .

Yeah, I already assigned my primary IP to br0. I can SSH into the Host server.

> **bodhi.zazen said:**
> 2. You then simply bring up a tap device and add it to the bridge.

It seems to me that the /etc/kvm/kvm-ifup script already does that whenever I start a virtual machine.

> **bodhi.zazen said:**
> 3. You then assign an IP address to the guest as you would any other (physical) machine. There is no need to be messing around with iptables or the route on the host at all.

The Ip address is assigned by vm-builder, and I can see it by VNC. But:

> **bodhi.zazen said:**
> For the guest use the same network defaults (netmask, nameserver, and gateway) as you do for your host. If the second set of ip addresses, X.Y.62.112-118, are not on the same network as the host (which I doubt) you will need to ask of a set of IP addresses on the same network.

That's the thing. Primary IP is:
```
inet addr:X.Y.**61**.18  Bcast:X.Y.61.31  Mask:255.255.255.224

```

Secondary set is X.Y.**62**.112-118.

I have to set my own gateway for the secondary IPs.

I enabled IP forwarding and disabled filtering. Shouldn't that be enough to bridge the two subnets?

I wish they had given me a single network, but they don't.

---

### Post by bodhi.zazen on 2009-07-13
> **patryk77 said:**
> Yeah, I already assigned my primary IP to br0. I can SSH into the Host server.

Perfect.

> It seems to me that the /etc/kvm/kvm-ifup script already does that whenever I start a virtual machine.

I did not see a tap in your previous output, and I personally do not use virsh, and you posted a ton of information on routing ...

> The Ip address is assigned by vm-builder, and I can see it by VNC. But:

That's the thing. Primary IP is:
```
inet addr:X.Y.**61**.18  Bcast:X.Y.61.31  Mask:255.255.255.224

```Secondary set is X.Y.**62**.112-118.

I have to set my own gateway for the secondary IPs.

I enabled IP forwarding and disabled filtering. Shouldn't that be enough to bridge the two subnets?

I wish they had given me a single network, but they don't.

Ah, well that is your problem. No you can not bridge 2 physical networks like that. To understand why you need to think about how DNS works. Basically your guests are not on the same physical network as your host, and so you can not bridge the traffic.

You could do it privately, for example, on the host, edit /etc/hosts and put in your guest.

X.Y.62.112 Guest 1
X.Y.62.113 Guest 2

Will work, you can even do your own private DNS (set up a DNS server on the Host), but you can not route public traffic so easily.

You could try using NAT, but you would need to route all (public) traffic to the server (DNS to the server IP, not the guest, and route from server to guests via 1 to 1 or 1 to many NAT). Of course if you use NAT, you do not need a public IP at all, you can use 10.2.10.1-10 for your guests.

For http you could use a proxy server.

But really, for what I think you want, IMO you should contact your hosting service and ask for a set of IP adresses on the same subnet. That will by far, IMO, be your best solution.

---

### Post by patryk77 on 2009-07-13
> **bodhi.zazen said:**
> I did not see a tap in your previous output, and I personally do not use virsh, and you posted a ton of information on routing ...


vnet0 should be a tap, as added by the kvm-ifup script when I start the VM.

How should the tap interface look in ifconfig?


And what is the difference between what I am trying to do and the examples on [http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QemuAndTuntap](http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QemuAndTuntap) ?

Sounds to me that IP forwarding should turn my Host into a Router, and allow access to the virtual machines. Or did I misunderstand something?

---

### Post by bodhi.zazen on 2009-07-13
> **patryk77 said:**
> Sounds to me that IP forwarding should turn my Host into a Router, and allow access to the virtual machines. Or did I misunderstand something?

You are misunderstanding how routing works.

Let us start with a basic set up. Say a private network, at home.

You have a public IP address, assigned by your Internet provider, and a router.

Your router assigns private IP adressess to you LAN.

Let us assume your public IP is 11.22.33.44 and your private LAN is 192.168.0.0. Your router is 192.168.0.1 and you have two desktops 192.168.0.2 and 192.168.0.3 and a server 192.168.1.10.

You router uses NAT to direct traffic from your desktops through your router to and from the internet. You have a single public IP address (11.22.33.44) and 3 private IP (192.168.0.x).

If you want your server to be public, you register a domain, say your_domain.com and you point it to your public IP address, ie 11.22.33.44, and your router then forwards port 80 (http) to your server, 192.168.1.10

With me so far ?

Now say I too am behind a router with a public IP of 55.66.77.88 and a LAN of 10.0.0.0 and a server on 10.0.0.10

Your router can not direct traffic to my server. Why not ? First off, no traffic going to 55.66.77.88 (my public IP) ever goes to your public IP (IE this is the DNS part. I register my_domain.com to point to 55.66.77.88 and not 11.22.33.44). and your router can not route to my private LAN (because we are not on the same sub net, or NAT part).

So now let us assume we wanted to fix that.

First I would point my_domain.com to 11.22.33.44 (DNS part). You would then use NAT to direct my_domain.com back to 55.66.77.88 and I would forward port 80 to 10.0.0.10.

You have no way to directly route my_domain.com directly to 10.0.0.10.

Now if you had 2 nic, one going to 11.22.33.44 and the other to 10.0.0.0/24 and myserver was on you 10.0.0.0/24 net you could. IN that case both my_domain.com and your.domain.com woudl DNS to 11.22.33.44 and you would use NAT to direct my_domain.com to 10.0.0.10.

Returning to your case ...

If you DNS your_domain_1 to X.Y.**62**.112 it never gets to X.Y.**61**.18 (just as my_domain.com never gets to 11.22.33.44 above).

If you DNS your_domain_1 to X.Y.61.18, you can then NAT to X.Y.62.112 ONLY if your server is on the same sub net (similar to how you can not route to 10.0.0.10 above).

Now if you assign DNS your_domain_1 to X.Y.61.18 and give your guests a virtual domain, say 10.10.2.0/24, you can route to your virtual domain, using your server and NAT (router). You can do this as your server is, by virtue of KVM, on the same virtual subnet. In this case you DNS all your domains to the same public IP address (just as if if you were using the router above to use a single IP address, 11.22.33.44, for a private subnet, 192.168.0.0).

In this case you only need one public IP, in your case X.Y.61.18 , the rest are virtual.

Hope that helps you understand. The difference is public IP vs Private IP.

---

### Post by patryk77 on 2009-07-13
Yeah, I understand all that, but my IP addresses are all public.

If I traceroute X.Y.62.113, which is the first usable IP for the X.Y.62.112 network, it goes to X.Y.61.18 and times out from there.

If I ping X.Y.62.113, X.Y.61.18 replies with a Destination Host Unreachable.

X and Y have the same values for both X.Y.61.18 and X.Y.62.112/29, which is my secondary network.

Basically, I have built the server into a rackmount case and delivered it to a datacenter, which provided me with 1 primary IP and a subnet with 6 IP addresses to use for VPSs. All of those are public addresses for which I have to set the route from the primary IP to the virtual servers.

This should be feasible, is it not? I don't want NAT, as I don't want the servers to pretend they are X.Y.61.18. All requests should be sent directly to the eth0 NICs on the VPSs, and X.Y.61.18 should just be used for administration.

As for DNS, it's not really relevant at the moment as I am trying to set everything up using IP addresses for now, and then each VPS will have its own DNS entry on its own domain, or subdomain at least.

---

### Post by bodhi.zazen on 2009-07-13
Well, I am sorry I can not tell from your post.

As I said, I am not very familiar with virsh and you have not posted your config file.

If you can not connect between host and guest then either:

1. Your network connection is not bridged (ie if you are using NAT you can not ping).

Can your guests connect to the internet ?

2. Your routing tables / iptables are bad.

What happens if you manually start your guests, with kvm, and a tap ?

bring up a tap, say tap0

```
kvm -cdrom /media/ubuntu.iso -net nic,vlan=0,macaddr=your_mac_here,model=virtio -net tap,vlan=0,ifname=tap0 -vnc :5
```

You should be able to connect to the guest via vnc on port 5905 (X.Y.61.18:5905)

If that works you can trace back from there ?

---

### Post by bab1 on 2009-07-13
@bodi and @patryk77

I'm not sure that you are both on the same track.

patryk77 -- Are you trying to run *live IP addresses* (valid) on the guests of your own host OS?  I believe that this is what you want to accomplish.  The fact that it is co-lo'ed is a complication but not really pertinent to your problems.

To restate -- Your host OS has x.x.61.18 assigned to the physical NIC (eth0) and you have multiple guest hosts that are going to use the IP range of x.x.62.62.112-129.

This should be correct and doable.

Bodhi says..

> Ah, well that is your problem. No you can not bridge 2 physical networks like that. To understand why you need to think about how DNS works. Basically your guests are not on the same physical network as your host, and so you can not bridge the traffic.


I say you can.  IP addresses are not physical anyway.  DNS has nothing to do with what you are attempting to do.  When you bridge you are associating mac addresses on dissimilar IP address ranges.  Layer 2 is Ethernet and the addressing is the MAC address of the NIC.  In other words your bridge is to create a virtual MAC bus (on the physical NIC) for all the virtual IP/MAC dupals.  In this case the IP is not the important point as we are in using arp to ID the correct virtual MAC to send the packets to their final destination.

I'm not sure that I have fully explained this, as I type I think of more, but I think you get the idea.

On the issue of the proper gateway, I think you touched on the correct idea.  The gateway is what ever the physical NIC uses.  Every packet leaves the physical machine via this NIC and the gateway is the next hop from there.

I want to comment on some points that Bodhi says.  not to be picky, but to help out in understanding.  I have followed his enlightened work and respect his ideas and judgment.  That being said;

Bodhi says... 

> You are misunderstanding how routing works.

Let us start with a basic set up. Say a private network, at home.

You have a public IP address, assigned by your Internet provider, and a router.

Your router assigns private IP adressess to you LAN.

Let us assume your public IP is 11.22.33.44 and your private LAN is 192.168.0.0. Your router is 192.168.0.1 and you have two desktops 192.168.0.2 and 192.168.0.3 and a server 192.168.1.10.

You router uses NAT to direct traffic from your desktops through your router to and from the internet. You have a single public IP address (11.22.33.44) and 3 private IP (192.168.0.x).

If you want your server to be public, you register a domain, say your_domain.com and you point it to your public IP address, ie 11.22.33.44, and your router then forwards port 80 (http) to your server, 192.168.1.10

With me so far ?

This might not be relevant as you are not using NAT> 

Now say I too am behind a router with a public IP of 55.66.77.88 and a LAN of 10.0.0.0 and a server on 10.0.0.10

Your router can not direct traffic to my server. Why not ? First off, no traffic going to 55.66.77.88 (my public IP) ever goes to your public IP 
Sure it does.  DNS is not needed to speak IP to IP.  DNS is needed if you ID a host by a name.  DNS maps it to the IP address and  the packet  is sent.  When the packet gets to the LAN (the router knows host), it uses ARP to resolve  (map) the IP address to the MAC address.> 
(IE this is the DNS part. I register my_domain.com to point to 55.66.77.88 and not 11.22.33.44). and your router can not route to my private LAN (because we are not on the same sub net, or NAT part).

So now let us assume we wanted to fix that.

First I would point my_domain.com to 11.22.33.44 (DNS part). You would then use NAT to direct my_domain.com back to 55.66.77.88 and I would forward port 80 to 10.0.0.10.

You have no way to directly route my_domain.com directly to 10.0.0.10.

Now if you had 2 nic, one going to 11.22.33.44 and the other to 10.0.0.0/24 and myserver was on you 10.0.0.0/24 net you could. IN that case both my_domain.com and your.domain.com woudl DNS to 11.22.33.44 and you would use NAT to direct my_domain.com to 10.0.0.10.

Returning to your case ...

If you DNS your_domain_1 to X.Y.62.112 it never gets to X.Y.61.18 (just as my_domain.com never gets to 11.22.33.44 above).

Just a small point here.  Nothing to do with NAT is relevant, but you should note that when you register your domain, you can point to ANY legitimate IP address.  It does not matter whether it is bound to a physical NIC or a virtual one.  As an aside, I would setup everything using IP only and then setup the DNS.  It will simplify things.> 

If you DNS your_domain_1 to X.Y.61.18, you can then NAT to X.Y.62.112 ONLY if your server is on the same sub net (similar to how you can not route to 10.0.0.10 above).

Do not do this.  Think of the host machine as a 1 port physical switch (the bridge) with virtual ports for the guest OS's virtual NIC's> 

Now if you assign DNS your_domain_1 to X.Y.61.18 and give your guests a virtual domain, say 10.10.2.0/24, you can route to your virtual domain, using your server and NAT (router). You can do this as your server is, by virtue of KVM, on the same virtual subnet. In this case you DNS all your domains to the same public IP address (just as if if you were using the router above to use a single IP address, 11.22.33.44, for a private subnet, 192.168.0.0).

In this case you only need one public IP, in your case X.Y.61.18 , the rest are virtual.

I know I am being redundant but -- You can (and should) use the valid internet IP's.  This helps you administer the various guest VM's.> 

Hope that helps you understand. The difference is public IP vs Private IP. 

Sorry Bodhi.  I feel that patryk77 should create a virtual live network and leave NAT alone (no forwarding and header alteration of packets)

---

### Post by patryk77 on 2009-07-14
> **bab1 said:**
> patryk77 -- Are you trying to run *live IP addresses* (valid) on the guests of your own host OS?  I believe that this is what you want to accomplish.  The fact that it is co-lo'ed is a complication but not really pertinent to your problems.

To restate -- Your host OS has x.x.61.18 assigned to the physical NIC (eth0) and you have multiple guest hosts that are going to use the IP range of x.x.62.62.112-129.

Yeah, that's right.

For now, I only have 2 VPS guests, which can't access the internet.

I have more information to provide, as I have been running tshark (wireshark) on the connection, and have to copy the xml information.

Unfortunately, I have another job to work on now and do not have time to do this before tomorrow afternoon.

But basically, the data center gave me an entire subnet with 6 usable addresses and the primary IP for which they provide the gateway.

All are accessible from the internet, or at least will be once I manage to bridge the two subnets together.

Only thing to note, I am using br0 and not eth0 for the primary IP; br0 bridges eth0 with the tap interfaces.

---

### Post by bab1 on 2009-07-14
> **patryk77 said:**
> Yeah, that's right.

For now, I only have 2 VPS guests, which can't access the internet.

I have more information to provide, as I have been running tshark (wireshark) on the connection, and have to copy the xml information.

Unfortunately, I have another job to work on now and do not have time to do this before tomorrow afternoon.

Take your time.  When you post I will be notified.  :-)> 

But basically, the data center gave me an entire subnet with 6 usable addresses and the primary IP for which they provide the gateway.

All are accessible from the internet, or at least will be once I manage to bridge the two subnets together.

Only thing to note, I am using br0 and not eth0 for the primary IP; br0 bridges eth0 with the tap interfaces.

Just like the URL you cited in your first post!

---

### Post by patryk77 on 2009-07-14
> **bodhi.zazen said:**
> 1. Your network connection is not bridged (ie if you are using NAT you can not ping).

Can your guests connect to the internet ?

Running 'brctl showmacs br0' shows me the MAC address of the Guest OS. This leads me to believe that the bridge is setup properly.

But no, the guests cannot connect to the Internet. Even running (by VNC) 'nc X.Y.61.18 80' gives me 'No route to host'.

I can access Apache from my home connection, however.


> **bodhi.zazen said:**
> 
2. Your routing tables / iptables are bad.


Yeah, that's what I'm thinking must be it.

However, I didn't set any rules in IPTables yet. I am trying to understand how to set the gateway and whether I should have another IP address from the second subnet assigned to the Host machine, and why routing doesn't work with my current setup.

Unfortunately, this is all pretty new to me. I have setup many small home and SMB networks, and have used my home computer as a router with NAT using Webmin, but it's the first time I ever have to configure this kind of routing.

I have been looking for a solution for over 2 weeks, and while I have learned a lot I am still not sure what to do.

---

### Post by bodhi.zazen on 2009-07-14
I think you mentioned this earlier , but ...

Output of :

```
cat /proc/sys/net/ipv4/ip_forward
```

---

### Post by patryk77 on 2009-07-14
> **bodhi.zazen said:**
> I think you mentioned this earlier , but ...

Output of :

```
cat /proc/sys/net/ipv4/ip_forward
```

1

Every time I reboot, the bridge filtering options (/proc/sys/net/bridge/* ) go back to 1, but 'sysctl -p /etc/sysctl.conf' fixes that. I will add it to an init script eventually.


From virsh dumpxml:

```
    <interface type='bridge'>
      <mac address='52:54:00:89:21:54'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
    </interface>

```

vnet0 gets created when I start the VPS.

It has a different MAC address. The MAC address in the xml file gets assigned to the virtual eth0 on the VPS.

I have seen in the tshark output file that the VPS (X.Y.62.114) was sending out ARP requests looking for the host's br0 address, as I set br0 as the default gateway for it (X.Y.61.18 ).

I didn't see a reply, and it didn't create a route on the VPS.

Also, I saw the VPS sent out its MAC address and Wireshark displayed it with a note saying something about a duplicate entry.

Running 'arp -n' on the Host returns (incomplete) for the MAC address of the VPS.

Could it be that ARP filtering stays enabled?

After I run sysctl, if I cat the bridge-nf-* files they all echo 0, but maybe I have to flush the tables some other way.

Thanks to both of you for the help :)

---

### Post by bodhi.zazen on 2009-07-14
I still think you are going about this all wrong, I think your network configuration is wrong in your guest, but I am not sure.

Did you run KVM directly , bring up a tap as I asked ?

If you want my assistance, please run a guest w/ a tap as I asked.

Also, please post the relevant networking information. This ipaddress of x.y.z is not helpful and it makes it difficult to help  you if you do not post network and configuration information.

I run KVM all the time and none of what you are doing is required with a bridge.

Please post your:

1. ip adresses , cleary specify your host and let us work with one guest.
2. netmask
3. nameserver
4. default gateway.

All of those should have been assigned by your hosting service. Your bridge is NOT your default gateway for your guest if you are using a bridge.

Then post the configuration of your network (/etc/networking/interfaces) for host and guest.

On my KVM **guest**, using a bridge :

> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

#cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1


route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
karmic.net      *               255.255.255.255 UH    0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0As you can see, the gateway is NOT the bridge interface on the host.

Also the term NAT has been used very loosely in this conversation. NAT is used if you are using something as a router.

Please post, for host and one guest,:

1. Run KVM with a tap.

2. Post the relvant networking information on host and guest.

1. ip address, netmask, default gw, and nameserver assigned to you by your provider,
2. contents of :
/etc/network/interfaces

and

/etc/resolv.conf

3. output of the "route" command

---

### Post by patryk77 on 2009-07-14
deleted

---

### Post by bodhi.zazen on 2009-07-14
You are getting too fancy, see man qemu.

Just start a simple machine for now.

Your problem is the -S flag ;)

You can drop the -M pc ; -smp 1 (this is default) , -usb (we are not testing usb devices right now),[FONT=monospace] [/FONT]-monitor pty -pidfile /var/run/libvirt/qemu//pato.pid (do not need these right now either), and both -serial none -parallel none (not really doing much with those options either).

And try again.

And to add a gw (which I have never had to do with KVM and bridged networking, well OK with wireless, but that is different).

```
sudo route add default gw 174.142.61.1 eth0
```

---

### Post by patryk77 on 2009-07-15
I get the same problem if I run KVM directly. On top of that, xvnx4viewer constantly disconnects me after complaining of an "unknown message type 255" or type 16. Starting the VPS with libvirt doesn't disconnect me usually.

At this point, I'm pretty sure it's just a routing problem.

As I said in my previous post, I can add the default gateway on the VPS if I first add 174.142.62.114 (eth0) as the default and then add 174.142.61.1

I see (with tshark) the packets going out through br0, and the replies getting to 174.142.61.18 (br0), which sends ICMP Destination unreachable packets back to the server that answered the original query.

I.e. if I run 'nc [www.google.ca](www.google.ca) 80' from the VPS, the Host receives a reply from the DNS servers with destination 174.142.62.114.

However, it doesn't know what to do with it and replies with ICMP dest unreachable to the DNS server.

I added the entries I thought I needed myself, but it didn't resolve it:

```
$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
174.142.61.1             ether   00:00:0c:07:ac:01   C                     br0
174.142.62.114           ether   52:54:00:89:21:54   CM                    tap1

```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
174.142.62.114  0.0.0.0         255.255.255.255 UH    0      0        0 tap1
174.142.61.0    0.0.0.0         255.255.255.224 U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         174.142.61.1    0.0.0.0         UG    100    0        0 br0

```

Maybe I need another device on my secondary subnet.

I tried adding one, but I can't bring it up, unless I bring it up as a tap device, which is not what I want as I don't have an application to hook into it.

```
$ ifconfig 
br0       Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:174.142.61.18  Bcast:174.142.61.31  Mask:255.255.255.224
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:36710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3749580 (3.7 MB)  TX bytes:1392484 (1.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4256466 (4.2 MB)  TX bytes:1409124 (1.4 MB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr f2:ca:ba:22:e8:ed  
          inet addr:174.142.62.118  Bcast:174.142.62.119  Mask:255.255.255.248
          inet6 addr: fe80::f0ca:baff:fe22:e8ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:26475 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap1      Link encap:Ethernet  HWaddr 96:61:d6:3e:3e:87  
          inet6 addr: fe80::9461:d6ff:fe3e:3e87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:7242 (7.2 KB)  TX bytes:2032406 (2.0 MB)

virbr0    Link encap:Ethernet  HWaddr 62:c8:fc:7e:5d:0d  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::60c8:fcff:fe7e:5d0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
```

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address 174.142.61.18
	network 174.142.61.0
	netmask 255.255.255.224
	broadcast 174.142.61.31
	gateway 174.142.61.1
	bridge_ports eth0 tap0
	bridge_stp off
	bridge_maxwait 5
	bridge_fd 0
post-up ifconfig br0 up promisc

auto tap0
iface tap0 inet static
	pre-up sudo tunctl -u patryk -t tap0    #Without this line, the device just doesn't show up in ifconfig.
	address 174.142.62.118
	network 174.142.62.112
	netmask 255.255.255.248

```

If I change tap0 in interfaces to br0:0, networking doesn't work at all.

---

### Post by bodhi.zazen on 2009-07-15
To be honest I think you are not understanding KVM or networking and are making things more complicated then they are.

I have used QEMU/KVM for years and have not had to do any of this with a bridged network option.

You should know that virsh != kvm just as ufw != iptables.

You are also, to some extent, mixing apples and oranges. You are using a bridge, br0, and thus you do not need to manually set a route or use iptables, those options would come into play with a wireless network card on the host and if your were to use NAT, using the host as a router.

Furthermore you are adding unrelated things to the mix. br0:0 and vncserver.

I suggest you simplify what you are doing. I suggest you do this by running kvm directly, and not using virsh for the moment.

In your last post you did not post your kvm command, the most critical piece of information right now. In your last (KVM) command you did not do as I asked, you posted a KVM command from your logs, which was generate by virsh, and will not work because of that.

You keep posting routing information, but not the information needed to help you.

As I have said, you do not need to do anything special with iptables or route and in fact I suggest you reboot to reset your networking and routing to default. You need only a bridge, br0, which you must manually configure (or edit /etc/network/interfaces).

You then add eth0 to the bridge (or put the relevant lines in /etc/network/interfaces).

How about if we start with you posting the content of /etc/network/interfaces on the HOST ?

Next you bring up a tap, with tunctl (manual) or with the network script I posted on my blog. You do NOT assign an ipaddress to the tap.

So now you have br0 , with eth0 and tap0 , no ?

Now start KVM nice and simple, nothing fancy.

kvm -cdrom /media/ubuntu.iso -net nic,vlan=0,macaddr=your_mac_here,model=virtio -net tap,vlan=0,ifname=tap0 -vnc :5
Put in a mac address for "your_mac_here

Now we should be runing a live CD in kvm. 

KVM has a BUILT IN vnc server. The line " -vnc :5" puts it on the HOST

host_ip:5905

so from a remote location VNC in to host_ip:5905

Boot the guest.

In the guest, become root, and assign a static IP using a public IP, netmask, gatweay, and name server as given to you by your service provider. DO NOT use the HOST ip address at all, the host is NOT your gateway or your router.

Re-start networking in the GUEST.

viola, that is all you need to do.

If you have a problem I want to see what you assigned in 

/etc/network/interfaces in BOTH HOST and GUEST.

and output of sudo ifconfig in BOTH HOST and GUEST.

Once you are running with kvm , we can go back to virsh .

---

### Post by patryk77 on 2009-07-15
> **bodhi.zazen said:**
> To be honest I think you are not understanding KVM or networking and are making things more complicated then they are.

Quite probable. This is the first time I have to mess with subnets and VMs, aside from a simple virtualbox setup.

> **bodhi.zazen said:**
> You are using a bridge, br0, and thus you do not need to manually set a route or use iptables

Well, my host still doesn't see the guest, for some reason. It forwards the guest's DNS requests and discards the replies saying the guest is unreachable.

> **bodhi.zazen said:**
> Furthermore you are adding unrelated things to the mix. br0:0 and vncserver.

I tried adding br0:0 on the secondary subnet, as many posts I have seen suggested using two IPs on different subnets.

> **Henri Cook]... we were able to come up with a solution, using a virtual device (br:0) bound to one of the IPs in subnet Y to act as a gateway, effectively bridging the connections between addresses on subnet Y with the main address on subnet X.[/quote]
From [http://blog.henricook.com/?p=86](http://blog.henricook.com/?p=86)


As for VNC, I am using KVM's built-in VNC server only. I access the host by SSH, and will disable VNC altogether once I can get the networking to work for the guests. For now, VNC is the only option to see the guest.


[QUOTE=bodhi.zazen said:**
> I suggest you reboot to reset your networking and routing to default.

Done. Here's my interfaces file as it is now:

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address 174.142.61.18
	network 174.142.61.0
	netmask 255.255.255.224
	broadcast 174.142.61.31
	gateway 174.142.61.1
	bridge_ports eth0 tap0
	bridge_stp off
	bridge_maxwait 5
	bridge_fd 0
post-up ifconfig br0 up promisc

```

```
$ sudo tunctl -u patryk -t tap0
Set 'tap0' persistent and owned by uid 1000
$ sudo ifconfig tap0 0.0.0.0 up
$ ifconfig 
br0       Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:174.142.61.18  Bcast:174.142.61.31  Mask:255.255.255.224
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:134411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192188965 (192.1 MB)  TX bytes:10170239 (10.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:194070721 (194.0 MB)  TX bytes:10171241 (10.1 MB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr c2:ca:7f:42:31:79  
          inet6 addr: fe80::c0ca:7fff:fe42:3179/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 0a:0e:fd:bf:ac:4d  

```

> **bodhi.zazen said:**
> Now start KVM nice and simple, nothing fancy. Now we should be runing a live CD in kvm.

Just have to load an ISO now. I have KVM running my VM with
```
sudo kvm -drive file=/mnt/second/Virtual/pato/disk0.qcow2,if=ide,index=0,boot=on \
-net nic,macaddr=52:54:00:89:21:54,vlan=0,model=virtio -net tap,vlan=0,ifname=tap0 \
-vnc :5

``` in the meantime

---

### Post by bodhi.zazen on 2009-07-15
OK, that will suffice.

Can you VNC into the guest ? Set a static IP on the guest, use the ip address, netmask, gateway, and name server given to you by your provider, and NOT the host IP.

If it does not work, then I assume there is something wrong with your bridge.

---

### Post by patryk77 on 2009-07-15
Here is my guest's interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 174.142.62.114
	netmask 255.255.255.248
	network 174.142.62.112
	broadcast 174.142.62.119
	gateway 174.142.62.114
	dns-nameservers 208.67.222.222
	dns-search elpato

```

I use that as default gateway, as I can't add **174.142.61.1** directly.

If I try manually, without setting **174.142.62.114**, it can't find it and route returns **SIOCADDRT: No such process.**

If **174.142.62.114** is set as the default gateway (even if I add it to route manually), I can add **174.142.61.1**

sudo ifconfig on Host:
```
 sudo ifconfig 
br0       Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:174.142.61.18  Bcast:174.142.61.31  Mask:255.255.255.224
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:553040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:762021124 (762.0 MB)  TX bytes:59857058 (59.8 MB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet6 addr: fe80::222:15ff:fe98:371a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:769750294 (769.7 MB)  TX bytes:59874052 (59.8 MB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2180 (2.1 KB)  TX bytes:2180 (2.1 KB)

tap0      Link encap:Ethernet  HWaddr c2:ca:7f:42:31:79  
          inet6 addr: fe80::c0ca:7fff:fe42:3179/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3329 errors:0 dropped:10107 overruns:6 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1440 (1.4 KB)  TX bytes:258365 (258.3 KB)

virbr0    Link encap:Ethernet  HWaddr 0a:0e:fd:bf:ac:4d  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::80e:fdff:febf:ac4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```


And on guest:
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:98:37:1a  
          inet addr:174.142.62.114  Bcast:174.142.62.119  Mask:255.255.255.248
          inet6 addr: unimportant Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3675 (3.6 KB)  TX bytes:1476 (1.4 KB)
          Interrupt:252 Base address:0xa000 


```

Loopback is there too, but I didn't include it as I can't copy from VNC.

Edit: I noticed that when I try to ping or netcat the Host from the Guest, they both get an ARP entry added, with the br0 IP's added to the guest, and virtual eth0's address added to the host's ARP table.

The connection still doesn't go through though.

```
arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
174.142.62.114           ether   52:54:00:89:21:54   C                     br0

```

Shouldn't iface be tap0?

---

### Post by bodhi.zazen on 2009-07-15
The settings in your guest do not look right to me.

On the host you have :[FONT=monospace]

> [/FONT]iface br0 inet static[FONT=monospace]
[/FONT]address 174.142.61.18[FONT=monospace]
[/FONT] network 174.142.61.0[FONT=monospace]
[/FONT] netmask 255.255.255.224[FONT=monospace]
[/FONT] broadcast 174.142.61.31[FONT=monospace]
[/FONT] gateway 174.142.61.1

What were the network, netmask, broadcast, nameserver, and gateway values given to you by your provider (for your guest IP) ?

---

### Post by patryk77 on 2009-07-15
Primary IP address: 174.142.61.18
Subnet mask: 255.255.255.224
Gateway: 174.142.61.1
Secondary IP: 174.142.62.112/29
Usable Secondary IPs: 174.142.62.113-118/29
Subnet Mask: 255.255.255.248

Primary DNS server (if needed): 209.172.41.202
Secondary DNS server (if needed): 209.172.41.200

That's all the info they provided me with.


```
$ ipcalc -b 174.142.62.112/29
Address:   174.142.62.112       
Netmask:   255.255.255.248 = 29 
Wildcard:  0.0.0.7              
=>
Network:   174.142.62.112/29    
HostMin:   174.142.62.113       
HostMax:   174.142.62.118       
Broadcast: 174.142.62.119       
Hosts/Net: 6                     Class B

```

But I see the requests coming from the Guest to the Host using wireshark on br0.

It seems to be working fine from the Guest to the Host, but the Host can't answer.

---

### Post by bodhi.zazen on 2009-07-15
Is the guest using network manager ? If so I suggest you disable it.

Then set a static ip in the guest using the values given by yoru provider :

GUEST /etc/network/interfaces :

```
[FONT=monospace]
[/FONT]auto lo[FONT=monospace]
[/FONT]iface lo inet loopback

auto eth0[FONT=monospace]
[/FONT]iface eth0 inet static[FONT=monospace]
[/FONT] address 174.142.62.114
netmask 255.255.255.248[FONT=monospace]
[/FONT] network 174.142.62.112[FONT=monospace]
[/FONT] broadcast 255.255.255.0[FONT=monospace]
[/FONT] gateway 174.142.62.112
```

And in /etc/resolv.conf put

```
nameserver  209.172.41.202
nameserver 209.172.41.200 #This second entry is probably not needed
```[FONT=monospace]
[/FONT] 
You may need to change the broadcast ([FONT=monospace] [/FONT]174.142.62.119 ) and/or the gateway (try 174.142.61.1)

---

### Post by patryk77 on 2009-07-15
No network manager... The Guest is running JeOS, built using vm-builder. It has no X, just the basics.

This is what I had:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 174.142.62.114
	netmask 255.255.255.248
	network 174.142.62.112
	broadcast 174.142.62.119
	gateway 174.142.62.114
	dns-nameservers 208.67.222.222
	dns-search elpato
```

I changed the gateway to **174.142.62.112** and broadcast to **255.255.255.0**.

Still failing.

But I really think that the problem is with the host, not the guest.

I can ping the router (174.142.61.1) from the guest, and br0 receives replies. It just doesn't forward them.

---

### Post by bodhi.zazen on 2009-07-15
> **patryk77 said:**
>  I can ping the router (174.142.61.1) from the guest, and br0 receives replies. It just doesn't forward them.

Let us try a few things then.

From the guest, what happens when you :

```
sudo apt-get update
```

And on the guest, output of:

```
sudo iptables -L -v
```

---

### Post by patryk77 on 2009-07-15
> **bodhi.zazen said:**
> 
```
sudo apt-get update
```

Could not resolve archive.ubuntu.com 
Could not resolve security.ubuntu.com 

> **bodhi.zazen said:**
> 
And on the guest, output of:

```
sudo iptables -L -v
```

On the guest, I don't even have iptables.

On the host:

```
Chain INPUT (policy ACCEPT 554K packets, 762M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  virbr0 any     anywhere             anywhere            udp dpt:domain 
    0     0 ACCEPT     tcp  --  virbr0 any     anywhere             anywhere            tcp dpt:domain 
    0     0 ACCEPT     udp  --  virbr0 any     anywhere             anywhere            udp dpt:bootps 
    0     0 ACCEPT     tcp  --  virbr0 any     anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT 65637 packets, 5513K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    virbr0  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  virbr0 any     192.168.122.0/24     anywhere            
    0     0 ACCEPT     all  --  virbr0 virbr0  anywhere             anywhere            
    0     0 REJECT     all  --  any    virbr0  anywhere             anywhere            reject-with icmp-port-unreachable 
    0     0 REJECT     all  --  virbr0 any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 542K packets, 69M bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by bodhi.zazen on 2009-07-16
I think your network settings are wrong in the guest.

Here is a step-by-step walk though. [COLOR=darkred]NOTE: All commands are run as root (sudo -i)[/COLOR]

HOST

/etc/network/interfaces

> auto br0
iface br0 inet static
address 192.168.0.10
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
bridge_ports eth0
bridge_stp off
bridge_maxwait 5Now manually bring up a tap 

```
tunctl
ip link set tap0 up
brctl addif br0 tap0
```Show bridge w/ tap

```
brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.001e686159a9    no        eth0
                                                         tap0
```Start KVM

```
kvm -m 512 -cdrom /mnt/ZEN/karmic-desktop-amd64.iso -usb -usbdevice tablet -net nic,vlan=0,macaddr=DE:AD:BE:EF:12,model=virtio -net tap,vlan=0,ifname=tap0,script=no
```The guest is assigned an ip automatically by my  router (dhcp). I can set a static IP if I wish. Install openssh-server , and ssh into guest.

Nothing to add to route or iptables.

config :

Host 


```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *             255.255.255.0   U     0      0        0 virbr0
link-local      *                  255.255.0.0      U     1000   0        0 br0
default         192.168.0.1     0.0.0.0         UG    100    0        0 br0

tap0      Link encap:Ethernet  HWaddr 22:77:f3:98:a8:ee  
          inet6 addr: fe80::2077:f3ff:fe98:a8ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:28899 (28.8 KB)  TX bytes:339760 (339.7 KB)

```Also as you can see the tap does not have an IP address on the host, the guest IP address is set on the guest.

Guest :

```
eth0      Link encap:Ethernet  HWaddr de:ad:be:ef:12:34  
          inet addr:192.168.0.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dcad:beff:feef:1234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329494 (329.4 KB)  TX bytes:20475 (20.4 KB)


route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```I do not know what your problem is. I suggest you eliminate as many variables as possible, download an iso and fire it up manually following the setps I outlaid.

I am still guessing your problem is in your configuration (ie netmask, nameserver, gateway) you are using for your guest.

Really, no manual configuration is required on the host (as you can see).

---

### Post by patryk77 on 2009-07-16
> **bodhi.zazen said:**
>  

```
address 192.168.0.10
netmask 255.255.255.0
broadcast 192.168.0.255
```

```
eth0      Link encap:Ethernet  HWaddr de:ad:be:ef:12:34  
          inet addr:192.168.0.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dcad:beff:feef:1234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329494 (329.4 KB)  TX bytes:20475 (20.4 KB)



```

I am still guessing your problem is in your configuration (ie netmask, nameserver, gateway) you are using for your guest.

My guess is the problem stems from having two different subnets and no path from the gateway to the secondary subnet.

The gateway (174.142.61.1) has a direct link to the Host (174.142.61.18 ) on the IP layer:

```
Address:   174.142.61.18        10101110.10001110.00111101.000 10010
Netmask:   255.255.255.224 = 27 11111111.11111111.11111111.111 00000
Wildcard:  0.0.0.31             00000000.00000000.00000000.000 11111
=>
Network:   174.142.61.0/27      10101110.10001110.00111101.000 00000
HostMin:   174.142.61.1         10101110.10001110.00111101.000 00001
HostMax:   174.142.61.30        10101110.10001110.00111101.000 11110
Broadcast: 174.142.61.31        10101110.10001110.00111101.000 11111
Hosts/Net: 30                    Class B

```

Which is why I thought I should have a second interface on the secondary subnet.

So my host can do the routing for the secondary subnet.

I guess everything is OK on the Ethernet layer, but my host gets packets destined to the secondary subnet on the IPv4 layer and gets confused as it has no route to the subnet. It would need to have an interface on the same subnet, same as in your setup your router is on the same subnet as the guests:

```
Address:   192.168.0.1          11000000.10101000.00000000. 00000001
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.0.0/24       11000000.10101000.00000000. 00000000
HostMin:   192.168.0.1          11000000.10101000.00000000. 00000001
HostMax:   192.168.0.254        11000000.10101000.00000000. 11111110
Broadcast: 192.168.0.255        11000000.10101000.00000000. 11111111
Hosts/Net: 254                   Class C, Private Internet

```

Makes sense?

---

### Post by bodhi.zazen on 2009-07-16
> **patryk77 said:**
> So my host can do the routing for the secondary subnet.

I guess everything is OK on the Ethernet layer, but my host gets packets destined to the secondary subnet on the IPv4 layer and gets confused as it has no route to the subnet. It would need to have an interface on the same subnet, same as in your setup your router is on the same subnet as the guests:

```
Address:   192.168.0.1          11000000.10101000.00000000. 00000001
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.0.0/24       11000000.10101000.00000000. 00000000
HostMin:   192.168.0.1          11000000.10101000.00000000. 00000001
HostMax:   192.168.0.254        11000000.10101000.00000000. 11111110
Broadcast: 192.168.0.255        11000000.10101000.00000000. 11111111
Hosts/Net: 254                   Class C, Private Internet

```Makes sense?

That is what I said in my second post, you need the host to be on the same subnet as the guests.

You did not like the work around(s) and I think it is best if you go back to your provider and ask for a set of public IP on the same network.

The work arounds  involve using your host a a router. To do this you would need to direct your public domain (DNS) to your host and use NAT (either one-to-one or many-to-one). NAT is basically what a router does and is standard. Or you can run yor own private DNS server.

See : [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Masquerading_.28Many_to_One_NAT.29](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Masquerading_.28Many_to_One_NAT.29)

and the next section (one-to-one).

---

### Post by patryk77 on 2009-07-16
OMG OMG OMG!

I got it :D

Without NAT.

I can ping [www.google.ca](www.google.ca) from guest, ping guest from host and from home, apt-get update / install... Everything!

I'm going to play around with it, clean it up a bit, update my scripts, make sure everything works A-OK and post the solution soon :D

Thanks so much for the help and time you spent on it :)

---

### Post by bodhi.zazen on 2009-07-16
Congrats, no problem. I am interested to see your solution. Was it a configuration error or something else ?

---

### Post by patryk77 on 2009-07-16
I'm ashamed to admit it's so simple I should have thought about it LONG ago lol.

Bringing the alias up once the server is running works properly.

```
sudo ifconfig br0:0 X.Y.62.118 netmask 255.255.255.248 broadcast X.Y.62.119
```

And voila!

I'm gonna edit this soon with my final config files and what not.

---

### Post by patryk77 on 2009-07-17
So, I have finally got everything working as it should. Here is a brief HOWTO:

Create a bridge using your primary address and assign an alias to one of your secondary addresses. This is my resulting /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address 174.142.61.18
	network 174.142.61.0
	netmask 255.255.255.224
	broadcast 174.142.61.31
	gateway 174.142.61.1
	bridge_ports eth0
	bridge_stp off
	bridge_maxwait 5
	post-up ifconfig br0 up promisc
	post-up ifconfig br0:0 174.142.62.118 netmask 255.255.255.248 broadcast 174.142.62.119

```

If you notice, this is a strange way of editing the interfaces file. If I defined the alias **br0:0** as a separate entry, networking would simply not work.

Setup libvirt / KVM and build your server using vmbuilder.

See the Server Guide for instructions:
[https://help.ubuntu.com/9.04/serverguide/C/virtualization.html](https://help.ubuntu.com/9.04/serverguide/C/virtualization.html)

In my case, I passed the following networking flags to vmbuilder:

```
--ip=174.142.62.113 --gw=174.142.62.113 --mask=255.255.255.248
```

I set the default gateway to the virtual machine's eth0 IP address, as it wouldn't be able to see the gateway provided by the datacenter otherwise.

Then, edit your virtual machine using **virsh edit MachineName**

Look for the line
```
 <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
``` and replace **127.0.0.1** with your primary IP.

Use xvncviewer to connect to the virtual machine:
```
xvncviewer 174.142.61.18
```

Then I added the following line to the VM's /etc/network/interfaces file:

```
post-up route add default gw 174.142.61.1
```

And voila! All my troubles have gone away.

Install SSHd, edit the XML file back to 127.0.0.1 (why have an unencrypted VNC session when SSH is faster and safer?) and carry on with your work.

It may not be a pretty solution, but it's the only one that worked for me and this problem drove me up the wall for a long time.

---

### Post by bodhi.zazen on 2009-07-17
Thank you for posting the solution, networking is always so darned complex, lol. I am sorry  I was not more helpful.

---

### Post by patryk77 on 2009-07-17
No problem :)

I'm wondering whether I should file that as a bug, or if it's really a feature.

Definitely seems odd that something which can be done relatively easily breaks networking if you phrase it differently in the config file.

And I just hope it can save someone the trouble I went through lol.

---

### Post by bodhi.zazen on 2009-07-17
You can try filing a bug, but IMO the problem is your guest is not on the same subnet as the host.

So you need to manually configure routing, which can be done several ways. I am familiar with aliasing br0:0 (or other interfaces) but have not seen them used in this exact way before.

Now that you posted your solution I would have done it different , but your method works as well.

---

