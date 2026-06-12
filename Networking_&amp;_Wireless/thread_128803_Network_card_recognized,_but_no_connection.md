---
title: "Network card recognized, but no connection"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by barrel on 2006-02-12
Hi,

Today I installed Breezy. First issue I had was the nvidia driver that made x hang. Replaced by 'vesa' in the xorg.conf and it worked. :-k 

Second problem (and I don't think that this is installation specific ;-): Network comes up, but no ip addresses are assigned from the dhcp server and static ip address assignation doesn't work either. During installation, this was already a problem but I figured that I could fix that later. So far no luck.

What is happening? eth0 is active, ifconfig eth0 shows a bunch of information including an ipv6 address, but no ipv4 address 

dmesg shows the following

NET: regisrered protocol family 2
IP: routing cache hash table of 16384 buckets, 128Kbytes
TCP established has table entries: 262144 (order: 9, 2097152 bytes)
TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8 
NET: Registered protocol family 20

... a bity further on ... (no network connection from that specific PC, don't feel like typing the whole dmesg output ;) 

NET: Registered protocol family 1
NET: Registered protocol family 10

... and at the end ....

skge addr 0xf7efc000 irq 5 chip Yukon rev 1
skge eth0: addr 00:0c:6e.2f.3d.cd

skge eth0: enabling interface
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present



Most of the information seems alright to me... Perhaps this might be a problem related to ip6? I tried to disable ipv6 but doing the following:
edit the file '/etc/modprobe.d/aliases and on line 10 change
alias net-pf-10 ipv6 to alias net-pf-10 off
No luck...
Before the change, the system timed-out (during boot) on configuring the network interface, afterwards it didn't. In the first case, I get an ipv6 address assigned (no ipv4), in the second case, I simply do not get an ip address at all.

Concerning the skge; I also read that I should use sk98lin, but I cannot find that  driver... :( 
Ok, reenable IPv6 again. So I have an ip6 address....
When I try to ping my default gateway (192.168.1.1), I get the following message:
connect: Network is unreachable

Assigning a static ip address? 
ifconfig eth0 192.168.1.11
Address shows up when asking the ifconfig. When I ping my default gateway, the message shows that the destination host is unreachable.

I know that the network works (cables plugged etc) because I downloaded Breezy from an old SuSE installation that was on the same PC (and I remember that I had the same issues with a Hoary install, a while ago)

lshw shows the following:
*-network
description: Ethernet interface
product: 3c940 10/100/1000Base-T [Marvell]
vendor: 3Com Corporation
physical id: 5
businfo: pci@02:05.0
logical name: eth0
version: 12
serial: 00:0c:6e:2f:3d:cb
capacity: 1GB/s
width: 32 bits
clock: 66Mhz
capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-ft 1000bt-ft autonegociation
configuration: autonegociation=on broadcast=yes driver=skge driverversion=0.7 firmware=N/A link=no multicast=yes port=twisted part
resources: iomemory:_addressrange_ ioport:_addresstange_

(no use in typing over the addressranges I guess...)

Any help appreciated
Barry

---

### Post by bscbrit on 2006-02-12
Please show me the contents of /etc/network/interfaces and tell me what is the IP address of your gateway.  Also what is your make and model of modem and/or router?

---

### Post by barrel on 2006-02-12
[QUOTE=bscbrit]Please show me the contents of /etc/network/interfaces and tell me what is the IP address of your gateway.  Also what is your make and model of modem and/or router?[/QUOTE]

Default gateway is 192.168.1.1 (this is a small router with DHCP server built in).
Note that when installing Hoary, I had another router (also DHCP server). Also my SuSE installation used this router for automatic ipaddress assignment. This has most likely nothing to do with the router.
First router was a linksys WTR54G, now I have a USRobotics.

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.1.1 212.100.160.51 212.100.160.52

Since nameservers run over ip, I guess the last line is of no importance, since ip doesn't work yet.... :-?

---

### Post by bscbrit on 2006-02-12
I haven't a clue what a 'skge' is - I will have to google for that :) 

First of all I cannot see where you have told the computer which gateway to use to access the internet.  This should be the IP of your router.  Add the following:

gateway 192.168.1.1

Secondly, when you manually change settings are you restarting you network i.e. 'sudo /etc/init.d/networking restart'?

Finally, from the command line is the output of 'ifconfig' showing that your NIC is up and running and, if it is, can you now ping your gateway (192.168.1.1) ?

There appear to be a few discrepancies between your initial interfaces file and the current one but I assume that you have been trying changes in between the posting of each?

---

### Post by barrel on 2006-02-12
Wow, fast reply! :D 

> **bscbrit]I haven't a clue what a 'skge' is - I will have to google for that :) 
[/QUOTE]

Apparently skge is the driver that loads the onboard ethernet controller. his used to be sk98lin, but apparenly has changed...

> 
First of all I cannot see where you have told the computer which gateway to use to access the internet.  This should be the IP of your router.  Add the following:

gateway 192.168.1.1


Was done via installation script and the provided network admin tools, I never tried this manually. However, added this after your hint said:**
> 
Secondly, when you manually change settings are you restarting you network i.e. 'sudo /etc/init.d/networking restart'?


Actually, I used; invoke-rc.d networking restart
but I guess this does the same...

> 
Finally, from the command line is the output of 'ifconfig' showing that your NIC is up and running and, if it is, can you now ping your gateway (192.168.1.1) ?

There appear to be a few discrepancies between your initial interfaces file and the current one but I assume that you have been trying changes in between the posting of each?

Yep. I have been trying quite a bit, however, always returning to the initial settings is an attempt failed, so discrecpenacies should normally not be there.
What are the ones you are referring to?

 Barry

---

### Post by bscbrit on 2006-02-13
OK, back to basics.  

Please confirm the address range that your router is issuing.  Confirm that dhcp is switched on.

Secondly, confirm that you NIC can be seen by the computer (System -> Administration -> Networking) and that the GUI shows that it is activated.  

When you have successfully completed those two items, go to the command line at show the output of 'ifconfig' and 'arp' please.

Let me know what the outputs are.

---

### Post by barrel on 2006-02-13
[QUOTE=bscbrit]OK, back to basics.  

Please confirm the address range that your router is issuing.  Confirm that dhcp is switched on.
[/QUOTE]

Address-range from 192.168.1.2 to 192.168.1.254.
Other computers connected to this DHCP server succesfully receive ip-addresses. The previous distro (SuSE 9.3) also succesfully received an ip address

> 
Secondly, confirm that you NIC can be seen by the computer (System -> Administration -> Networking) and that the GUI shows that it is activated.  


Yep, recognized. Interface shown as active

> 
When you have successfully completed those two items, go to the command line at show the output of 'ifconfig' and 'arp' please.

Let me know what the outputs are.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:50:BA:2E:C1:70
          inet6 addr: fe80::250:baff:fe2e:c170/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
etc... (again, no use in typing everything...): ip address v4 is not there, ipv6 is.

arp: nothing. 

This seems to be an issue related to my NIC in combination with specific drivers in Ubuntu that does not appear in SuSE.

Think I'll install SuSE 10.0 instead

Barry

---

### Post by bscbrit on 2006-02-13
OK it has confirmed that your NIC has not been provided with a gateway address from your dhcp server.

Please check your dhcp server configuration to ensure that the correct gateway address is present.

EDIT - I tend to agree that its a NIC problem or, more correctly, I don't know what else can be causing this fault :D

EDIT2 - if all your other NICs are happy with the dhcp server, it is probably not a fault with your server.

---

### Post by barrel on 2006-02-13
[QUOTE=bscbrit]OK it has confirmed that your NIC has not been provided with a gateway address from your dhcp server.

Please check your dhcp server configuration to ensure that the correct gateway address is present.

EDIT - I tend to agree that its a NIC problem or, more correctly, I don't know what else can be causing this fault :D

EDIT2 - if all your other NICs are happy with the dhcp server, it is probably not a fault with your server.[/QUOTE]

Well... more specifically; this is a NIC problem in relation to Ubuntu, the same configuration poses no problem for SuSE (which I am reinstalling as I am writing this... :???: 

Too bad.... but SuSE is a good distro as well... ;)

---

### Post by barrel on 2006-02-13
And SuSE is already happily downloading the latest updates.... Too bad, I really would have liked to use Ubuntu....

---

### Post by mips on 2006-02-13
Enjoy SuSe as it seems to require zero effort to get working in your setup.

---

### Post by bscbrit on 2006-02-14
Problem solved :-D

---

### Post by Johnking on 2006-02-14
Here is my scenario. I have a box(PC) running Ubuntu 5.10 with two NICs on it. I would like to use one NIC eth0 to connect to the internet via DSL using PPPoE while eth1 connects to the LAN with static IP. I would like therefore to set up this box as a router/gateway for rest of the PCs on the Network to go to the internet through this box (Ubuntu). I would like to setup Firewall on it, my preference will be Firestarter, unless someone can convince me otherwise.

My problem: I was able to install the Firestarter but it fails to recognize eth0 as the main source to the internet, even though the PPoE is running OK I get page can not be displayed when I tried to browse the web.

I would like also to be able to set up two subnets, that is 192.168.22.0/24 for the Linux PCs and 192.168.152.0./24 Windows PCs but use one gateway. As you can see I am cornered and I desperately need your expertise.
Can you please help me?
Thanks

---

### Post by bscbrit on 2006-02-14
johnking - Are you trying to start a new thread?  I'm not quite sure what your question has to do with solving the current thread?  

If you are trying to start a new thread, look near the top of each forum for the Tread_Starter. :D

---

### Post by mips on 2006-02-14
Should be a new thread but I already typed this out...

/etc/network/interfaces

```
### Config for Eth1
iface eth1 inet static
# You can assign IP details to the physical interface. I would actually recommend you assign it an address in the loopback range (ie 127.0.0.100/32)
# Most people configure the physical as the first interface but I personally prefer not to do this if I'm working with sub-interfaces/IP alliases.


# Linux
iface eth1:1 inet static
address 192.168.22.1  #or 192.168.22.2 if it is not the gateway
netmask 255.255.255.0
network 192.168.22.0
broadcast 192.168.22.255
gateway xxx.xxx.xxx.xxx # I dunno

#Windows
iface eth1:2 inet static
address 192.168.152.1  #or 192.168.152.2 if it is not the gateway
netmask 255.255.255.0
network 192.168.152.0
broadcast 192.168.22.255
gateway xxx.xxx.xxx.xxx # I dunno
```

Firestarter is pretty straight forward. Select internet enabled interface followed by interface sharing connection. I dont know how well it handles multiple interfaces if at all.

Either way, with the config above and this guide [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972) you should be able to do everything you want plus more. Might want to look into the webmin util for a gui frontend once setup.

---

### Post by barrel on 2006-02-15
Just for information, this seems to be a kernel related problem. SuSE 9.3 has no problems, but I just tried to install Mandriva 2006 and the same problems occur. I am now installing SuSE 10.... Just keep my fingers crossed but I will post the results anyway (in case someone else stumbles upon this thread) :-?

---

### Post by barrel on 2006-02-15
How to delete a reply?

---

### Post by barrel on 2006-02-15
Hooray for SUSE 10.0!

---

### Post by bscbrit on 2006-02-15
Stick with SuSE then - if it works, accept it :) 

Good Luck

---

### Post by dickohead on 2006-05-03
The ipv6 issue is related (seems to be) with the nforce chipset of integrated gigabit NICS, on two motherboards both with gigabit NICS using nforce chipsets, I hav been unable to get a network connection. Only windows can get a connection, no other versions of Linux can get a connection.

So far the only solution is to install a PCI/PCIE network card that you know has worked.

Very dissapointing for me, as I do not have room in my case for a PCI network card.... So if I come across a solution, I'll let you know.

---

### Post by mips on 2006-05-03
[QUOTE=dickohead]The ipv6 issue is related (seems to be) with the nforce chipset of integrated gigabit NICS, on two motherboards both with gigabit NICS using nforce chipsets, I hav been unable to get a network connection. Only windows can get a connection, no other versions of Linux can get a connection.

So far the only solution is to install a PCI/PCIE network card that you know has worked.

Very dissapointing for me, as I do not have room in my case for a PCI network card.... So if I come across a solution, I'll let you know.[/QUOTE]

I dont think the IPv6 issue is realted to the nForce chipset. I have a nForce4 MB and have not had problem thus far with IPv6.

Just for the record I have a Gigabyte GA-K8NXP-9 MB that has performed flawlessly so far.

You come to your own conclusions.

---

### Post by dickohead on 2006-05-03
Just because yours is working doesn't mean that there's not an issue. :)

Quite a few people using the same chipsets I've used have had issues with obtaining an ipv6 address but no ipv4, there is an ifconfig command to tunnel to an ipv4 address but this is only useful for static IP's, which when assigned haven't worked thus far anyway.

My solution was to get a PCI network card and use that, but due to the small size of my new case, this is not a good option!

I've tested my GA-K8N51GMF-9's network card (nForce 430 chipset) with the following:

Breezy 32bit, Dapper F3 & F6 32bit, Dapper 64bit, Suse 10 32bit
Dapper and Suse picked it up but couldn't use it, Breezy never saw it.

Am about to try the Dapper Beta2 and will post the results!

---

### Post by mips on 2006-05-04
[QUOTE=dickohead]Just because yours is working doesn't mean that there's not an issue. :)
[/QUOTE]

You have a valid point there ;)

---

