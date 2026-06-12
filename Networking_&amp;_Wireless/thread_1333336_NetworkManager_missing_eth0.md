---
title: "NetworkManager missing eth0"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by karthikb23 on 2009-11-21
Hi,
After trying what i could: I am unable to figure out why NetworkManager does not handle eth0 (a wired interface).
Glancing through the logs (I am running Ubuntu Hardy):

[COLOR="Magenta"]Nov 21 20:59:47 ubuntu NetworkManager: <info>  starting...
Nov 21 20:59:47 ubuntu NetworkManager: <info>  Updating allowed wireless network lists.
Nov 21 20:59:47 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
[/COLOR]

It does not however seem to detect eth0.

My /etc/network/interfaces:

[COLOR="Magenta"]auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
[/COLOR]

From nm-system-settings.conf (This file was missing! I created it manually):

[COLOR="Magenta"][main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
[/COLOR]

The NetworkManager applet simply states 'No network Connection', despite its settings showing eth0 correctly configured (The very reason I am able to post this thread :))

Any Help is greatly appreciated!!!

---

### Post by lswb on 2009-11-21
Nwtwork manager does not manage interfaces if they are managed in /etc/network/interfaces. Try with everything removed or commented out of /etc/network/interfaces except for

auto lo
iface lo inet loopback

---

### Post by Iowan on 2009-11-21
If you need the static configuration, you should be able to add that through Network Manager's "Manual configuration". If you upgraded to Hardy from previous version (like I did), the upgrade process left the manual configuration in */etc/network/interfaces*.

---

### Post by karthikb23 on 2009-11-21
Thanks Guys, but I had already tried these both b4 posting :)

I commented out everything from t interfaces file, and had NM configure it using t manual option.

Now, even though i can connect to t net, the NM icon on t panel shows an 'exclamation' mark, and on a mouse over, it shows 'No Network connection'.

Just to add (may its useful??), the NM folder in /etc was missing the file 'nm-system-settings.conf', and even now does not contain the folder 'system-connections', n likewise, a file for eth0.

This is t case with my Ubuntu box.

NM works fine for wired in OpenSuse on my other box, n even has the mentioned files.

I am really unable to find good documentation on NM!
Much as its easy to chuck it n turn to WICD, now my curiosity will not let me rest, until I know how to make it display my wired connection in active state ;)

Please Help :)

---

### Post by karthikb23 on 2009-11-21
n just to add again, the logs do not reflect NM accessing eth0.
This is what is bothering me........ :(

---

### Post by Iowan on 2009-11-21
My Hardy */etc/NetworkManager* directory contains only a directory named *dispatcher.d* I'll need to do some research to find (remember?) where NM stashes it's configuration.

---

### Post by karthikb23 on 2009-11-22
Thanks!
Even i am checking on it.... will post if i do catch hold of something.

---

### Post by VastOne on 2009-11-22
OP FYI

I had this same issue and from another thread I read about WICD

I installed it from Ubuntu Software Center and then followed these instructions - 

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

to the  T including getting network interfaces back to its original state of: 

auto lo
iface lo inet loopback 
 

I then configured wicd as a static ip and am very impressed with it over network manager.  It is working flawlessly

---

### Post by karthikb23 on 2009-11-25
Well, finally i did away with NM!
IT even resolved my firefox automatically starting in offline mode. (I had tried modifying the config for firefox.... but i did not see it use NM).

I use WICD btw :).... on my laptop... It is really neat with wireless!

I am just curious to know what is it that WICD does that NM does not..... (Why on earth wont it work, for such a simple setting of mine!)

Thanks!

---

### Post by ManzTiara on 2009-11-25
Dear all,

but we already try with WICD and looks like good enough from NM, when the NM is ignored settings in /etc/network/interfaces beside lo

But right now i have a question, when i set the static address for eth0 with 192.168.1.15 at WICD, after restart i always get 192.168.1.101 , when see the proses use ps, i saw the dhclient is running.
so everytime after restart i should run the /etc/init.d/networking restart 
this problem is make inconvenience to me because networking is not run smoothly.

but if i turned off, my wireless connection cannot connect to the network.

Why we should get the 192.168.1.15 ? because my laptop is engaged with factory machine that we have get the data on it. that machine is only know the 192.168.1.15 address.

How do i resolve this problem ?

I'm use the karmic.

TIA

---

