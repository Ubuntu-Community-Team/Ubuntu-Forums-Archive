---
title: "Deluge BitTorrent client"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by lferg on 2013-01-18
I have read and read and done all I know to do to get Deluge BitTorrent client to work with a proxy.  I have done what I THINK needs to be done on my router, turned on UPnP. I haven't done anyhting in the way of port forwarding because my router (Netgear V2000V3) doesn't have a TCP option.  I don't know what  a DAEMON port is or if I should change it.  I am convinced it is just some command I have to run in Terminal to open some port I have no idea about?  This is a screen shot of my router hoping it will help.  I know ya'll will need to see some stuff in Terminal but I don't know what that will be.

---

### Post by helpee on 2013-01-18
Are you using a proxy and port forwarding, or just port forwarding? I assume you've also got firewalls on at every stage of your network.

If you are just using port forwarding, your network interface should just point at the address that gets you out to the internet. If you are using a proxy, point your network interface at that address.

You can edit these things in the /etc/networking/interfaces file

---

### Post by lferg on 2013-01-18
Are you using a proxy and port forwarding, or just port forwarding? [COLOR=Red] I am just using a proxy, my VPN [/COLOR]I assume you've also got firewalls on at every stage of your network. [COLOR=Red]Nope, no firewall at all. just default Ubuntu settings[/COLOR]

If you are just using port forwarding, your network interface should just point at the address that gets you out to the internet. If you are using a proxy, point your network interface at that address.  [COLOR=Red]How do I accomplish this?  Baby steps please[/COLOR].  :)

You can edit these things in the /etc/networking/interfaces file  I have attached a screenshot of my interface file.

---

### Post by helpee on 2013-01-19
Sorry, the easier way to do this is to go to System Settings>Network>Network Proxy, then select "Automatic" from the "Method" dropdown list and then enter your proxy's ip in the configuration box. Then hit "Apply System Wide". If your proxy server is setup correctly, that should do it.

---

