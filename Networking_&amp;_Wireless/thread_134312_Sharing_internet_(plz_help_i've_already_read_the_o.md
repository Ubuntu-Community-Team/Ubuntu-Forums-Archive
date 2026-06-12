---
title: "Sharing internet (plz help i've already read the other threads but dosen't work)"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by bmccruz on 2006-02-21
Hello

I want to share my internet connection on my ubuntu desktop with two other computers. A desktop and a notebook both running XP.

My internet connection on my ubuntu pc is provided by a USB ADSL that I was able to put online. I got dynamic ip.

The way to share the internet connection will be WIFI. But i guess there is no big problem there since the ubuntu detected the wireless card.



What should i do?

Should i use a wifi manager? Witch one?

I've to change some configuration or do something on the XP computers?


I have tried firestarter but i didn't work... (nothing happend on the XP computer altought on the ubuntu it said that was connected by wireless)


Thanks and sorry for my english

---

### Post by Killgore on 2006-02-21
I cant help you much with the wifi, but wired is ok.

First of all you need to give the ubuntu PC a static ip. Open Administration -> Networking. Find the ethernet card that the XP machine is attached to and click Preferences. Where it says DHCP change it to Static IP and enter something like 192.168.0.1
The subnet mask will be put in automatically. Restart the computer and make sure you can still connect to the internet.

On the XP machine click on Start -> Control Panel -> Network Connections.
Find the ethernet card that is attached to the ubuntu machine and right click then Properties. Scroll down to TCP/IP and click properties underneath. Change "obtain an IP address automatically" to "use the following IP address". Enter something like 192.168.0.2. Enter the subnet mask and make the default gateway:
192.168.0.1 (or whatever you entered in the ubuntu machine).

Restart the windows computer and try to use the internet.

Hope this helps
PS. Any veterans who can see a problem here feel free to scold me

---

### Post by br4inwash3r on 2006-02-22
no luck here man. still can't connect.

by the way, my ubuntu pc is connected to the net using usb cable modem. and i'm also trying to share the connection with an winXP machine. these two pc's are connected through a hub.

i'm dying to get a simple walktrough. coz all the stuff i found on the net is way too many, and yet different from one another.

sorry if i sound so demanding. but i really need a simple solution...linux is still too complex for me. that's all for now....thx

---

### Post by Zeroangel on 2006-02-22
Well, I don't know much about setting up Wifi (i've only set up corded Windows networks) but this is what I would do.

1) Establish that your other PC's can 'see' your Ubuntu machine. This can be done by sharing a folder on the network or by having the other machines 'ping' the Ubuntu machine. 

For example, open up the command line in the other machines ( start -> run -> 'command' for Win98/ME or 'cmd' for Windows2k/XP) and type in the following:
ping 192.168.0.1
Of course, replacing that IP address with the one that you've set up on your Ubuntu machine.

If your other machines cannot 'see' your ubuntu machine then you will need to configure them automatically. Also note that if you change the IP address of your Ubuntu box while the other machines are on, then they will not know that the IP address has changed! So you will need to restart them so that they rescan the network and actually see your machine. IOW: Restart the other computers whenever you change your IP address.

~~~~~~~~~~~~~~~~~~~~`
Remember that, whenever you want to have the other machines on the same network as you (ie: for file sharing or internet connection sharing) then you the first 3 sections of IP addresses of them must be the same as your main box, and the main box must be have .1 as their fourth address. Like this.

Ubuntu: 192.168.0.1 (.1 designates it as a server)
Client1: 192.168.0.2 (.2 can be any number from 2 to 255, but it must be unique)
Client2: 192.168.0.3 (.3 can be any number from 2 to 255, but it must be unique)

Most of the time Client1 and Client2 will search the network when they boot and autoconfigure themselves. When they see that there is a computer available (especially a *.*.*.1 computer), they will set their IP's to be similar (but different) to that computer's IP, and so be able to access the network.

---

