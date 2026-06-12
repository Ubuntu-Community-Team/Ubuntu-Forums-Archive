---
title: "cant create virtual eth1 in /etc/network/interfaces"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by Karottenbaum on 2011-10-12
hi, i'm following a guide from snort.com [http://www.snort.org/assets/158/012-snortinstallguide291.pdf](http://www.snort.org/assets/158/012-snortinstallguide291.pdf)

it says:

```
sudo vi /etc/network/interfaces

**Change the following lines from this:**

auto eth0
iface eth0 inet dhcp

**to these values:**

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

**Now add the following lines at the end of the file to start the second card without an IP adress:**

auto eth1
iface eth1 inet manual
ifconfig eth1 up

**Save and exit the file then either reboot or issue this command:**

sudo /etc/init.d/networking restart

```

but ifconfig doesn't show an eth1 (reboot didn't helped either). only eth0 but that's the one i got in my laptop...

my ifconfig only shows: **lo, wlan0, eth0**

i don't know why it doesn't work, i even tried it with **eth0:1** and fix IP, didnt show up either...

thanks!

---

