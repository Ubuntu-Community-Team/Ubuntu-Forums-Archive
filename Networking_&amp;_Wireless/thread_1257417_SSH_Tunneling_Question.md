---
title: "SSH Tunneling Question"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by jjt288 on 2009-09-03
Ok. I have a dedicated server set up in a datacenter running Ubuntu and at home I have a MacBook. Sometimes I create an SSH tunnel to my server and use it as a SOCKS proxy on my MacBook. I use this command:

ssh -D 8080 user@host

Then I can set up the SOCKS proxy with:

localhost : 8080

on my MacBook.

Here's my question: If my MacBook is at home connected to my server in this way, and I'm not at home, can I SSH into my MacBook from a third computer through my server? The reason is that my server always has the same IP, so if I leave my MacBook connected to it, I want to be able to access it through this tunnel, but in reverse, rather than set up port forwarding on my router and dynamic DNS.

Does that make sense? Is there an easy way to accomplish this?

Thanks in advance.
jjt

---

### Post by Brandon Williams on 2009-09-04
No, you won't be able to use the existing socks proxy in reverse that way. Ssh is only listening for incoming connections on the MacBook. However, you could run a proxy on the server and configure port-forwarding on your router/gateway to allow external access to the server. This would allow you to use your server as a proxy for connections to machines on your internal network. Even better, you can configure the router/gateway to allow external ssh connections to the server, and then use an ssh -D tunnel on the external client to get traffic to machines on your internal network.

---

### Post by i.r.id10t on 2009-09-04
You could forward a remote port (one on your server) to your macbook on the same ssh command - look at the -R option in the ssh man page.

---

