---
title: "Softap airbase-ng dhcpd iptables"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2010-01-22
Hello, this is my first tutorial i will try to be as specific as possible.

References:

IPTABLES: 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[http://forum.aircrack-ng.org/index.php?PHPSESSID=175264d2aaf388739350642fae99a34a&topic=4495.0](http://forum.aircrack-ng.org/index.php?PHPSESSID=175264d2aaf388739350642fae99a34a&topic=4495.0)

DHCPD.conf file examples:
[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

[http://oob.freeshell.org/nzwireless/dhcpd.html](http://oob.freeshell.org/nzwireless/dhcpd.html)

Airbase-ng:
[http://www.aircrack-ng.org/doku.php?id=airbase-ng](http://www.aircrack-ng.org/doku.php?id=airbase-ng)

Script that i borrowed parts of:
[http://forums.remote-exploit.org/newbie-area/15354-softap-airbase-ng-wireless-testing.html](http://forums.remote-exploit.org/newbie-area/15354-softap-airbase-ng-wireless-testing.html)

GOAL: to set up a basic soft AP that can be expanded upon once you learn more about how to use the tools required to do so.

Packages:
Aircrack-ng
Macchanger
GADMIN-DHCPD <<< dhcpd3 server with a GUI interface to make life easy
iptables <<< already installed on your system we will be tweeking them a little

Hardware:
My laptop running 9.04 ubuntu
WUSB54G - called wlan1 used as soft AP
Internal card called eth0 as connection to internet

1. Start wlan1 into monitor mode and change the mac address to cover your butt.
sudo bash    <<puts you into root mode so you don't have to type sudo all the time
airmon-ng start wlan1   <<starts wlan1 into monitor mode  mon0
ifconfig mon0 down   << takes mon0 down so we can change the mac
macchanger -m 00:11:22:33:44:55  << can be any mac you want
ifconfig mon0 up  <<brings mon0 back up

2. Test your mon0 to make sure it can packet inject and bring up airbase-ng.
aireplay-ng -9 mon0        << -9 is test mode should return   "Injection is Working!"
airbase-ng -c 1 -e testap  << brings airbase-ng up on channel 1 with a name of testap

When airbase-ng comes up you will notice it created at0, this is where the airbase comunicates with any other program you wish. at0 could be routed though a packet sniffer or pointed at an internal dns or http server. for now we will point at0 at eth0 so that all traffic on at0 can go out to the internet though your box.

3. Setting up the DHCPD server. This has to be configured to your box using your specified ip numbers. I will provide an example of how mine is set up.
after installing dhcpd-server with or without the gui.

open a terminal

sudo gedit /etc/dhcp3/dhcpd.conf << this is the config file for dhcpd. it might have a different path on your machine

option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;
ddns-updates off;
ddns-update-style interim;
authoritative;


subnet 192.168.0.0 netmask 255.255.255.0 {
        interface at0;
                range 192.168.0.2 192.168.0.10;
                option routers 192.168.0.1;
                option subnet-mask 255.255.255.0;
                option domain-name-servers 192.168.0.1;
                allow unknown-clients;

        }

this sets up an internal dhcp server that allows anyone to connect and assigns ips between 192.168.0.2 and 192.168.0.10 as you can see the interface is at0 this is where the server is listening for devices to assign ips to.

After you save this config file you can start it by either opening gadmin-dhcpd and without modifying any of the fields just hit activate, this will run the current dhcpd.conf file or you can use command line like this:

root@lappy:/etc/init.d# service dhcp3-server start

if you get an error with either of these methods then you most likley have a syntax or illegal action in your dhcpd.conf file. i use gadmin-dhcpd because it can help trouble shot the problems.

---------------------------------------------------------------------------------------------------
Now you should have airbase-ng up and visible on the wireless network you should be able to connect to it and get assigned an IP address and ping the "router" which is acutally the softAP. You should also be able to ping any other device on the network.
---------------------------------------------------------------------------------------------------

4. Now we will set up IP tables to send the traffic from your softAP to eth0 this part i am not extreamly familiar with, but what i am doing works so i will keep doing it.

IP tables are not perminate so if you mess something up really bad restart your system and start over.

# iptables cleanup
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

 # iptables
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1 # DNS
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE # gateway to ext. router
iptables --append FORWARD --in-interface at0 -j ACCEPT # rogue gateway
iptables -t nat -A PREROUTING -s 192.168.1.128/25 -d 192.168.1.0/25 -j DROP # protect LAN from WLAN (DROP/REJECT)

echo 1 > /proc/sys/net/ipv4/ip_forward <<this line has to be ran after any update to IP tables to activate the changes

________________________________________________________________________
At this point you should be able to connect to your AP from a test device and get full internet access.

it looks something like this.
AP - running on a wifi1 but is refered to as mon0
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
airbase-ng started on mon0 and starts at0
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
at0 points at the dhcp server which assigns addresses to incoming requests
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
ip tables route the traffic from the AP though your box out to the internet though eth0
________________________________________________________________________

Extras:
Good commands to know

sudo bash  <<<puts you into root mode
ifconfig <device> up/down  << brings the device up or down
airmon-ng start/stop <device> <<will start or stop a device in monitor mode
ifconfig -a   <<will show all devices regardless of status
iwconfig  <<shows wireless devices
man <command> <<will bring up the manual for that command ex "man ifconfig"

---

### Post by rtsthanks on 2010-09-06
Good tutorial! Thanks randumnumber

---

