---
title: "VPNC on Ubuntu 12.04 Server"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by madods on 2013-08-29
I have vpnc installed on a Ubuntu 12.04 LTS (64 bit) server. This is to support client applications on the workstations behind the server which access data on servers accessed via the VPN connection.

The server with vpnc is the default route for the workstations.

The problem is that the first time the client application tries to retrieve data across the VPN connection the client application hangs.

If I kill the client application and perform _exactly_ the same process to access the data again, its retrieved straight away. The client can then continue to retrieve data until there is a break of some minutes, then the application hangs again.

This behaviour doesnt occur using either the 32 or 64 bit Cisco VPN client for windows on the workstation.

Can anyone suggest how I could go about debugging this?

---

