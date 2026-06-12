---
title: "VNC over WAN with Remmina"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by nobodyfamous on 2013-08-26
I am stuck - I can SSH into my MAC from Ubuntu, I can also use SSHFS and mount the drive.  I can use VNC on my LAN without a problem.  But when I try to do VNC over the WAN Remmina just hangs.

I have tried with my basic LAN settings, and replaced the local IP of the machine with the WAN IP and with the dyndns name I also have set up, neither work.

The only port I have forwarded in the router is port 22.  Like I said, SSH & SSHFS work fine over the WAN - but I cant get Remmina VNC to connect.

Do I need to forward additional ports?  I'd like to do it over SSH for what should be obvious reasons.

---

### Post by steeldriver on 2013-08-26
You *could* forward the VNC port, however for security imho it's better to tunnel the VNC over ssh - Remmina does all the hard work for you, if you go to the SSH tab and check the 'Enable SSH tunnel' and 'Tunnel via loopback address' and provide your SSH credentials in the boxes below (with many other clients it's necessary to set up the tunnel manually with a separate SSH command)

---

### Post by nobodyfamous on 2013-08-26
Wow, thanks a ton!!!  All I was missing was to check off the "Tunnel via loopback address" and it works.

---

