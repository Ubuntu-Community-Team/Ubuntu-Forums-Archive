---
title: "Does ubuntu suport WEP Key for WIFI?"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by USA1 on 2006-02-15
Hello,

Replaced my WIFI router and at least in windows all my problems are solved.

I did setup a WEP key to secure the router, but now ubuntu won't connect to the router.  I find the connection, it sees it, but won't latch on to it.

I use the gui interface to try to set it up. I selected the correct connection, I selected the HEX option and pasted the network key from a windows txt document, but it won't connect.

Help please....

If there is an area of computer that I hate the most, is networking.
Everything that has to do with networking has a mind of its own and work whenever it feels like it.

I am tire of spending money and time for nothing to work no matter what I do.

Got to go to linux class today, I will ask my teach about this issues, hopefully I can get help on stuff that is some what out of the class.

---

### Post by odix on 2006-02-15
maybe you entered the wep key in the wrong format, for my prism54 I have to enter it in one row without any other character, e.g. "123456789abe78...

regards

---

### Post by USA1 on 2006-02-15
After class today I stayed at school trying to connect and it wouldn't even connect to the open WIFI that they have in that area of campus.

I wonder what could have changed since last night.  Just before I went to bed it was working fine at home with an open connection on the linksys router.

In the morning after setting up a WEP, neither XP nor Ubuntu would connect anymore.  I reset the router to its defaul with no special settings. At that point XP was able to connect but at a very slow speed. Ubuntu would not connect.

Ran and got a new Belkin router and set it up right after the Linksys router so that now both routers are connected. XP still working at snail speed with the linksys, I switched it to the Belkin router and it picked up rightaway.

Booted Ubuntu, it connected this time but it choose the Linksys, I guess because it already had settings in memory for that router.  Tried to change it to the new Belkin, it would not do it.

Finally I took out the linksys router and put it to rest. Then I setup the new router properly and secured it with a 128bit WEP.  XP picks up on the new configured router rightaway.  Booted Ubuntu and configured with the new WEP Key. It still refuses to connect.

AFter that I went to class, tried to connect from school to an open connection, it acts like is setup right but it won't connect.

Ndiswrapper shows the device active. It is up, I sees all the networks in the area, but it just won't let go of its old values. It continues to try to connect to the new connection using settings from the old Linksys.

How can I clear the memory for the network connections...

Help Please.

---

### Post by DarkED on 2006-02-15
I used the GUI inside Gnome in Ubuntu. I knew the name of my network and typed it in, don't use WEP, everything works fine...

---

### Post by Lambert on 2006-02-15
Run this command to reset the device, I take it you're using ndiswrapper.

sudo iwconfig wlan0 ndis_reset

Post the output of this command

sudo lshw -C network

Just want to see info on your device.

Network settings are not cached, the only thing I know cached is any dhcp settings which is found in /var/lib/dhcp3/dhclient.leases But this is just a fall back if you're connected to the same router and no dhcp packet is received. It goes to this file as a backup and tries those settings to see if they work, so it might be this. 

You can try to configure the interface at the command line with this command sequence

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ___ key ______
sudo dhclient wlan0

you can read more in the man page of iwconfig

After plugging in the card and trying to connect to the ap, run dmesg and look for messages referencing the card or driver and also look in /var/log/syslog for information.

---

### Post by USA1 on 2006-02-15
I took the computer to class early today, my teacher played with it for about 4 minutes just before class, but it would not connected to the open connection in that area of campus.  I was in the room next to where the router is located, very close to the source.

Now I am at the library where they also have several open WIFI connections that are active throughout the whole building.  Guess what, I am typing this reply from Ubutun connected to one of the Open WIFI.  I booted Ubutun, when to network manager, selected one of the connections from the list, clicked okay and it connected rightaway.

I wish I could find a more reliable way handle this WIFI because at this point there is nothing solid that I can go buy, it works now, then it doesnt work later. It works here, it might not work there...

What do you people think of all this....

I bet you when I get home it won't connect tonite, but it might in the morning, who knows... there is no control of it!



[QUOTE=USA1]After class today I stayed at school trying to connect and it wouldn't even connect to the open WIFI that they have in that area of campus.

I wonder what could have changed since last night.  Just before I went to bed it was working fine at home with an open connection on the linksys router.

In the morning after setting up a WEP, neither XP nor Ubuntu would connect anymore.  I reset the router to its defaul with no special settings. At that point XP was able to connect but at a very slow speed. Ubuntu would not connect.

Ran and got a new Belkin router and set it up right after the Linksys router so that now both routers are connected. XP still working at snail speed with the linksys, I switched it to the Belkin router and it picked up rightaway.

Booted Ubuntu, it connected this time but it choose the Linksys, I guess because it already had settings in memory for that router.  Tried to change it to the new Belkin, it would not do it.

Finally I took out the linksys router and put it to rest. Then I setup the new router properly and secured it with a 128bit WEP.  XP picks up on the new configured router rightaway.  Booted Ubuntu and configured with the new WEP Key. It still refuses to connect.

AFter that I went to class, tried to connect from school to an open connection, it acts like is setup right but it won't connect.

Ndiswrapper shows the device active. It is up, I sees all the networks in the area, but it just won't let go of its old values. It continues to try to connect to the new connection using settings from the old Linksys.

How can I clear the memory for the network connections...

Help Please.[/QUOTE]

---

