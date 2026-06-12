---
title: "Wireless - can't ping the router or 127.0.0.1"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by cybernetic toaster pastry on 2011-06-06
_When on wireless_
I can ping the computers themselves and the internet (i.e. google.com) 
I cannot ping 127.0.0.1 or my router or the other computer
[U]
When hard wired[/U]
I can ping the router, 127.0.0.1, google.com, my computer

All I want is to be able to access files on one Ubuntu computer from another Ubuntu computer via a home wireless network.
I have been at this for a week now. Scouring the web for answers and so far I have come up with this:

[COLOR=DarkRed]Port 22 is open and listaning on both computers
I have both computers IP addr's via right clicking on the network icon-> Connection Information
ssh, openssh-server, and openssh-client are installed and running on both[/COLOR]


But when connected to wireless I try Places->Connect to server enter the other computers IP
I get "no route to host"
I'm not a networking guru and I'm at a complete loss on this. To my knowledge this should work, right?
 I think this is all the info I have so far. Any suggestions?

---

### Post by macburn on 2011-06-06
Maybe I am wrong, but ICMP traffic could be blocked in your router for wireless access, and not for wired access (considered as more secure).

You could search this option in the control panel of your router ("allow ICMP packets" or something like that).

macB.

---

### Post by cybernetic toaster pastry on 2011-06-06
> **macburn said:**
> Maybe I am wrong, but ICMP traffic could be blocked in your router for wireless access, and not for wired access (considered as more secure).

You could search this option in the control panel of your router ("allow ICMP packets" or something like that).

macB.
I don't see anything like that in the set up. maybe this will help, when I ping the router via wireless I get "connection refused by server"

---

### Post by macburn on 2011-06-07
Okay, according to me, it is clear that something stop the traffic.

Maybe a firewall, SElinux policy ? Check your security settings on both computers (and in the router too), I think your problem is here.

---

### Post by cybernetic toaster pastry on 2011-06-07
Don't know if this makes a difference but under system->Preferences->Remote Desktop I checked the box "Configure network automatically to accept connection" It changed my address from 192.168.1.2  to a completely different number.

 since my wife has gone to bed and refuses to give her password because of what I *might* do, I cant test the connection between the computers. Sure I could go into the grub edit menu and change her password but I have to live with her.

However I tried to ping the router (192.168.1.1) but "connection refused by server" still

---

### Post by doas777 on 2011-06-07
if you cannot ping 127.0.0.1, then usually that means that your adapter is not up. what do you get from 
```
ifconfig -a
```

since you say you can access the internet over wifi, this is obiviously not the case, so I wonder if the loopback interface has trouble linking to the wnic.

---

### Post by cybernetic toaster pastry on 2011-06-07
```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:5d:fe:31  
          inet6 addr: fe80::21f:16ff:fe5d:fe31/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5508439 (5.5 MB)  TX bytes:938652 (938.6 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13612 (13.6 KB)  TX bytes:13612 (13.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:2b:70:7e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe2b:707e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19269017 (19.2 MB)  TX bytes:5334845 (5.3 MB)


```

---

### Post by doas777 on 2011-06-07
everything looks good. 
I have to agree with the others, your router is likely blocking imcp requests inbound.
I used to use a wifi router inside my lan, using an alternate network, and routing it though my core. I never could get the router to not act as a firewall no matter what I tried to disable. I answered the problem by reconfiguring it as a bridge, and squashing the networks together. in bridge mode, it carries everything.
I can see why it would be desirable to keep a wireless host from scanning the other network devices, but it would be nice if it were configurable.

---

### Post by cybernetic toaster pastry on 2011-06-07
well, crap. I have no idea how to go about doing setting it up as a bridge. I guess I'm just stuck then. Thank you for your help. I at least know have an idea of why it wont work.

---

### Post by crispy_420 on 2011-06-07
Do you have an ssh server running on each? If so try to ssh over to each to test that level of connectivity. I really doubt something is blocking ping locally on the router level, it must be a firewall on the local box. 

Do both systems have valid IP addresses? Are they on the same subnet? These are the basics for connecting.

---

### Post by cybernetic toaster pastry on 2011-06-07
> **crispy_420 said:**
> Do you have an ssh server running on each? If so try to ssh over to each to test that level of connectivity. I really doubt something is blocking ping locally on the router level, it must be a firewall on the local box. 

Do both systems have valid IP addresses? Are they on the same subnet? These are the basics for connecting.
Most of your answers are in my OP
"[COLOR=DarkRed]Port 22 is open and listaning on both computers
I have both computers IP addr's via right clicking on the network icon-> Connection Information
ssh, openssh-server, and openssh-client are installed and running on both[COLOR=Black]"[/COLOR][/COLOR]
They are both on the same subnet.

---

### Post by crispy_420 on 2011-06-07
What is the make/model of router? Some units have a guest mode available in wireless that allows people out but not able to dig around in the network. That could be a possibility.

So you can't ping and you have made it readily clear they are on the same subnet/network you shouldn't have an issue using ssh to get it each other right? If not they are not on the same network not matter the IP address or subnets.

Have you tried using nmap to scan the network of hosts?

---

### Post by cybernetic toaster pastry on 2011-06-11
Sorry for the long inactivity, I'm just now getting a chance to reply. I got it working. It was just a simple check box for isolating the network i.e. just Internet connections only. It was kind of in an obscure area you wouldn't think to look in on the settings page. I am now going to mark this as solved.

---

### Post by crispy_420 on 2011-06-14
Like a way of isolating the wifi from wired LAN?

---

