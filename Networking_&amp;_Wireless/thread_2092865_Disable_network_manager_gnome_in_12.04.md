---
title: "Disable network manager gnome in 12.04"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by chrisc200 on 2012-12-09
Need to disable gnome-network manager/network-manager to configure my interfaces manually, however doing the action below still results in it being enabled:

echo "manual" | sudo tee /etc/init/network-manager.override

or

sudo gedit /etc/NetworkManager/NetworkManager.conf

and changing managed to true.

How can I disable networkmanager without removing it?
thanks

---

### Post by ibjsb4 on 2012-12-09
look here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+network+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+network+manager&as_qdr=all&sa=Google+Search&lang=en)

---

