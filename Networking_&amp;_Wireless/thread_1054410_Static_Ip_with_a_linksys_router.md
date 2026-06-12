---
title: "Static Ip with a linksys router"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-01-29
I am trying to set up a static ip for my ubuntu box to use as a server for a bunch of PCs.

I think the issue is that i only have a linksys WRT54G Firmware Version: v4.21.1

I was told to  /etc/network/interfaces

it looks like this...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface , all the 3rd level "1" were "0"
auto eth0
iface eth0 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 10.10.10.2

(end)

I've also tried the 3rd level as zeros.
In the router I set the DHCP to go from 192.168.1.100 - 192.168.1.119
The router address is 192.168.1.1

that's about all i know thanks for the help.

---

### Post by theozzlives on 2009-01-29
your router is acting as a DHCP server. You need to first get a static IP from your ISP. Set that up in your router, then setup reservations for your computers and use port forwarding to forward your static IP to which ever computer you want.

---

### Post by Coreigh on 2009-01-29
Do you want to use the server to serve files to the 'world' or just your private network?

If just your private network then manually assign an IP to the server in the same address range as the router. I.e. if the router address is 192.168.1.1 then assign the server 192.168.1.10. Then set up DHCP server on the router to assign address starting at 100. All the client computers will get addresses by DHCP and because they start at 100 none will interfere with the server which is at 10.

If you do want to server web pages to the 'world' then like 'theozzlives' says you will need a static IP for the router from the ISP. Or use a DynDNS service to keep track of your IP address so people can find your server on the web. Be aware that some ISPs do not alow HTTP saerver (web servers) on residential networks, in which case you will have to use a web host service to host the web site and just use the sever as a development platform.

---

### Post by linux6994 on 2009-01-29
Are the PCs that you wish to serve behind this particular router? 

If so then just set the individual PCs for static IP within the configured router range and set the dns & gw of those to the router address 192.168.1.1 vice the noted 10.10.10.2
The router will do the rest. 

If not then you will need to get a static IP from your ISP since the WAN side IP address will change periodically. 

In either case under the the Applications & Gaming tab within the router configuration you will need to set Single Port forwarding (ie .. ftp 21, http 80) to the particular PC that is hosting the service with your static ip of 192.168.1.120.

You can test the local web hosting by going to address 192.168.1.120 locally or from yourself then to you external ip address when you have the ports opened up.
Good Luck!

---

### Post by cariboo on 2009-01-29
You've got part of your  configuration file wrong.

> # This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface , all the 3rd level "1" were "0"
auto eth0
iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 10.10.10.2

You  don;t need the hotplugable section for a server, as it is never going to be hotplugged.

The auto eth0 section should look like this:

```
address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
gateway  192.168.1.1
```

I have the same router and I set the DHCP range from 192.168.1.100 - 192.168.1.115, and assign that static ip to 192.168.1.200 and up.

Jim

---

### Post by zzzuppermen on 2009-01-29
Yeah, same thought for the gateway, that should be 192.168.1.1

---

### Post by wlraider70 on 2009-01-29
ok i think im almost there. I changed the setting and the box can connect to the router but not to the internet.

I think the issue is as someone said...

Single Port forwarding (ie .. ftp 21, http 80) to the particular PC that is hosting the service with your static ip of 192.168.1.120.

Could I just get a little more detail on this. like what ports i should forward and what tab in the router would do this, there are two options that look similar.

---

### Post by frozenfyer on 2009-07-17
I have a very similar problem to the OP which is why I'm bumping this thread instead of starting my own.

I've configured my box as a server with a static IP outside of the DHCP range on my WRT54G router. In addition, I have port forwarding working on all my relevant ports. Inbound connections into the server are working fine both behind and outside the router. i.e. If I do a HTTP request to my ISP provided IP address, the router port forwards it to my server box and I get a web page back.

The problem is that I can't get outbound connections to work from my server. i.e. From my server, if I ping google.com, I get an unknown hostname error.

Here's my /etc/networking/interfaces file

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.18
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

My router is set to port forward ports 80 and 22 to 192.168.1.18.

Any pointers on how to get outbound connections restored while still keeping the static IP? Everything worked when my server set to DHCP, but constantly having to change my port forwarding every few days was too much of a hassle.

---

### Post by frozenfyer on 2009-07-22
Anyone have any ideas or steps on how to fix outbound connections when using a static ip?

---

### Post by chili555 on 2009-07-22
When you set up a static IP, you are responsible to also assign DNS nameservers. If you use DHCP, theses are provided by the DHCP server. Did you amend */etc/resolv.conf*? If not, this should get the job done:```
nameserver 192.168.1.1
```

---

### Post by frozenfyer on 2009-07-22
> **chili555 said:**
> When you set up a static IP, you are responsible to also assign DNS nameservers. If you use DHCP, theses are provided by the DHCP server. Did you amend */etc/resolv.conf*? If not, this should get the job done:```
nameserver 192.168.1.1
```

Worked like a charm. Thank you Chili555!

---

