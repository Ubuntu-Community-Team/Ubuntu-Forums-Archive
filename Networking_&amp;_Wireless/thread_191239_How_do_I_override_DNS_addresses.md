---
title: "How do I override DNS addresses"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by gmc on 2006-06-07
Hi Folks,

   I'm wondering if anyone can tell me how to get NetworkManager/DHCP to ignore the DNS addresses issued by my router. I have tried editing /etc/dhcp/dhclient.conf and removed the "domain-name-servers" so it reads:

```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;

```

and added the DNS servers that I want to use in /etc/resolv.conf. Unfortunately, when NetworkManager/DHCP negotiate the wireless connection, NM reports the DNS addresses that have beed issued from my router, not the ones I want to use from my resolv.conf.

Gord

Edited: Dopey me! I found the solution Basically I needed to add supersede/prepend options in /etc/dhcp/dhclient.conf

```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **domain-name-servers**, host-name,
        netbios-name-servers, netbios-scope;
[B]supersede domain-name-servers #.#.#.#;
prepend   domain-name-servers #.#.#.#;[/B]

```

Thanks for reading, Gord.

---

### Post by Iowan on 2006-06-07
Thanks for posting your results - I may need them later.

---

### Post by saus on 2006-06-08
Thanks a lot for posting this solution. I really needed that.
The internal dns in our linksys wireless router at work makes dns lookups hang for 10-30 seconds, but if I use or network supplier's dns servers, it works ok.

At home, however, it works great with the dhcp supplied dns server, and not so great with my office's network supplier's dns servers, as I'm not on their net.

Any idea how to override the dns setting only when I connect to this particular wireless router? :confused:

As of now, I have two different /etc/dhcp/dhclient.conf files, and have to manually switch between them. Is it possible to add a script to the /etc/dhcp3/dhclient-enter-hooks.d/ directory to handle this instead? I suppose I could modify the /etc/dhcp3/dhclient-script as well, but a hook would be a better solution in my eyes.

---

### Post by gmc on 2006-06-08
[QUOTE=saus]Thanks a lot for posting this solution. I really needed that.
The internal dns in our linksys wireless router at work makes dns lookups hang for 10-30 seconds, but if I use or network supplier's dns servers, it works ok.

At home, however, it works great with the dhcp supplied dns server, and not so great with my office's network supplier's dns servers, as I'm not on their net.

Any idea how to override the dns setting only when I connect to this particular wireless router? :confused:

As of now, I have two different /etc/dhcp/dhclient.conf files, and have to manually switch between them. Is it possible to add a script to the /etc/dhcp3/dhclient-enter-hooks.d/ directory to handle this instead? I suppose I could modify the /etc/dhcp3/dhclient-script as well, but a hook would be a better solution in my eyes.[/QUOTE]

I scanned over the documentation for dhclient but I don't see anything that would allow you to set the DNS addresses for one connection and allow the DHCP server to set the DNS server for the other. I'm sure there's probably a way to do it and I have a feeling the problem could be solved using the MAC address on the router(s) to determine when to set or not set the DNS.

Sorry I wasn't able to help. If anyone else can help, please do.

Gord

---

### Post by sandpaperback on 2006-06-19
> **gmc]
Edited: Dopey me! I found the solution Basically I needed to add supersede/prepend options in /etc/dhcp/dhclient.conf

```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **domain-name-servers**, host-name,
        netbios-name-servers, netbios-scope said:**
> supersede domain-name-servers #.#.#.#;
prepend   domain-name-servers #.#.#.#;[/B]

```

Thanks for reading, Gord.

This sounds like the same problem I'm having.  To make my internet work properly, I have to go into Networking every time I reboot and delete the entry for my router under DNS.

So, in the above file, does the router IP go in the "supersede" and the working IP go into the prepend?

---

