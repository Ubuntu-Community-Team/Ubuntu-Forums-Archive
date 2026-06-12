---
title: "problem after installation of ubuntu"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by thebugspreading on 2011-05-06
hi all! 
I am a new linux user, and i have installed ubuntu 10.10 on a laptop, the HP Compaq nx6110
for what i known, it have a Mobile Intel 915GM Express for the wireless internet connection, but i cannot figure how to connect to my home router.

i'm not very good with ubuntu interface, so i'm unable to understand what the problem is... but considering that i've installed the O.S. a few hours ago, may the problem depend on some missing driver?

the offline ubuntu guide suggest to use the command sudo lshw -c network, saing i would expect to receive claimed, unclaimed, enabled, or disabled, but what i read from that command is

description: ethernet interface
product: BCM4401-B0 100base-TX
vendor: broadcam corporation
physical id: e
bus info: pci@0000:02:0e.0
logical name: eth0
version: 02
serial: 00:14:c2:d8:e6:c8
size: 100mb/s
capacity: 100mb/s
width: 32bits
clock: 33mhz
capabilities: ps bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100mb/s
resources: irq:16 memory:d000e000-d000ffff



anyone could help? 

(maybe is very easy, but i'm pretty noob at linux)

any help will be very appreciate!!!

---

### Post by thebugspreading on 2011-05-07
up

ps, i was wrong, my wireless device isnt the  915GM (that is a vga..)

---

### Post by Vuk Serbia on 2011-05-07
You can try to install backports for your ubuntu release. 
Go to Ubuntu software center and type in 
linux-backports-modules-headers-maverick-generic or do in terminal:

sudo apt-get install linux-backports-modules-headers-maverick-generic
sudo apt-get update
sudo apt-get dist-upgrade

after that you can do:

sudo apt-get install hostapd 
but do this if it still doesn't work

---

