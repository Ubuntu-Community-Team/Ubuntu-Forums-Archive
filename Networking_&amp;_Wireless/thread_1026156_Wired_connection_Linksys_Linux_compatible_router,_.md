---
title: "Wired connection Linksys Linux compatible router, and won't run installation CD"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by mspike on 2008-12-30
I'm a newbie at Linux and I have Hardy Heron.  I just got a Linksys wireless router and I am trying to get a wired connection to my computer.The router says it is Linux compatible. So when I try to run the installation cd, it doesn't autorun so I click on on the setup.exe and other files that end in .exe, and none of them work.  So I don't know how to use a wired connection. Any help?

---

### Post by pytheas22 on 2008-12-30
The setup.exe program is only for Windows; don't try that.

Have you configured your router?  Are other computers able to connect to it using a wire?  If so, you should just be able to plug it into Linux and automatically get a connection--if it's just ethernet (not wireless), there's a 99% chance that Ubuntu already has a driver for it.

If the wired connection works on other computers but not on Ubuntu, please open a terminal from the Applications>Accessories menu, run the following commands (with the wire plugged into your computer) and post the output so that we can get a better idea of what's wrong:
```

lspci -nn
lshw -C Network
dmesg | grep eth
uname -mr
sudo dhclient eth0
```

---

### Post by mspike on 2008-12-30
I don't know why, but it is workin now. Thanks for your reply anyway.

---

