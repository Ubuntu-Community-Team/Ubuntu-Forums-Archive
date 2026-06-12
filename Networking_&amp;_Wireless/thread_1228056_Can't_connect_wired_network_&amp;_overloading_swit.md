---
title: "Can't connect wired network &amp; overloading switch"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by wildmanmatt on 2009-07-31
Hi,

I have a new install of Kubuntu 9.04, but I am unable to connect to my wired network. My motherboard has Gbit networking ports, but I don't seem to be able to use either of them.

I am running on an 
MSI K9N SLI Platinum nForce 570 SLi motherboard
with an
AMD Athlon 64 X2 5600+ processor
and an
Asus EN8800GTS/HTDP/320M 8800GTS 320MB DDR3 DVI-Ix2 HDTV PCI-E graphics card.

My network is setup with a Gbit unmanaged switch and a gateway router sitting behind an ADSL modem. I have no problems accessing the internet with any of my other devices (Mac, Vista, OpenSUSE and Voip phones)

Whenever I boot up my kubuntu box and login to KDE, the network doesn't start by default, and when I click on the ethernet icon in the tray, I am shown one Networking Interface as Unavailable and one as Disconnected (I presume because one is plugged in, but not connected and one is not plugged in)

I have then tried clicking on the Auto eth1 button (which I guess related to the top interface which shows Unavailable ?) and then all of the other wired devices are kicked off my network and I have to unplug the kubuntu box from the network and reset the switch to get them back on again.

When I installed, I had to use the alternate installer and use the nolapic flag - could this have any impact? (but I haven't manually added this to my bootloader after installing)

It would be great to know what might be causing my problems and perhaps find a resolution...

I have tried the following in /etc/network/interfaces

The default: 
```
auto lo
iface lo inet loopback
```

and tried to set statically:
[HTML]# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.123.101
gateway 192.168.123.254
netmask 255.255.255.0
network 192.168.123.0
broadcast 192.168.123.255[/HTML]

and then run
```
sudo /etc/init.d/networking restart
```

This just led to the same problem with all other wired devices being unable to access the network.

Help would be much appreciated.

Thanks,

Matt

---

### Post by wildmanmatt on 2009-07-31
As an aside...the install tried to setup the network connection automatically, but for some reason was unable to contact the DHCP server (even though I know it's active and everything else connects fine with it) - I did encounter the same problem with all other wired devices being disconnected when setup did try to connect though...

---

### Post by wildmanmatt on 2009-07-31
This is what my router's DHCP log shows: 

```
2009 Jul 31 16:57:30 [DGFV338] [dhcpd] DHCPDISCOVER from 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:30 [DGFV338] [dhcpd] DHCPOFFER on 192.168.123.101 to 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:34 [DGFV338] [dhcpd] DHCPDISCOVER from 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:34 [DGFV338] [dhcpd] DHCPOFFER on 192.168.123.101 to 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:39 [DGFV338] [dhcpd] DHCPDISCOVER from 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:39 [DGFV338] [dhcpd] DHCPOFFER on 192.168.123.101 to 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:48 [DGFV338] [dhcpd] DHCPDISCOVER from 00:16:17:95:a2:05 via bdg
2009 Jul 31 16:57:48 [DGFV338] [dhcpd] DHCPOFFER on 192.168.123.101 to 00:16:17:95:a2:05 via bdg
```Perhaps my system is not accepting / receiving the DHCPOFFER correctly? Would there be a reason for that?

---

### Post by wildmanmatt on 2009-07-31
Having wandered around the forum trying to solve my networking problem...I stumbled upon the following post in one of the stickies:

> **monkeylytics said:**
> I upgraded Jaunty, and networking wasn't available for my onboard ethernet on my Asus A8n-sli which is an Nvidia MCP55 setup even though it was working on Intrepid. After struggling for hours to find a solution for Jaunty and my ethernet setup, I remembered that I had the same problem on my upgrade to Intrepid and this did the trick:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

This also works for Jaunty (surprising to see the problem persist into Jaunty.)

Steve

Following on to that url on launchpad there is the following solution in post 69:

```

a) become superuser
$ sudo su
 b) remove forcedeth kernel module (it's the ethernet's driver)
# rmmod forcedeth
 c) load forcedeth kernel module again with new parameters
# modprobe forcedeth msi=0 msix=0
 d) restart networking
# /etc/init.d/networking restart
 You should be able to connect to your network now.
```


That solution solves my problem and allows my network interface to connect properly and for me to browse the net...


However, I find myself unable to make this permanent by following the further steps, also shown in post 69:


```


Step 2, configure the system to do this automatically from now on when it starts
(otherwise you'll need to do the above steps every time you boot).
 Open a terminal and become root with
$ sudo su
 a) go to /etc/modprobe.d/
# cd /etc/modprobe.d/
 b) edit the options file
# gedit options
 c) go to end of file and add the following lines (without the quotes)
"#nVIDIA Corporation MCP55 Ethernet"
"options forcedeth msi=0 msix=0"
 d) save the changes and close gedit
 e) you'll need to rebuild your boot image, in the same terminal type:
# update-initramfs -u
 Reboot and you're done.
```


This is because I don't have an options file in /etc/modprobe.d/ that I can go to the end of and find nVIDIA Corporation MCP55 Ethernet


Am I looking in the wrong place? Might there be somewhere else that I can find a file to edit to make the workaround permanent?


Thanks,


Matt

---

