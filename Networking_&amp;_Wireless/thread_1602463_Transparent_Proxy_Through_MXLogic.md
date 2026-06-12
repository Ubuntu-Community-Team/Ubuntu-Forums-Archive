---
title: "Transparent Proxy Through MXLogic?"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by MastarChew on 2010-10-21
[SIZE=4]What I am trying to do is force a whole entire networking through a proxy called mxlogic. This network is currently using a Barucuda web filtering system and they want to get rid of it. Parts of this network are public, so this needs to be done with out touching the clients. Also this is a 99% windows environment. [/SIZE]
 
[SIZE=4]From my research it appears that the best way to do this is to set up a transparent proxy server using a linux kernal and squid. My question is though if I set it up this way and transparent proxy to a remote box, is this going to go through the proxy filtering traffic? Or is this just going to go to the proxy and lose internet connectivity? [/SIZE]
 
[SIZE=4]I know I probably sound like a noob here, and in comparison to most of you I probably am. If anyone can answer this question or help me find a solution to this situation, such as a router that can do this, or any other solution, please let me know.[/SIZE]

---

### Post by MastarChew on 2010-10-25
nobody has any input for me?

---

### Post by SeijiSensei on 2010-10-25
1) What is an "mxlogic" and what role does it play in your network?  Is it a router?  Does it sit between your network and the Internet?

2) I only know of the Barracuda spam filtering appliance that uses a customized version of Spamassassin to filter email.  It might do web filtering as well, I don't know.  Are you trying to replace this box with a Squid proxy?  What relationship, if any, does this have to the "mxlogic"?

3) If Squid can can make HTTP and, optionally, HTTPS requests successfully to the Internet, then you could put the workstations behind it and use it as a transparent proxy.  Is that what you're trying to do?

> **MastarChew said:**
> My question is though if I set it up this way and transparent proxy to a remote box, is this going to go through the proxy filtering traffic? Or is this just going to go to the proxy and lose internet connectivity? 

I don't understand this question; isn't the Squid box designed to be the proxy itself?  If the Squid box sits behind another proxy that does filtering, then all the requests from Squid will be filtered just as if you were sitting behind that other proxy with a PC and web browser.

Perhaps you're trying to end-run your network administrator and set up a proxy that can punch through the device already in place?  If so, we can't ethically provide support here for technologies designed to circumvent network policies.

---

### Post by MastarChew on 2010-10-25
1)MXLogic is an external webproxy that you pay a subscription fee for. It filters out spam, porn, etc. It is not involved in this particular network at all atm.
 
2)The Baracuda system filters all incoming and outgoing traffic on their network, it's litterally right after the modem. They want to get rid of it because of how expensive and slow it is. This would be where the squid proxy would go, yes. This has no relationship to MXLogic.
 
3)No. As far as i know squid does not support HTTPS at all. and if we ended up using a Squid box the only thing I want it to do is put all internet traffic through the external mxlogic server.
 
yes, The squid box is typically designed to be a proxy itself. In my case I don't want it to be.
 
No I'm not trying to go around a network administrator. I would be considered one of them.
 
In a nutshell this company wants to remove the barracuda and use mxlogic, instead. mxlogic is typically set up on each computer as a proxy in internet options. This is a public setting and as such parts of this network are public. I need all the computers in this network to go through this proxy with out ever touching them.
 
Thank you for the reply BTW

---

### Post by SeijiSensei on 2010-10-26
I don't know that you need Squid for this.  If you want to forward all outbound port 80 traffic to another IP/port (the MXLogic in this case), you can do that with iptables like this:

```
iptables -t nat -A PREROUTING -s 10.0.0.0/8 --dport 80 -j DNAT --to-destination 1.2.3.4:80
```

would send all packets from the 10/8 network intended for a remote port 80 to port 80 on host 1.2.3.4.  Getting the right source address will be tricky since you still need to masquerade this traffic with the router's external IP address.  I'm pretty sure it's possible to do this, but you'd need to study up on iptables.

With Squid, you'd need to figure out how to make it forward all the traffic to the upstream MXLogic host.  I've never tried using it for that.

---

### Post by MastarChew on 2010-10-26
With using IPtables, would that use mxlogic as a proxy?
Or would it just send all info to mxlogic and then not go to the internet?
Also Mxlogic uses a particular port number when you set it up as a proxy in internet settings.
Thank You for your reply

---

### Post by MastarChew on 2010-10-26
mxlogic settings are usually something like the following inside internet options:
[B]internet options->connections->lan settings->proxy server
address:[/B] example.com.web01.mxlogic.net **port:** 8080

---

### Post by SeijiSensei on 2010-10-26
> **MastarChew said:**
> mxlogic settings are usually something like the following inside internet options:
[B]internet options->connections->lan settings->proxy server
address:[/B] example.com.web01.mxlogic.net **port:** 8080

So you'd set the --to-destination to example.com.web01.mxlogic.net:8080 in the code I gave you above.  Only outbound HTTP traffic would get sent to MXLogic by this method.  However there's still that niggling issue of the source IP address these packets will carry.

It sounds to me like you don't have much experience with these technologies.  I suggest you start by installing another box in your office with two network cards.  Put Ubuntu on it, put another PC behind it, and begin experimenting with alternative solutions.  If you keep at it, you'll figure something out.  Give yourself a few days to get all the kinks out.

---

