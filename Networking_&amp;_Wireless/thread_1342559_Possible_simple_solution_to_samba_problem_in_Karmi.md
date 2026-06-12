---
title: "Possible simple solution to samba problem in Karmic"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Ginsu543 on 2009-11-30
I apologize in advance if this has been posted somewhere else but I thought I'd share a simple solution I've discovered to deal with the samba browsing problem in Karmic.

Some background first: When I moved from Jaunty to Karmic (fresh install), I had trouble browsing the network in Nautilus to see samba shares on other computers on my home network. When I clicked on "Network" in "Places,"  there would be a long pause and then I would get an "Error: Failed to retrieve share list from server" message. I came to these forums and followed a suggestion I found to type in "smb://ip_address/share_name" to access the samba shares and it worked for me. So I had at least a usable workaround to the problem.

Since then, I've discovered that network browsing works normally if you edit the /etc/hosts file and add IP address definitions for the hosts/computers you are trying to access. In my case, I was trying to access a folder I had made shareable on my main rig (running Karmic) with my Dell Mini 9 (also running Karmic). I added the following line to the /etc/hosts file on my Mini:

192.168.0.253     Ginsubuntu
(IP address)        (Name of host)

When I saved the file and rebooted, I could now browse the network normally and see the samba shares on the hosts I've defined. I hope that this helps other people with a similar problem.

---

### Post by lostlinuxkiwi on 2009-12-01
Thanks man this works for me. Its been bothering me for days. Thought it was a firewall problem but obviously not.

---

### Post by Ginsu543 on 2009-12-01
Excellent!

---

### Post by basily on 2010-04-25
Thank you thank you thank you! I've been scouring the web for a solution to this problem and here it is!

---

