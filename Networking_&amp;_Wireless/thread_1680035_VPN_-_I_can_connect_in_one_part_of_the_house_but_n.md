---
title: "VPN - I can connect in one part of the house but not another"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by dgw on 2011-02-01
This isn't really an Ubuntu issue, but in searching for info on this, I've found a lot of people who have similar problems to mine when using Ubuntu but not when using Windows, and I'm using Ubuntu of course.

I'm trying to connect to Ipredator. If I plug my laptop into the wired network in one part of my house, I am able to connect to the VPN. If I connect to the wifi in another part of the house, network manager fails to connect to Ipredator. I have a wall-plugged wireless range extender, Netgear WGX102, connected to the wired network in the part of the house where Ipredator works, and it is providing the wireless access point in the part of the house where Ipredator does not work. 

I checked the Netgear website and they don't seem to have any newer firmware for it. I've tried everything I can think of in terms of changing settings in the wireless range extender. Am I doing something wrong, and if so, what? If the problem is with the wireless range extender, then what can I get to replace it? 

I'm frustrated and don't know where else to ask this.

---

### Post by dgw on 2011-02-02
So...I was wrong. I was able to connect to Ipredator with the wired connection to the router, but not the wireless in my room, and thought it was due to the range extender. Then I tried connecting to the wireless provided by the router, and Ipredator doesn't work with that either. I suppose it may be an Ubuntu issue or a network manager issue or something. It seems to work fine with a wired connection, but not at all with wireless. I can't run cables to my room, and I'm very very far from the router.


edit! SOLVED!!!  Figuring out what the actual problem was made it much easier to search for an answer. I found one here: [http://www.cognitivecombine.com/2007/10/network-manager-vpn-wireless-no-go-in-ubuntu-710/](http://www.cognitivecombine.com/2007/10/network-manager-vpn-wireless-no-go-in-ubuntu-710/) . The gist of it is that network manager will only connect to the PPTP VPN using eth0. If you switch your wireless connection to be eth0 instead of eth1 in /etc/udev/rules.d/70-persistent-net.rule[FONT=monospace]s[/FONT], it works. :D

---

