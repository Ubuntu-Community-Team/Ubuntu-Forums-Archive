---
title: "Using Maverick as VPN remote gateway"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by cog1 on 2010-12-02
Hi all
 
I'd like to use an Ubuntu Maverick machine as a remote gateway. This machine is out on the internet and has permissions, thanks to its IP address, to access remote resources.
 
I need to access those resources but I don't want to add my own IP address to all the services the machine has access too, so a good solution would be to route my internet traffic THROUGH the Maverick box.
 
I've tried setting up pptpd which starts up fine; I can connect to it OK until my (Windows) client is waiting to be registered on the network. This is probably because I don't know exactly how to specify the 'remoteip' in pptpd.conf
 
This machine has one NIC. I can specify in pptpd.conf what it's IP is, and specify 'remoteip' to give a range of addresses that will be issued to clients.
 
However; this machine is in Amazon's EC2 cloud - can I achieve this without knowing about the local network?
 
I tried setting 'remoteip' to the next couple of addresses about the address the NIC has - doesn't seem to work though.
 
 
Thanks

---

