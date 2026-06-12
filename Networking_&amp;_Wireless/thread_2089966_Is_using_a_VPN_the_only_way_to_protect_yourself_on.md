---
title: "Is using a VPN the only way to protect yourself on a public network?"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by Wiking on 2012-11-30
?

---

### Post by ahallubuntu on 2012-11-30
No, it's just the most comprehensive way to protect yourself.  If you run your own VPN from home like I do, no third party is involved, either.

When you are on a public network, all transactions that use https: (SSL) are secure.  Some sites like Google do EVERYTHING with https now so all of your google searches are secure.

There is also a browser extension called "HTTPS Everywhere" that you can use to add SSL to even more sites:

[https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)

That would encrypt web traffic but not open FTP, POP3 email, etc.

---

### Post by Wiking on 2012-11-30
> No, it's just the most comprehensive way to protect yourself. If you run your own VPN from home like I do, no third party is involved, either.

would the public network still be able to log the final destination adress, the vpn server? in your case your running it at home.

---

### Post by SeijiSensei on 2012-11-30
> **Wiking said:**
> would the public network still be able to log the final destination adress, the vpn server? in your case your running it at home.

If someone is anal enough to sniff all the traffic on the network, and has hours and hours of spare time to browse through the logs, then sure.

The nature of your questions may be creeping into territory considered off-limits by the [Forum rules]("http://ubuntuforums.org/index.php?page=policy").  I can understand wanting to use encryption over public networks, but why does it matter whether the end point of the tunnel can be identified? I connect to my home network over a VPN when away; I could care less whether anyone logs that event. Perhaps you should tell us why you are asking about this.

> We do not support circumventing TOS, EULA, etc here.

---

### Post by Wiking on 2012-11-30
> **SeijiSensei said:**
> If someone is anal enough to sniff all the traffic on the network, and has hours and hours of spare time to browse through the logs, then sure.

The nature of your questions may be creeping into territory considered off-limits by the [Forum rules]("http://ubuntuforums.org/index.php?page=policy").  I can understand wanting to use encryption over public networks, but why does it matter whether the end point of the tunnel can be identified? I connect to my home network over a VPN when away; I could care less whether anyone logs that event. Perhaps you should tell us why you are asking about this.

I figured since your on a public network that it would be wiser to use a hosted VPN instead of running one from your house.

---

### Post by SeijiSensei on 2012-11-30
Why?

---

### Post by Wiking on 2012-11-30
Will it not make your home network vulnerable if you're connecting via a public network? If it is advisable not to connect to your bank or email account using a public network why would it be different for your home network, even though you are using vpn?

---

### Post by SeijiSensei on 2012-11-30
VPNs like OpenVPN or Microsoft PPTP set up a point-to-point connection between machines.  Only one port is open on the server end, and it is usually some randomly-selected "high" port (> 1023).  When you connect, the local machine sets up the connection by sending traffic to that port, then all communication between you and the remote is encrypted and sent directly to that same port using the UDP protocol.  If you eavesdropped on the connection, all you would see is a stream of bits.  Unless you have access to the encryption keys you can do nothing with that data.  Nor is there much an attacker could do were he or she to discover the listener on your home server.  They would need your encryption keys to gain any traction.

Usually the concerns about things like financial transactions include other types of threats.  Suppose, for instance, that you are in a cafe, and someone has futzed with the cafe's DNS provider so that queries for mybank.example.com get sent to badguy.somewhere.net.  Now there are many ways where an informed user would realize this is happening.  Your computer might complain about the validity of the remote site's SSL certificate.  Maybe the page doesn't look quite right.  My bank uses personalized icons.  If I don't see the starfish I chose, I'll know it's not the real site.  Actual eavesdropping on the connection is pretty much a non-starter since all financial sites use HTTPS and, again, the connection is encrypted from end-to-end.

Most threats like these are more theoretical than practical.  I doubt you would have to worry about connecting to your bank from a Starbucks using HTTPS.

---

### Post by ahallubuntu on 2012-11-30
My home VPN is secure (I believe), so no, I am not worried about it being compromised while I am connected from a public network.  It is possible to be sloppy and set up a VPN that is not secure, however.  For example, you can create a simple password-protected VPN and not use keys or certificates; then the only security you have is the strength of the password.  My VPN uses certificates and keys.  If the public network I'm on detects the IP I am connecting to (my VPN), so what?  My IP is on a domain anyway so it is already publicly known.

---

### Post by BertN45 on 2012-11-30
You could look at a P2P network Hamachi, the peers are free. It is secure and encrypts all data. The easiest is to use the P2P server from the company, to maintain the encryption keys and peer addresses. It also solves the problem with respect to your own internet dynamic IP address, since at start-up it will be reported to the P2P server. In this way you can connect more locations together and share folders like on a normal LAN. I have used it in the past to connect Windows and Ubuntu systems on both sides of the Atlantic. I even controlled my XP file server here in Santiago from Brussels or Antwerp using RDP over that Hamachi network. The advantage compared to VPN is, that it works both ways. If you want you could set up your own P2P server, but I do not remember, whether that server is free.

---

### Post by Wiking on 2012-12-29
What about the first few seconds or minutes that it takes set up the VPN, any vulnerabilities then?

I'd assume the firewall would take care of that.

---

