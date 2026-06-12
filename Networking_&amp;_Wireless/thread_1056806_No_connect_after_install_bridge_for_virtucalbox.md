---
title: "No connect after install bridge for virtucalbox"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by gretarsson on 2009-02-01
I have ubuntu 8.10 and my network was fine but I put up virtucalbox and install microsoft vista on it it worked fine but it was saying I need to put up bridge for vista so it can go on line and know my ubuntu have no connection. I have static ip address and I can see it there and also my mac address.
 I install this
sudo apt-get install bridge-utils uml-utilities
sudo gpasswd -a [user] uml-net ( I put in my user name instead of user)
and then edit network interface
sudo nano /etc/network/interfaces
and put in this line in the end.
auto tap0
		iface tap0 inet manual
			up ifconfig $IFACE 0.0.0.0 up
			down ifconfig $IFACE down
			tunctl_user [user]

	auto br0
		iface br0 inet static
			address 192.168.xxx.xxx (here I put in my static ip address)
			netmask 255.255.255.0
			gateway 192.168.xxx.xxx (here I put in my gateway address)
			bridge_ports eth0 tap0
close and restart network
sudo /etc/init.d/networking restart
and then I lost my network
here is this webpage I follow [http://dirn.name/2008/11/network-bridge-setting-for-virtualbox-on-ubuntu-810-static-ip-intrepid-ibex/](http://dirn.name/2008/11/network-bridge-setting-for-virtualbox-on-ubuntu-810-static-ip-intrepid-ibex/)
I took a pictures from my outprint in terminal, it take too long time for me to type it here
If some one can take a look on this. Thanks

---

### Post by Krydox on 2009-02-01
I guess the settings you did put in the interfaces file are incorrect then, or if you haven't yet, try another static IP.

---

