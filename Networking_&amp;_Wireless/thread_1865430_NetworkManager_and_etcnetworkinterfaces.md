---
title: "NetworkManager and /etc/network/interfaces"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2011-10-20
Hello !
I use a laptop with a wifi card to connect to my network at home.
My home directory is stored on a server, so I need the network connection to be up and running in order to log in (the home directory gets mounted using autofs).
So I've configured the Wifi network to be set up at boot time using /etc/network/interface.
This worked perfectly for a very long time. Since a few days, NetworkManager messes around the network setup trying to configure the already configured network card and making it unusable.
I'm unable to tell NetwokManager to forget about the Intel 5100 wifi card, so I beg for your help ! (for now I've uninstalled NetworkManager, but this is not a good solution as I someties use the laptop outside home...)
Thanks a lot in advance for your help.
Context : Gnome desktop on Ubuntu 10.04.3 LTS Intel 5100 AGN Wifi card.

---

