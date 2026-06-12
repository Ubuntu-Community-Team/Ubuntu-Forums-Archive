---
title: "Can't Add OpenVPN Connection"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by abarilla on 2012-10-01
I'm following these instructions: [https://www.ipredator.se/guide/openvpn/ubuntu/gnome](https://www.ipredator.se/guide/openvpn/ubuntu/gnome)

To setup an OpenVPN connection. However, the Save button is disabled. I found references online to fixing the polkit but that didn't help.

I then enabled root logon to LightDM and tried that and as logged in as root, the Save button is also disabled.

This would leave me to believe that the problem is a dependency issue or something and not permissions.

Any suggestions?

---

### Post by abarilla on 2012-10-05
Turns out of I'm sort of a nitwit. I needed to select the crt file on the first tab. This enabled the Save button.

---

