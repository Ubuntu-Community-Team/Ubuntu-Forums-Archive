---
title: "I can't add a IPsec tunnel using Network Manager"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by kgust on 2011-11-02
Is anyone else seeing this?

I am trying to add a IPsec VPN connection using Network Manager.

When I attempt to add it I can get to the "Choose a VPN Connection Type" and I choose "IPsec/IKEv2 (strongswan)" from the dropdown.  However, when I click "Create..." it hangs.

For the hardcore techies, I've attached a text file containing the errors I see on the console when I click "Create...".

---

### Post by darkway on 2011-11-03
i have the same problem, i try to reinstall network manager, gnome applet, strongswan plugin but the result is the same... i use xubuntu how can you read the log that you have posted? thank you (sorry for my English)

---

### Post by darkway on 2011-11-03
perhaps i resolve it!
the strongswan plugin is not compile with support for gtk3 so i recompile from source and it start!
you find a guide [here]("http://wiki.strongswan.org/projects/strongswan/wiki/NetworkManager")
you must install some libraries (as explained in the guide, and install  libnm-glib-vpn-dev library) and recopile and install only network manager plugin!

---

