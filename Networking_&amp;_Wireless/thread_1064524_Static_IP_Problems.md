---
title: "Static IP Problems"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by Godd on 2009-02-08
I'm not exactly new to linux, but I don't know a whole lot.

I need to forward two ports from my router (Netgear WGR614 v6) but I'm converting from DHCP to Static first.

I've edited my /etc/network/interfaces to look like this

> auto lo
iface lo inet loopback

#This is my static IP

iface eth1 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network  66.189.171.120
        gateway 192.168.1.1


auto eth1

and /etc/resolv.conf to

> nameserver 192.168.1.4

But as soon as I restart my network, I drop off.

I've tried pinging my router and google to check if nameserver was incorrect, but to no avail.

I've scanned through numerous help threads on the subject, yet again, to no avail.

I've triple checked all the IP's but I'm still not sure they're all right.

When I restart after I comment out the new script, it says "Ignoring unknown interface eth1=eth1."

What should I do?

---

### Post by Godd on 2009-02-09
Also, I've read that there are two different ways to find out your routers IP. either to use route -n or to go to whatismyip.com, or whatever it is.

However, they give me different IP's.

And a different thread say that your comp should obviously be under the same network, meaning if router IP = 10.0.0.0.1 then my IP should be 10.0.0.0.*.

But that doesn't seem to be the case with my setup. My router's IP is 63.251.179.* but mine is 192.168.1.*.

Hmmmm...

---

### Post by punx45 on 2009-02-09
looks like you may have a couple things mixed up.   heres an example /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.10   <---- this is the ip of this computer
        netmask 255.255.255.0
        network 192.168.1.0   <---not sure what this does but it should not be your external IP
        braodcast 192.168.1.255
        gateway 192.168.1.1  <---- this is the IP of the router


```

also the nameserver in /etc/resolv.conf should either be the router IP (it uses the DNS settings of the router) or a specific DNS server (like OpenDNS servers)

your router via NAT hands off connectivity from the external IP to other devices on the network, so nothing on your LAN needs to be configured with that IP.

192.168.1.x and 10.x.x.x are IP ranges reserved for private networks.   you can use either system.   most consumer routers are configured for the 192 set.

port forwarding you set in the router.  there should be a port forwarding setting in the configuration.   i forward HTTP requests (port 80) to my server, so in the router setup i tell TCP port 80 to forward to 192.168.1.10

makes sense?

---

### Post by Godd on 2009-02-09
I've just tried that and it still doesn't want to hook up.

My current config settings are...

> auto lo
iface lo inet loopback

#This is my static IP

auto eth1
iface eth1 inet static
        address 192.168.1.6
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.225
        gateway 192.168.1.1


> ### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4900
#
### END INFO



nameserver 192.168.1.1

The router wont respond to pings whether or not I have internet access. and I can't get a ping from the interweb.

How can I double check all the IP's?

Because, all the normal routes to retrieve the router IP's give me bs. and the one it should be as stated by the manufacturer doesn't work either.

And yes, you were very concise, thankyou for that. :)

---

### Post by Godd on 2009-02-09
I'm attempting to set up the router, I still haven't gotten my laptop to work...

But I can't seem to figure out my DNS address. How do I go about doing that?

---

### Post by Godd on 2009-02-09
I believe that I found a way around having to set my IP to static.

I reserved my IP on my server. Hopefully that will work.

---

### Post by Godd on 2009-02-09
Hey,

First off, thankyou for your help. Without your help I wouldn't be posting from a static IP enabled laptop. :]

But for future reference, you should ask if they are running wireless. I tried putting my ssid and wep key in my config file, but I didn't realize that the key i put in was missing a number. Haha.

Thankyou so much.

You saved me a huge headache, even though it still to me eight hours of trial and lots of error to get it to work.

Godd

---

