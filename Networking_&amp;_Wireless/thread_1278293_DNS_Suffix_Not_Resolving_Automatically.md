---
title: "DNS Suffix Not Resolving Automatically"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by jcortes on 2009-09-29
I have a  ubuntu LAMP server set up on my local network. The problem im having is that the Ubuntu server on the network requires the fully qualified name (server.scc.local) however the windows servers with the same DNS Suffix do not.

I can solve this by adding the dns suffix to the TCP/IP settings of every workstation however this is a pain.

I do not have any reference to the dns suffix in the hosts or hostname file. 

why would the windows server resolve using just (server) and the Ubuntu server requires (server.scc.local)

---

### Post by doas777 on 2009-09-29
because the windows server is using netbios/wins naming, in which the ubuntu server is not configured to participate. you will find copius information about differant ways to configure your network to compensate.

my recomendation is to install bind on your ubu host, and define an internal zone for your network. then configure teh bind to forward unresolvable queries to another dns server (usually an isp one). last, set DHCP on your network to pass down the ubu server address as your primary dns server addr, and it shoudl work out. when a host needs a resolution, it asks ubu, who passes it on to the ISP if it is external, and relays the reply back to the host. 

another option is to configure samba on the ubu host to act as a wins server and point your clients to it.

---

### Post by jcortes on 2009-09-29
could you direct me to a good guide for winbind I have it installed just wanted to know if you knew any good tutorials.

---

