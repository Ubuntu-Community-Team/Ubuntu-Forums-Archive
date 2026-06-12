---
title: "automating dhclient ath0"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by neominds on 2005-02-26
I am using a Proxim a/b/g wireless card and each time I boot up I have to manually enter 'sudo dhclient ath0' it to work. Is there a way to automate this and not have to type it in?

Thanks,

Michael

---

### Post by alastair on 2005-02-26
This is the soft of thing set in the file :

/etc/network/interfaces

i.e.

a section like :

iface ath0 inet dhcp
  ... etc.

---

