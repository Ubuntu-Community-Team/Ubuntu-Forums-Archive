---
title: "2nd NIC"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by satimis on 2012-08-08
Hi all,

Ubuntu 12.04 server 64bit

I have TP-Link Gigabit ethernet card installed on the PC as 2nd NIC

eth0 onboard LAN nVidia chip
eth1 TP-Link NIC RTL chip

the driver is r8168-8.032.00.tar.bz2 download on;
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

I have following questions;

1) 
On booting the PC it prompts on screen;
RPL-ROM-ADR: 90F6 5203 5786
RPL-ROM-IRQ: 11
RPL-ROM-PIO: AC00

RPL-ROM-FFC: 1/50 (running from 1 to 50)

on each boot.  Whether it is necessary?  If NO how to skip it?


2)
The cable used for eth0 is CAT5e connected to the router.  Can I use CAT5 cable to connect eth1 to the same router?  If YES I have spare CAT5 in store room.  If NO I have to purchase a new CAT5e cable.


3)
I need to set static IP address as follow:-

(#eth0)
auto eth0
iface eth0 inet static
address	192.168.0.10
netmask 255.255.255.0 ?
network 192.168.0.1


(#eth1)
auto eth1
iface eth1 inet static
address 10.0.0.1
netmask ?
network ?

Please help.  TIA

B.R.
satimis

---

