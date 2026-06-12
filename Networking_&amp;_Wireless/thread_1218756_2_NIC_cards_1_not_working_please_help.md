---
title: "2 NIC cards 1 not working please help"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by artgressick on 2009-07-21
ok, so I am not a uber linux guy but very well rounded in Ubuntu. I have a DELL t-100 which has a built in Broadcom NIC and a Linksys NIC, I did (2) installs to verify that both cards work each time setting each card as the primary NIC.

All connect to the internet just fine. So my problem is that I can't get both cards to work together (I am not talking about bonding or anything like that). I want to use each card on a separate IP like 192.168.1.250 and 192.168.1.251. Each card has a name such as eth0 and eth1. When I setup the iface in the /etc/network/interfaces all appears well but when I test the connection by running a ping and then disconnecting the wire it appears as though the primary NIC card keeps the connection for both IP addresses. I replicated this twice and each time both IP addresses map back the the primary link.

I have checked that the NIC cards are active using "lshw -C network" Is there a bug for this? I am running the latest 9.04 release and can't figure out an answer anywhere.

---

### Post by Kraut~salat on 2009-07-21
your problem is that both IPs are in the same network. Why would you need two NICs for one network unless you want to bond those and (theoretically) double your connection speed. Which as you explicitly stated is not your intention.
What do you want to do? If you just want two IPs all you need is a virtual eth device, no additional hardware needed.

---

### Post by artgressick on 2009-07-21
Well my plan is to use each nic to run NFS sharing and allow our ESXi VMware servers to run images directly from this computer. It is possible to have multiple nic cards on the same network, Mac, Windows even CentOS this works. So how do I make this work on 9.04. I am going to try the 8.10 version and see if it will work this morning.

---

### Post by Kraut~salat on 2009-07-22
so what happens if you disconnect the primary card? Does the secondary handle both IPs as well? I would assume that Linux knows your two IPs and therefor both NICs handle both adresses. The data received on the "wrong" NIC is then internally forwarded to the correct application.

From what you said your intention is I would try and bond the two NICs, that is a much cleaner solution.

---

### Post by Iowan on 2009-07-23
What are results of **route**? I guess it's possible to have two NICS in same subnet... there's a thread around here somewhere with information. (as I recall, it requires some tricky iptable rules). I'll see if I can find it.

---

### Post by aleyva on 2009-07-24
We have exactly the same problem, we're using Ununtu 9.04, we have four servers, each of them have 4 nics, two of them (eth1 and eth3 of each server) are connected to an iSCSI SAN with open-iscsi and multipath.

We've used Debian lenny with xen, but right now we're migrating to KVM so we choose Ubuntu for that. Three of the servers still have Debian with Xen and they work fine.

We have the following config:

eth1      Link encap:Ethernet  direcciónHW 00:22:19:ad:61:e1  
          inet dirección:10.251.0.104  Difusión:10.251.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::222:19ff:fead:61e1/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:15965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1181 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1066402 (1.0 MB)  TX bytes:118176 (118.1 KB)
          Interrupción:16 Memoria:d6000000-d6012700 

eth3      Link encap:Ethernet  direcciónHW 00:15:17:a5:ef:f3  
          inet dirección:10.251.0.105  Difusión:10.251.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::215:17ff:fea5:eff3/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:41625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26934 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:3362654 (3.3 MB)  TX bytes:2406452 (2.4 MB)
          Memoria:d5ea0000-d5ec0000 

If we ping the addresses from another host we observe that the MAC for both is eth1 MAC. With the Debian servers we don't have any problem, eachs address use the correct eth. The problem is that the iSCSI box assign LUN's based on MAC and initiator, so we are unable to effectively use multipath.

We have tried with arp_filter and other common solutions for the arp flux problem but we still have no luck.

---

### Post by aesis05401 on 2009-07-24
If you want to run service instances specific to each nic then you require two things:
A separate subnet for each card (and therefore for each service instance)
A packet forwarder (router or Linux based packet forwarding located on the client subnet).

If you just want to use two nics for general service with it not mattering what nic handles what, then use bridging with addressed tunnels for each virtualized instance.  

It really does come down to use case, but if you are not finding the solution that works for your situation you need to refine your question.  

Linux has very powerful and malleable networking stack technology, it can do pretty much whatever you want if you know what you want.

---

### Post by aleyva on 2009-08-04
The question that remains to me is why with Debian it works without problem? iSCSI is a standard requirement, and having two NICs per server is a common practice, i think that there would be a kernel setting to make it work, but I don't know which switch is it.

---

