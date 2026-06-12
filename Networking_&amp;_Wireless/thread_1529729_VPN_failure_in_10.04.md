---
title: "VPN failure in 10.04"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by RabbyC on 2010-07-12
Firstly I would like to say that despite this issue I still use and recommend ubuntu for everyday stuff but...

I have had a really frustrating problem with connecting to VPN. I have tested it in windows and confirmed that the problem does not lay in the firewall and is just in ubuntu.

Simply what happens is I can connect, or rather network manager tells me im connected. If I leave it for approx 30 seconds it will fail.
If I open terminal services client it will allow me to connect to the server and even get passed the login screen but will just simply fail and the TSC program will crash.

below are a list of forums and fixes I have attempted. I am beginning to think that the open VPN program supplied with ubuntu is completely inadiquate (based on the number of other people with problems) and I cannot see why ubuntu comes shipped with it on CD when it clearly undermines the good work they have done to produce the rest of the OS.

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)
[http://ubuntuforums.org/showthread.php?t=1506254&highlight=VPN+failed](http://ubuntuforums.org/showthread.php?t=1506254&highlight=VPN+failed)
[http://ubuntuforums.org/showthread.php?t=1476312](http://ubuntuforums.org/showthread.php?t=1476312)
[http://ubuntuforums.org/showthread.php?t=1502910&highlight=VPN+failed](http://ubuntuforums.org/showthread.php?t=1502910&highlight=VPN+failed)
[http://ubuntuforums.org/showthread.php?t=1476312&highlight=VPN+failed](http://ubuntuforums.org/showthread.php?t=1476312&highlight=VPN+failed)

Anyway, I have tried using MPPE, refuse-eap = yes

I have tried changing EVERY single option available in the VPN properties and restarting the network after each one.

I am stuck.

As an alternative are there any other network managers available for ubuntu 10 that anyone can recommend to avoid using the standard one?

---

### Post by RabbyC on 2010-07-12
not to worry I have installed openVPN and it seems to be working.

---

