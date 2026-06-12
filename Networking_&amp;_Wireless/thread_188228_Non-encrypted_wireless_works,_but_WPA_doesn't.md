---
title: "Non-encrypted wireless works, but WPA doesn't"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by briangs on 2006-06-03
First time using Linux.

I got my Broadcom wireless card on my Dell 600m to work with Dapper, but it only connects to my Netgear router through a non-encrypted connection. 

When I revert back to WPA-PSK (which works for me under XP), NetworkManager hangs on "Waiting for Network Key for the wireless network" and fails to connect.

I went through the steps located here [http://www.ubuntuforums.org/showthread.php?t=179643]("http://www.ubuntuforums.org/showthread.php?t=179643"), adding a wpasupplicant file to /etc/default/ and editing /etc/network/interfaces as suggested. This did not work for me.

It's possible I'm doing something wrong, but I have quadruple-checked my steps and nothing I do seems to get Ubuntu to connect through WPA.

Any suggestions would be helpful.

---

