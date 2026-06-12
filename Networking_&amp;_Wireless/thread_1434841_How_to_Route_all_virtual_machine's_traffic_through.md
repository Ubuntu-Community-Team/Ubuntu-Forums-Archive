---
title: "How to Route all virtual machine's traffic through PPTP VPN"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by snowbourne on 2010-03-20
Hey All!

I have a complex situation that I need to solve, I'll try to describe it the best I can, but if you need more details just let me know.

I have Ubuntu 9.10 SERVER installed on my home server here in California, I have installed Virtualbox 3.1.4, and have created a virtual machine called MICRO, running Ubuntu Hardy JeOS. I'm using bridged network across my server eth0 nic. I can access MICRO throughout my network without any problems.

My goal is to establish a persistent VPN connection across PPTP within the virtual machine, and route all it's traffic through the vpn tunnel. I have installed the appropriate PPTP server on my server in Europe, I have tested it on Windows XP and Mac, it works on both (routing all network traffic.)

Within the Virtual Machine, I have already installed the apt-get package: pptp-linux, I followed the instructions found here:

[http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html](http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html)

and used this as a reference:

[http://pptpclient.sourceforge.net/routing.phtml](http://pptpclient.sourceforge.net/routing.phtml)

I've successfully managed to install the client software, setup the correct peer in /etc/ppp/peers/., and connect to my vpn such that I can access the VPN server, and all clients connected to it.

The problem I'm having is this, my virtual machine cannot access the outside network. When I run this command while connected to the vpn:

```
traceroute google.com
```

It shows the path from my virtual machine, to my router, to my modem, to my ISP and to google.com. It SHOULD show the path from my virtual machine, to my VPN server, to my dedicated servers routers, and then to google.

This tells me that not all network traffic is not being routed.

I found this section regarding "routing all network traffic through the VPN"

[http://pptpclient.sourceforge.net/routing.phtml#all-to-tunnel](http://pptpclient.sourceforge.net/routing.phtml#all-to-tunnel)

I've followed their instructions, but nothing has worked.

A few preliminary questions:

1.) They describe two scripts, which belong in /etc/ppp/ip-up.d/ and ip-down.d/ respectively. Following the previous tutorial, I created a route-traffic script, (which i made executable.) Should I add this code to my existing route-traffic script? Or make a new script? Does it matter what I name it?

2.) Does the fact that this machine is a virtual machine using bridged networking add some nuance I'm not recognizing and not able to read a tutorial about appropriately?

NOTE: I have done NOTHING in terms of networking commands locally, either on my router or the host machine. If there is some routing that needs to occur WITHIN my network in order for this to work, I have no idea what needs to be done.

---

### Post by snowbourne on 2010-03-21
here is the output of ip route before I connect to the VPN:

```

192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.4 
default via 192.168.1.1 dev eth0  metric 100

```

here is the output AFTERwards.

```

192.168.0.1 dev ppp0  proto kernel  scope link  src 192.168.0.234 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.4 
default via 192.168.1.1 dev eth0  metric 100 

```

My home network, is located at the address: 192.168.1.1

My VPN is 192.168.0.1 and issues ips such as 192.168.0.234-237 to connected VPN clients.

---

### Post by Saghaulor on 2010-03-22
As I understand it, the vm guest, while in bridged mode, is using the exact same network parameters of the host os.

So, from what I understand of your post, you just need to start your vpn tunnel at your host os's connection, as you indicated, eth0.

Then from what I understand from all this, the vm guest os should also route through the vpn tunnel via the bridged network.

Hope that helps.

---

### Post by snowbourne on 2010-03-25
Thank you for the response,

If I understand you correctly, you'd like me to try these same procedures on the host machine? I'll try it, but the whole reason I wanted to do this in a virtual machine, is so that the host machine could remain within my network while the virtual was over the VPN.

---

### Post by Saghaulor on 2010-03-29
> **snowbourne said:**
> Thank you for the response,

If I understand you correctly, you'd like me to try these same procedures on the host machine? I'll try it, but the whole reason I wanted to do this in a virtual machine, is so that the host machine could remain within my network while the virtual was over the VPN.

You should still be able to connect to your network, while connected to to the vpn.

You may be able to set up the vpn on the guest, without setting it up on the host. I'm not sure how, however. Best of luck.

---

