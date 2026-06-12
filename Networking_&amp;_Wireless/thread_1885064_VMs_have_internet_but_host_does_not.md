---
title: "VMs have internet but host does not"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by BreezySeas on 2011-11-22
Hi all,

Running Ubuntu 10.10 desktop, suddenly I can no longer ping or browse websites beyond my LAN gateway, however, any machines running in VirtualBox can access other networks & internet just fine (with virtual adapter set to 'bridged'). I can set up an httpd server in VirtualBox and access it from the internet. To make it stranger, DNS seems to be fine on the host, ie nslookup google.com returns the expected IPs, but pinging or browsing to google.com or any remote IP fails.

No other computer on the network has this problem.

It has a static IP configured (correctly) in /etc/network/interfaces, but I have tried pulling an address from the DHCP server, as well as patching over to a different subnet with a different gateway router, and in both cases LAN access is fine but I can't get to any remote address from the host machine. 

Restarting the computer does not fix the problem.

Possible related things- The host machine having this problem has some Samba shares, and last night I was playing with tunneling Samba over SSH. I had no issues doing this but it is possible I left an SSH tunnel and/or Samba share mounted to a remote host and some time overnight these connections were ungracefully interrupted. I have tried stopping the Samba service and, again, restarting the computer, to no avail.

Thanks for any help!

---

### Post by praseodym on 2011-11-22
If you configure manually in the "interfaces" and you are using the NetworkManager as well you need to change "false" to "true" in the /etc/NetworkManager/nm-system-settings.conf

---

### Post by BreezySeas on 2011-11-22
praseodym - I don't use the network manager. I tried the change you suggested but it seems that because I only ever use the interfaces file, this does not work for me.

Thanks

---

### Post by jonobr on 2011-11-22
> I can no longer ping or browse websites beyond my LAN gateway

Hello


quote above implies that pinging and accessing internal devices works ok?

Can you connect directly via IP and not FQDN?

Also, no harm posting /etc/network/interfaces /etc/resolv.conf
and maybe dmesg | grep eth

---

### Post by BreezySeas on 2011-11-22
Yup, all internal access is fine, I can't access any internet locations by IP or FQDN.

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.2.2
	netmask	255.255.255.240
	gateway 192.168.2.1

# auto eth1
# iface eth1 inet dchp

/etc/resolv.conf

nameserver 192.168.2.1

dmesg | grep eth (hm....)

[    1.867952] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc900117b4000, 6c:f0:49:ec:8f:e2, XID 083000c0 IRQ 43
[    1.957833] radeon 0000:01:05.0: Error during ACPI methods call
[    1.970524] r8169 0000:04:07.0: eth1: RTL8110s at 0xffffc900117d8000, 00:22:3f:f1:fa:ed, XID 04000000 IRQ 21
[    9.521858] r8169 0000:03:00.0: eth0: link up
[    9.521988] r8169 0000:03:00.0: eth0: link up
[   17.468149] r8169 0000:04:07.0: eth1: link up
[   28.460062] eth1: no IPv6 routers present
[  129.827819] r8169 0000:03:00.0: eth0: link up
[  209.946260] r8169 0000:03:00.0: eth0: link up
[ 1409.594744] r8169 0000:03:00.0: eth0: link down
[ 1411.736524] r8169 0000:03:00.0: eth0: link up
[ 1539.662928] r8169 0000:03:00.0: eth0: link up
[ 1549.950077] eth0: no IPv6 routers present
[ 1599.367068] r8169 0000:03:00.0: eth0: link down
[ 1603.418589] r8169 0000:03:00.0: eth0: link up
[ 1621.639591] r8169 0000:03:00.0: eth0: link up
[ 1773.950056] device eth0 entered promiscuous mode
[ 2006.902129] device eth0 left promiscuous mode
[ 2017.033634] r8169 0000:03:00.0: eth0: link up
[ 2017.035780] device eth0 entered promiscuous mode
[ 2689.887015] device eth0 left promiscuous mode
[ 2700.022729] r8169 0000:03:00.0: eth0: link up
[ 2700.024936] device eth0 entered promiscuous mode
[ 6912.913270] device eth0 left promiscuous mode
[ 6962.641928] r8169 0000:03:00.0: eth0: link up
[ 6962.644563] device eth0 entered promiscuous mode
[ 8467.655195] device eth0 left promiscuous mode
[ 8477.803743] r8169 0000:03:00.0: eth0: link up
[ 8477.805962] device eth0 entered promiscuous mode


I don't like that eth0 is going into promiscuous mode... do we have something there?

---

### Post by jonobr on 2011-11-22
Nope I dont believe thats anything unusual.

One question I do have though is that I notice your using VLSM with a /28
Does your router understand VLSM and is it able to route with that?
Do your other working machines have the same netmask?

---

### Post by BreezySeas on 2011-11-22
Yes, the router knows it's a /28 network and other physical machines, as well as virtual machines on the troubled box, see the internet just fine.

I tried giving a VM the 192.168.2.2 address to see if that specific address was a problem (ie duplicate, etc) and the VM, with the 2.2 IP, gets to the internet no problem, so that's one more thing ruled out.

---

### Post by jonobr on 2011-11-22
I think your going to have to run a packet trace using tcpdump or wireshark to see whats going on at a packet level from that machine.
If you want to grab one from that machine, do some browsing and post here I could help you with that if you want.

Given the traffic is going locally it sounds dns-sh related , but again a packet trace is probably the next best step

---

### Post by BreezySeas on 2011-11-22
Thanks for your time.

I tried to analyze the capture as best I could but failed to draw any conclusions. There are lots of multicasts like this coming from the gateway router... 

15:30:55.165843 IP dlink.gw.2048 > 239.255.255.250.1900: UDP, length 328

maybe that's normal...

I did my best to explain the network and posted the dump file here:
pastebin.com/tj4LKN8q

Thanks so much to anyone who takes the time to look at this. I'm spending plenty of time on it myself!

Let me know if I should run the dump with different parameters.

---

### Post by jonobr on 2011-11-22
Hey There


Had a look at your description and results (which were top class BTW)
I notice bigblueserver - 
is this bigbluebutton? The collabrative, opensource go to meeting type stuff?

If so , I have done some work with that in the past (helping a non profit company when I was on R&R between companies)

I believe BBB would use multicast as its the nature of what it does, having multiclients viewing a presentation etc.

I notice a lot of IPv6 stuff also, which I am not sure how or if that plays into the whole thing.

The one thing that does jump out is after the first google lookup,
you can see the right lookup information returned, but it never uses it to go to google.
There is a bit of spanning tree and then cisco discovery going on, and then an ARP request from your gateway.

The response has a > (oui Unknown) , in around that.

That confuses me a bit. I havent seen that before

OUI is part of the build up of the mac address for devices.
The mac is made up of a company specific information so hardware can be identified by company , that's in the first 3 bytes of the Ethernet frame

Next is the unique id within that company.

Here is the thing. without the OUI, a Ethernet frame cannot be created.

Ill need to do a bit of reading on this, but did you change around the hardware address by chance?

Is there anything in dmesg if you
dmesg |grep oui
or
dmesg | grep OUI

---

### Post by jonobr on 2011-11-22
Additional,

Just searched for your OUI based on the information in the trace

	6C:F0:49 	
GIGA-BYTE TECHNOLOGY CO.,LTD.
No.215,Nan-Ping Road,
Pin-Jen Taoyuan 324
TAIWAN, REPUBLIC OF CHINA

I would recommend checking arp caches against ifconfig to ensure the mac hardware information all jives...
Just a wag at the moment

---

### Post by jonobr on 2011-11-22
Sorry about this, but another additional,

are you using the iputils-arping package on your 10.10 installation?

---

### Post by JKyleOKC on 2011-11-22
> **BreezySeas said:**
> I don't like that eth0 is going into promiscuous mode... do we have something there?Nope; it has to do that to support your bridged VMs. I worried about it for a long time, until I finally noticed that the times corresponded to the times when I was running one of my VMs (the normal state of my VMs is "saved" and I run them only when needed, then save their state for next time).

EDIT: A correlation just occurred to me: your bridged VMs get out okay, but the host system cannot. When the VMs are running, ETH0 is in promiscuous mode; when they are not, it's not. Could this be a clue to the problem? If my brainstorm actually applies, then the host machine ought to be able to get out when at least one VM is running to put ETH0 in promiscuous mode, but you've probably already tried this and it failed...

---

### Post by BreezySeas on 2011-11-23
Thank you gentlemen, I have solved my problem and I have no one to blame but myself. I see now that I neglected to mention a few things that I thought were completely irrelevant and had even forgotten about. The full story, if you are interested:

This machine is dual-homed; I never brought this up because the 2nd NIC (eth1) is not used for anything and as you can see is even commented out of the /etc/network/interfaces file. I had been occasionally bridging it to a VM in order to log into and play with an old Sonicwall without having to change the machine's working IP, and the rest of the time it sat idle, but remained plugged into the Sonicwall's LAN port. 

The past day, I configured a management IP on the LAN's Cisco switch so I could ditch the console cable, and after setting up the IP, I was at a loss for why I could neither ping nor SSH to it, and eventually discovered that I'd given it the same IP as the Sonicwall's WAN port. Being lazy and tired, I simply unplugged the WAN port, confirmed that I could indeed SSH to the Cisco switch, and called it a day. 

Moments ago I discovered that the internet suddenly worked on the troubled machine when and only when the Sonicwall's WAN patch that I removed the other night was plugged in, regardless of the IP assigned to it (on the same 192.168.2.0/28 net as the problem machine).

Long story short, ever since some unknown point in the past, my internet traffic has been departing via eth1, going through the (completely open) Sonicwall, and out of the building. Of course the VMs continued to work when the WAN was unplugged, because they were "hard wired" to eth0.

I am not sure how exactly the machine was using eth1, as it had no address configured, but regardless, everything is back up.

Marking as solved, thanks again :D

---

