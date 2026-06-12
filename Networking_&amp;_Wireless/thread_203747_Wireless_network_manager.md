---
title: "Wireless network manager"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by Blazeix on 2006-06-25
Hi, I'm looking for some tools that will allow me to scan for wireless networks and let me connect to them under Xubuntu. I believe I already have the wireless drivers set up, I just need the tool that lets me connect. The thing is that I would prefer a non-KDE and non-Gnome tool, because I'm using xubuntu and I don't want all the frameworks. Can anyone point me toward a good tool? Thanks.

---

### Post by Agent86 on 2006-06-26
There's gtkwifi: [http://sourceforge.net/projects/gtkwifi]("http://sourceforge.net/projects/gtkwifi")
I don't use it myself, since it doesn't support WPA. I have to use Gnome Network Manager to get WPA working for my Netgear WG311v2.

---

### Post by Blazeix on 2006-06-26
Hmm, it says that GTKWifi is a GNOME panel applet. When I check the dependencies, it says that it needs python2.4-gnome2. Is it really independant of gnome?

I've downloaded and installed 'network manager' ([http://packages.ubuntu.com/dapper/net/network-manager](http://packages.ubuntu.com/dapper/net/network-manager)) via apt-get, but I can't seem to figure out how to start it. I might need a front end for it, but I'm not sure.

---

### Post by Agent86 on 2006-06-26
[QUOTE=Blazeix]Hmm, it says that GTKWifi is a GNOME panel applet. When I check the dependencies, it says that it needs python2.4-gnome2. Is it really independant of gnome?[/QUOTE]I thought that it was lightly dependent on GNOME, since the standard Xubuntu has some GNOME in it already - if you're logging in at the pretty blue Xubuntu or brown Ubuntu screens, you've got at least gdm installed, along with it's GNOME dependencies. When I last looked at GTKwifi, I only saw a couple of GNOME dependencies, maybe it's more tied to GNOME now.
> I've downloaded and installed 'network manager' ([http://packages.ubuntu.com/dapper/net/network-manager](http://packages.ubuntu.com/dapper/net/network-manager)) via apt-get, but I can't seem to figure out how to start it. I might need a front end for it, but I'm not sure.Open up a terminal and type```
nm-applet
```you should get the Network Manager icon in the upper-right corner next to your clock. Click on the icon to get a list of available networks, click on the one you want to connect to.

---

### Post by Blazeix on 2006-06-27
Thanks for all your help.  I'm using xdm and I don't have any gnome dependencies. I decided to install the gnome network manager anyway, since I will eventually need WPA. I'm using fluxbox as my window manager. I didn't get a response from nm-applet, so I tried running 
nm-tools. I got the following output:

```
$ nm-tool

NetworkManager Tool

State: disconnected

print_devices(): didn't get a reply from NetworkManager.
There are no available network devices.
```

I thought I had all my drivers worked out, but does this mean that I don't? when I run "ndiswrapper -l" I get this output:

```
$ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
```

It appears that everything is working, but not the network manager.

---

### Post by Agent86 on 2006-06-27
[QUOTE=Blazeix]```
$ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
```It appears that everything is working, but not the network manager.[/QUOTE]
Is ndiswrapper currently loaded? Does the result from```
lsmod | grep ndiswrapper
```show ndiswrapper? If not, check your /etc/modules file, ndiswrapper should be listed in this file so it's loaded at bootup.

Check your /etc/network/interfaces file. All lines for interfaces other than lo should be commented out, since NetworkManager likes to handle the network interfaces by itself.

---

### Post by Blazeix on 2006-06-28
I put ndiswrapper into /etc/modules, and rebooted. Now lsmod shows that ndiswrapper is loaded. I checked /etc/network/interfaces, and eth0 was uncommented, so I commented it out. However, upon reboot I could not connect to the internet at all, so I have since uncommented it. Some other pertinent info is that the light that usually is on when wireless is enabled (under windows) is not on under linux. Maybe this means that the driver is unconfigured?

EDIT: I was following the instructions from here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)
I sucessfuly complete the 'Install Windows Driver' section, but I do not see something like this: 
"ndiswrapper: driver ''driver1'' added"
in dmesg. I will try reinstalling the driver tomorrow.

---

### Post by Agent86 on 2006-06-29
[QUOTE=Blazeix]I put ndiswrapper into /etc/modules, and rebooted. Now lsmod shows that ndiswrapper is loaded. I checked /etc/network/interfaces, and eth0 was uncommented, so I commented it out. However, upon reboot I could not connect to the internet at all, so I have since uncommented it. Some other pertinent info is that the light that usually is on when wireless is enabled (under windows) is not on under linux. Maybe this means that the driver is unconfigured?[/QUOTE]If you've got live wired ethernet port(s), it should be ok to leave the eth0 and eth1 lines uncommented. You should comment out lines dealing with wlan0 or ath0 or anything like that.
> EDIT: I was following the instructions from here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)
I sucessfuly complete the 'Install Windows Driver' section, but I do not see something like this: 
"ndiswrapper: driver ''driver1'' added"
in dmesg. I will try reinstalling the driver tomorrow.Before reinstalling, do a clean reboot, then immediately open up a terminal and do dmesg and see if ndiswrapper successfully loaded on boot. I also followed that instruction page and didn't see a successful ndiswrapper load in dmesg after running the ```
modprobe ndiswrapper
```command, but did see success after listing it in /etc/modules and rebooting.

---

