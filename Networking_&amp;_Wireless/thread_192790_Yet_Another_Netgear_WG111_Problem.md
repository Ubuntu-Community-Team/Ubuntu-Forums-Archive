---
title: "Yet Another Netgear WG111 Problem"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by ihatecrayons on 2006-06-09
So, I had my netgear wg111 working fine under Breezy, but when I did a clean install of Dapper on my PC, and I followed the same steps as I did to get it working on Breezy, the card won't work.

These are the steps I followed:
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i netwg111.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

usually at the end of the "modprobe" one the blue light on the card comes on, but not this time.

ndiswrapper -l tells me that the driver is present, and the hardware is present, but in networking there is no wlan0. Also, when I do "iwconfig wlan0" it tells me that there is no such device for wlan0.

Anyone have any help for me? :D

---

### Post by eternalsword on 2006-07-13
please post the output of lsmod

---

