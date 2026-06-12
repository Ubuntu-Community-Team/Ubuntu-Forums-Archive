---
title: "Static address"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by thep8ntballfreak on 2009-08-09
for some odd reason i cannot get my server to keep a static address
if i type /etc/init.d/networking restart 
it will keep the address that i want for about 30 seconds then it goes back to the dhcp address its had since install

ive edited the /etc/network/interfaces file and it seems to do nothing.

any help would be greatly appreciated

---

### Post by SoftwareExplorer on 2009-08-09
Does your server have a GUI(mouse, point and click), or is it all CLI(type commands only)?

---

### Post by Adina on 2009-08-09
please post your /etc/network/interface file.

It could be that the address you are trying to make static is in the dhcp range and/or is being used by an other machine on the network.

---

