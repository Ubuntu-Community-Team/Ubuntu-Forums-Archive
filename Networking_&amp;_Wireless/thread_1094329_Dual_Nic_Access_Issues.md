---
title: "Dual Nic Access Issues"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by Meldawn on 2009-03-12
I have a server running Ubuntu 8.10 it is a basic web server with ssh and apache running. The only extra pieces is that I have two NICs one set to my internal IP and plugged into out local network and one has a public IP that is outside our network.

The problem that I am having is that SSH and Apache are responding differently to either IP. I get 403 errors from apache and Permission denied from SSH, on the external IP. While, on the internal IP every things is working as it should.

I have verified that all the permissions are set as they should and neither system are generating any debug logs when I try to access the services via the external IP.

Any help would be greatly appreciated.

---

