---
title: "Internet connection sharing (DHCP server)"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-10-14
I set up DHCP using [this]("http://ubuntuguide.org/wiki/Ubuntu:Maverick#Internet_connection_sharing_.28DHCP_server.29") guide.

Can anyone advise me if this is possible without setting up the firewall? And for what exact purpose is the firewall required for setting up a DHCP server?

---

### Post by sikander3786 on 2010-10-14
Hi.

What is exactly the purpose of setting up a dhcp-server? Only to assign IP addresses or you also want to share internet connection?

Having a firewall enabled is always a good idea. It will limit all incoming/outgoing connections to the services and ports you allow.

On  that guide, I found instructions to install firestarter. But as far as I know, firestarter's development is stopped thus not a good idea to implement. Instead you should consider using UFW, the builtin Ubuntu firewall.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by Oxwivi on 2010-10-14
I'm using the DHCP server to share internet connection.

I'm just planning to share it with one other computer directly connecting through LAN, so I'd prefer not to put any firewall restrictions because it's gonna be used just by myself.

---

### Post by sikander3786 on 2010-10-14
Internet Connection Sharing is a job done by the firewall. You can either use UFW or Firestarter whatever you prefer. But you'll need a firewall setup definitely.

It will be fine to just follow the guide in your link posted above.

---

### Post by Oxwivi on 2010-10-14
Can you tell me how to configure the UFW firewall according to the instructions?

---

### Post by Iowan on 2010-10-14
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing... dunno if Meerkat has different requirements, though.

---

### Post by Oxwivi on 2010-10-15
Thanks! So much for the for the configuration of the guide I found. Iowan, you da man! :P

---

