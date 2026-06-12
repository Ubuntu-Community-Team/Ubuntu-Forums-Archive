---
title: "VPN on DG834G Wless"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2009-06-14
Hi,

Can someone pls explain roughly, if I can setup VPN so that the router will be as a server? I just want to encrypt the PC-router traffic not using the WAP2 etc. Is that possible? 
I think the router is 'clever' enough only to pass through any VPN connections etc, but it cannot act as a server correct? The idea is:

PC---VPN---Router -Cable-Internet
      |
PC----|

Any other ways to encrypt the wless data to this router?

thanks!

---

### Post by ilchymis on 2009-06-14
As far as I know this router does not have any built-in VPN capabilities.  However, you should be able to install OpenWRT on it—and OpenWRT can run OpenVPN, which is well-integrated into the Ubuntu environment (install network-manager-openvpn for one-click VPN access through Network Manager).

---

### Post by [pl]ice on 2009-06-20
> **ilchymis said:**
> As far as I know this router does not have any built-in VPN capabilities.  However, you should be able to install OpenWRT on it—and OpenWRT can run OpenVPN, which is well-integrated into the Ubuntu environment (install network-manager-openvpn for one-click VPN access through Network Manager).

Interesting. I'll look into it. 

thanks

---

