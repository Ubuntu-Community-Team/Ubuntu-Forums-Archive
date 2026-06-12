---
title: "use Tor under university lan (proxy server)"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by edajai on 2009-10-27
I wanted to use Tor to browse anonymously but Tor doesn't seem to use the default http_proxy. We usually have to use a proxy server in out lan in order to get internet access.
Is der anyway tht i can redirect tor to use the proxy settings?

---

### Post by scragar on 2009-10-27
I don't believe you can, since tor itself is a proxy. You could try a free tor redirection service itself such as tor2web, see if those offer what you are after.

---

### Post by edajai on 2009-10-27
i don't know if u understood my problem. Tor software (or any other for that matter) cant connect to the internet unless it uses our proxy server (in the LAN). So once i redirect my Firefox to use tor, all connections are routed to tor, which cant access the online tor-servers since it itself cant connect (as it is trying to connect to the internet directly).

So is there any config file wherein i could alter some settings to enable the same?

---

