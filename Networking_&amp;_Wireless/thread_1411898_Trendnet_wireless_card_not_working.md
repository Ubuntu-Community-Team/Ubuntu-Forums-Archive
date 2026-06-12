---
title: "Trendnet wireless card not working"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by darkstarfa22 on 2010-02-20
I have been trying to get my Trendnet TEW-649UB wireless card to work on Karmic.  I have ndiswrapper "installed", but it doesn't seem to be working.  I have reinstalled ndiswrapper-utils 1.9 and ndiswrapper-common from synaptic, but not ndisgtk (the GUI for ndiswrapper). When I try to see if any drivers are installed using terminal (ndiswrapper -i) the terminal freezes on me.

Previously I tried using the help doc for [installing Trendnet wireless drivers]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W:B1_%28ndiswrapper%29"), but I was met with no success.  After my first try using the help doc it seemed that ndiswrapper was working correctly and the driver was installed, but when I tried to connect to my network my wireless was listed as "device not managed".

If this helps at all the current state of my /etc/network/interfaces is:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

When I run iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

but when I try to install the driver using ndiswrapper -i I get the message: driver net8192su is already installed

Right now my computer is not even reading that the wireless card is avaliable.  When I left click on the network icon I can only see that I am on a wired network {ifupdown (wlan0)}.

My computer is dual booted with Vista and the card works there, but for some reason I am having trouble with Ubuntu. :-k
Thanks for any help you can provide!

---

### Post by Bleek on 2010-04-21
Bump

same type of issue with the trendnet tew-649su

any help would be appreciated

---

### Post by arjuntank on 2010-04-21
if driver net8192su is already installed then try 

$ sudo depmod -a

Might help..

---

### Post by Bleek on 2010-04-22
Tried that and nothing happens. 

It seams that when I installed 9.10 it defaulted a realtek driver to the tew-649su. 

When I use ndiswrapper with GUI I install the net8192su.inf and it shows hardware detected. But network configuration pops a message "network tools could not be located" along those lines as I am not at the machine right now.

Should I blacklist the default driver and try the 8192su or is the realtek driver good and I need to configure something else?

Thanks

---

### Post by nilbus on 2010-04-29
I didn't have to use ndiswrapper to get my TEW-624UB USB card working. 

This post got it working for me:
[http://ubuntuforums.org/showpost.php?p=8786509&postcount=16]("http://ubuntuforums.org/showpost.php?p=8786509&postcount=16")

---

