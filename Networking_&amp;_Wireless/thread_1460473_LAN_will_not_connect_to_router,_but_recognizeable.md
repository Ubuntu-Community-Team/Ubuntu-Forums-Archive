---
title: "LAN will not connect to router, but recognizeable"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by mr clark25 on 2010-04-22
this is real strange. my LAN just suddenly stopped working. we had a power outage, and it just stopped. it will still recognize the network, but it wont connect. i was experimenting with setting up a web server (trying to set it up on the standard distro). i know its not the network card (on board) because i can put in my pci card and it still wont connect. it will connect when in the live environment. i thought that maybe it had updated, so i tried to boot from a different (older) kernel. that still didn't help.

i stopped apache. i was experimenting with portforwarding at the time (i had everything else working on my server), but i could not get it to work. after this happened, i restored the original settings on my router. i had applied the settings only a day before the power outage.

everything still works on another computer on the network (also running linux). (all computers run 9.10)

its almost like my router won't assign me an ip address. 


if anymore information is needed, i would be more than happy to get the info for you.

---

### Post by mr clark25 on 2010-04-23
just tried pppoefconf. it said to check the ethernet cable. i swapped it (the cable) with the cable on the working computer on the network. that still didn't seem to help.


sorry if i am hard to understand in my original post.

---

### Post by Iowan on 2010-04-23
> **mr clark25 said:**
> i know its not the network card (on board) because i can put in my pci card and it still wont connect. it will connect when in the live environment. I was gonna say that just because the pci won't connect doesn't mean there's no problem with the onboard - but the live environment connection suggests the card DOES work.> it will still recognize the network, but it wont connect.:confused: What are results of **ifconfig -a** - does the card get (valid) IP address? Is this a server (CLI) install - or is it controlled by Network Manager? What is in */etc/network/interfaces*?

---

### Post by mr clark25 on 2010-04-23
here is ifconfig -a and */etc/network/interfaces.*

```

james@james-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:b0:d0:18:95:24  
          inet6 addr: fe80::2b0:d0ff:fe18:9524/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5606 errors:0 dropped:0 overruns:1 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1105160 (1.1 MB)  TX bytes:1554 (1.5 KB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4217140 (4.2 MB)  TX bytes:4217140 (4.2 MB)

james@james-desktop:~$  cat /etc/network/interfaces
auto lo
iface lo inet loopback

```this is a regular install of 9.10, with apache installed on it. it is controlled by network manager.

after look at ifconfig, i noticed that it has transmitted something. it must have been me trying to connect to it countless times.

under the network icon in the top (tool)bar, i can see "eth0", but it wont connect to it when i click on it.

---

### Post by Iowan on 2010-04-23
OK, so Ubuntu knows it has an eth0...
I doubt it'll work, but try **sudo dhclient eth0**

---

### Post by mr clark25 on 2010-04-23
it returned with something that i believe is good:
```

james@james-desktop:~$ sudo dhclient eth0
[sudo] password for james: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:b0:d0:18:95:24
Sending on   LPF/eth0/00:b0:d0:18:95:24
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 38985 seconds.

```

one problem: its not giving me the ip address that i used to have (before it broke)

as you can see, my router is 192.168.1.1
and its trying to give me 192.168.1.3

it used to give me 192.168.1.4

i remember looking at a network manager file, but i can't remember it's name or where it is located. the contents of it were this:
```

#generated be network manager
192.168.1.4

```

i think i only looked at this file (never changed it). could this be whats messing with me?

---

### Post by Iowan on 2010-04-23
That's the nature of DHCP. The server will provide an address - not necessarily the same one (unless you configure the DHCP server to issue a static lease based on MAC address). But it does seem like progress. :)

---

### Post by mr clark25 on 2010-04-23
thanks for the quick reply.

messing with resolv.conf didnt help.

ill see if i can give myself a static ip on my router.

any other ideas?

---

### Post by mr clark25 on 2010-04-23
that still didn't do anything, but ill leave the static ip in place because ill need it later...

---

### Post by Iowan on 2010-04-23
> **mr clark25 said:**
> that still didn't do anything, but ill leave the static ip in place because ill need it later...:confused: What didn't it do?  If you've rebooted, the address may go away (we still need to fix that part). */etc/resolv.conf* should have the [s]name[/s] IP address of your nameserver - on my system, it's the modem, but could be either ISP's or one like OpenDNS or Google's DNS.

---

### Post by gallaau on 2010-04-23
Have you looked at your arp table and do you see the IP and mac of default gateway are tied together. I forget the command arp -a i think. You should see 192.168.1.1 and then the mac like ##-##-##-##-##-##
If you dont see this then your machine may not even be sending any frames.

Get a sniffer and take a look at what is going on.
Load wire shark on the other machine and check what it is doing.

---

### Post by mr clark25 on 2010-04-24
arp -a just starts a new line in the terminal (no output) i take that that isn't good...

trying wireshark now... (i may need some help...)

---

### Post by mr clark25 on 2010-04-24
wireshark has got to be the coolest thing i have seen yet!

but, i think i found the problem: my router isn't responding to DHCP request :(

as you can see in the screenshot, it receives a request, but confirmation is never sent.

would a video be helpful?

---

### Post by gallaau on 2010-04-24
I thought you gave yourself a static. 
1.2 looks like he is up and running OK, so you should give yourself a static addresses to rule out dhcp. It will give you a known starting place.

If you select a packet in the top window "layer 3 or IP"
the lower window will display the mac layer info "layer 2"
If you have questions about this you can google OSI model.

This is the mac address of the machine you are having problems with correct? 00:b0:d0:18:95:24 

after you give yourself a static addresses, reboot just to be sure you have a known starting place again. 
do an ifconfig -a and make sure you have the IP and that you know your mac address. I think it is ifconfig -a
I don't have my system running right now and I have used every kind of unix under the "Sun OS" Ha, I made a funny. So anyway I get confused about what command goes with which one.

start the sniffer
go to a teminal window and ping 192.168.1.1 and watch the sniffer.
you should see either a arp broadcast trying to find the 1.1
or if he already has the arp entry he will send a echo request
then the router will send an echo reply.

If you don't see anything then you know it is your system
when you loaded the web server did it start some kind of firewall, you might search for something like that or remove the web server it. I think that was what yo said in the start of this post anyway.

Post a status when you are done.

---

### Post by mr clark25 on 2010-04-24
i gave myself a static ip in my router's configuration. is there something i need to do inside the OS?

yes, that mac address is correct.

i rebooted, but my router isn't giving me an IP. ifconfig -a gives me the same output as before (except for the Rx and Tx part).

trying to ping my router only yields an error:
```

connect: network unreachable

```

---

### Post by Iowan on 2010-04-24
Doubt [this]("http://ubuntuforums.org/showthread.php?t=1156441") will help, but it solved a DHCP problem on my Jaunty laptop.

---

### Post by gallaau on 2010-04-24
OK, so now we see the problem. 
You have assigned a static IP
You gave it a mask of 255.255.255.0
you have put in the default gateway of 192.168.1.1
You will need to add the DNS server but it is not necessary for a ping.
Now when you ping it says network unreachable.
The network is directly connected, so this points to a software problem inside your machine.
Obviously your network card is connected because your sniffer picked up other traffic on the network and it is not a hardware problem. 
Did you say you loaded or where in the process of loading a web server. Maybe remove that and get back to where you were before.

A good way to fix a problem with the IP stack in a machine is to reinstall the NIC.

---

### Post by mr clark25 on 2010-04-24
i read through that post you made (IOWAN) and it didn't help :(

ill try uninstalling apache (:()

the sniffer (wireshark) is on the computer that works. (sounded like you thought it was on the broken one)

---

### Post by mr clark25 on 2010-04-25
removing apache didn't help :(

maybe my router doesnt like my mac address? how would i change it? i know its possible with aircrack (or a similar program).

---

### Post by mr clark25 on 2010-04-26
maybe i could re-install network manager? does it come in a .deb that i can get some where?

any ideas on how to change my mac address?

i would really like to be able to use the internet on the computer...

---

### Post by Iowan on 2010-04-26
Has something changed along the way or am I just confused?
Does the machine get an address via **sudo dhclient eth0**? (it did back at post #6)  Do you know what the address range is for the DHCP server? Have you tried setting a manual address and DNS address via Network Manager?

---

### Post by mr clark25 on 2010-04-27
it does get access through that command, but i cant connect on the user interface.

i dont know the range for the server. it is still set at the default option.

i have done nothing with network manager yet. could i have instructions on how to set up a DNS and an address?

---

### Post by mr clark25 on 2010-04-28
i found another computer to use as my experimental server.

now, i need help with portforwarding. i will start another thread under "server platforms"


sorry for taking so long to get back in the previous post.

---

