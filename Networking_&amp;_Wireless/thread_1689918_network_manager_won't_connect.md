---
title: "network manager won't connect"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by peedeeramone on 2011-02-17
I have a desktop on a wired campus network. typically i use DHCP on this machine. The campus network went down for a bit and I noticed later that my other devices were able to connect and access the internet through the campus network, but my desktop was not. decided to try to pull a new address from the DHCP server.  i went to do this through network manager, but its icon was not there. i couldnt remember the command to start network manager at the time so i looked up on another devices ways to pull a new IP from the command line. long story short none of them worked, i remembered the command to start network manager (when did it move to being an indicator applet? i thought that was only being tested in natty?) and was unable to connect through that either. when auto eth0 is selected (my usual connection type) it showed the signal bars but they didn't show any sign of activity (the lighter colored bar moving up and down etc. like when its actually connecting). I even tried to manually assign an IP address. It would "connect" but there was no internet access. I know that the settings should work because i have used them on other machines in the past. regardless i want to have a dynamic IP instead of static because of typical university policy. 

anyway, can someone help me figure out how to revert it back to proper settings or whatever the defaults are? for reference i will try to copy over the commands i used:

sudo /etc/init.d/networking restart
sudo dhclient -r
sudo dhclient
sudo /etc/init.d/network restart
sudo ifdwon eth0
sudo ifup eth0
killall -9 dhcpd
sudo dhclient

^i assume my problem lies with one of these commands

after that i ran nm-applet and got the network manager running, but still couldnt connect. i have also restarted a few times to no avail either. 

any help would be appreciated.

i can give the results of an ifconfig if needed, but as im not on that computer i dont want to manually copy over any info unnecessarily.

thanks
Pd

---

### Post by peedeeramone on 2011-02-17
i played with it a little more.

whats odd is that when run as a standard user nm-applet (network manager) runs as an indicator-applet, but when run as root nm-applet functions as a notification-area icon. also the terminal reports a bunch of glib warning and critical messages. i want to say that not long before i started experiencing this problem i either did an upgrade or the upgrade only partially occurred. I dont really remember, but could this have had something to do with my problem?

---

### Post by peedeeramone on 2011-02-18
shameless bump.

---

