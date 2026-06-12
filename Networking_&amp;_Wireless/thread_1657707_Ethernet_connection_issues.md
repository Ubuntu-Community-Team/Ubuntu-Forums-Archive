---
title: "Ethernet connection issues"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by shuvra on 2011-01-01
Hi!

Happy New Year!

I have an IBM Thinkpad T60 (which I have been using since July 2006) and I have Ubuntu 9.04 installed on it.

I am right now visiting Calcutta on vacation and signed up for an ethernet connection and I need to configure stuff to be able to connect but unfortunately I have failed to do so.

My /etc/networks/interfaces looks like:
auto eth0
iface eth0 inet static
address 10.0.3.243
netmask 255.255.255.0
network 10.0.3.0
broadcast 10.0.3.255

and my /etc/resolv.conf file looks like:
nameserver 10.0.3.2
nameserver 4.2.2.3

After I restart my network with the command:
sudo /etc/init.d/networking restart

I am able to ping the network at 10.0.3.2 but when I click the network and choose the Auto eth0 (Wired Network) option, it returns the message "You are now disconnected".

Can you please help me?

Thanks a ton,
Shuvra.

---

### Post by PatchesTheCaveman on 2011-01-01
It's my understanding that if you configure your connection manually via the interfaces file you will need to remove NetworkManager for it to work correctly:
```
sudo apt-get remove network-manager
```

You can also configure your connection using NetworkManager, just right-click on your network icon, choose *Edit Connnections...*, and edit eth0 to your liking.

---

### Post by Iowan on 2011-01-01
Network Manager *should* let you set up a manual configuration. You can disable the "Connect automatically" for "Auto eth0" and turn it on for your manual configuration. *IF* it works, it'd be less effort to return to the other (original) configuration later...

You'll probably need to manually configure the gateway, and maybe DNS server.
[Here]("http://www.howtogeek.com/howto/19541/how-to-assign-a-static-ip-to-an-ubuntu-10.04-desktop-computer/") is a How-To for 10.04...
Oh, you'll need to comment out your changes to */etc/networks/interfaces *. If it doesn't work, you can un-comment the changes and remove NM...

---

