---
title: "Home Exchange server and NAT stopping me from using it"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by OliverHaslam on 2012-04-25
I've set up Exchange 2010 in a VM on my home server. For the most part it is working well, and outside my home network it is fine. However, NAT obviously means that when I am on my home network, I cannot access the Exchange server via my external IP because the router has a fit.

Does anyone have any tricks up their sleeve for getting around that? I'm contemplating using my spare MIFI over USB, which I could dedicate to the one VM with Exchange on it and that would obviously do the trick. It's a bit of a hack though, and I wondered if there was any kind of fancy routing I could do to get around NAT?

I can't be the only one with an issue like this.

Cheers.

---

### Post by HermanAB on 2012-04-26
Howdy,

You must be the only geek in the world that will voluntarily torture yourself with Exchange on a home server...

Anyhoo, one of the problems is that Exchange uses RPC with random high ports, so making it work through a firewall requires some reconfiguration and wrapping with something like stunnel to make it secure.

Once you are tired of it, you should install Citadel. It takes about 20 minutes and it 'just works' using standard protocols like IMAPS.

---

### Post by OliverHaslam on 2012-04-26
> **HermanAB said:**
> Howdy,

You must be the only geek in the world that will voluntarily torture yourself with Exchange on a home server...

Anyhoo, one of the problems is that Exchange uses RPC with random high ports, so making it work through a firewall requires some reconfiguration and wrapping with something like stunnel to make it secure.

Once you are tired of it, you should install Citadel. It takes about 20 minutes and it 'just works' using standard protocols like IMAPS.

It wouldn't matter what I used, it still wouldn't work. NAT stops me from accessing anything on my own network via an external IP when I'm inside it. It's how NAT works.

---

### Post by nothingspecial on 2012-04-26
*Thread moved to **Networking & Wireless**.*

---

### Post by OliverHaslam on 2012-04-26
> **nothingspecial said:**
> *Thread moved to **Networking & Wireless**.*

Cheers. I didn't know whether to put it in there or not because it's not technically Ubuntu.

---

### Post by lisati on 2012-04-26
> **OliverHaslam said:**
> It wouldn't matter what I used, it still wouldn't work. NAT stops me from accessing anything on my own network via an external IP when I'm inside it. It's how NAT works.

Except when you do something like port fowarding.

---

### Post by Grenage on 2012-04-26
Hi there,

Do you have any internal DNS resolution?  If so, the most common way is to use that for internal resolution, and public DNS for external resolution - assuming you even have a DNS name for your external address.

Failing that, you'd need a router capable of handling internal clients when they use the external address, some do.

> **lisati said:**
> Except when you do something like port fowarding.

Most home routers won't let you use the external address through the internal network.

---

### Post by OliverHaslam on 2012-04-26
> **lisati said:**
> Except when you do something like port fowarding.

I think you're misunderstanding.

I can access the whole thing from outside the network fine, because I have forwarded the port for ActiveSync to the server. That's all fine, no worries there.

The problem is that NAT won't let you be inside a network, go outside it and then come back in.

EDIT: Not sure that was clear. What I mean is I can't be inside my home network and then connect to it via my external IP. NAT blocks that, no matter what ports you forward, because you're basically trying to connect from one IP back into itself.

Unless I'm being dense, and there's a trick I don't know?

---

### Post by Grenage on 2012-04-26
> **OliverHaslam said:**
> Unless I'm being dense, and there's a trick I don't know?

You're not being dense; as I said in my earlier post, most home routers do not support connections to the external interface from the internal interface.

About the only elegant solution I'm aware of is the use of DNS records, both internally and externally.

---

### Post by OliverHaslam on 2012-04-26
> **Grenage said:**
> You're not being dense; as I said in my earlier post, most home routers do not support connections to the external interface from the internal interface.

About the only elegant solution I'm aware of is the use of DNS records, both internally and externally.


Cheers, thought I was going mad for a minute.

How does your potential solution work? I figure there has to be a way, even if it's a bit of a mess.

---

### Post by Grenage on 2012-04-26
> **OliverHaslam said:**
> Cheers, thought I was going mad for a minute.

How does your potential solution work? I figure there has to be a way, even if it's a bit of a mess.

Well if you have any sort of DNS server operating at home, and the external address also has a public DNS entry, you're in a good position.  The public entry need not be anything fancy, a free dyndns.org account would do; let's assume that your DNS entry for the public IP is oliverexchange.dyndns.org.  If you have an internal DNS server, you can simply add a static entry for oliverexchange.dyndns.org which points to the internal IP address of the exchange server.

The only problem I can see is if a device was used externally, had the record cached, then tried to work internally.  This could be remedied by lowering the maximum cache time from 1 day (which it could be) to 5-30 minutes.

---

