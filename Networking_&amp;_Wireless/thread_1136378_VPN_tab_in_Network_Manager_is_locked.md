---
title: "VPN tab in Network Manager is locked"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by emendelson on 2009-04-25
Here's a puzzling one that I hope someone can help with.

Jaunty running in VMware (but without the VMware Tools installed): When I click on the network manager icon, and then Configure VPN, the VPN tab has an icon that shows it as locked, and I can't create a VPN connection. I've gone into Users and Groups and given myself the privilege of doing just everything that's listed, and restarted, but I still can't unlock that VPN tab.

Curiously, this problem didn't occur with Jaunty beta, but I wiped out the beta and installed a fresh copy.

If anyone can suggest a solution, I'll be grateful.

---

### Post by mykrob on 2009-04-25
you need to install a vpn package in synaptic, for example, openvpn-networkmanager or something to that effect.

Open up Synaptic, and search for vpn. Install the network manager vpn package that pertains to the type of vpn you need to connect to.

---

### Post by emendelson on 2009-04-25
Edit: This solution worked. Thank you! (My original version of this post was mistaken; apologies.)

---

### Post by dvimont on 2009-08-24
I have been trying for several weeks to enable my Dell Mini 9 with Ubuntu 8.04 to be configured to access a PPTP-based VPN.

Like the first poster in this thread, my VPN tab in my "Network Connections" GUI interface is locked.

After googling for hours, the most straightforward advice I have founds seems to come from:  
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)
This page says that the following packages must be installed for VPN access to be possible:
network-manager-gnome
network-manager-openvpn
network-manager-pptp
network-manager-vpnc

The first package, network-manager-gnome, came pre-installed on my machine, and I have had no problem installing two of the other three packages, HOWEVER, when I use Synaptic Package Manager to try to install network-manager-pptp, I get a message saying that installation of this package will require UNINSTALL of network-manager itself, as well as network-manager-gnome!!
I appear to be very close; I apparently just need to find a way to install the plug-in network-manager-pptp without needing to uninstall network-manager and network-manager-gnome.

Any assistance would be greatly appreciated by this Ubuntu newbie!

Thanks

---

### Post by Fungus on 2009-08-27
I'm no expert at this, but I got the impression that PPTP is a different protocol than standard VPN.

Hence, you may not really need openvpn, and its conflicting with the other plugins, and you got the installation problem.  

Your documentation link says, [SIZE="3"]"If you need VPN support via network manager in Kubuntu Feisty you have to install the following packages:

network-manager-gnome
network-manager-openvpn
network-manager-pptp
network-manager-vpnc"[/SIZE]

you are running Hardy 8.04 not Kubuntu Feisty which may require both.

you might try removing the openvpn and seeing if the pptp will install.

---

### Post by dvimont on 2009-08-31
Thank you for the suggestion.  I did try removing network-manager-openvpn, but I am still experiencing the same problem (i.e., when I use Synaptic Package Manager to try to install network-manager-pptp, I get a message saying that installation of this package will require UNINSTALL of network-manager itself, as well as network-manager-gnome).

But it was certainly worth trying out your suggestion.

I remain stumped.  Any additional recommendations would be very much appreciated!

---

### Post by Fungus on 2009-09-02
Maybe it is trying to tell you that you need to start with a clean slate?  

Have you tried un-installing the built-in network manager and/or network-manager-gnome?  (I thought they were the same thing?)  I think you can uncheck them in the applications/add-remove thingy.

THEN try to install network manager-pptp.

Good luck, buddy.

---

### Post by itchyball on 2009-09-15
I have the same problem, do you find something that worked?

---

### Post by dvimont on 2009-09-16
To itchy:  No, I have not found a solution for this problem.

To fungus:  Your last suggestion is certainly reasonable -- simply follow the instructions you are given and see if it works.  This is actually the very first thing that I tried, about a month ago.  When network-manager and network-manager-gnome were UNinstalled from my machine, this disabled all Internet connectivity, which of course is not a workable state for my machine to be in.  After the uninstall I unfortunately could not use Synaptic Package Manager to reinstall the two packages (since I had no Internet connectivity), so I had to use another machine to download the appropriate .deb files for the reinstall.

I am still in a quandary as to how to enable VPN on my Dell Mini running Ubuntu 8.0.4 ...

---

### Post by Fungus on 2009-09-18
Sorry to hear of your difficulty.  I know how frustrating this stuff can be.

Maybe something in this post will spark an idea for you? 

[http://ubuntuforums.org/showthread.php?t=1250825]("http://ubuntuforums.org/showthread.php?t=1250825")

I used 9.04. Maybe the wireless networking works differently on this.

---

