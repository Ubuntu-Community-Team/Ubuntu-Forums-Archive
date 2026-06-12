---
title: "Network Manager is gone and I'm stuck"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by sdmike6 on 2010-05-28
I'm using Ubuntu 10.04 amd64 

Ok in short I removed network manager and now I need it back.

If I'm plugged in using an Ethernet cable what terminal commands would I used to enable the Ethernet port so I can go online and download network manager again?

Thank You

:)

---

### Post by mituw16 on 2010-05-28
Pop open termiNal and enter the following commands 

```

nano /etc/network/interfaces

```

Then add this 

```

auto eth0 
iface eth0 net dhcp 

```

Then save the file and close nano and enter the following command 

```

sudo /etc/init.d/networking restart 

```

Cheers

---

