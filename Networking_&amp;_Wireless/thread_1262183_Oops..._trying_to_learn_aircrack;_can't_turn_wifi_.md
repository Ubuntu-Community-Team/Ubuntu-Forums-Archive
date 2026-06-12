---
title: "Oops... trying to learn aircrack; can't turn wifi back on!"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by mailman1175 on 2009-09-09
Errrmmm... yeah. I'm trying to learn how to use aircrack-ng, using this [tutorial]("http://ubuntuforums.org/showthread.php?t=514723") I found here. So I

```
sudo airmon-ng stop ath0
        sudo airmon-ng start wifi0
```

and, then I try an injection test. It's not working, for whatever reason, so I decide to scrap it, only... I don't know how I'm supposed to resume normal function with wireless networking. No network I thought a reboot might solve it. Nope.

Compared with a nearly identical machine (different wifi driver) sitting next to it, iwconfig seems normal. lspci tells me the hardware's still recognized. lshw -C network, though, doesn't show it to have an assigned i.p. The network-manager applet doesn't show any wireless networks available, even though iwconfig does.

Just for grins, I tried re-compiling the wifi driver, and that didn't work, either.

I learn everything the hard way, it seems. Any help, you know, would be appreciated.

---

### Post by community nerd on 2009-09-09
Try this in case your wireless card is disabled:
sudo ifconfig wlan0 [FONT=Verdana]up[/FONT]

---

### Post by mailman1175 on 2009-09-09
> **community nerd said:**
> Try this in case your wireless card is disabled:
sudo ifconfig wlan0 [FONT=Verdana]up[/FONT]

My machine actually calls it wifi0, I think.

```
$ sudo ifconfig wifi0 up
$ password:
$ sudo ifconfig wlan0 up
$ wlan0: ERROR while getting interface flags: No such device
$ 
```Note that after the first command, it went straight back to the prompt. Other than that, nothing's changed. I tried a reboot again, just to be sure. The only option Network Manager gives me is manual configuration; it recognizes no wireless network, no matter what I do.

I also tried a soft reset of my router, but that didn't do anything either.

What were we looking for?

Here's what I've been up to, and I'll attach a couple more terminal outputs, and a screenshot of what Network Manager's showing me when I click on the toolbar applet:

```
teena@teena-laptop:~$ sudo ifdown ath0
ifdown: interface ath0 not configured
teena@teena-laptop:~$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:22:69:21:09:a3
Sending on   LPF/ath0/00:22:69:21:09:a3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
teena@teena-laptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:22:69:21:09:a3
Sending on   LPF/ath0/00:22:69:21:09:a3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
teena@teena-laptop:~$ 

```

---

### Post by mailman1175 on 2009-09-09
Here's another screenshot, taken after I enabled roaming mode.

---

### Post by realzippy on 2009-09-09
Security test special ubuntu: Nubuntu

[http://www.nubuntu.org/](http://www.nubuntu.org/)

..should run out of the box with your atheros card..

---

### Post by mailman1175 on 2009-09-09
> **realzippy said:**
> Security test special ubuntu: Nubuntu

[http://www.nubuntu.org/](http://www.nubuntu.org/)

..should run out of the box with your atheros card..

Dude, if I wanted to go through the hassle of configuring again, I'd reinstall Hardy again. I know it works. I've been using it without a problem for 3 or 4 months. I just busted something.

Thanks for the offer, but I'll pass.

---

### Post by mailman1175 on 2009-09-09
Well, I re-enabled roaming mode, told it to connect to other wireless network, gave it the name, and boom: It connected. I don't know why it never FOUND the network in the first place, but here we are.

Thanks anyway.

I promise I'm not just trying to get my post count up.:lolflag:

---

### Post by community nerd on 2009-09-09
look at my profile and look at the screenshots albums and look at hardware drivers ... right here:
[http://ubuntuforums.org/album.php?albumid=1353](http://ubuntuforums.org/album.php?albumid=1353)

---

