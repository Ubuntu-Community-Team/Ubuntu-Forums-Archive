---
title: "Scan clients connected to the LAN"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by alessandro1997 on 2011-08-29
Hi guys,

I was wondering if there's a way to check which clients are connected to my LAN? I'd want to know their IP and hostname.

Any suggestions?

Thanks in advance.

Regards,
Alessandro Desantis

---

### Post by SeijiSensei on 2011-08-29
```

sudo apt-get install nmap
nmap -sP 192.168.1.0/24

```

That will ping all the addresses between 192.168.1.0 and 192.168.1.255 and give you a list of all the hosts it finds.  Whether the hostnames are returned depends on whether you have reverse-DNS resolution correctly configured on your network.

**nmap** is an incredibly powerful tool with a lot of scanning options.  Hell, even Trinity uses it in the second Matrix film.

If there are Windows clients on the network, you can use the "nmblookup" utility that comes with Samba to get hostnames.  "nmblookup -A 10.10.10.10" will return that host's "Netbios" name, the one that appears in a network search using Windows.

---

