---
title: "IPTables Startup for NetworkManager Lucid"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by impresionist on 2010-08-03
Hello all,
I'm setting my dedicate server under Lucid server, and i followed this tutorial [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) to configure IPTables.

In the startup configuration section, the tutorial advice that for users after Feisty, should jump to Solution #2 /etc/network/if-pre-up.d and ../if-post-down.d.

SO, I:
-Create the script into /etc/network/if-pre-up.d/iptablesload
-also modified the contain in /etc/network/if-post-down.d/iptablessave
-I changed their chmod

BUT to configure the Startup for NetworkManager the tutorial send me back to edit /etc/NetworkManager/dispatcher.d/01firewall, which is seem an error, or dosen't exist such as directory in lucid.

I looked for it, in ./etc/ I have only /network/if-pre-up.d, but it's no more directories in, so should I create a dispatcher.d their?

thanks for help,

Chears,

---

### Post by Nostalos on 2010-08-03
Unless you have the need for complex NAT'ing, i would recommend skipping manual iptable configs and just use ufw.

"sudo ufw enable" turns it on with auto boot start including network manager

"sudo ufw disable" turns it off

"sudo ufw allow from 192.168.254.254"  should be self explanitory as well

[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

oh and there is "gufw"  if you want a GUI

---

