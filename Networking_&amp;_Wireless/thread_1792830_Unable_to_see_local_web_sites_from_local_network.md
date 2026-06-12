---
title: "Unable to see local web sites from local network"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by jorgecachoh on 2011-06-28
Hi all,

I have installed a web server on my local network. Everything is well configured and web pages are shown correctly from Internet (outside the local network) using the domain or the public IP.

The issue is if I try to see that web pages (using the domain or the public IP) from inside the local network. In that case the router config page (192.168.1.1) is shown instead of the web pages.

From inside the local network I'm only able to see the web pages using the internal IP address (192.168.1.XX).

Does anyone know how I can fix this issue?

THANKS!

          Jorge

---

### Post by Dangertux on 2011-06-28
> **jorgecachoh said:**
> Hi all,

I have installed a web server on my local network. Everything is well configured and web pages are shown correctly from Internet (outside the local network) using the domain or the public IP.

The issue is if I try to see that web pages (using the domain or the public IP) from inside the local network. In that case the router config page (192.168.1.1) is shown instead of the web pages.

From inside the local network I'm only able to see the web pages using the internal IP address (192.168.1.XX).

Does anyone know how I can fix this issue?

THANKS!

          Jorge

This is normal and part of the magic of network address translation. 

If you want to cheat it a little bit you can add an entry in your /etc/hosts file something like this

website.com         192.168.1.x(IP of server)


This won't actually make it go through the external IP address, but it will at least allow you to type the domain in your browser.

make sure to do sudo /etc/init.d/networking restart after you add the entry

---

### Post by jorgecachoh on 2011-06-29
Thanks Dangertux!!

---

