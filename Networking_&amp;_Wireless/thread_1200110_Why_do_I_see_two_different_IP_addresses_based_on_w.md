---
title: "Why do I see two different IP addresses based on where I look"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2009-06-29
I am trying to set up an ssh to my home computer from travel and am finding it difficult.  Conky and ifconfig show me that my ip address in 192.xxx.x.x  However, gmail and the what is my ip website both show me that my ip address is 7x.xxx.1xx.3x I am behind one router.  Is there an explanation for this?  Which IP address should I use for my ssh/freenx system?

---

### Post by Iowan on 2009-06-29
The 192.168.x.x address is the local IP address (that's what **ifconfig** shows you).  The router has an external address (7x.xxx.1xx.3x) that the rest of the internet sees and probably an internal (192.168.x.1?) address that you can **ping** from your machine.  Which address you use for SSH  depends on which side of the router you are.  If you are remote, (Internet side of the router) youi would use the router address... and would need to port-forward (on the router) to the internal IP address.  Things get a bit more complicated when DHCP addresses come into play...

---

### Post by lykwydchykyn on 2009-06-29
The 192 address is your computer's IP.  That's what's known as a private IP (I'm betting the next number is "168").  Private IP's don't route over the Internet, so your router has a public IP that outside hosts (such as gmail or "whatsmyip") would see.  That'd be the 7x address.

To use ssh/nxserver from OUTSIDE your network, you'd need to give the router's IP (the one that starts with 7), but you'll also need to configure your router to forward ssh/nx traffic to your computer (the 192 address).

Be aware your router's IP is probably dynamically assigned by your ISP, and probably changes periodically.  Hence the need for a dynamic DNS service.

More information can be found here: [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

---

### Post by josephellengar on 2009-06-29
> **lykwydchykyn said:**
> The 192 address is your computer's IP.  That's what's known as a private IP (I'm betting the next number is "168").  Private IP's don't route over the Internet, so your router has a public IP that outside hosts (such as gmail or "whatsmyip") would see.  That'd be the 7x address.

To use ssh/nxserver from OUTSIDE your network, you'd need to give the router's IP (the one that starts with 7), but you'll also need to configure your router to forward ssh/nx traffic to your computer (the 192 address).

Be aware your router's IP is probably dynamically assigned by your ISP, and probably changes periodically.  Hence the need for a dynamic DNS service.

More information can be found here: [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

Thank you.

---

