---
title: "Basic home LAN and file transfer using Dukto and TOL"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by stevenlake on 2012-03-01
I am a beginner and would like to share how I set up my home LAN 
and transfer files using Dukto and Transfer-on-Lan with other beginners.

PC 1: Windows XP SP3; User name: **XP**; Computer name (host name): **Desktop**
PC 2: Linux Mint 9 Isadora; User name: **Mint**; Computer name(host name): **Laptop**

**1. Assign IP manually**
On XP computer: 192.168.1.1
On Mint Computer: 192.198.1.2
Subnet mask: 255.255.255.0
Connect two computers with an Ethernet cable. 
You might need a crossover cable for older computers.
You might need to reboot and disable your firewall.

In Windows XP:
Start > Settings > Control Panel > Network Connections > Right-click Local Area Connection > 
Properties > Internet Protocol (TCP/IP) > Properties > Use the following IP address

[IMG]http://i.imgur.com/930ET.jpg[/IMG]

[IMG]http://i.imgur.com/qraGf.jpg[/IMG]

In Linux Mint:
System > Preferences > Network Connections > Wired > Add

[IMG]http://i.imgur.com/Q8PtB.png[/IMG]

**2. Using Dukto to transfer files**

[IMG]http://i.imgur.com/UhxOa.jpg[/IMG]

Choose where to save your files.
You can also drag and drop files on selected user to transfer files.
[IMG]http://i.imgur.com/I2jL7.jpg[/IMG]

You can also click on buddies, recent, about and icons at the bottom for more information.
[IMG]http://i.imgur.com/PUvIE.jpg[/IMG]

---

### Post by stevenlake on 2012-03-01
**3. Using Transfer On Lan to transfer files**

On my computer it says this IP is not available. Just click OK and ignore it.
[img]http://i.imgur.com/9Pnth.jpg[/img]

[img]http://i.imgur.com/viiQ2.jpg[/img]

[img]http://i.imgur.com/RZlcB.jpg[/img]

Here's the tricky part.
I have to use Ctrl+Enter to go in the folder to select the file I want to send.
Click on the folder doesn't work for me.
[img]http://i.imgur.com/IEmzH.jpg[/img]

For Dukto and Transfer-On-Lan:
No internet connection required.
No user name and password required.
Recommended for Local Area Network.

TeamViewer is another option:
Internet connection required.
Password required.
Recommended for transferring files to a friend via the Internet.

[http://code.google.com/p/dukto/](http://code.google.com/p/dukto/)
[http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)
[http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

---

### Post by Roasted on 2012-03-01
Just to add, I didn't use a 3rd party utility, but if you set up your static IPs just like you did, you can access the other machine via:

Ubuntu to Windows - Open Nautilus, hit CTRL L, type smb://192.168.1.X (x being the IP Windows has)

Windows to Ubuntu - Start - Run - \\192.168.1.X (x being the IP Ubuntu has)

Great tip!

---

