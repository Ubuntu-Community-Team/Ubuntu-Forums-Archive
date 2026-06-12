---
title: "¨PERMANENT¨ MAC ADDRESS CHANGE in UBUNTU 10.4"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by vastvet on 2010-09-14
Hi for several reasons i need to change the mac address of my interfaces in ETH and WLAN so i tried several times, i ended up killing the nasty network manager ,than i stuggled a long time and i finally found soemthing that keep the spoofed macs in place for a while but i am not sure i did it the right way, the following i did is;

in shell
sudo su
password [root]

gedit /etc/network/interfaces
interfaces file;

auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth6

iface eth6 inet dhcp
hwaddress ether 00:00:0E:C0:00:00
auto eth6

its now eth6... because i tried macchanger [GNU] also in random mode and i dunno how to disable the random mac address mode... i tried things like macchanger -m eth6 --mac=00:00:0E:C0:00:00

it stays a nfew reboots and than it says eth7 when do ifconfig this keeps going on.......](*,)eth8 eth9 eth10... and not sure it is the macchanger tool in random mode that does this...
[ofcours an working macs this is just excample]

And getting the WLAN0 to work is an ####### ##### to i tried ndiswrapper first and after that i tried administration ,wireless drivers instal inf driverfile of the cd of the nic ,the nic was online for 3 seconds.... only with ndiswrapper.

any ideas to get safely an permanent mac change and also how to get wifi working with mac change without the network manager? :?:

---

