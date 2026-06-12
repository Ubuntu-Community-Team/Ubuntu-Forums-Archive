---
title: "internet sharing"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by gameguy on 2010-04-05
I am running Ubuntu 9.10 and I need a mac, ipod touch, and my laptop to  acess the internet all at once. My laptop is connected to a modem  through ethernet. I effectively need to turn my laptop into a router,  because my modem does not have that capability.
Thanks

---

### Post by Iowan on 2010-04-05
[This]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") help page might be useful for wireless clients. There's a [similar]("https://help.ubuntu.com/community/Internet/ConnectionSharing") article for ethernet sharing.

---

### Post by gameguy on 2010-04-05
In through ethernet, out through wireless, so that cancels the second link out.
The first link says:
do this: "sudo /etc/dbus-1/event.d/25NetworkManager stop"
which returns "sudo: /etc/dbus-1/event.d/25NetworkManager: command not found"

it also says to change the /etc/network/interfaces from:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0

to:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wireless0
iface wireless0 inet static  #indented till the end of the file
                   wireless-key 1234567890
                   wireless-channel 6
                   wireless-mode ad-hoc
                   wireless-essid 'Wireless Connection'
                   address 192.168.0.2
                   gateway 192.168.0.1
                   netmask 255.255.255.0
          iface wlan0 inet dhcp


But here's my /etc/network/interfaces:
auto lo
iface lo inet loopback

By the way, I use ubuntu 9.10, so there's a possibility that it could be outdated.

---

### Post by gameguy on 2010-04-05
It says last edited 24 July 2008 so that's definitely a possibility.

---

### Post by gameguy on 2010-04-11
Any ideas?

---

### Post by stilling on 2010-04-11
let me understand you have a laptop and you need to give internet from that laptop to other computers wireless and cable is that what you are trying?

---

### Post by gameguy on 2010-04-11
Get internet through ethernet, give it to other devices through wireless.

---

### Post by stilling on 2010-04-11
ad-hoc connection from laptop 


see this [---> HERE]("https://help.ubuntu.com/community/WifiDocs/Adhoc")   and    [----> HERE]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html")


see this for router [----> HERE]("http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/") and [---> HERE]("https://help.ubuntu.com/community/Router")

or by using webmin [-----> HERE]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")



HOPE this HELPS you 2

---

### Post by gameguy on 2010-04-11
If I create the network it disconnects me from the other network. So either I have internet acess and no-one else does or everyone can connect to an ad-hoc network without internet.

---

### Post by stilling on 2010-04-11
if you maked the connection with network manager go to wireless tab hit edit go to ipv4 and see if shared to others is selected in that tab if you made it in command line make shore that you activated the ipv4 ip_forward
i thing that was something like
 iptables -t nat -A POSTROUTING -o ( internet network board ) -j MASQUERADE
 echo 1 > /proc/sys/net/ipv4/ip_forward
 and edit /etc/sysctl.conf
 the line net.ipv4.ip_forward =1 delete the # that is in front of it
 and if it worcks add 
sudo iptables -t nat -A POSTROUTING -o ( internet network board ) -j MASQUERADE

in /etc/rc.local before the exit 0 line to come up on restart 
maybe i am wrong but i hope this can giveyou an ideea of how to do it
i did the wireless ad-hoc from network manager formy home andworks like a dream in my jaunty jackalop ubuntu machine

---

