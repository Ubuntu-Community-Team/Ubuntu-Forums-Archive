---
title: "Firewire Networking"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by thomlark on 2012-01-31
I have been reviewing my firewire networking after upgrading to newer versions of Linux (Ubuntu 10.10, Mint 12, and Ubuntu 11.11)

It seems that things have changed since I did this a few years back. I'm hoping my comments will help others solve their problem.

If I make a mistake and get something wrong, please feel free to correct me.

1.First connect two computers with firewire connections. 
2.Comment out the blacklist eth1394 line in /etc/modeprobe.d/blacklisr.conf
3. Load eth1394 driver:  sudo modprobe eth1394
4. Check to see if module is loaded : lsmod | grep eth1394
5. List network interfaces : sudo ifconfig -a
6. sudo gedit /etc/network/interfaces and add new lines

   iface "interface-name-from-ifconfig-a" inet static
   address "DESIRED-IP-ADDRESS"
   netmask 255.255.255.0

   auto  "interface-name-from-ifconfig-a"

7. Open Network Tools and copy Mac Address of firewire device.
8. Open Network Connections and add new wired connection with new name such as Firewire, Mac Address copied from Network Tools and IPv4 settings of Manual, "DESIRED-IP-ADDRESS" and netmask of 255.255.255.0
9. reboot
10. from another computer ping the IP address.
11. If that works try "connecting to server"  with window share option.

I hope this helps someone. I know it helped me getting my thoughts in writing.

---

