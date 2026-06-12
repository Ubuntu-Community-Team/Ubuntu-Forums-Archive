---
title: "Ubuntu 11.10 -&gt; Ubuntu 11.10 RDP failing"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by Goat Boy on 2011-12-21
Hello,

EDIT: As I'm not a network guy, the difference between RDP/VNC is lost on me.  Using the stock applications, I think VNC.

I am building an HTPC out of an old HP Workstation.  I don't intend to put any peripherals on it, and if I need to make changes I planned to login remotely using my laptop (Win7/Ubuntu) or Desktop (Win7).

I'm connecting through a Cisco DPC3825 WiFi gateway, which I know is complete garbage.  The firewall is definitely causing issues, so for the purposes of trying to solve this issue it is turned off while troubleshooting.  I'll get to it/replace it next.

Both machines are running Gnome, but otherwise basically setup as Ubuntu ships.  HTPC "Desktop sharing" is enabled, without needing to confirm access.

Go to the laptop and type local address, 192.168.0.XX, 'An error occurred, Connection to host 192.168.0.XX was closed.'

Try through my Android phone, 17X.X.4X.XX1:5900, connection times out.

Really not sure where else to go.  Can easily ping back and forth between machines in the terminal, but a network guy I am not.

Cheers.

---

### Post by Goat Boy on 2011-12-21
Samba share offers complete access both ways.

Every search comes up with;
"Uncheck 'only allow local access' in Remote Desktop settings" which no longer exists in 11.10.

---

