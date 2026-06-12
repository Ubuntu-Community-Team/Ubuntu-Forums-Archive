---
title: "Windows Shares Only Work with IP Address (10.10)"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by gdea73 on 2011-03-03
My computer running Ubuntu 10.10 cannot see the Samba shares on either of my two Windows XP machines.

I have Samba installed and configured, I am on the correct workgroup. However, under "Network", there is only one item - Windows Network, which contains no workgroups.

I am hosting a share on this Ubuntu PC, but I haven't had the time lately to see if I can view it from the Windows XP computers. If it would help, I can try later.

If I click Connect to Server, and enter the **IP Address** of one of my XP computers, I can connect to them. However, if I enter the computer's name I get "Failed to retrieve share list from server" without a specific share, and with it I get "Failed to mount Windows share."

Any help would be greatly appreciated.

- gdea73 -

---

### Post by gdea73 on 2011-03-05
BUMP

FRESH INSTALL of 10.10 now - because of a separate issue.

I have Samba and the samba configuration gui. Everything worked great out of the box after setting my workgroup and adding netshare. But suddenly after a reboot, I have the exact same problem. When I go to Network, click Windows Network, I get "failed to retrieve share list from location"

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Is your ubuntu machine using the same DNS servers? If you can access by IP, chances are - its a name resolution issue. Also, do you have a firewall enable, that could be blocking the NetBIOS announcements from the XP machines.

---

