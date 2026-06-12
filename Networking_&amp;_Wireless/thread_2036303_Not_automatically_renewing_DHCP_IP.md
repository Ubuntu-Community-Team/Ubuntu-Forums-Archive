---
title: "Not automatically renewing DHCP IP"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by yang on 2012-08-01
I have a headless server on my network (actually it's just running Ubuntu Desktop 10.04) that for some reason isn't automatically renewing its DHCP lease when it gets reconnected to the network. How do I fix this?

Some more info: the router our systems are connected to has been going down and coming back up occasionally, in the span of a second. The other Ubuntu 10.04 boxes seem to handle this fine - within a second, they're connected again. It's just this one box that doesn't seem to be behaving. It's annoying because every time this happens I have to go to the server and reconnect a monitor (or at the very least a keyboard) just to run sudo dhclient.

```

$ pgrep NetworkManager 
1014

$ lsb_release -a 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

```

---

