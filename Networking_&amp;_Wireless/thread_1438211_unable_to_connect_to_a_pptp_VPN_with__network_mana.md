---
title: "unable to connect to a pptp VPN with  network manager"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by dgw on 2010-03-24
I followed (or at least tried to follow) tutorials on doing this. I installed network-manager-pptp and tried to configure network manager to connect to a VPN. In the settings when I select MPPE with 128-bit encryption, after I've selected it and applied it, I check the settings and it's invariably unchecked. I tried using KVpnc after getting frustrated with network manager, and I can't seem to get that working either. I've been trying to search for info on this, and I can't seem to find anything on why I can't select MPPE with 128-bit encryption. That seems like it might be why I'm unable to connect to the VPN? I need help with this.

---

### Post by dgw on 2010-03-27
Found the relevant bug report on network manager not keeping MPPE settings:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/346768](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/346768)

I'm using the packages from the PPA now and can check 128-bit encryption, and it keeps the setting. :D

Yeah, but I still can't connect. I think the relevant issue in my /var/log/syslog is:
   The synchronous pptp option is NOT activated

I don't know what I'm doing wrong, I've tried so many different settings. I'm not really expecting help with this, I'm just posting follow-up in case anyone searching for info on the bug happens to find this thread, to point them towards the bug report on launchpad, since there's a fix there.

---

