---
title: "Ubuntu Server Basic Networking"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by minigilani on 2012-05-17
Hey

I need advice, and i feel incredibly stupid right now. How do i make the **/etc/resolv.conf** on my 12.04 Server to stay the way i edit it! It's driving me crazy. I googled, but coudn't find a helpful answer on how to use **resolvconf**. I need to keep the nameservers persistently pointing to Google DNS. Did the mention, someone wrote the manpage for **resolveconf** in an obscure English dialect!

Also for some reason, my Ubuntu Desktop can't resolve the server's hostname (greg-the-butler).

```

amingilani@awesome:~$ ssh greg-the-butler
ssh: Could not resolve hostname greg-the-butler: Name or service not known
amingilani@awesome:~$ STFU AND RESOLVE!
STFU: command not found

```

If you need more details, here's my setup: wifi router (we shall call it Wiffles) is behind my ADSL modem (which we shall Diffles). My Ubuntu Server (let's call it greg-the-butler...get it? "greg-the-butler" is the *server*) is behind Wiffy, along with the rest of my pc's.. what's a domain? Ok, sorry, i'll go sleep it off now. Hahaha, i have a Financial Management quiz tomorrow, and i decided to study after i'd set up my headless box. Please, help, i don't want to have to drag the monitor over to the box everytime it starts. It isn't headless that way.

---

### Post by lukeiamyourfather on 2012-05-17
Routers typically have a DNS. It might be configured improperly or disabled. With a properly functioning DNS everything should work as you expect it to (type in the hostname and it works). If the router doesn't have a DNS you'd have to add each IP address and each hostname to the hosts file which is /etc/hosts. Using the hosts file method would require each computer to have a static IP address.

---

