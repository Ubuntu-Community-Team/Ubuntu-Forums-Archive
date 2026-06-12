---
title: "deleted dhcp3-client by mistake"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by ganewbie on 2010-08-25
Hello,
Had problems with internet and deleted this by mistake now how do I get it back?
Please note that I have no internet access so I cannot use Synaptic.
Please help:(

---

### Post by Brandon Williams on 2010-08-26
When you say that you don't have internet access, do you really mean that you don't have an internet address because dhcp3-client isn't installed? Or do you mean that you wouldn't have internet access even if you had dhcp client software?

If it's the former (you can access the internet if you have an address), then just configure an address manually, for example:
```
sudo ifconfig wlan0 192.168.1.2 netmask 255.255.255.0
sudo route add default gw 192.168.1.1
echo "nameserver 208.67.222.222" | sudo tee /etc/resolv.conf
```
In the ifconfig command, both wlan0 and 192.168.1.2 should be replaced with the actual interface name and an IP address that is available on your network. In the route command, 192.168.1.1 should be replaced with the real IP address of your default gateway. After the manual config, you should be able to use apt-get, synaptic, or whatever.

If what you really mean is that you can't get net access even with a dhcp client, then you should get yourself a USB thumb drive, mount it on a machine with internet access, download dhcp3-client and dhcp3-common to the thumb drive from here: [http://packages.ubuntu.com/lucid/net/](http://packages.ubuntu.com/lucid/net/), move the USB drive to the broken machine, and then 'sudo dpkg -i dhcp3-*'.

---

