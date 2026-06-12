---
title: "Yet another problem with WPA!"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by Pyro MX on 2006-03-08
Hi there folks, I installed Ubuntu a couple of months ago and I've never been as satisfyed as now of a Linux distro. But there's a little heck... recently, I decided to put WPA encryption instead of WEP for the wireless network at home. I configured WPA supplicant, it starts when the computer boots and it evens connect to the network when I check it over the debug mode.

But when I try to go on the internet, it does not work. When I try to ping the router, it says "network unreachable". I also check the log messages and there's a "no ipv6 routers found" somewhere. I don't know if it has anything to do...

The netowrk is in DHCP and I configured my network options for it. But I tryed to switch in static IP in my network config and I am able to ping the router. It's very odd since the router is configured for DHCP...

My wireless card is a D-Link AirPlus X-Treme G PCI adapter (DWL-G520)
The router is a Linksys WRT54G (I don't know the version tho)

Here are some pics to help:
[[IMG]http://img126.imageshack.us/img126/8893/networkstatus4ix.th.png[/IMG]](http://img126.imageshack.us/my.php?image=networkstatus4ix.png)
[[IMG]http://img406.imageshack.us/img406/1461/noipv6routers5vo.th.png[/IMG]](http://img406.imageshack.us/my.php?image=noipv6routers5vo.png)

So if somebody could help me out to get my computer on the internet again, it would be very nice :mrgreen:

---

### Post by thnogueira on 2006-03-08
What does ifconfig gives to you? Have you configured the default gateway correctly?
(You can change it in System->Admin->Networking)

---

### Post by Pyro MX on 2006-03-08
[QUOTE=thnogueira]What does ifconfig gives to you? Have you configured the default gateway correctly?
(You can change it in System->Admin->Networking)[/QUOTE]

How do I know what ifconfig gives me?

And I'll check for the default gateway (which I think is not configured right) but I don't even know if that option is available in my networking options... I'll check that out thx!  :)

---

### Post by thnogueira on 2006-03-09
ifconfig is a command, then open a terminal (Apps_>Acessories->Terminal) and type *ifconfig*.

Have you found the gateway option in network configurator?

---

### Post by Pyro MX on 2006-03-09
The gateway cannot be configurated because my connection is set for DHCP:
[[IMG]http://img530.imageshack.us/img530/3587/lockedindhcp6cl.th.png[/IMG]](http://img530.imageshack.us/my.php?image=lockedindhcp6cl.png)
Maybe I was in the wrong place?
EDIT: "Masque de sous-réseau" stands for Subnet Mask and "Passerelle' is Gateway.

I also found something while I was re-activating my connection to test it out, DHCLIENT gives me multiple errors and I noticed that it was not using the right subnet mask. Maybe this it the problem?
[[IMG]http://img325.imageshack.us/img325/916/wrongsubnet2zu.th.png[/IMG]](http://img325.imageshack.us/my.php?image=wrongsubnet2zu.png)

I'll check out the ifconfig thing thx! :-D

---

### Post by thnogueira on 2006-03-09
In the firt picture of your last post I can see in the background window (where the adapters are listed) something like

*périphérique par défaut de la passerelle* and it's blank.
You need to set it to your wireless adapter (ath0 in your case)

---

### Post by Pyro MX on 2006-03-09
Yea well I tryed to put ath0 therre but it was resetting to blank automatically maybe I forgot to save the settings before rebooting. But when I had it checked it didn't change anything unforunately :(

---

### Post by thnogueira on 2006-03-09
Can you pos the result of the command
[HTML]route[/HTML]

---

### Post by retsaw on 2006-03-09
I've got the same router and card as you, and when I installed Kubuntu 5.10 and set up WPA I couldn't get DHCP working either with the default dhclient or using dhcpcd.  Since I had it working on the same computer using SLAX, and I could get networking working using a static IP I figured it was an Ubuntu bug, so I gave up and settled for configuring a static IP.  I'd advise you to do the same.

You can pick any IP address to use outside your routers DHCP range as long as you haven't got any other computers running with a static IP, so that would be any IP address between 192.168.1.2 - 192.168.1.99 and 192.168.151 - 192.168.254, I choose 192.168.1.50 myself.

Then set your default gateway to 192.168.1.1.

Next you make sure you have your DNS servers set.  If you don't know what they are, once you have a static IP you can point a browser to [http://192.168.1.1](http://192.168.1.1) and check the status page for your router and it should be able to tell you what it has configured for its DNS servers.

---

### Post by Pyro MX on 2006-03-10
ifconfig gave me general info about my connection and I noticed that there was an incredible amount of error in the package reception (I'm not sure but I think it was package reception). And DOH I forgot to try "route". But if it's to get the routing table, I cannot get it (tryed it via the network tools interface). I'll try the static IP setup.

---

### Post by Pyro MX on 2006-03-19
Got it working using the static IP trick! Thanks a lot to all of you for your help!

---

