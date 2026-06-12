---
title: "Static ip creation problems"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by hiddeninfluence on 2013-04-14
I have been trying to assign my computer static IP address, as I want to perform network traffic monitoring. 

I have used the the standard "[I]sudo nano /etc/network/interfaces"
[/I]
assigned my 

auto eth0
iface eth0 inet static
Address
Netmask
Broadcast
Dns-nameserver

Reset the connection, didnt connect. What am I doing wrong?

---

### Post by steeldriver on 2013-04-14
What version? what flavor? how did you reset the connection?

Current Desktop versions of Ubuntu use network-manager, you should really use the nm-applet GUI to edit the connection and set the static IP there (it's in the IPv4 settings - change the drop down from DHCP to Manual and enter the IP details)

Anything you specify in /etc/network/interfaces won't take effect until you restart the older networking service (or reboot) - it's OK to do that if you really want to, however if network-manager is still installed / running it can make things unnecessarily complicated imho

---

### Post by Iowan on 2013-04-14
You *should* be able to assign a static address via Network Manager.

Oops - out-typed!

---

### Post by hiddeninfluence on 2013-04-14
I am running Ubuntu 12.10 desktop, I reset the connection using "*Sudo ifconfig eth0 down, **Sudo ifconfig eth0 up"* I dont know about network manager, from what you have described I can do that in network settings. Is this what you are on about?

---

### Post by Iowan on 2013-04-14
The one I use is in the top bar towards the right side. It is an up/down arrow icon in 12.04.
Network Connections looks like the same tool...

---

### Post by hiddeninfluence on 2013-04-14
That's it brilliant, should it update the */etc/network/interfaces *&#8203;file after I have done this?

---

### Post by steeldriver on 2013-04-14
you will need to go back and manually revert any changes you made to /etc/network/interfaces (i.e. so it contains only the lo / loopback definition)

---

### Post by hiddeninfluence on 2013-04-14
thank you very much :)

---

### Post by Iowan on 2013-04-14
Network Manager keeps it's own settings (I don't remember where). It *shouldn't* modify */etc/network/interfaces*

---

