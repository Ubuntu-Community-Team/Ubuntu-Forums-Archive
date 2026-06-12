---
title: "sharing internet connection (I know: I've read the other threads!)"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by hatstand on 2006-01-03
Here's my problem. I run Ubuntu and the wife runs XP. We have one wired
cable internet connection. We want to share it. I naively thought that buying a switch would simply give me some and her some. Well, whichever computer boots forst gets the connection and the other has none (although XP states "limited connectivity but doesn't connect to anything").

 I first ran Firestarter. Great but you cannot have eth0 as both "internet connected Device" and "local network connected device". It instead detects something called sit0 that it promptly says
is not ready. I can't find any onformation on how to make it ready.<br> <br>
I installed samba: no change.

So I searched these forums and found the guide. I tried this handy thread. It assumes that you can have a static IP address. I apparently cannot: as soon as I set a static IP address (192.168.0.1) and the (255. thing follows automatically), I lose the internet, even after reboot. If I change it back to DCHP it works immediately.

SO the question is: how do I get the XP box to access the internet when I am accessing it on ubuntu?


My connection goes like this:

cable modem --- switch --- ubuntu + XP

---

### Post by darth_vector on 2006-01-03
here are some things you could try:

1) log onto the cable modem and make sure that you have a large enough DHCP range for two computers - seems dumb, but some ISP's have been known to set things up strangly

2) look at the IP address of the router and set a static IP in the same subnet. if the routers IP is 192.168.1.x then you using an IP of 192.168.0.x wont work

3) boot both computers and make sure that they can ping each other and the router. if they cant, then one of them isnt getting a DHCP lease at all.

---

### Post by dickohead on 2006-01-03
Did you connect the switch to the cable modem correctly?

The computers each need to be conected to the switch using "Straight-through" cables, and the switch needs to connect the modem via an uplink port with a straight-thorugh cable, or via one of the ports with a cross-over cable.

Good luck.

---

### Post by hatstand on 2006-01-03
OK: thanks for the prompt replies. I have now followed the instrcutions on the troubleshooting sticky and found the subnet mask and IP  and gateway addresses. I have entered similar but not  igual stuff into the TC/ICP properties in the XP box.

The netwrok fisrt came up that there was an IP adress conflict and sure enough I had enetered the same address. At least that means the computers are ecognising each other, I hope!

Then i changed the adresses and XP said "LAN is now connected". Imagine my joy. However, no internet access still.

All the cables are straight through. I am just about to try a new static adress.

---

### Post by darth_vector on 2006-01-03
you will need to put in more than an IP. in the "gateway" section you will have to put the cable modems IP. the windows box should be online after that.

---

### Post by hatstand on 2006-01-03
Here is what the route -n gives me:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.135.0.0      0.0.0.0         255.255.224.0   U     0      0        0 eth0
0.0.0.0         10.135.0.1      0.0.0.0         UG    0      0        0 eth0

I have set my static address on my ubuntu box as 10.135.0.2
I have set the IP in TCP/IP on XP as 10.135.0.3
I have set the gateway on both as 10.135.0.1
and the mask as 255.255.244.0

XP is saying that I have full connectivity but cannot connect to server.

sigh

Any more suggestoins would be more than welcome!

---

### Post by darth_vector on 2006-01-04
can you post the output of typing "ifconfig /all" in the windows XP cmd thingy? also, can you ping 10.135.0.1 from the windows box?

---

### Post by hatstand on 2006-01-04
ifconfig/all not recognised as a command. I tried ifconfg/all as well and if config/all. same

ping timed out.

---

### Post by darth_vector on 2006-01-04
sorry, it should have been
```
i**p**config /all
```


so the linux machine can ping the cable modem and browse the net?

---

### Post by hatstand on 2006-01-04
OK with ipconfig /all, I get:
Host: acer etc
Primary DNS suffix:
Node Typre: Unkown
IP routing enabled: No
WINS Proxy enabled: No

Connection Specific DNS Suffix:
Description; Realtec etc. etc
Physical address: 00-02 etc
DHCP enabled: No
IP Adress: 10.135.0.3
Subnet: 255.255.224.0
Default Gateway: 10.135.0.1

I guess it has someything to do with the Ip routing thing?

---

### Post by hatstand on 2006-01-04
[QUOTE=darth_vector]sorry, it should have been
```
i**p**config /all
```


so the linux machine can ping the cable modem and browse the net?[/QUOTE]


Yep no problems with the linux machine. Still same on XP

---

### Post by mips on 2006-01-04
Please double check your subnet masking. In one instance you have 255.255.224.0 and in another you have 255.255.244.0.

Can I recommend using a 255.255.255.0 mask on all devices wich is a bit easier to type/follow and still alows for 254 hosts on your network. You really do not need a 255.255.224.0 mask.

---

### Post by hatstand on 2006-01-07
BUMP

Here's a recap: I have an Ubuntu box. Wife has XP. I want to share my internet connection with her. I have this set up:

cable modem>>>Ubuntu Box>>>Switch>>>XP Box

I have set Ubuntu imcoming internet connection (eth0) to DCHP. I have set outgoing (eth1) to:
IP 192.168.0.1
subnet 255.255.255.0
Gateway address blank. 
The DNS entries for this are 10.3.1.111 and 10.3.1.100. 

I have followed the insrtuctions on the thread "sharing Internet Connection" in the general how to forum. I have installed firestarter.

My XP TCP/IP reads as follows:
IP 192.168.0.2
Subnet: 255.255.255.0
Gateway Address: 192.168.0.1

DNS 10.3.1.111
Alternate DNS: 10.3.1.100


Internet works fine on Ubuntu (as you can see: here I am!)
I can ping the Ubuntu box from XP and vice versa. BUT XP cannot ping the internet and cannot acces the internet through (the despised) Internet Explorer.

What am I doing wrong?

---

### Post by hatstand on 2006-01-07
Not waiting, it seems. Internet on XP has magically started working with no further "fiddling" from my good self!

Confused, but happy!

---

### Post by nick4mony on 2006-01-08
Hmmm,

I will share the broad steps I went through to share an internet connection amongst 3+ computers.  However, mine was a dialup connection, not cable.

I made one of the computers "The Gateway", and installed the modem into it.  It runs Fedora Core 3, but Ubuntu is very similar. 

We use masquerading - what this does is to make all connections to the internet appear to come from a single IP address.

The broad steps were:
[list]
[*]Set up pppd, in the gateway
[*]use 'iptables' to enable masquerading (in the gateway).  Also used it to block various types of traffic (example: incoming TCP connections)
[*]enable IP forwarding (in the gateway)
[*]setup a DNS forwarding arrangement
[*]setup a private network with ethernet cable and a hub
[*]on the other computers (ubuntu, Win2000, Win-eXtraPain), set the default gateway to the gateway + the DNS.
[*](optional)Set up DHCP on the gateway (this I haven't done)
[*](optional)Set up squid or some other proxy (this I haven't done)
[/list]
A couple of things to bear in mind:
[list]
[*]I imagine the ISP only gives you one IP address - this might be a dynamic one that changes every so often - but that why you use iptables/masquerading.
[*]A few ISP's might try to stop you from masquerading - they may have a clause in their Terms & Conditions - and some may use technological means to detect masquerading, but it's mostly bullshit.
[*]You'll have to switch on both machines if the XP wife wants the internet.  However the benefit (at least in Aussie where we pay 15c per untimed phone call) is that you can reboot the windows machine without dropping the internet connection.
[*]pppd may not be an issue if you have cable internet.
[/list]
More information: 'man pppd', 'man iptables', the bind A.R.M. (dns forwarding), ifconfig.

It's rather a lot, but I'm sure if you read through the information and start planning, it will work.

---

