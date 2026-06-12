---
title: "vpn creation in karmic?"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by bhart007 on 2009-11-12
Im running Astaro Home edition at home and I'm wanting to setup a vpn connection from my Karmic laptop.  however the only choice in the network-manager drop-down is Cisco compatible.. Am I missing something or is this another Karmic/NM issue?

---

### Post by bhart007 on 2009-11-13
bump

---

### Post by Kelvin Gardiner on 2009-11-13
First I think it's a bit unreasonable to expect a reply in 7 minutes. You may want to wait longer before bumping in the future.


From memory I think you need to install the pptp and pptp-networkmanager(-plugin), not sure of the second package name. These will all connection to MS VPNs.

---

### Post by bhart007 on 2009-11-13
I actually waited a day.. might wanna check post times before jumping to conclusions.

Thanks for the suggestion, I will look for those packages.  I had assumed that by default the VPN config included support for more than just Cisco endpoints.

---

### Post by Kelvin Gardiner on 2009-11-14
Sorry about the time thing. It post times had a 7 minute different before I posted, I'm sure. I see there is a day between posts.

I find this quite annoying that these packages aren't included by default. It one of those thing you need to do after every install.

You also need to select the point-to-point encryption box in the advanced options.

---

### Post by pmains on 2009-11-17
How is VPN working for you in Karmic? I'm still running Jaunty, and I've had difficulties establishing a PPTP VPN connection. Tutorials online ([http://ubuntuforums.org/showthread.php?t=1136020](http://ubuntuforums.org/showthread.php?t=1136020)) discuss editing all kinds of configuration files, but that hasn't worked for me so far.

Does Karmic have support pretty much "out of the box" once the appropriate packages are installed? If not, is Lucid Lynx scheduled to have PPTP working?

---

### Post by Kelvin Gardiner on 2009-11-17
VPN has worked for me in Juanty and Karmic "Out of the box" with after installing the pptp package (see above). In the thread you linked to, have you tried the method in [post 23]("http://ubuntuforums.org/showthread.php?t=1136020#23"). I've only every used the network manager applet to setup vpn connections.

---

### Post by pmains on 2009-11-17
My issue may have been putting the username and domain together in the username field. I don't recall if I've tried it the other way along with the EAP unselected, etc. Right now, I'm at work, and our network isn't configured to permit internal users to VPN into the internal network.

---

### Post by wantares on 2009-11-17
What is going on with this forum, Suirebit did you gave up?!
Common people

---

