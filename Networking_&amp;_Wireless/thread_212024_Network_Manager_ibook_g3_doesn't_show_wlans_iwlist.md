---
title: "Network Manager ibook g3 doesn't show wlans iwlist does."
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by slackmase on 2006-07-09
I've got an ibook g3 800 with an airport 802.11b card under the keyboard. 

I did a brand new install of dapper, and installed both network manager and network-manager-gnome. This displayed networks but wouldn't allow me to join them..or rather it looked like i had joined them  but it wouldn't aquire a dhcp lease. I could however manually join them with iwconfig and dhclient eth1

I then did and apt-get update, apt-get upgrade which put my kernel and system up to date. Now network manager doesn't display any networks other than wired networks. 

iwlist will dispay the networks however so the airport card actually is being detected and seems to be working. I can't however aquire a dhcp lease after manually joining .

This applies to both WEP and open networks. All networks are seen and work ok under OSX.

Aside from network manager (which wasn't included), everything worked fine under hoary.

Any way i can debug this ?

thanks

---

### Post by slackmase on 2006-07-10
do i  need to give more info or does no one have any idea how i can debug this ? [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

