---
title: "Configuring a wlan0 VPN connection"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by the silent 1 on 2011-02-20
I'm trying to setup a VPN connection through my laptop that is connected through a wireless router.  I would like to configure the VPN as so I can connect to my network/computer file system from another network.  I guess you could say I'm somewhat new to Linux, although I've had experience with Fedora/RedHat and Ubuntu through my University.  Also, I've created a distro of my own which didn't seem to be that difficult, but we havn't touched much on the subject of VPN's.  Bumping this thread is fine, although I will still need the help with host/client configuration.
 
Any help is appreciated, thank you Ubuntu community.

---

### Post by kn0w-b1nary on 2011-02-20
have you tried hamachi?

---

### Post by the silent 1 on 2011-02-20
I was trying to configure OpenVPN, if Hamachi has secure connections maybe that could be the easier choice?  Also, would I have to configure .config files to adapt a bridged connection, or is it as simple as a host name/ip address and password?

---

### Post by YesWeCan on 2011-02-20
I use a couple of OpenVPN tunnels, both tun and tap, for remote access to a server across the internet. Top quality software and bullet-proof connections.

What would you like to know?

---

### Post by the silent 1 on 2011-02-20
I was just trying to setup a simple, secure (if it can be simple) one client wlan0 VPN connection so I can access my network and/or computer file system from a distant location.  Basically, I would like to access music files (and others of course) on my personal system and be able to playback on another system not connected to my local network.  I imagine a VPN+File Server could take care of this?  Thank you for any help, and quick responses.

---

### Post by kn0w-b1nary on 2011-02-20
I don't use hamachi, but I have a friend who does. Check this link out: [https://secure.logmein.com/US/products/hamachi2/features.aspx](https://secure.logmein.com/US/products/hamachi2/features.aspx)

---

### Post by YesWeCan on 2011-02-20
It can be very simple. :)

Just install openVPN from the Ubuntu Software Centre. Then try this simple example: [http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html)
You have a very simple text file on the server and one on the client, and a shared static key file. That's it.

I don't know what you know about VPN. There is a point-to-point tunnel, called tun, which basically gives your remote server an IP address on your client. It is as if your client is connected by a separate NIC and an invisible ethernet cable to your server, except it is encrypted. So you access your files in exactly the same ways you would with a direct connection. There is no need for bridges unless you want other PCs to join in or unless you want to use Windows clients.

Once you get the simple example working you can move on to more sophisticated stuff.

---

### Post by YesWeCan on 2011-02-20
Just to add you will need to configure some ports in your router and server firewall too. Best to get it working with client and server on the same network first. This will be the case whichever type of VPN software you choose.

---

### Post by the silent 1 on 2011-02-20
Thank you very much for the quick response, I've looked at the site a little, unfortunately I have to run.  I will start on this tomorrow morning and post progress I have made, thanks again :)

---

