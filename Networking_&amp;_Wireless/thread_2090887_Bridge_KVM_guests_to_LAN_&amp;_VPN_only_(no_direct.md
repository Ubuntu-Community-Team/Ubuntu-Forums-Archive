---
title: "Bridge KVM guests to LAN &amp; VPN only (no direct internet)"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by scotjam1981 on 2012-12-03
Hi 

I'm *relatively* new to Ubuntu. I used Linux some time ago, but haven't used it much for a while, and was really using it more for basic tasks + a bit of coding rather than complex set-ups. I'm posting this here (having toyed with the idea of posting it in the Absolute Beginners section because this is only my second post or so, and in the Virtualization section because it involves KVM network bridges), but decided that ultimately it was a pretty specific question that belongs in the networking forum. I hope that's ok.

I have in the last few months been getting back into linux (specifically Ubuntu Desktop 12.04 x64), and have set up KVM virtual machines to run multiple servers on my LAN. After (significant) tweaking, it now works great.

However, I would like to be able to set certain VM guest machines to only be able to access external networks securely via a VPN connection. I also want this to "fail safe" rather than "fail dangerous", i.e. if a setting gets inadvertently wiped / program crashes, the relevant VM guest machines are denied internet access rather than being given unsecured external network access over something other than the VPN. Ideally, I would like to be able to manage this from the command line, but if necessary a GUI solution would be a good start.

What I have tried reading up on so far:
[LIST]
[*]Using firestarter to set up Internet Connection Sharing to share the VPN connection to the other VMs: I have tried this, and this works to share the VPN connection (tun0) with the bridge connection (br0) so that the KVM guests can access the VPN connection. However, I have found that if firestarter is disconnected, in certain circumstances the VM guest machines can then access the internet via the bridge connection just as they could before firestarter was installed (i.e. this "fails dangerous" rather than "fails safe") (also this is via a gui, which is not ideal)

[*]Using shorewall (e.g. [http://www.shorewall.net/OPENVPN.html](http://www.shorewall.net/OPENVPN.html)) - at first glance shorewall looks potentially useful, however upon further reading it looks like this is only useful to prevent access / filter packets, i.e. it doesn't act as a router but rather as just a pure firewall.

[*]Using iptables - I am aware that this could probably be done using iptables, however I'm struggling to understand based on the iptables documentation how I might set up a situation like this. I understand the basics of setting up iptables rules / chains (and which tables to put them in) now, but I don't understand how one might construct something more complex like what I have described above. If iptables is the solution, again I would like it to fail safe (i.e. the VPN connection is run on the host and it shares the connection with the guest VM, and the connection is *enabled* through iptables forwarding) rather than bridging the host and guest network completely and then using iptables to block insecure access to the external network from the guest VM, (i.e. I want a setup where if the iptables rules get flushed, access is lost rather than gained).
[/LIST]

The simplest solution would seem to be setting up a bridge connected only to tun0 (my VPN tunnel interface) which is then used by each of the guest VMs - if tun0 goes down, they lose internet access completely (as per my requirements). However, when I try to set that up by changing the bridge settings to the following in the /etc/network/interfaces file on the host machine:
```
 auto br0
 iface br0 inet dhcp
         bridge_ports tun0
         bridge_stp off
         bridge_fd 0
         bridge_maxwait 0
```
then restart networking, I get the following:
```
hypervisor@hypervisor:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 4922
can't add tun0 to bridge br0: Invalid argument
Failed to bring up br0.  
                                          [ OK ]

```

My LAN subnet is 192.168.0.xxx mask: 255.255.255.0 gw: 192.168.0.1

My VPN subnet (which is not managed by me, I just connect to it) is 10.8.0.xxx

Currently (while connected to the VPN), ifconfig output on the host looks like:
```

br0       Link encap:Ethernet  HWaddr 2a:0d:xx:xx:xx:xx
          inet6 addr: fe80::280d:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:22250 (22.2 KB)

br0:avahi Link encap:Ethernet  HWaddr 2a:0d:xx:xx:xx:xx
          inet addr:169.254.aaa.aaa  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 14:da:xx:xx:xx:xx
          inet addr:192.168.0.bbb  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6469598 (6.4 MB)  TX bytes:721434 (721.4 KB)
          Interrupt:49 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5527 (5.5 KB)  TX bytes:5527 (5.5 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.ccc  P-t-P:10.8.0.ddd  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:30435 (30.4 KB)  TX bytes:14485 (14.4 KB)

tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.eee  P-t-P:10.8.0.fff  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1162486 errors:0 dropped:1158611 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:96421 (96.4 KB)  TX bytes:1740467809 (1.7 GB)

virbr0    Link encap:Ethernet  HWaddr c6:d3:xx:xx:xx:xx
          inet addr:192.168.122.ggg  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

My /etc/network/interfaces file on the host machine looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

My guest VM xml config file contains the following:
```

<interface type='bridge'>
    <source bridge='br0'/>
    <mac address='14:da:xx:xx:xx:xx'/>
    <model type='virtio'/>   
    <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
</interface>

```

I would be grateful for any solution (based on iptables or otherwise), because I have been tearing my hair out over these iptables rules...

Many thanks

sj1981

---

### Post by scotjam1981 on 2012-12-05
I am continuing to bang my head against a wall on this, and have come up with a few more pointers / insights, mostly based on the OpenVPN website (previously I was mostly looking at KVM / virtualization sites):

[LIST]
[*]It looks like in order to bridge to a VPN, I would need to connect using a tap interface rather than a tun interface (Source: [http://openvpn.net/index.php/open-source/faq/75-general/311-what-are-the-fundamental-differences-between-bridging-and-routing-in-terms-of-configuration.html](http://openvpn.net/index.php/open-source/faq/75-general/311-what-are-the-fundamental-differences-between-bridging-and-routing-in-terms-of-configuration.html) ). You can't bridge a tunnel (which is a virtual cable) only a tap (which is a virtual interface) to another interface.
[/LIST]
[LIST]
[*]My VPN provider only seems to provide a tun interface (I tried changing my client .conf file to say "dev tap" and it still created a tun when I connected), so I guess bridging is off of the table (also bridging is apparently not normally recommended - [http://openvpn.net/index.php/open-source/faq/75-general/309-what-is-the-difference-between-bridging-and-routing.html](http://openvpn.net/index.php/open-source/faq/75-general/309-what-is-the-difference-between-bridging-and-routing.html) ).
[/LIST]
[LIST]
[*]Therefore it would seem that I should revert to iptables. I found a guide that described a similar setup to mine (again on the openvpn site - this is really helpful!!: [http://community.openvpn.net/openvpn/wiki/BridgingAndRouting](http://community.openvpn.net/openvpn/wiki/BridgingAndRouting) )
[/LIST]

I think the routing that I need to set up is as follows:

```
# (1) Allow initiation of connections from the virtual machines
#     (guest machines) to the VPN connection
iptables -I FORWARD -i br0 -o tun0 -s 192.168.0.0/24 -d 10.8.0.0/24 -m conntrack --ctstate NEW -j ACCEPT

# (2) Allow bi-directional and related traffic once 
#     connection is established
iptables -I FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

```

There may also be an additional rule required for the other direction, but I'm assuming the RELATED, ESTABLISHED rule takes care of that.

This is my intended network:
**[http://pastebin.com/fMDT90qt](http://pastebin.com/fMDT90qt)**
(I can only put it on pastebin because ubuntu forums recognises my 'ascii art' as images and won't let me post it here directly)

 
NOTE: [Example guest VM] is shown outside of the perimeter of [OpenVPN client, KVM host and ICS server], but in fact is inside that perimeter in hardware terms, as it is a guest virtual machine running on the [OpenVPN client, KVM host and ICS server] box

For this to work, I also need to break the direct link between br0 and eth0 (and let the packet forwarding of iptables work its magic instead). 

However, if I comment out the line:
bridge_ports eth0
from the definition of br0 in /etc/network/interfaces on the [OpenVPN client and ICS server] machine, and restart networking using init.d (and remove the bridge interface from the guest VM XML file using virsh edit [guestVM]), then I lose network connectivity completely on both machines, i.e. ping 8.8.8.8 and ping 192.168.0.1 both fail.

Other observations:
[LIST]
[*]virbr0 seems to be automatically set up by qemu init scripts
[/LIST]
[LIST]
[*]Not sure what br0:avahi and br1 are for, or where they come from.
[/LIST]

Key questions: 
[I]Why does my connectivity fail on both machines when I disconnect the bridge and rely on forwarding? Even if the VM's virtual network interface loses all connectivity, shouldn't the host system still have access?
If the guest OS will lose all connectivity when I break the bridge connection to host OS eth0, is there a way to forward the tun0 to the guest OS without using bridging?
[/I]

I would really appreciate some guidance on either of these points!

Many thanks

sj1981

---

