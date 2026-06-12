---
title: "NetBios broadcasts, SMB connecting"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by cpsully69 on 2010-12-02
Using 64-bit 10.04 trying to connect to shares on our Windows 2003 server.  Everything works great when I'm on the LAN in the office, I can browse the network, open shares, etc.  I don't think my laptop is officially joining the AD domain, but I do get a dialog box, the first time I try to browse the network, and I enter in my credentials, domain name, etc.

When I connect to the office via VPN, I can ping the server, I can RDP to the server...but cannot browse or connect to shares.  It never shows the dialog box asking for my credentials.

I ran IPTRAF for a while when I was in the office and I notice that when I connect to the network and browse, before it shows me the dialog for credentials, my laptop sends a broadcast on my LAN NIC IP address, port 137.

When I am on the VPN, I looked at IPTRAF and, again, this broadcast is sent, but on the LAN NIC that is my home network IP address...that broadcast never goes over the tunnel, so I never get a response from our server.  So, eventhough I have a route to the office LAN 192.168.90.0/24 network, the broadcast is on my home 192.168.1.0/24 network.

I have modified the smb.conf file to indicate the IP address of the WINS server.  I've also changed the "name resolve order" parameter and removed the "bcast" option.

And yet, the broadcasts still occur.

Is there another way to force Ubuntu to talk directly to a WINS server?  Or am I misinterpreting my problem?

Thank you.

---

### Post by cybergnome on 2010-12-02
Why would you think that your laptop is not "officially" joining the office domain?  It probably is.  Not only a domain, but a true server-client network, and not a peer-peer file sharing network.  The VPN may well be restricted on the server end by IT.  You should ask them, not here.  [-X

---

### Post by cpsully69 on 2010-12-03
For better or worse...I *am* IT. :oops:

I assumed I needed more "stuff" on my linux machine to join the domain, I figured I was just accessing the shares via my user credentials.

I don't think there are any restrictions on the VPN, as Windows clients using the same VPN can access network shares just fine.

---

