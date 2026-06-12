---
title: "Need to manually run dhclient wlan0 each boot"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by WalmartSniperLX on 2010-05-05
I did a search on the Forum and on Google but failed to find a direct answer to how I can fix needing to type this in the CLI after each boot. I'm fairly new with wireless networking in Linux beyond the realm of broadcom chipsets. My current chipset is:

```
05:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

Or is there a way to create a init script to do that for me? Sorry, once again, I'm new at this.

---

### Post by GSF1200S on 2010-05-05
> **WalmartSniperLX said:**
> I did a search on the Forum and on Google but failed to find a direct answer to how I can fix needing to type this in the CLI after each boot. I'm fairly new with wireless networking in Linux beyond the realm of broadcom chipsets. My current chipset is:

```
05:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

Or is there a way to create a init script to do that for me? Sorry, once again, I'm new at this.

Do you use nm-applet to connect to the internet or are you not running a network manager? Im actually having somewhat of the opposite problem. I can connect fine to a network (wireless in my case) using nm-applet yet invoking dhclient with X killed never gets a dhcp release. My thread is here:
[http://ubuntuforums.org/showthread.php?t=1463982]("http://ubuntuforums.org/showthread.php?t=1463982")

I dont know how to fix your problem if you do use nm-applet, but you could use /etc/network/interfaces to setup your network. Lets say your wireless device is wlan0. The file (/etc/network/interfaces) that originally looks like this:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

you would change by adding the information for wlan0:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Wireless device- call this whatever you want
auto wlan0
iface wlan0 inet dhcp
wireless-essid networkessid

Then save and exit. If you have a WEP network, it only requires one more line:
> auto wlan0
iface eth1 inet dhcp
wireless-essid networkessid
wireless-key 5BA323BF25
WPA im not sure with, but there should be posts out there for this..

It should work fine when you boot up once these changes are made. Again, this is only if you dont use network manager (nm-applet). Of course, it would probably be beneficial to have /etc/network/interfaces handle things in case you ever needed to do work with APT from the command line (X fails, etc) anyways.

Good luck :)

---

### Post by WalmartSniperLX on 2010-05-05
Hello. Thanks for the reply. I do use nm-applet however if I can't get past this issue I may drift to an alternative way, like the one you've mentioned. I'll give it a shot and see how it works out. Good luck to you too! I would give some advice, however I'm struggling to even grasp what I'm doing here :p

---

### Post by GSF1200S on 2010-05-05
> **WalmartSniperLX said:**
> Hello. Thanks for the reply. I do use nm-applet however if I can't get past this issue I may drift to an alternative way, like the one you've mentioned. I'll give it a shot and see how it works out. Good luck to you too! I would give some advice, however I'm struggling to even grasp what I'm doing here :p

Ehh.. I noticed in your reply to my thread that you use WPA encryption. So, if you are gonna get this setup by /etc/network/interfaces, it will take a little work. This thread covers it pretty thoroughly:
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834") 
Ill try to answer any questions you have since I can startup WPA on my router..

---

### Post by GSF1200S on 2010-05-06
> **WalmartSniperLX said:**
> Hello. Thanks for the reply. I do use nm-applet however if I can't get past this issue I may drift to an alternative way, like the one you've mentioned. I'll give it a shot and see how it works out. Good luck to you too! I would give some advice, however I'm struggling to even grasp what I'm doing here :p

I strongly suggest giving wicd a shot. You will have to remove gnome-network-manager in order for it to work, however. It fixed my dhcp problem (although your problem and my problem are different from one another), and it seems to work well/stable. Its in the repos:
```
sudo apt-get install wicd wicd-gtk
```
If you ever need network from the command line (or just have it as a precaution), I would suggest installing the ncurses interface for wicd allowing you to get a connection even if X is killed:
```
sudo apt-get install wicd-curses
```
and it can be started by using:
```
wicd-curses
```
This might be much less of a pain then trying to setup /etc/network/interfaces, assuming it works as it should.

I suggest grabbing a debian package for both network-manager and network-manager-gnome BEFORE you remove it, just in case wicd doesnt work for you. Alternatively, you can use dpkg-repack:
```
sudo apt-get install dpkg-repack
```
and then to make the packages:
```
sudo dpkg-repack network-manager
sudo dpkg-repack network-manager-gnome
```
and it will place the deb packages in your home folder. Then, you can just double click on them to install them if wicd doesnt work for you.

Good luck :)

---

### Post by konradpiskorz on 2010-05-23
Hey,

If your still dealing with this problem there is a easy workaround for this.  NetworkManager, the backend of nm-applet runs scripts every time you connect to a new network.  These scripts are stored in /etc/NetworkManager/dispatcher.d

As long as all your wireless is DHCP this will work great.  Otherwise the code would have to be modified.

Add this to /etc/NetworkManager/dispatcher.d as a file.
```

#!/bin/bash
# This script runs dhclient when using wireless

if [ "$1" = "wlan0" ]; then
	if [ "$2" = "up" ]; then
		dhclient wlan0
	fi
fi
```

Network Manager runs scripts in alpha order, you would want this script running after 01ifupdown (which is included there) so name it 02dhclient.

1]So, to add this script, open gedit, copy and paste this code into a new file.

2]Save the file to your home folder as 02dhclient.

3]Open a Terminal and go to your home folder (should be there by default).  just to be safe.
```
cd ~
```

4]Type the following code to copy the file over to network managers settings.
```

sudo mv 02dhclient /etc/NetworkManager/dispatcher.d
```

5]You have to make the file capable of being run.  So chmod it
```
sudo chmod +x /etc/NetworkManager/dispatcher.d/02dhclient
```

6]Restart networking services with the following command
```
sudo /etc/init.d/networking restart
```

And you shouldn't have to type in the dhclient command again as long as your running nm-applet.  I have to say this isn't my favourite solution as have to add a script to a network manager to allow the network manager to do it's job is a bit ludicrous... However nm-applet is causing a lot of problems in Lucid and this seems to be the most efficient solution as far as your time is concerned.


Alternatively if you wanted dhclient to run on boot so that you have it running even without nm-applet.  You would have to add a script to /etc/init.d which would be a simple
```
#!/bin/bash
# This script runs dhclient

dhclient wlan0
```

chmod it to allow it to run.  Then create a symbolic link to it in /etc/rc#.d where rc# would be the run level you wish for it to run.  i.e. rc5.d for run level 5

A further explanation of this can be found in [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")

---

