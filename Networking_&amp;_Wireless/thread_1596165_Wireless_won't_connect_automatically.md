---
title: "Wireless won't connect automatically"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by mpc_mythtv on 2010-10-13
Hi,

I'm on Kubuntu 10.10. I have set wireless to connect automatically to my home network. However, after each reboot of the laptop, wireless is disabled and I need to enable it by hand with the network manager.

I noticed that "rfkill list" gives:
```
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```Could that be related to my problem? The command "sudo rfkill unblock all" does not change anything to the output of "rfkill list", however.

I did not have this specific problem on Lucid.

Any idea?
Thanks in advance.

Wireless chipset: Atheros AR928X
Driver: ath9k

---

