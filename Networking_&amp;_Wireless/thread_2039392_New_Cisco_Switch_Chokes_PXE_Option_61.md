---
title: "New Cisco Switch Chokes PXE Option 61"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by LydaRA on 2012-08-08
My school had an Ubuntu 10.04 LTSP cluster which was PXE booting thin clients ok.  

Then we changed to new Cisco switching gear...  
   The initial DHCP works and the TFTP pulls the boot image.
   The image then appears to make another DHCP request--with an option 61 and a zero length payload--which Cisco then drops!!!  Client stalls...  :-(

The Cisco VAR says the switches have DHCPsnooping turned off.  But it appears the Cisco iphelper is doing it anyway.  If we put the thin client in the same VLAN as the DHCP server (hence no iphelper used) the client boots fine.


Where and how do I edit the PXE image (or config) to remove this incomplete DHCP option?

Many thanks!

---

