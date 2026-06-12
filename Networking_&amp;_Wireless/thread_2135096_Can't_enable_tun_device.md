---
title: "Can't enable tun device"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by prismctg on 2013-04-13
I m following ubuntu server guide for openvpn . i have done everything on my server side .For client side , i m using ubuntu 12.10 desktop ; I can't find tun device in my os ```

$ ifconfig tun0
tun0: error fetching interface information: Device not found


```... what should i do ?

---

### Post by prismctg on 2013-04-14
no reply from anyone  :(

---

### Post by The Cog on 2013-04-14
ifconfig is for configuring existing tunnels. You have to create a tunnel before you can configure it.
Depending on what you want the tunnel for, you might find this reference useful
[http://www.techonia.com/1400/create-tunnel-interface-linux](http://www.techonia.com/1400/create-tunnel-interface-linux)
If not, please post more details on why you want a tunnel interface, how it is to be used etc.
Some applications such as openvpn will create a tunnel interface themselves when configured to do so.

---

