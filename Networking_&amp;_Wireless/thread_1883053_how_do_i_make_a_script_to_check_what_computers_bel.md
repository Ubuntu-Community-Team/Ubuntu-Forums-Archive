---
title: "how do i make a script to check what computers belong to what Ip"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by jewfromdahood on 2011-11-18
I want to make a script that automatically runs on the Linux server say once an hour that references the IP address to the computer name or Mac address, and throws it in a log. As we have many computers and for some reason the Winblows IT person keeps screwing up the static IPs for our X-rays and such. 
and double addresses an IP to a device.

---

### Post by SeijiSensei on 2011-11-18
Does your network have a DNS server already set up with reverse resolution from IP addresses to names?  If so, the quickest solution is to use nmap:

```
nmap -sP 192.168.1.0/24
```

will ping each address in the 192.168.1.0/24 subnet and report which ones are up.  It will resolve each host's name if that is possible and display its MAC address.

Might I suggest a simple organizational solution to the problem you describe?  Either designate a set of addresses within your subnet for devices like x-rays, or put them in a separate subnet with appropriate routing configured on your router.  For instance, you could designate 192.168.1.0/24 as the subnet for desktop clients and 192.168.2.0/24 as the subnet for servers and other devices.

---

