---
title: "How to find all hosts on LAN"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-11-16
Is there a way to get the IP and hostname of all clients on the LAN?

I've tried this command:
 nmap -sn 192.168.0.0/24

Which DOES locate the hosts but does NOT seem to report hostnames.

Here's an example of the scan:
```
 nmap -sn 192.168.0.0/24

Starting Nmap 5.21 ( http://nmap.org ) at 2012-11-16 17:14 EST
Nmap scan report for 192.168.0.1
Host is up (0.00015s latency).
MAC Address: 00:18:E7:DF:1A:53 (Cameo Communications)
Nmap scan report for 192.168.0.20
Host is up (0.022s latency).
MAC Address: 00:10:83:F2:03:89 (Hewlett-packard Company)
Nmap scan report for 192.168.0.44
Host is up (0.00018s latency).
MAC Address: 00:16:17:A6:16:37 (MSI)
Nmap scan report for homalinux (192.168.0.67)
Host is up (0.00013s latency).
MAC Address: 00:22:64:9A:FB:4A (Hewlett Packard)
Nmap scan report for 192.168.0.103
Host is up (0.00014s latency).
MAC Address: 00:23:7D:1B:BF:8D (Hewlett Packard)

```

Most of the hosts are Windows PC's.  

It seems nmap is reporting the OEM of the host's network adapter but not the hostname.

Is there a way to find the hostnames?

Thanks

---

### Post by AlexBooton on 2012-11-17
I found nbtscan.  

Works great!

---

### Post by bab1 on 2012-11-17
> **AlexBooton said:**
> I found nbtscan.  

Works great!

Those are NETBIOS names not hostnames.  You will not pick up devices that have hostnames and are not broadcasting NETBIOS names.  Only Samba commonly uses NETBIOS names on Linux hosts.

---

### Post by AlexBooton on 2012-11-17
Yes, my bad. I think of the netbios name in Windows a the equivalent of the hostname in Linux.

Sorry about the confusion.  But the bottom line is I got what I wanted.

---

