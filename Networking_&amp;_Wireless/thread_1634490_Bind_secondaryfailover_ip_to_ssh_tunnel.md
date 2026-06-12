---
title: "Bind secondary/failover ip to ssh tunnel"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by composites on 2010-11-30
My friend has a server with 2 ips, 1 primary and 1 secondary/failover. He has given me a shell account and I want to use ssh to route my home http traffic through it like a socks proxy. I connect to his server using the secondary ip like this:

ssh me@secondary_ip -p port -D forwarding_port

It builds a proxy, however it uses the primary ip of the server, not the secondary ip that I logged in with. When using irssi I've bound it to the secondary ip with no problem. If I try to use the -b flag I get the error: cannot bind: Cannot assign requested address.

Any ideas how I can bind the ssh tunnel to the secondary ip?

---

### Post by TSJason on 2010-11-30
Is the "secondary" ip on the same interface as the primary? Any more info on the configuration would be helpful.

---

### Post by composites on 2010-12-01
I think the secondary ip is on a separate interface (eth0:1)

If the contents of /etc/network/interfaces would help let me know. I'm still new to ubuntu/debian/linux..

---

### Post by TSJason on 2010-12-01
I'm guessing that the primary IP is on 'eth0' which is the same device as eth0:1 (that :1 indicates it is just an alias). Assuming the IP's both route through the same gateway then you may be able to just include the IP in your bind address definition. Maybe:

```
ssh me@secondary_ip -p port -D bind_address:forwarding_port
```

---

### Post by composites on 2010-12-01
Thank you for the reply.

> **TSJason said:**
> I'm guessing that the primary IP is on 'eth0' which is the same device as eth0:1 (that :1 indicates it is just an alias). Assuming the IP's both route through the same gateway then you may be able to just include the IP in your bind address definition. 

Yes the primary_ip is on eth0 and both ips use the same gateway. Here's what /etc/network/interfaces looks like (where x.x.x. are the first three octets of the primary_ip):

> **interfaces]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address primary_ip
        netmask 255.255.255.0
        network x.x.x.0
        broadcast x.x.x.255
        gateway x.x.x.254

auto eth0:1
iface eth0:1 inet static
         address secondary_ip
         netmask 255.255.255.0[/QUOTE]

[QUOTE=TSJason said:**
> Maybe:

```
ssh me@secondary_ip -p port -D bind_address:forwarding_port
```

That yields the error: 
"bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: forwarding_port
Could not request local forwarding."

Which is similar to the error when trying to use the -b flag to bind to the secondary_ip:

```
ssh -b secondary_ip me@secondary_ip -p port -D forwarding_port
```

"bind: secondary_ip: Cannot assign requested address
ssh: connect to host secondary_ip port port: Cannot assign requested address"

---

### Post by composites on 2010-12-07
Think I'll just set up a socks server.

---

