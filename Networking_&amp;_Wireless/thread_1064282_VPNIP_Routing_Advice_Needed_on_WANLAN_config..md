---
title: "VPN/IP Routing Advice Needed on WAN/LAN config."
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by yknivag on 2009-02-08
Not sure whether this should be in Security of Networking, I'm plumping for the latter...

My local network seems to be growing as I discover more and more smart things I can do with Linux that I could never do in Windows. I have a public facing website on one of the machines so have some WAN traffic on my local network too and so am, obviously, concerned about security.

Also I'd like to be able to access all my network when I'm away (or at work) and so there is a trade-off to be had, I guess, between tightening things down and letting myself in.  I used to do this using the built-in VPN service on my router, but as Linksys don't offer a Linux port of [QuickVPN]("http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=16787&lid=8801236168B03") and I've now got rid of Windows from my laptop this is no longer an option. So my plan is to set up my own VPN server.

My network looks something like this:

```

- WAN - Router (10.X.Y.2) -|- Server 1 (10.X.Y.3) - Public WWW Server, OpenVPN
                           |- Server 2 (10.X.Y.4) - Fetchmail, Dovecot, NAS
                           |- Desktop (10.X.Y.5) -  Desktop
                           |- etc (10.X.Y.etc) - etc

```

My intention is to set the router to block all incoming requests on all ports except :80 which will forward to 10.X.Y.3 and the OpenVPN port which will also forward to 10.X.Y.3 (expanding any further public access services on that one machine).

Am I right in my assumption that this will protect the rest of my network from outside access but that I will be able to access the other boxes via VPN? Or do I need to do something like this (with 2 NICs in 10.X.Y.3 and 2 diff subnets):

```

- WAN - Router (10.X.Y.2) -|- Server 1 NIC 1 (10.X.Y.3) - Public WWW Server, OpenVPN
                              Server 1 NIC 2 (10.A.B.3) -|- Router 2 (10.A.B.2) -|
                                                                                 |- Server 2 (10.A.B.4) - Fetchmail, Dovecot, NAS
                                                                                 |- Desktop (10.A.B.5) -  Desktop
                                                                                 |- etc (10.A.B.etc) - etc

```

Are there any other precautions I should take. Particularly on Server 1? to ensure that it is only accepting traffic from the WAN to port 80 and the openVPN port?

I'm guessing I'm going to have to do some fancy routing on Server 1 to get the top model to work, and also maybe with the bottom one if I need Server 1 to connect to Server 2 (or anything on Router 2 to be able to connect to the WAN!)

IP routing has never been my strong point, I guess this is obvious. Any ideas would be much appreciated...

Thanks in advance. :)

---

### Post by yknivag on 2009-02-09
Nobody?

---

### Post by dmizer on 2009-02-09
I used this: [http://www.untangle.com/](http://www.untangle.com/) in a virtual machine with vmware ([very well written directions in their wiki](http://wiki.untangle.com/index.php/Untangle_Virtual_Appliance_on_VMware)) to handle the subnet setup and VPN traffic.

---

### Post by yknivag on 2009-02-10
Hi dmizer, thanks for your response. I'll be sure to check out the software when I've sorted the physical layout...

I guess I need to clarify my questions, what I'm really looking for is some guidance on the following:

- Physical architecture, do I need the second router and subnet (as per the second diagram) or is the first just as secure?

- Will I need to add routing tables to Server1 to be able to do this?

- Are there other things I need to consider security wise to ensure that only Server 1 can receive external traffic?

---

### Post by dmizer on 2009-02-10
Untangle is essentially a virtual router. If you configure it correctly, it will work as though you have a physical router. This way, you only need one server for handling all of your network traffic, and you can configure your physical network in a variety of configurations easily, quickly, and securly.

This will keep you from having to purchase additional equpment as well as allow you fine grained control and security across your local network.

What I'm essentially suggesting is something like this:

modem -> physical router -> gateway server (with untangle vm) -> two subnets

One subnet would be dedicated to inbound WAN traffic, the other would be dedicated to the rest of your network.

The physical router would be functioning as nothing more than a firewall, and the gateway server could host any number of services to either the WAN traffic subnet or the LAN traffic subnet.

Obviously you don't have to use Untangle, there are a large number of gateway tuned OSs available which you can run in a virtual machine. I just suggest it because I use it and find that it works well, and is easy to configure because the documentation is so well written.

A solution like this means you don't have to mess with configuration files on your server (like routing tables and IPtables). All you have to do is turn the thing on, set your network preferences, and off you go.

---

### Post by yknivag on 2009-02-11
Hi dmizer,

Thanks again for you response.

Maybe I'm reading it wrong but untagle seems to require a GUI for config and my server is a headless box with a minimal ubuntu install (I don't like having GUIs on servers).

I don't mind the extra router if that's what's required as I have a spare one anyway.

I'd really like to do this as a learning excersise natively in Linux if it's possible.

---

### Post by dmizer on 2009-02-11
What kind of specs does your headless box have?

---

### Post by yknivag on 2009-02-11
The box in question (server 1) is quite small, it's a PIII-900MHz with 64MB of RAM (expandable as I have some more) and a 40GB HDD.  It's currently running Ubuntu Server 7.04. It servers multiple low traffic websites and is the box I'll be using to host the VPN.

Server 2 is a rather more powerful box (twin 600MHz PIII with 4GB of buffered RAM) hosting a 4 drive, 1500GB true-hardware-raid5 storage solution, a POP to IMAP relay and a number of other services. It access the outside world but doesn't listen on any ports open on the router from WAN to LAN.

---

### Post by dmizer on 2009-02-11
```
- WAN - Router (10.X.Y.0) -|- Server 1 NIC 1 (10.X.Y.3) - Public WWW Server
                           |- Router 2 (10.A.B.0) -|
                                                   |- Server 2 (10.A.B.4) - Fetchmail, Dovecot, NAS, OpenVPN (in a virtual machine)
                                                   |- Desktop (10.A.B.5) -  Desktop
                                                   |- etc (10.A.B.etc) - etc
```
This is the solution I would suggest because I wouldn't suggest having www and vpn traffic routing through the same box.

What I'm trying to suggest is adding a third virtual server. Forwarding VPN through both routers (change ports through each network device) into a VPN server installed in a virtual machine on server2. This will put your external device on the proper subnet for accessing local services and keep www traffic isolated.

You can use Untangle as your OpenVPN server and/or your second router, you can use another ready made solution, or use a second physical router and manually configure a VPN server yourself. Whatever you decide, I highly recommend taking advantage of the multiplicity that virtualization can offer you.

---

### Post by yknivag on 2009-02-12
But that would mean coming all the way through to the second subnet before authenticating on the VPN.  So effectively both Server 1 and Server 2 now have public facing open privileged ports.

I think this is going to take a considerable amount of research...

---

### Post by dmizer on 2009-02-12
Perhaps I'm not explaining virtualization well.

Virtualization is not like Wine which runs inside the host OS like any other program. Virtualization gives direct hardware (CPU, RAM, HDD, and NIC) access to a completely independent OS, so you can run services on the guest OS without compromising the host. Virtualization allows one computer to become two, or three, or more.

so, while VPN will be traversing both routers, this does not mean that both servers will have open facing ports. And since server 1 is on a completely different subnet, it would be impossible for VPN traffic to get to it. Also, as long as neither server has OpenVPN installed, then neither server will be listening for your VPN traffic. But most importantly, your VPN traffic can't touch the WWW server.

Either way, virtualization allows you to have a third virtual server functioning independently of your other servers. And, even though the virtual machine is running on your second server, it's as good as having a physically separate computer. You can even route all of your lan traffic through it like so:
```
- WAN - Router (10.X.Y.0) -|- Server 1 NIC 1 (10.X.Y.3) - Public WWW Server
                           |- Virtual server 3 - VPN, NAT (10.A.B.0) -|
                                                                      |- Server 2 (10.A.B.4) - Fetchmail, Dovecot, NAS
                                                                      |- Desktop (10.A.B.5) -  Desktop
                                                                      |- etc (10.A.B.etc) - etc
```

Where "virtual server 3" is a virtual machine running in vmware on server 2. (This is actually how I have my network configured)

Both the solution I posted earlier, and this one are far superior to having both VPN and WWW traffic handled on the same computer.

---

### Post by yknivag on 2009-02-14
Dmizer, firstly thank you for your continued interest and assistance - you're making me think about a lot of options, many of which I hadn't considered. I can't thank you enough!

I'm not sure about this though:

> **dmizer said:**
> Virtualization is not like Wine which runs inside the host OS like any other program. Virtualization gives direct hardware (CPU, RAM, HDD, and NIC) access to a completely independent OS, so you can run services on the guest OS without compromising the host. Virtualization allows one computer to become two, or three, or more.

That's not quite how I understood it. Clearly a VM isn't an emulator like Wine; but neither does it (to the best of my knowledge) have direct access to any physical resource - the virtualised OS sends instructions and data to pseudo devices presented to it by the virtualisation software. This in turn passes those transactions to CPU/RAM/HDD/NIC etc via the 'host' which is actually in control of the real hardware and sees the virtualisation software as simply that - software.

Something like this:
```

------------------
|                |
| Host  -------- |
|       |      | |
|       |  VM  | |
|       -------- |
|                |
| CPU  NIC  HDD  |
|                |
------------------

```

This makes a VM potentially more vulnerable as they are susceptible to security flaws in both host OS, virtual OS and in the virtualisation software itself which could, theoretically, leave open the possibility of the VM executing code on the host.

Also (and I accept this is my fault for not mentioning the possibility earlier) but what if "etc" were a wireless device? It would be connected directly to the router and would, in your diagram, be upstream of "Server3" and thus in the same subnet as "Server1"...

Maybe I'm rather over-parranoid, coming from a corporate environment where most services are designed in either 3 or 4 layer configurations with multiple hardware firewalls between each layer.  This is horrendously expensive but exceptionally secure. Hence my favouring:
```
WAN->Router/Firewall->VPN termination->Router/Firewall->LAN
                    ->WWW
```

To replace:
```
WAN->[Router/Firewall/VPN Termination]->LAN
                                      ->WWW
```

I've got a lot to learn!

---

### Post by yknivag on 2009-02-14
Thinking about this, I'm being drawn to the following:

```

WAN->Router1->[Server1 VPN Term {WWW in a VM}]->Router2 (DHCP/WiFi AP)->LAN machines
                                                                      ->Wireless

```
where Server 1 contains 2 NICs (one facing each router) in different subnets and the VM containing the WWW server is on the same subnet as Router1.

What do you think?

---

### Post by dmizer on 2009-02-15
Virtual machine software like VMware access the hardware directly, nearly independent of the host OS. So much so, that it controls physical resources both for the host OS as well as the guest OS. Some virtual software even runs directly on the hardware as an independent os. So the biggest worry you would have is the security of the virtual software itself. More information here: [http://www.vmware.com/virtualization/](http://www.vmware.com/virtualization/)

You're really looking at something more like this:
```

--------------------
|                  |
|         -------- |
|  Host   |      | |
|         |  VM  | |
|~~~~~~~~~|~~~~~~|~|
|  V M W A R E     | 
|                  |
| CPU  NIC  HDD    |
|                  |
--------------------

```
Though, less so with the HDD, as the Virtual machine's hard drive is simply a file on the host's physical hard drive. But, the host cannot access this file while the guest is running, and can only make copies if the guest is turned off.

Either way though, VMware brings the virtual machine so close to the hardware that you can actually route host traffic through the virtual guest as though the guest were physically between the host and the router This is how I have my LAN configured, and how I diagrammed the configuration I suggested earlier.

So, even though the VPN, NAT virtual machine is a guest inside server 2, Server 2 can still get it's IP from server 3.

It's good to be paranoid if you're administering your own network. So there's no problem with discussing this issue to your satisfaction. If you're willing to try an all virtual solution, there are also open source virtual OS which run directly on the host hardware and give true direct access to the physical layer. In my opinion, this is ideal but more effort than I was willing to put up with when I designed my network.

> **yknivag said:**
> Thinking about this, I'm being drawn to the following:

```

WAN->Router1->[Server1 VPN Term {WWW in a VM}]->Router2 (DHCP/WiFi AP)->LAN machines
                                                                      ->Wireless

```
where Server 1 contains 2 NICs (one facing each router) in different subnets and the VM containing the WWW server is on the same subnet as Router1.

What do you think?

Sorry, there are several problems with this. First of all, while server 1 has enough CPU for virtualization, it certainly doesn't have enough RAM. Secondly, your VPN is terminating on the WWW subnet rather than the LAN subnet where you would need to be if you wanted access to the file server.

Obviously, with virtualization there are a variety of different options for you. I do like to have my WWW server in a virtual machine because it's dead easy to make backups. I also like to have my gateway running in a virtual machine because it allows me to do nifty things like traffic shaping, and failover while making a cakewalk of subnetting. I can also easily isolate inbound WAN and wireless traffic without having gobs of equipment.

---

### Post by dmizer on 2009-02-15
If you upgraded server 1 with about a gig of ram, it could probably handle something like this:
```
                                                  |- Virtual Public WWW server (10.X.Y.2)
= WAN - Virtual gateway - NIC 1 (10.X.Y.0) - NAT -| 
                        - NIC 2 (10.A.B.0) - NAT, VPN -|(Hub)
                                                       |- Server 1 (10.A.B.4) - Fetchmail, Dovecot, NAS, VMware
                                                       |- Desktop (10.A.B.5) -  Desktop
                                                       |- etc (10.A.B.etc) - Wifi etc.
```
Where both the virtual router and the WWW server run in virtual machines on physical server 1. This would cut down the cost of having two physical servers running constantly. This way, you could also do things like adding dedicated virtual database servers with failover for the WWW server.

Edit:
If you are paranoid about that kind of setup (nothing wrong with that), you could increase security by adding a physical firewall/wifi-router between the virtual router and the WAN. Then you could route wifi traffic through the virtual gateway's VPN for access to LAN resources.

---

