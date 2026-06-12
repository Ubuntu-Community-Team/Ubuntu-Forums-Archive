---
title: "Setup a Wireless card to connect to a specific AP on CLI and static IP"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by Davlav on 2009-07-23
Hello,

I need to setup a wireless connection on a headless computer on command-line for it to connect to an AP using a pre-programmed static IP. 

Once this is working, I'll be able to ssh it wirelessly. To set it up, I'm using ethernet LAN.

Is there a way to edit /etc/network/interfaces so that the computer does that automatically?
What commands should it contain? 

For the IP, would be enough something like that?

	iface ra0 inet static
        address 192.168.1.37
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

How to deal with the 'auto connect'?

Through ssh on wire I've tried manually:

	sudo ifconfig ra0 up
	iwlist ra0 scanning
	sudo iwconfig ra0 essid "My ACCESSPOINT"
	sudo iwconfig ra0 key "s:My Alphanumeric WEP key"

But it does not connect... :(

Any tips?

Thanks for your help!

Best regards,

David

---

### Post by t0mppa on 2009-07-23
[Here]("http://ubuntuforums.org/showthread.php?t=571188")'s a nice thread that answers most of the above questions. And if you run into trouble, just drop a post there and kevdog will help you out.

---

