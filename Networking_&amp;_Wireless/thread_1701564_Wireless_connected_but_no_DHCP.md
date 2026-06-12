---
title: "Wireless connected but no DHCP"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by bind00 on 2011-03-06
Solution: [blush]I had the wrong WPA password.[/blush] It appeared to me that it was connected OK at the physical/datalink level but apparently that was not the case. Anyway it works now and although you might think I'm a berk, at least I came back to publish the solution.
:o)

=================================================================================

Hello
I've set up an old PC with the latest Ubuntu desktop and am trying to set up wireless networking with a TP-Link TL-WN722N. It only came with Windows drivers but from a thread elsewhere I got it to where it finds my router and connects with the password. However, it doesn't pick up its IP details. The router is working fine wirelessly on my phone and wirefully on my other PC.

I've edited /etc/network/interfaces with "auto wlan0" and "iface wlan0 inet dhcp" but after restart the wlan0 interface has no IP details. Originally the interface had IPv6 details but I cleared that with ifconfig. 

Under the Network Connections Wireless tab it has "Auto" followed by the name of my wireless connection so it appears to have connected OK. Now when I click Edit for that connection nmame, the IPv6 tab says Ignore and IPv4 says Automatic (DHCP) but Addresses is greyed out and the other fields are all empty.

Is there something else I need to do?:confused:

Thanks for any help.

---

### Post by chili555 on 2011-03-06
Doesn't this show the address?```
ifconfig wlan0
```By the way, /etc/network/interfaces should not contain any wlan0 lines if you expect Network Manager to manage your wireless. It will try to manage them as long as it's installed and running.> Addresses is greyed out and the other fields are all empty.Those lines are to be filled in by you for static IP addresses, not DHCP.

---

### Post by bind00 on 2011-03-06
Many thanks for the instantaneous response!

No, wlan0 doesn't show any addresses except MAC address.

When you say Network Manager, is that the Network Connections dialog under System > Preferences?

I've removed the wlan0 entry from the interfaces file and restarted the PC (as I'm never sure of the surest way to make changes take effect). Now it's come up with an IPv6 address again. Odd because in Network Connections it still says v4: Automatic (DHCP), v6: Ignore.

---

### Post by Dillz on 2011-03-07
I'm having the same exact problem! I've tried setting it to static and everything, still will not work =/

---

### Post by chili555 on 2011-03-07
> **bind00 said:**
> Many thanks for the instantaneous response!

No, wlan0 doesn't show any addresses except MAC address.

When you say Network Manager, is that the Network Connections dialog under System > Preferences?

I've removed the wlan0 entry from the interfaces file and restarted the PC (as I'm never sure of the surest way to make changes take effect). Now it's come up with an IPv6 address again. Odd because in Network Connections it still says v4: Automatic (DHCP), v6: Ignore.By Network Manager, I mean the whole system but primarily the icon at the top right that you click to see networks and connect. If there is no IP address in ifconfig, you are not actually connected.

Typically, you needn't fill in any details; you need only click the icon, see your network and after you supply the encryption key, connect.

---

### Post by bind00 on 2011-03-07
Thanks again chili555. I've actually solved this and edited my first post so as not to bump it.

You're quite right in saying that it was not actually connected. That's what I misinterpreted. I had mistyped my cryptic password and hadn't realised that it wasn't accepted. The SSID was appearing under the wireless connection so it looked to me like it was connected. I think that could be made clearer in future updates.

---

