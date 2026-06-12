---
title: "No eth0"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by JD32 on 2010-11-30
Im using an old dell tower as a server and im trying to give it a static IP and when i opened the file "etc/network/interfaces" all i got was "auto lo" settings, no "auto eth0"? weird, so i ran "sudo ifconfig" and my auto eth0 was running apparently, there was an ip, netmask etc.

So i just added to the /etc/network/interfaces file-

auto eth0
iface eth0 inet static 
           address 192.168.1.101
           netmask 255.255.255.0
           broadcast 192.168.1.255
           gateway 192.168.0.1

Then ran-

"sudo /etc/init.d/networking restart" 
"failed to bring up eth0


Any ideas???? could it be becasue the Ethernet adapter im using is a PCI card and not directly on the mother board?

---

### Post by uncaspi on 2010-11-30
You most probably had to remove network-manager from your system I have read on several threads.

---

### Post by JD32 on 2010-11-30
> You most probably had to remove network-manager from your system I have read on several threads. 

What does that mean?

---

### Post by uncaspi on 2010-11-30
That mean that all lines applied to the interface file are not handled by nm. And if you need to auto connect you have to remove nm to accomplish that.

---

### Post by JD32 on 2010-11-30
ooo ic, ill give it a try, thanks!

---

### Post by uncaspi on 2010-11-30
I read on a thread earlier today that there are 4 items that should be removed.

---

### Post by JD32 on 2010-11-30
could you point me in the direction of this forum?

---

### Post by uncaspi on 2010-11-30
It was today, but I can see if I can find the thread.

---

### Post by uncaspi on 2010-11-30
> **TennTux said:**
> Your version of '/etc/network/interfaces' does not do it either. When I boot 'eth1' gets a DHCP (IPv4) address while 'eth0' gets no IPv4 address. Both get a IPv6 addresses.

I guess I am down to it and must de-install network-manager, network-manager-gnome, network-manager-pptp and network-manager-pptp-gnome.



This thread:

[http://ubuntuforums.org/showthread.php?t=1633973](http://ubuntuforums.org/showthread.php?t=1633973)

---

### Post by Iowan on 2010-12-01
I suppose one of the advantages of the server version is that it doesn't come with Network Manager (unless it's changed recently...). The gateway line seems odd - as it's outside the 192.168.1.X subnet. Also - what IP address  (or subnet) does eth1 get/use.

---

