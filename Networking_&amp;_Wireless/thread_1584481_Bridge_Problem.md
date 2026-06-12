---
title: "Bridge Problem"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by cemzafer on 2010-09-29
Hi all,

I have two interfaces, one of them is eth1 and the second one is wlan0, I want to built a dhcp bridge interface. How can I do that?
Thanks

Here is my interfaces file details.

auto eth1
iface eth1 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0

auto wlan0
iface wlan0 inet static
    address 192.168.1.101
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    wireless-mode ad-hoc
    wireless-essid ubuntu

auto br0
iface br0 inet static
    address 192.168.1.201
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge_ports eth1 wlan0

---

### Post by cemzafer on 2010-09-30
After a little bit searching, I tried dhcp with 8712u module and dhcp is not working or I missed something.
This is my usb card info:

Bus 001 Device 005: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

And it uses 8712u module, and here is the following commands I tried after the fine boot.

sudo iwconfig wlan0 essid "ubuntu"
sudo iwconfig wlan0 mode Master
sudo iwconfig wlan0 rate auto
sudo ifconfig wlan0 up

Here is the output:

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Master  Access Point: 02:11:87:61:6D:00   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here is my dhcp3-server file;

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="wlan0"

When I execute the sudo dhclient wlan0 from another client dhcp server replies these outputs but it is not working properly.

Sep 30 19:03:59 cemzafer-desktop kernel: [ 1234.070640] fwdbg:get survey cmd
Sep 30 19:03:59 cemzafer-desktop kernel: [ 1234.070645] 
Sep 30 19:04:00 cemzafer-desktop kernel: [ 1235.839253] fwdbg:survey done(00000005, 00000000)

I hope this gives some clue for the proper installation.
Thanks in advance.

---

