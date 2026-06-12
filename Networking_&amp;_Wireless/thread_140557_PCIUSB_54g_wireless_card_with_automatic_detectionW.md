---
title: "PCI/USB 54g wireless card with automatic detection/WEP on Ubuntu installation?"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by sgreszcz on 2006-03-06
Is there a PCI/USB 802.11g wireless card that will be automatically detected by Ubuntu during installation?

When I installed Ubuntu on my laptop with an Orinoco PCMCIA card it was automatically detected, it asked for my WEP key/password, and then proceded to continue the installation over the wireless network connection.

Is there a PCI/USB card that would work for sure on installation with Breezy?  If not, will more wireless cards be supported during installation if I wait for the next release of Dapper Dan?  The reason I need this is I need to guide a non-computer person to install Ubuntu on a remote machine for me, enable wireless, and allow me to complete the configuration over SSH/VNC.

Thanks,
Stephen

---

### Post by csevcik on 2006-03-09
Belkin 54g F5D7010 works quite well using the Win XP drivers provided with the card and using ndiswrapper.

1- Make sure the ndiswrapper-utils package is installed in your machine. You can easily install it with the adept package manager if it is not installed.
2- Copy the content of the "driver" folder in the CD to some folder in your machine say "WiFi" (I am assuming that WiFi is in youre home folder and that you are also in your home folder while type what follows).
3- open a terminal window (konsole in Kubuntu).
4- type in the teminal window
**sudo ndiswrapper WiKi/PMCIAbcml5.inf**
(I renamed this file to bcml5.inf to avoid writing the PMCIA part)
5- If your card is plugged and you type
**ndiswrapper -l**
you should get a message saying
[B]bcmwl5  driver present, hardware present
[/B]
6- Type
**sudo ndiswrapper -m**
if you get a message
**modprobe config already contains alias directive**
just ignore it.
7- Type
**sudo modprobe ndiswrapper**
8- Type
**modprobe -l ndiswrapper**
you should get a message like
**/lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko**
which means that your kernel has ndiswrapper suport.

9- Type
**sudo ifup wlan0**

Here you will get a series of mesages while the card goes up. Now you may need to configure the card with iwconfig to set your network name and WEP crypt password. Suppose your WiFi network is called "home" and requires a crypt passwd like 2c34bb56a31245dd2367c8e4f5, then:

[B]iwconfig wlan0 essid home
iwconfig wlan0 key 2c34bb56a31245dd2367c8e4f5[/B]

should do it

10- Type 

**iwlist scanning**

to get info on you card. Is advisable to check "man iwconfig", "man ifconfig", "man ifup", "man ifdown" and "man iwlist" for more info in case of troubles.

Any further configuration you may require for your net is is easier configurin the wlan entry in your "Network Settings" entry from the "System Settings".

---

### Post by sgreszcz on 2006-03-10
Thanks for the detailed post.  I would try something like this if it was me doing the installation, but I'm trying to remotely support the installation of Ubuntu by a complete Linux novice.  

I did some more research, and I think that I will try and pick up the D-Link DWL-G520 as according to this link [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("Ubuntu Supported Wireless Network Cards") this card should be supported upon install (like my Orinoco Gold PCMCIA card on my laptop was).



Thanks again, and hopefully this can help someone else installing with ndiswrapper.

Stephen

---

