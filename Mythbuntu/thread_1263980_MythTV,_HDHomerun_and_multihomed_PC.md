---
title: "MythTV, HDHomerun and multihomed PC"
date: 2009-09-11
forum: Mythbuntu
---

### Post by heathramos on 2009-09-11
How can you configure Mythtv to use hdhomerun over one network card?

I have two nics and I want to record over one and stream over the other.

---

### Post by newlinux on 2009-09-11
You need to run dhcp on your machine and set it to use one (and only the one connected to your HDHomerun) of your nics.
I think your dhcp server will have to be configured as a different subnet. So if your home network is already set up as 192.168.0.xxx, you could set up the subnet for the HDHR as 192.168.1.xxx

This link may help:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server)

---

