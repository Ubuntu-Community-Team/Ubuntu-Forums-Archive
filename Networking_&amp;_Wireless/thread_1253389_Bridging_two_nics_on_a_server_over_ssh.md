---
title: "Bridging two nics on a server over ssh"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by jms1989 on 2009-08-30
Hello, I am looking for a way to bridge to nics on my server to act as a strong firewall for a small 2-3 node network. The server's primary nic (eth1) is connected to a 8-port switch with 4 other computers attached that's also connected to our router that stands as the master firewall, dhcp server, and as a wireless access point. It uses WAP Personal encryption to provide  good protection. The second router uses a weaker encryption setup for tempory access for two Nintendo DSes and a laptop that doesn't like the wap encryption. Now the second router and switch are located in my room so i can just run a cable to the switch to bypass the wireless router for my laptop and unplug the router to improve the security of the lan.

Now, at the moment, the router is attached to the switch but I want to connect it to the server to block all incoming and outgoing ports but the ones I want open, mainly, http, shttp, ssh, nintendo's global trading center for pokemon games. Or, don't block the ports but to open up more ports on the switch and router for more devices. Or, simply provide a way to attach a virus infected pc to the network without infecting the healthy machines so I can fix the poor thing.

How can this be accomplished without loosing connectivity to the server from my workstation using ssh and webmin?

Basicly, I want to tunnel traffic through the two nics without interrupting access to its services.

---

### Post by dmizer on 2009-08-30
Why not use the ssh socks proxy and pipe everything through the socks proxy. Your ssh command would look something like this:
```
ssh -D 1080 user@server-ip
```
Then configure your client to use the socks proxy host of localhost and port 1080.

You now have encrypted access to the internet and CLI access to your server.

---

### Post by jms1989 on 2009-08-30
sounds good but that wouldn't work with the nintendo ds.

---

