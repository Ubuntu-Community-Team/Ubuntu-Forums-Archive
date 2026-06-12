---
title: "Ubuntu 13.03 Problems with Ethernet"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by Joe_Sweeney on 2013-08-03
Hello all, I have Ubuntu 13.04 64 Bit running on a desktop with a Realtek 8111e chipset. After initially, I could not connect to my network at all, I tried the solution posted [here]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/") with the latest drivers. After this I ensured that only the new module was running, and that the Ethernet connection was indeed using that module. Now, Ubuntu says that I am "connected," and I have the two arrows indicating so in the top right of my screen. Now, setting my connection to use DHCP fails and times out completely, but I am able to get the "connected" message if I manually enter my connection details. From here I can ping localhost and such, but I cannot access the internet, and I cannot ping my router. Windows 8 works fine with this desktop, but every Linux distribution I try seems to fail. I have tried CentOS 6.4, Ubuntu & Ubuntu Server 12.04 LTS, and Ubuntu & Ubuntu Server 13.04, and in each instance I encounter similar problems.

My interfaces file looks like this:
```
auto lo
iface lo inet loopback
```

And I have my settings in the GUI network config tool as such:
IP: 192.168.1.31
Subnet: 255.255.255.0
Gateway: 192.168.1.1
DNS: 8.8.8.8
I'm very much a newbie so I don't know what much of this means. :)

---

### Post by praseodym on 2013-08-03
Please show these outputs:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

