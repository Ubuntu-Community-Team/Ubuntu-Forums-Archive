---
title: "current command line wifi config tool?"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by awestin on 2010-07-20
I'm relatively new to Ubuntu, having just installed Ubuntu 10.4 Server on an AMD home built. Ethernet works fine, and the old Netgear WPN311 PCI card I stuck in there also plays well with my WPA2-PSK router. (I got this working using the GUI networking tools after installing gnome-desktop.)

What I would like to do is replicate this, but manage and configure the wlan0 interface using the command line without GNOME. An extensive surf through the Ubuntu documentation as well as ancillary forums (including other than this one--horrors!), revealed what appears to be a mish-mash of obsolete and inaccurate references. Some say add the wlan0 data to /etc/network/interfaces, others say no, use NetworkManager. Some say WiCD replaces NetworkManager, others say it's deprecated. No one says what the CLI to NetworkManager is.

I started piecing through wpa_cli and the shell programs in /etc/wpa_supplicant and decided I didn't want to spend the next 4 years in shell gulag in a re-education program.

Would one of you kind souls please point me in the direction of a modern, command line tool that would allow me to do the following:

- set the essid and pwd for wlan0 (like iwconfig)
- set a static IP address (like ifconfig)
- make these values stick for reboot
- understand what config files control all this

Your help would be most appreciated.

_AW

---

### Post by awestin on 2010-07-27
bump.

Maybe such guides do not exist. Yes?

---

### Post by mawhrin on 2010-08-12
NetworkManager 0.8.1 includes a command line tool, nmcli. See [this]("http://ubuntuforums.org/showthread.php?t=1549395").

You may want to check first that nmcli does what you want, and download the current network-manager package first in case things horribly break and you need to roll back.

---

### Post by awestin on 2010-09-04
Thanks for your reply, mawhrin. I'll have to upgrade to 0.8.1 and try it out.

---

### Post by yitz on 2011-04-14
I'm in the same boat as you.

From the man page, it looks to me like nmcli doesn't support enough actions to be able to configure a wifi interface on its own. The assumption is that things like the password are managed by the nm-applet panel applet. It appears that with nmcli you can only bring the wifi interface up and down once it has already been configured in NetworkManager.

There is another cli interface to NetworkManager, called cnetworkmanager It is still available in Ubuntu, even though its author seems to have abandoned the project once nmcli came out. That application, written in Python, does seem to support configuring a wifi interface from scratch.

Truth is, it could be that the commands to configure a wifi are just missing from the nmcli man page, and nmcli would actually support the required commands if you know what they are. And the source code of cnetworkmanager might be a good source of information for that.

However, I am out of time for fiddling around with this. For now at least, I'm just going to to "nmcli nm enable false" and set up my network interfaces the old way in /etc/network/interfaces. That still works, fortunately.

Another good source of hints about NetworkManager is here: [https://wiki.archlinux.org/index.php/NetworkManager](https://wiki.archlinux.org/index.php/NetworkManager)

If anyone has any more details about how to configure a wifi interface in NetworkManager without having to go through a GUI, please post it!

---

### Post by chili555 on 2011-04-14
If you are aiming to get a server running without Gnome, or any other windowing manager for that matter, then Network Manager will not run; neither will Wicd. They are GUIs and require a running windowing manager, such as Gnome, KDE, etc.

A server running headless and or runlevel 3; that is, no windowing manager, will connect perfectly on boot with a properly populated /etc/network/interfaces and /etc/resolv.conf. Here are redacted examples from my computer:```
cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid myrouter
wpa-psk mywpakey

#auto eth0
iface eth0 inet dhcp
``````
cat /etc/resolv.conf

nameserver 192.168.1.254
```Post back if I can help further.

---

### Post by yitz on 2011-04-14
@chili555 Thanks for posting that information! There are more examples here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

This is a desktop system, but it has a number of different users. Some of the users have special requirements: a few need to have networking disabled while they are logged in, one uses X without a desktop manager so cannot run nm-applet. I think the right thing to do is to stop NetworkManager from running at all, even though that probably means certain things will look a little broken for normal users. Please let me know if you have any other ideas.

---

