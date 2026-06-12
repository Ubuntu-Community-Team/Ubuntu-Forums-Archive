---
title: "How can I come up with DHCP server in Ubuntu?"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by musema on 2013-04-10
Hi,I am told to come up with a DHCP server in Ubuntu,and configure some users to share files using the same server? All Ideas are welcome.

---

### Post by papibe on 2013-04-10
Hi musema. Welcome to the forums ):P

> **musema said:**
> a DHCP server in Ubuntu
> **musema said:**
> configure some users to share files using the same server
Both possible, but note that they are necessarily dependent on each other .

To set up a DHCP server you have 2 alternatives:
[LIST]
[*][Dnsmasq]("https://help.ubuntu.com/community/Dnsmasq"), and 
[*][dhcp-server]("https://help.ubuntu.com/community/dhcp3-server")
[/LIST]
To share files and directories between users there are also several alternatives. If they are all using Linux I would recommend [NFS]("https://help.ubuntu.com/12.04/serverguide/network-file-system.html"), If there a Windows in the mix you may use [samba]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html").

Hope it help. Let us know how it goes.
Regards.

---

### Post by Iowan on 2013-04-11
> **musema said:**
> Hi,I am told to come up with a DHCP server in Ubuntu,and configure some users to share files using the same server? All Ideas are welcome.Told by whom?

The [serverguide]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") should provide some useful information. This link is for the 12.10 version - there are others available.

---

