---
title: "kubuntu 11.10 and the static ip address issue"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by fahd on 2011-10-17
Hi folks there...
Really i do not know what is the reason of omitting the lines within the resolv.conf file. Since i configed out my work machine as a static ip address computer, i edited the following lines in the resolv.conf as the next:

domain my.domain
search my.domain
nameserver 1.2.3.4

Everytime i start up my computer the the above mentioned lines are being automatically omitted. Thus the system can not solve the URLs. So if you use kubuntu on a dynamic configued machine it becomes perfect. Just try to give it a static ip address, weird things would happen, NO name resolution would be the result. It seems it is a bug in knetworkmanager. Thanks a lot.

Fahd
111017

---

### Post by Bobonov on 2011-10-17
I do not know if by "...i configed out my work machine as a static ip address computer" you mean you configured a static ip by desktop network manager or by /etc/network/interfaces


anyway, if you assign all network parameters from /etc/network/interfaces (ip, netmask, gateway, dns) the network card will go in "managed mode".
pro
the lan connection will be avail since network activation
cons
you can't configure this network card's connection from your desktop using the network manager

If you allow you desktop network manager to configure the connection
pro
you can modify the connection form your desktop and you can easily configure and switch between different profile for the same card.
con
you network connection will not be avail until you login and the desktop is loaded.


If you set up only the resolv.conf file it will be overwrite by the desktop network manager at desktop loading

---

### Post by SeijiSensei on 2011-10-17
On my Kubuntu 10.10 machine, both the wired and wireless network configuration dialogs include a "search domains" entry.  Did you put "my.domain" in that list?

---

