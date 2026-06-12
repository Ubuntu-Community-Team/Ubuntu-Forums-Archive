---
title: "How to revert to previous network manager?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by leftfootleashed on 2009-02-21
Hi,
In order to connect to my uni's network I need to use a VPN. This I achieved incredibly easily under Gutsy with Network Manager (version 0.6x I think) and network-manager-pptp, but now I am using Intrepid with Network Manager 0.7, it refuses to connect. I know other people with more Linux knowledge than me that haven't been able to make this work and so I think the only solution is to revert to a previous version of Network Manager (and possibly network-manager-pptp). Can anybody explain how I might go about doing that in Synaptic? I assume I need to add a repository for Gutsy and install the packages from that. I've tried installing v. 0.65 from the tarball on the GNOME download server, but got stuck with a dependency on wireless-tools that seems to be already filled.
Any help would be appreciated.
Thanks a lot,
Dave

---

### Post by Yashiro on 2009-02-21
Try using wicd instead before you roll back to an older nm-applet.

---

### Post by superprash2003 on 2009-02-21
hope this helps [http://www.prash-babu.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://www.prash-babu.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) till step 4

---

### Post by leftfootleashed on 2009-03-02
Thanks for your suggestions. I've looked into wicd, but it doesn't handle VPN connections yet. As an alternative I tried using kvpnc (which despite the name handles connections to Microsoft VPNs too) but had no luck - for some reason it fails to authenticate. Could anyone suggest how I can roll-back to a previous network manager?
Cheers,
Dave

---

### Post by Iowan on 2009-03-02
See if [this]("http://ubuntuforums.org/showpost.php?p=6623406&postcount=10") one helps.

---

