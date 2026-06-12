---
title: "Cisco 350 Wireless Card"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by stults on 2006-06-18
I have a Cisco 350 miniPCI in my Inspiron 8200 laptop and was using Breezy Badger (5.10) before with NO PROBLEMS!  I recently reinstalled with the new Dapper Drake (6.06) and am having some issues with my wireless card.  Apparently this card is assigned to interface eth1 and is supposed to set up a virtual interface at wifi0 that it uses for a monitor mode, which it did just fine in Breezy.  However, in Dapper it recognizes a device at wifi0 but will not configure it and I cannot scan for wireless networks outside of the one I am connected to using 'iwlist eth1 (or wifi0) scanning'.  Also, I cannot connect (or communicate) with my network at home that has wep encryption (I know it's weak).  It seems to connect fine, but I cannot ping anything.  I will be trying network-manager-gnome to see it will fix this last issue.  Any help would be great.
Also wondering if the wifi0 problem might be causing a problem when I try to use aireplay (from aircrack) to try associate with an AP.  Thanks up front for any suggestions or comments!

---

