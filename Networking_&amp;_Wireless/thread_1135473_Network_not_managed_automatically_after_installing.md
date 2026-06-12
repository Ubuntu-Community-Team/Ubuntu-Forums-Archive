---
title: "Network not managed automatically after installing kwlan"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by charafantah on 2009-04-24
Hello, network wired and wireless was managed automatically by my 9.04 new installation, untill i decided to try out the following packages:
 kwlan plasmoid-wifi plasma-widget-wifi


now the network manager widget disappeared from my panel, i have to start network manually using ifup eth0 after adding eth0 entry in /etc/network/interfaces

i tried removing the 3 packages but nothing happened.

please advice, thanks :)

---

### Post by charafantah on 2009-04-24
i found out i needed to reinstall network-manager and network-manager-kde and plasmoid-widget-network-manager

now i have the plasmoid back, wifi working fine.

but the ethernet says: networking interface [not updated yet]  and that eth0 is unmanaged

i cannot find any configuration options to tell network manager to manage the interface automatically again :)


thanks

---

### Post by charafantah on 2009-04-24
well...just in case anyone has the same problem, i solved this by restoring /etc/network/interfaces to original state
removed all manual editing for eth0 that ive done

reboot and everything works fine (offcourse after installing network manager)

---

