---
title: "cannont connect to internet over network"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by rogdawg on 2009-06-29
I have seen many similar posts but, I have not seen a solution yet. I hope this is not redundant.

I cannot connect to the internet from a new Ubuntu 9.04 installation over our windows network. The Ubuntu box is on our local network. If I go to Places >> Network, I can see the network, and see other computers on the network, and I can access the files on those computers. But, I cannot browse to any internet address in the browser. 

I cannot connect to either an ip address or domain name ([www.google.com](www.google.com), for instance) using telnet from the command line.

If I open System >> Network Connections. It shows the two eithernet cards that are installed on the machine (Auto eth1, Auto eth0), and they both have "never" listed next to them. If I select the active eithernet card (eth0) and click "Edit", then go to the IPv4 Settings tab, neither the "Automatic (DHCP)" option nor the "Automatic (DHCP) addresses only" option, with the DNS Servers and Search Domains information will work. 

I am stumped, and so is our IT manager. He has installed Ubuntu 9.04 on a laptop in his office and is experiencing the same issues. 

Any suggestions as to how we can debug this?

Thanks, in advance, for any help you can provide.

---

### Post by computer13137 on 2009-06-29
Hmm, but your Windows machines are working fine?  I would have pointed the finger immediately at your DHCP server, but not if some systems are working, I guess.

Perhaps you could run an ifconfig /all and paste the results here for me?

Also, are you able to ping your router's internal IP address?  From your question, it seems you can't ping Internet IPs like 4.2.2.1, but maybe you can ping your router.  Is this correct?

I'm guessing that the default gateway is not set correctly.  That being said, try assigning a static IP address just to try it and see if that fixes the problem.

To try this, edit your /etc/network/interfaces file... and include something like this.

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

I'm assuming from your message that you're in a corporate environment, so you may be using the 10.1.x.x range on the 255.255.0.0 subnet, I don't know from where I'm sitting.  Make sure you know what IP range you're using before you assign a static. :P

-Kirk

---

### Post by jonobr on 2009-06-29
hello


type ```
nslookup google.com
```

with the returned ip address

enter

```
w3m <ipaddress>
```

See if you get a text response from google.

---

### Post by rogdawg on 2009-06-29
Thank you for your quick responses.

jonobr: I was able to use nslookup to get the ip address for google. But when I attempted to use "w3m 74.125.45.100", I received, after a long pause, the message "Can't load 74.125.45.100".

computer13137: Here are the results of ifconfig for the eth0 card:
eth0      Link encap:Ethernet  HWaddr 00:15:f2:a5:cd:03  
          inet addr:192.168.2.68  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fea5:cd03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:260719 (260.7 KB)  TX bytes:102012 (102.0 KB)
          Interrupt:21 Base address:0xda00 

Our IT manager said he can ping the DNS server and he can ping the gateway without any problem.

We will continue to work this but, any other debugging suggestions would really be appreciated.

I will try editing the interfaces file, as you suggest, and I will post the results.

Thanks very much.

---

### Post by Polaris96 on 2009-06-29
Do you have more than one NIC (multiple network card and/or network and wireless)?  

Code:

sudo route -n 

copy the output and post it here - we can probably work through this without too much headache

---

### Post by jonobr on 2009-06-29
HEllo


Im thinking there is some routing issue on your network.,


Whats your default gateway?

Can you ping it?

You have an address of 192.168.2.68.
Can you ping 192.168.2.1?

could you post the result of

```
netstat -rn
```
The result should show you what default gateway you are using

It should say something like

> 0.0.0.0         192.168.1.1      0.0.0.0         UG        0 0          0 eth0


---

### Post by rogdawg on 2009-06-29
ok, Here is what we have found...

Our IT Manager was talking through the problem with our internet service provider, and here is what they tried. The ISP cleared the ARP Cache (?) on the switch and we were able to see the internet from both ubuntu machines. But, when we rebooted them, they were both unable to see the internet again. So, this seems like a problem with the way Ubuntu is communicating with the DHCP server. 

Polaris96: Here are the results of route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


Thanks again for your suggestions.

---

### Post by jonobr on 2009-06-29
Actually theres an interesting problem here,
if clearing out the arp cache of the switch fixed the problem initially then it sounds as if you have a problem with your switch unless your mac address is changing on your ubuntu box,


The Arp cache contains a cache of hardware addresses for ports and ip addresses,, so for example your hw adddress from your ifconfig is 
00:15:f2:a5:cd:03 

this will be associated with a port on your switch.

This means when a request comes through for your machine, it doesn't need to shout out to everyone to look for you, it will route to the right port.
Most devices keep an arp cache and if you do arp -a you will see the arp cache on your ubuntu machine.

The only two things I can think of are,

you are changing the mac address on your machine which is causing a difference to your arp cache or, most likely,

you are chaning the port you are connected to requiring the arp cache to be flushed.
Some devices have problems when you change the physical port you are connected to , the switch doesnt update its cache soon enough and packets are sent in the wrong direction.

---

### Post by Polaris96 on 2009-06-29
your routing table looks pretty normal.  Everything Jonoby says makes sense and I wouldn't know how to correct a changing MAC adr.

One thing I would try is setting up a static IP adr on the ubuntu machines.

I had originally thought you were misrouting, but that looks ok.

---

### Post by jonobr on 2009-06-29
I would be interest to know, when you got it working, did you change to a different switch port or move your ethernet connection around?

---

### Post by rogdawg on 2009-06-29
I will let you guys know as soon as we get it worked out. Our IT manager is working with our ISP. They are trying different approaches, and monitoring the switch to see what information is being passed to it. It seems as if the addresses, once assigned, are not being released for some reason.

I'll post our conclusion in a little while (hopefully).

Thanks again for your efforts. I am always incredibly impressed by the help I get on the Ubuntu forums.

---

### Post by rogdawg on 2009-06-29
OK. 

We are stumped. Our IT manager assigned a static IP address to the ubuntu laptop he was testing, and he is getting the same behavior. (He connected "directly into the Cisco firewall" from the laptop, and I was connected over the LAN from the desktop I have set up...two different machines connecting in two different ways, but getting the same behavior). 

If we clear the ARP cache on the switch, we are able to connect, until we reboot the ubuntu machines. Then, we are no longer able to connect. All our configuration stuff looks correct on the ubuntu machines, as far as our IT manager can tell (he is experienced, and knows what he is doing). 

We are at a loss as to what the next step will be. Our IT manager has to leave town at the end of the day so, he will not be able to help me out tomorrow. 

Very bizarre. Very frustrating.

---

### Post by rogdawg on 2009-06-29
Does anybody have a suggestion?

Anybody?

---

### Post by jonobr on 2009-06-29
Your IT Manager should run a wireshark/tcpdump trace to see whats going on.

What I would look for specifically is if there is something different occuring after the reboot on the packet level.

---

### Post by rogdawg on 2009-06-29
Thanks very much.

I will pass that along and see what we can find. 

Thanks again.

---

### Post by rogdawg on 2009-11-17
I just wanted to update this thread. 

We never figured out what the problem was when using 9.04. I installed 9.10 today and the problem was immediately fixed.

We have Internet connectivity on that machine now.

I wish I could give more helpful information than that. But, at least it is working now.

On to other things...

---

