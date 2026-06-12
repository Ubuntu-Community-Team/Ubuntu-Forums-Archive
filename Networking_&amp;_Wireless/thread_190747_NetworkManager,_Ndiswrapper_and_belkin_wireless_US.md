---
title: "NetworkManager, Ndiswrapper and belkin wireless USB F5D7050"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by rief on 2006-06-06
Hi all,
i have a strange problem with the new network utility of Dapper, Networkmanager: i'm using an USB belkin wireless adapter to connect with original driver ( for windows xp ) under ndiswrapper ( Ndiswrapper rulez ). Network start up with


```

sudo dhclient rausb0

```


The normal ubuntu program to manage the network give me some problems. It see my wireless connect but when I try to activate my network with the utility of ubuntu, dapper crash.  
I change network every day and i need  Network Manager of Dapper.  

Network manager see my wireless network with the name "G604T" that is right. But when I try to bring up my net with networkmanager, it seems work but it doesn't do .

My /etc/network/interfaces is:


```

auto lo
iface lo inet loopback

```


If i start up network with dhclient, network start but NetworkManager DON'T SEE it up. I'm using this util in this moment and i'm connect :D.
Any ideas? 

Thx and sorry for my english :oops:

---

### Post by jml on 2006-06-06
No need to apologize for the English.  Here are two web sites that mey be of help.

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Hope they help.

Joe

---

### Post by rief on 2006-06-07
I have followed the guide but the problem is remained. I don't understand why the command dhclient works from shell and not from any utility of gnome...

Dhclient found the network, therefore it cannot be a problem of ndiswrapper.

It could be a problem of dhcdbd? NetworkManager start up with no problems..


p.s. there is a debug for NetworkManager? Maybe from shell?

---

### Post by defconoii on 2007-08-02
network manager does not work with this card, I have it, ive googled the earth around 50 times and found a solution
1. download these drivers rt73 cvs
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
2. install them
3. set up /etc/network/interfaces to work with this once everything is installed.  

make sure u modprobe rt73 and also have removed the ndiswrapper rt73 driver because they will conflict, do ndiswrapper -r rt73 to remove then finish installing, make sure you add rt73 to the /etc/modules file to load the new kernel module after make ; make install, btw u must recompile/install this driver each time u install a new kernel
I hope this is helpfull

---

