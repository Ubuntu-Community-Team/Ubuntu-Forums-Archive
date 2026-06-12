---
title: "dhcp3-server is not committing correct dns-address to win XP client"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Freestyler on 2010-10-15
Hi

I'm troubling setting up my dhcp3-server.

Although I've configured "option domain-name-servers 192.**168**.1.1" in my dhcpd.conf my windows-xp-clients dns-server address is set to 192.**186**.1.1.

This is strange! All other things seem to work correctly.

This is my dhcpd.conf:

```
ddns-updates on;
ddns-update-style interim;
update-static-leases on;
ignore client-updates;

default-lease-time 86400;
max-lease-time 86400;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
	range dynamic-bootp 192.168.1.31 192.168.1.60;
}

option domain-name "local.invalid";
option domain-name-servers 192.186.1.1;
option netbios-name-servers 192.168.1.1;

authoritative;

option routers 192.168.1.1;
```

I would appreciate if anyone can help me.

THX

---

### Post by sikander3786 on 2010-10-15
I see this line in dhcpd.conf

```
option domain-name-servers **192.186.1.1**;
```

;-)

---

### Post by Freestyler on 2010-10-15
Ooops! :oops:

I was checking out some things before and it seems I posted the dhcpd.conf with the wrong line.

Anyway, I corrected the line to ```
option domain-name-servers 192.168.1.1
```

The problem is still the same. I even tried some fantasy ip's like 192.145.13.45. On the winXP client the dns-server stays at 192.186.1.1

It is not reacting to any changes.

---

### Post by sikander3786 on 2010-10-15
A dumb question, probably 2. Did you clear the ip cache on Windows XP after those changes?

```
ipconfig /all flushdns
```

```
netsh interface ip delete arpcache
```

Also did you restart the server or reload the config?

```
sudo service dhcp3-server restart
```

```
sudo service dhcp3-server reload
```

---

