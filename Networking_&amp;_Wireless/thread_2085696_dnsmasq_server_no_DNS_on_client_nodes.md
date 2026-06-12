---
title: "dnsmasq server no DNS on client nodes"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by m47h3us on 2012-11-18
I've got a problem with dnsmasq on my server everything but dns works on it, it currently gives out dhcp fine and points to the router etc however when i go to a website it wont find it, the dns is pointed to the server on the client machines.  i will post some of my configs to see if it helps.

dnsmasq.conf
```

#Dns & dhcp config
no-hosts
#except-interface=lo
interface=eth0
local=/localnet/
listen-address=127.0.0.1
dhcp-range=192.168.1.50,192.168.1.150,12h
dhcp-option=3,192.168.1.254
server=/localnet/192.168.1.2
resolv-file=/etc/nameservers.conf

#PXE Boot
dhcp-boot=pxelinux.0
enable-tftp
tftp-root=/pxe

#Fixed Ip
dhcp-host=XX:XX:XX:XX:XX:XX,192.168.1.5

```

Dig on the server
```
 dig ubuntu.com

; <<>> DiG 9.8.1-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 5231
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.                    IN      A

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Nov 19 01:07:09 2012
;; MSG SIZE  rcvd: 28


```

NSlook up on server

```

nslookup ubuntu.com
Server:         127.0.0.1
Address:        127.0.0.1#53

** server can't find ubuntu.com: REFUSED


```

ask for anything else that might be needed.

---

### Post by m47h3us on 2012-11-19
I'm i missing a program or conf?

---

### Post by m47h3us on 2012-11-22
Dump

---

