---
title: "Alert possible when network manager looses VPN-connection?"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by js31 on 2010-11-12
Today I got aware that network manager (I guess after the DSL-router changed the IP) lost connection without notifying me. I'm wondering, is there a way over some config-setting to get an alert in this case, or block the network access completely if not established via VPN?

I'm not an advanced user, so depend on that the OpenVPN connection is provided by the program, for which the VPN service had an easy configuration tutorial. Of course, if not possible elsewise, I guess I'd have to check for alternatives.

Thanks in advance :)
Joerg

---

### Post by Cabalbl4 on 2010-11-12
Well, you can use nmcli tool for NetworkManager, and the given script for VPN auto-reconnect (from my VPN autoconnect tutorial [ _URL LINK_]("http://art.ubuntuforums.org/showthread.php?t=800330")), but instead of the following string in autoconnect script (post  #3) ```
nmcli VPNNAME start
``` use something like ```
 zenity --error --text='VPN DISCONNECTED'
```

I think this is the fastest way for the NM.

PS this requires NetworkManager and zenity to be installed.

---

### Post by js31 on 2010-11-12
That's something wonderful, thank you for the script! :cool:

---

### Post by Cabalbl4 on 2010-11-12
Mark the thread as SOLVED if it helps :)

---

