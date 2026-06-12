---
title: "Access VPN from Ubuntu 64 through virtual machine running Windows XP and Cisco VPN"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by axeoth on 2010-08-20
Hello everybody,

[SHORT VERSION]

 I want to reproduce the solutions presented by users *seani* and *dhyan* at: [http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html) in order to connect to my university VPN.

 They wrote:

 "However my current method (“real” Cisco VPN Client running in a minimal XP setup under VMWare) has the advantage that I don’t lose local internet access."

and

  "Ya its true .Best thing according to me is using Sun’s virtual box and have winxp inside ubuntu ."

 The difference is that I am using VirtualBox instead of VMWare. And, of course, I am clueless... :(

[LONG VERSION]

 I want to access a VPN network from my laptop. In Windows XP + 
Cisco VPN client, on the same machine, the VPN works flawless, I can even ssh (through PuTTY) the machines at my university.

 To connect to Internet, I use a PPPoE connection (configured using PPPoeConf).

 Anyway, I would very much like to access the same VPN from Ubuntu Lucid 64 bit. Unfortunately, I did not succeed to compile the Cisco VPN client for my linux, neither to use the VPNC or Shrew Soft alternatives. Please do not direct me that way again.

 What I finnaly succeed to do is to install a copy of Windows XP as a guest in a VirtualBox virtual machine on my Ubuntu host. I provided two network adapters, one using NAT (through which the guest is able to connect to internet) and another one using Host-only adapter (which I hopefully will be able to use to communicate between host and guest).

 Inside the guest Windows XP, I installed the Cisco VPN client for Windows, and I am able to access the VPN, and even to ssh the machines from the guest using... PuTTY. Anyway, I cannot ssh my host, I don't know why (pinging works, it seems).

 What I would like is to use the VPN connection available in the guest to connect from the host. Basically, a way to redirect the traffic destinated to my VPN through the tunnel that already exists between the guest and the VPN. Unfortunately... I have no idea how to do it (I messed a bit with route commands, without success). Please help.

 Thanks.

---

### Post by axeoth on 2010-08-21
Just to let anybody reading this thread that I posted the question on the original page that I mentioned above, namely here: [http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html/comment-page-1#comment-44524](http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html/comment-page-1#comment-44524)

I am still looking for the answer, I hope it will be useful for other people, too.

---

### Post by axeoth on 2010-08-25
bump

---

### Post by maphilli14 on 2010-08-25
I cannot say for sure, but it could be that you are connecting to a VPN head end that is setup for full tunnel.  This would mean that all network traffic would be encrypted, including the host network.  That would effectively cut off your guest (XP) host only network from talking to the host (Ubuntu).

HTH,

Mike

---

### Post by axeoth on 2010-08-26
Thank you very much for answering, maphilli14. However, the network adapters that are running inside the guest Win XP (and I mean: the Cisco VPN connection and the Host-Only adapter) should be able to see each other (they are on the same machine). More, I am able to talk from the host (Ubuntu) to the Host-Only network adapter on the guest.

Specifically, the traffic between the host and the VPN gateway of my university should be routed as follows:

Host OS -> vboxnet0 network interface (on the Host) -> Host-Only network interface (on the Guest) -> Cisco VPN network interface (on the Guest) -> University VPN Gateway.

Among those, links 1, 2 and 4 work, although I don't know how to route traffic (but I succeed in pinging one machine from the other one). I imagine that link 3 could be set up using Bridge Connections in the guest WinXP.

Finally, I need a way to set up the routing trajectory, which I have no idea how to do it.

Anyway, thanks a lot, really.

---

