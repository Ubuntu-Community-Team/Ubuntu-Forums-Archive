---
title: "REquire help setting static ip"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by EmpVal on 2012-08-21
[ifconfig output]("http://paste.ubuntu.com/1159140/")

I did find [this post]("http://ubuntuforums.org/showthread.php?t=1985170") but I am still none the wiser.

I am trying to set up a static ip in order to run transmission on my server, however, I am slightly confused about where I can find the requisite details. I have started to edit /etc/network/interfaces and my file looks like this:

auto eth0
iface eth0 inet static
address 192.168.1.48
netmask 255.255.255.0
gateway

My question is, how do I find out what my gateway is, and do I need to know my DNS address?

Thanks in advance!

---

### Post by TheFu on 2012-08-21
Networking can be extremely complex.  I'm assuming you have a common home router with the answers below.  Other networks and complex home networking may not follow what is suggested below.

In a home environment, the "gateway" is the router.  Based on the IP in your example, I'd assume the router IP that you'd want to enter is 192.168.1.1.  This may not be correct.

The most correct way to get the data you want is to log into the router administrative interface and find the 
* netmask, 
* DNS, and 
* DHCP ranges.  
With that information, you can safely select a static IP for any device on the network. Just be certain that no other device is using it ... ever.  If you don't have the login to the router, you can still get the DNS and netmask and gateway by using DHCP.

Set you PC to use DHCP again and reconnect to the network. Then run **ifconfig -a**.    
* "inet addr" is the DHCP address.
* "Mask" is the netmask
Now run the **route **command.  The "default" route should point to the "gateway" and it will either have a hostname or IP address.

You can choose any IP address that you want within the netmask and IP range, however, you probably want to be 100 IPs away from whatever your DHCP address is.  DHCP servers seem to advertise starting from the bieginning address, so if your DHCP address is 192.168.1.100, it is a good bet that .100 is the first DHCP address provided.  A static IP that is from .10-.99 would probably work fine, assuming a netmask of /24 (also 255.255.255.0) is used.

Now you just need a DNS server.  Different versions of Ubuntu handle that differently.  12.04 wants you to add it into the same file, but only on "server" installations. If you are on a desktop install, using the GUI will store the static data in a different place - /etc/NetworkManager/ ... I think.  I use server more than desktops.  

In theory, you can use any DNS server in the world, but you really want to pick a trustworthly DNS because SSL (HTTPS) security is 100% dependent on DNS being honest. Your ISP runs a DNS, but you don't need to use it if you prefer something else. OpenDNS is a popular choice with added features ... like blocking unwanted categories of servers.  Some ISPs block external DNS and redirect all DNS queries to their servers. Comcast residential does this unless you specifically have your account setup to **not** do that.  

A slow DNS will make everything on your network slower.  This article explains how to find the fastest DNS for your location [http://www.howtogeek.com/howto/16372/find-a-faster-dns-server-with-namebench/](http://www.howtogeek.com/howto/16372/find-a-faster-dns-server-with-namebench/)

Hopefully, I was clear.
If you reply, please include the exact version of Ubuntu so that someone can point you towards the easiest GUI method.

Also calling something "my server" can confuse us.  Is this a hosted server somewhere or are you trying to do this from a home network? Changing the IP on a hosted server is a bad idea - like you'll be disconnected and never get reconnected - bad idea.  
At home, you'll need to do some router work to allow inbound ports from the WAN through the router, to your "server" on a static IP.

If your public IP is not static (WAN side of the router), then you'll need/want a dynamic DNS service to redirect inbound traffic to whatever IP address that your cable-modem or DSL modem is currently using. DynDNS or NO-IP are/were popular services for this.  Whichever service that your router supports is probably the best to use. DynDNS seems to be supported by every home router I've seen.

Very little of what I'm describing is Ubuntu/Linux specific. This is simply how IPv4 and the internet works.  Every network device works this way, if they use IPv4 networking.  Starting with a "basic networking" tutor might be a good use of your time.  [https://www.grc.com/securitynow.htm](https://www.grc.com/securitynow.htm) episode #25 is a good start.

---

