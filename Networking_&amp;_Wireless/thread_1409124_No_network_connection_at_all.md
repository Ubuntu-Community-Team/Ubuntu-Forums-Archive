---
title: "No network connection at all"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by jdbell63 on 2010-02-17
[COLOR="Blue"][/COLOR][FONT="Arial Black"][SIZE="4"][/SIZE][/FONT]
Hi there!  I have a new one for you.  I've tried many searches for this but the result is always WIRELESS - I have Ubuntu 9.10 installed.  Been using it no problem for months.  I have a Belkin wireless USB.  Worked fine.  Until 8 days ago.  Just stopped working.  During troubleshooting I also discovered that the wired connection also does not work.  Rebooted, checked settings, did all that.  Nothing.  I've plugged the network wire into another machine.  It picked up IP via DHCP within seconds proving that it's not the network.  I've tried everything that I can think of.

What would cause the network within Ubuntu to just stop working?  Wired and wireless.  The only thing I can think of doing now is to reinstall Ubuntu.  Any ideas?

Thanks much for your time!

---

### Post by mk4umha on 2010-02-17
I have a Dell E6400 with the Intel 5100 which was working last night until I powered off my system then booted it up this morning and the wirless is not working. Network Manager won't let me check the Enable Wireless box, it's grayed out now. I tried 2.6.31-17-generic, 2.6.31-19-generic with zero success. Anyone have any idea what happened? I'm wondering if Network Manager got updated. I'm currently on 0.7.996, is that what was packaged with Ubuntu 9.10?

---

### Post by superprash2003 on 2010-02-17
plug in the cable to this machine and type **sudo dhclient** and post output here

---

### Post by mk4umha on 2010-02-17
Interesting, if I do sudo dhclient eth0, i get an IP but I can't get out of my local network.

---

### Post by butlerproductions on 2010-02-17
I am also having trouble with the internet connectivity. I just installed Ubuntu Studio 9.10 on my laptop and it failed to autoconfigure dhcp during setup. I have cable internet through a linksys router. It is set to automatic dhcp. I don't understand because last time I installed Ubuntu Studio 8.04.1 it worked automatically on the same machine. (no internet whether wired or wireless). 
I have an atheros wireless network adaptor.
 
I have tried to install madwifi but, the build-essential part doesn't work. I am very new to Linux and could really use some help. If I could just get the internet to work I could say goodbye to Microsoft forever, but I need it for school.

---

### Post by mk4umha on 2010-02-17
I found these 2 bugs related to the Wireless switch, Network Manager and 9.10.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441161)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430809)

---

### Post by mk4umha on 2010-02-17
I figured out how to work around my issue. Somehow the Wireless Switch is off sync with the Kernel. Basically, my dell-wifi is hardblocked but my phy0 is not. They should be in sync.

I booted clean then rand this command with the wireless switch in ON position:
```
sudo rfkill list
```
[sudo] password for <username>: 
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Notice how the "HARD BLOCKED" are not the same.

I then moved the wireless switch to the OFF position.
```
sudo rfkill list
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

See how they switched states?

Now I this command to unblock all then list the options again.
```
sudo rfkill unblock all
sudo rfkill list
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
ubuntu910:~$ 

Notice now that both the "HARD BLOCKED" are now YES?

Now I put the wireless switch to the ON position.

```
ntu910:~$ sudo rfkill list
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

They're no longer "HARD BLOCKED" and my wireless is no longer grayed out on Network Manager. I don't know why it's out of sync but that's what's going on every time I boot into Ubuntu now.

---

