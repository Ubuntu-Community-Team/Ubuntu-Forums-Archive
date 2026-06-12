---
title: "Connecting to VPN through terminal"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by nickpick on 2009-05-29
Is there any way to connect to a VPN, you've previously specified in nm-applet, though terminal?

What I want to do is to initiate a VPN connection automatically every time I'm connected to a specific network (but not to all). Browsing through the forums, I found that a script in /etc/network/if-up.d :

```

#!/bin/bash
if iwconfig|grep -c NETWORK_SSID
then                                                         
        Does_something_here
fi
```

would help. The only remaining question is how to initiate the said connection.

Thanks in advance.

EDIT: It's a Cisco VPN, using the package *network-manager-vpnc*.

---

