---
title: "Port forwarding assistance."
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by DatSik on 2012-12-26
Hello all, im trying to get optimum performance for transmission, but i cant seem to properly open my ports. Here are a couple screen shots
[IMG]http://imageshack.us/a/img845/8388/portl.png[/IMG]
[IMG]http://imageshack.us/a/img822/9281/belk.png[/IMG]

[B]Where it is labeled Lan ip address it only allows me to type in 3 character..so im a little lost on what goes there and im unsure if thats what is causing the problem. but im hoping someone will be able to tell me what im doing wrong.

P.S - It is a Belkin router

I appreciate any assistance/input[/B]

---

### Post by Cheesehead on 2012-12-26
'LAN IP Address' means the IP address of your server. The router is asking you which machine on the network to forward the port to.

For example, if your router is at 192.168.2.0
Your torrent machine is probably in the 192.168.2.* range. Or not, it depends upon how you set up the router.

To find the IP address of your torrent machine, you can look for the dhcp client table in the router, or you can use the commands [FONT="Courier New"]ifconfig[/FONT] or [FONT="Courier New"]ip address[/FONT] on the server.

Don't forget to make the connection the same IP every time (there are several ways to do that), or next time your torrent machine may get assigned a different IP...which will break the port forwarding.

Don't forget to check the firewall on your torrent machine, too. You may have the port blocked there.

---

### Post by DatSik on 2012-12-26
> **Cheesehead said:**
> 'LAN IP Address' means the IP address of your server. The router is asking you which machine on the network to forward the port to.

For example, if your router is at 192.168.2.0
Your torrent machine is probably in the 192.168.2.* range. Or not, it depends upon how you set up the router.

To find the IP address of your torrent machine, you can look for the dhcp client table in the router, or you can use the commands [FONT="Courier New"]ifconfig[/FONT] or [FONT="Courier New"]ip address[/FONT] on the server.

Don't forget to make the connection the same IP every time (there are several ways to do that), or next time your torrent machine may get assigned a different IP...which will break the port forwarding.

Don't forget to check the firewall on your torrent machine, too. You may have the port blocked there.

thanks cheese ill check that out, i appreciate your assistance

---

