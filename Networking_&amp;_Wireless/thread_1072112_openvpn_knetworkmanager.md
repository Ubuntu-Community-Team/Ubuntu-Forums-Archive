---
title: "openvpn knetworkmanager"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by peterroots on 2009-02-17
Hi I am trying to connect to an IPCop server using OpenVPN
I have downloaded the openvpn client package from IPCop which contains a configuration file and a file peter.p12.  I have also downloaded the host certificate from the IPCop server servercet.pem

In the openvpn plugin for knetworkmanager it is asking for the gateway (I assume this is the name or public ip address of the computer I am trying to connect to)
Also it wants, under X509, a CA file, a certificate and a Key
My question is which of the 2 files I got from IPCop go where and where do I get the one I am missing?

If anyone knows what to do next to get things working, I would love to hear from you!!
Thanks

Right, getting closer - I now know that only the file peter.p12 is needed but it is totally useless as it is.
I followed these instructions to extract the three files I really need
[http://www.myhren.org/technical-stuff/networkmanager-and-openvpn](http://www.myhren.org/technical-stuff/networkmanager-and-openvpn)
Would never have guessed this in a million years!
Now I get to the point of activation stage: getting ip configuration  80% in NW before it throws a a VPN Connect Failure message

---

### Post by peterroots on 2009-02-18
So still can not connect with networkmanager but openvpn does connect using the configuration file I got from IPCop only the FQDN IPCop supplied did not work so I replaced it with the IP address of the server.  Fine with openvpn but still not with NM.
I suspect that I need to fill in something on the optional tab under TLS auth (I have already selected lzo compression and set the cipher to match the IPCop offering).

My other issues (which is probably an IPCop one not a NM one) is that I can only see the IPCop machine, not the rest of the network. (am looking on IPCop forums for the answer to this so not starting a new thread here)
I fixed this by choosing a subnet for the vpn connection totally unrelated to the network i was trying to get into and the network i am trying to get out from.

---

