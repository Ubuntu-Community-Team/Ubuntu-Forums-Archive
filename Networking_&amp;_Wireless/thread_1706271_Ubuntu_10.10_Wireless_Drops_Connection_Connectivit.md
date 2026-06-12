---
title: "Ubuntu 10.10 Wireless Drops Connection Connectivity Issue Disconnecting"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by halis on 2011-03-13
I had an issue after installing Ubuntu 10.10. I connected to a wireless router (2Wire for AT&T DSL). The router would connect fine at startup, but several minutes later the connection would drop and was unable to reconnect. After rebooting I was able to connect again, with the same problem again, dropped connection.

Here's how I fixed it. First, I found my router IP Address, go to a shell and type 'route -n' and the router is the one with the 'UG' flag (G for gateway). The IP for my version of the 2Wire was 192.168.1.254. 

After going into my router setup in the browser ([http://192.168.1.254](http://192.168.1.254)), I went to settings and typed in the password that I created when I setup the router. Then I changed the password from WEP to WPA2 personal.

Then I changed the connection settings on my Linux and my Windows computers to WPA2 personal and re-typed the 10-digit encryption key. Now I don't have connectivity issues.

---

