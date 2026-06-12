---
title: "Proxy system wide setting"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by balkrishna on 2010-10-11
I am using Ubuntu 10.10 . At work , I have to access the internet using a proxy with authentication . In Ubuntu 10.10 , after setting the proxy settings to the appropriate server with the username and password I get the following error when I run sudo apt-get update even after applying the settings system - wide . 

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  407  Proxy Authentication Required


```

A solution to this is editing the /etc/apt/apt.conf file . This file although accepts the proxy server address correctly it fails to set the username and password . 

Is there any way to configure the proxy settings from the GUI for all applications ?

---

### Post by cuby on 2010-10-25
This affects me to.

---

