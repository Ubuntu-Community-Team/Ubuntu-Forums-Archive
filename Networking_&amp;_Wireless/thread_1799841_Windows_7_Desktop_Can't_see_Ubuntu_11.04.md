---
title: "Windows 7 Desktop Can't see Ubuntu 11.04"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by country0129 on 2011-07-08
I can access my Windows 7 machine completely from my Ubuntu laptop. Both machines access the internet. Both machines can ping the other. But Windows 7 does not see my laptop Ubuntu on my network. Desktop LAN to linksys modem/router supplied by ISP. Laptop connected wirelessly.
 
I'd installed software on the Win 7 machine. Thought that might have "dinged" it; so uninstalled. Restored the machine to a time that it did work.
 
HOMEGROUP is the name of the HomeNetwork on both machines. Usernames and passwords the same. Windows firewall disabled. Norton firewall set to allow the laptop.
 
Realize this isn't a Windoze forum, but perhaps someone has solved this problem and can help?
 
Thanks,
 
 
 
 
Dean

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
Its most likely a bug with samba, or a name resolution issue. Try typing \\ServerIP into the windows explorer URL bar.

---

### Post by Randy Flagg on 2011-07-09
When you say homenetwork do mean workgroup?

I made this work by making sure my windows workgroup entry matched my ubuntu samba workgroup entry.

---

