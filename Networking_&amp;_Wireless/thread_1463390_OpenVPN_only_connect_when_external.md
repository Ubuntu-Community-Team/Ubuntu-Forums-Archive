---
title: "OpenVPN only connect when external"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by koan on 2010-04-26
We use Openvpn for remote access to the office network.  It would be nice to keep this running and automatically connect to the office at all times.

Once started, it does this anyway.  The problem lies when the user comes into the office.  Openvpn connects as usual to the vpn gateway, but this causes weird routing loops.

Is there a way to say to Openvpn "Always connect to the gateway unless you are on network 10.10.10.0/24" ?

We use openvpn in routed mode btw.

Thanks,

Paul

---

### Post by tacom6 on 2010-04-27
Paul, can you upload the server configuration file?

---

### Post by prezbedard on 2010-04-29
Hey Paul,

I hate to hijack your thread but noticed you mentioned you have openvpn working. I am trying to setup site to site tunnel. The furthest I have been able to get is I can ping from both sides the virtual ip and real address of the other vpn server. I can also use some services that may be running webserver etc . I can not communicate with anything on the local network on either side though. Before I post anything I want to make sure you may be able to help.

Thanks and sorry for the hijack!

---

