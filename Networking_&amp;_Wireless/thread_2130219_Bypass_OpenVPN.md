---
title: "Bypass OpenVPN"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by SASDOE2 on 2013-03-19
BUMP ! i have the same problem, only i don't have the answer. Would appreciate if someone (if not author) could explain what he/she did ? Thanks !

---

### Post by eldaria on 2013-03-19
Well my solution was not pretty.
Basically I opted to upgrade my VPN to 30mbit, that satisfied most of my needs.
But for certain services I simply added their IP range as a separate route, and set the gateway of that route to use my home router, this way the traffic to those services use my main Internet connection, and all other traffic use the VPN.

---

### Post by SASDOE2 on 2013-03-19
so there would be no way for my server to be accessible to all queries made at xxx.dyndns.com ? Can't apache listen specifically to the non-vpn ip ?

---

### Post by eldaria on 2013-03-19
Well, the VPN connection is only grabbing outbound traffic by setting itself as the default route.
Unless you specify Apache to only listen to the VPN interface, it should also server traffic coming in on other interfaces.

If you do not want Apache to listen on the VPN, then you need to specify what interface it should listen to, I think by default it listens to all.

I should not that I no longer run a webserver, nor do I have the VPN anymore. I do still have my server, but it is only used for outbound traffic, so I have no need for the VPN anymore.

---

### Post by SeijiSensei on 2013-03-19
You can specify which interface a virtual server binds to in the <VirtualHost> directive.

```

NameVirtualHost   10.10.10.10:80

<VirtualHost 10.10.10.10:80>
    ServerName ...
</VirtualHost>

```

---

### Post by SASDOE2 on 2013-03-28
> **SeijiSensei said:**
> You can specify which interface a virtual server binds to in the <VirtualHost> directive.

```

NameVirtualHost   10.10.10.10:80

<VirtualHost 10.10.10.10:80>
    ServerName ...
</VirtualHost>

```

Sorry but I don't understand what you mean by that. 

What I've understood so far, and i am sure to be wrong so please correct me, is I could create a "virtual interface" connected straight to internet, and have an another one, I suppose default eth0 that would be connected to the vpn, and map apache to the new virtual interface, thus bypassing the vpn.

How could I do that ?

[QUOTE=eldaria][]("http://ubuntuforums.org/member.php?u=51813")Well, the VPN connection is only grabbing outbound traffic by setting itself as the default route.
Unless you specify Apache to only listen to the VPN interface, it should also server traffic coming in on other interfaces.[/QUOTE]

Only when I am connected to the VPN I cannot connect to my server. Maybe this is due to the VPN's falt, but going having my hostname point to the vpn's address isn't really an option as I would be seriously damaging connection times to the webserver.

---

### Post by wildmanne39 on 2013-03-28
Moved to own thread! Please do not post in a thread that has been a year or so without a reply.
Thanks

---

