---
title: "ping works but apache does not"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by silentIm on 2009-07-29
hi all,

The title is what exactly I am facing. I don't know where to start, so I am asking gurus here to help me. 

I connect my laptop to an access point installed in my accomodation, and it got ip from dhcp from the router. I ping my laptop and it replies, but if I test apache from my windows box it times out.

I can access the internet from my linux laptop.

If I access from localhost it works.

I set up some localhost subdomain for my uni projects, so I edit /etc/hosts like this,

127.0.0.1 localhost
127.0.0.1 site1.localhost
127.0.0.1 site2.localhost
127.0.0.1 site3.localhost
127.0.1.1 mylaptop

#ip v-6 config is left default
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
fe00::0 ip6-mcastprefix
fe00::1 ip6-allnodes
fe00::2 ip6-allrouters
fe00::3 ip6-allhosts

---

### Post by superprash2003 on 2009-07-29
do you run firestart or anything similar running?

---

### Post by Iowan on 2009-07-29
I usually leave 127.0.0.1 as simply localhost, and use 127.0.1.1 for aliases... How (and from where) do you ping the laptop (which I presume has Apache)?  By name or IP address? How are you attempting to access Apache from the Windoes box? The "localhost" may have the Windows box looking for the site locally (on the Windows box).

---

### Post by dmizer on 2009-07-29
All of your hosts need to go on the same line like so:

```
127.0.0.1 localhost site1.localhost site2.localhost 127.0.0.1 site3.localhost
127.0.1.1 mylaptop

#ip v-6 config is left default
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
fe00::0 ip6-mcastprefix
fe00::1 ip6-allnodes
fe00::2 ip6-allrouters
fe00::3 ip6-allhosts
```

Also, unless you have a properly updated local DNS server, you'll also have to edit the hosts file in Windows so it points to the LAN IP of your Apache server. %SystemRoot%\system32\drivers\etc\hosts

---

