---
title: "Qwest wireless dsl modem"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by trumsey2005 on 2006-01-21
anyone ever connected successfully to a wireless DSL modem. Mine is an Actiontech gateway, just curious cause I am trying to get my friend to switch to Ubuntu or Kubuntu Linux and that is gonna be the selling point.

---

### Post by Bone Down on 2006-01-23
I am currently utilizing qwest dsl via actiontec with no problems... i have two linux machines and three windows machines soon to have 3-4 lin machines soon.

---

### Post by Bone Down on 2006-01-23
you will most likely only have issues with IPv6.. I worked around this by disabling it all together within the aliases file within modprbe.d directory.

now giam and xchat work fine as well as firefox.

---

### Post by azteech on 2006-01-23
[quote=trumsey2005]anyone ever connected successfully to a wireless DSL modem. Mine is an Actiontech gateway, just curious cause I am trying to get my friend to switch to Ubuntu or Kubuntu Linux and that is gonna be the selling point.[/quote] 
I have been using the 710 actiontec DSL gateway modem (with wireless) provided by Qwest for about 2 1/2 years now. I have experienced no problems with the modem when using the ethernet and usb connections, or when using the wireless option without security options enabled. 

I am running a home network where I currently have a desktop (Ubuntu and Kubuntu installed) and 2 laptop computers (running Ubuntu), a file-sharing server (running linux), and three winblows machines - a desktop (wife's - who refuses to switch to linux because of the graphics work she does), a print server, and a backup laptop. All the linux based computers are connected via a linksys hub to the actiontec DSL gateway modem. I have the wife's computer connected directly to the modem via USB (gives her a slower connection) and the print server is connected to the modem via wireless.

When I first set up the home network, I kept the DSL Gateway modem's wireless side active all the time; however, a while back I discovered there are several others in my general area who are running wireless. When my network and internet access slowed to a crawl one day, I investigated and found that others outside my network had made inappropriate connections to my wireless modem. Therefore, to maintain network security I have the actiontec DSL Gateway modem set up to accept only specific MAC addresses and not broadcast the SSID, and have winblows network options on the print server set to not share files and folders. When the print server is not in use, I turn off the wireless modem on the server, and disable wireless on the dsl modem (note: this causes the dsl gateway to do a reboot). Until I can find time to sort out the security side of the wireless port (wep,  wep+802.1x, wpa, etc.), I will continue to do what I have been doing. 

Please note that the wireless security problem is not a Ubuntu or linux only issue - this is a problem within the computing community as a whole. There are many good articles on the Internet that point out just how widespread the wireless security issue is.

---

### Post by trumsey2005 on 2006-01-24
I need to know a basic how to step by step to configure the connection in Ubuntu, the modem is set and the drivers are installed I just need to configure.

---

### Post by azteech on 2006-01-24
[quote=trumsey2005]I need to know a basic how to step by step to configure the connection in Ubuntu, the modem is set and the drivers are installed I just need to configure.[/quote] 
Please expand on "the modem is set and the drivers are installed".

What modem is set and what drivers have you installed?
Are you using Ubuntu, or another flavor of linux?

If you need help configuring a network connection there is plenty of howto information available if you search the forum. Another place to look is [http://help.ubuntu.com/starterguide/C/ch07.html#confignetwork](http://help.ubuntu.com/starterguide/C/ch07.html#confignetwork)

If you need help configuring the actiontec modem, the basic instructions that came with your qwest install package, will suffice. Once you have the modem set up, either connect the computer directly to the modem's ethernet port, or if you are trying to set up a home network connect each computer to a hub, and the hub's uplink port (with a standard patch cable) to the ethernet port on the actiontec modem.

Then when it is all installed, you can then install Ubuntu. As long as the Ubuntu software recognizes the NIC, and the actiontec modem is set for DHCP, the Ubuntu software will properly configure the network card for internet access.

---

### Post by trumsey2005 on 2006-01-24
I mean the modem itself is already configured and the rtl8180 drivers are properly installed. I need to configure the wireless network connection in Ubuntu. I dont really know where to start, it is dhcp broadcast essid which the wireless card picks up, 64 bit wep, where to I enter all the values in linux?

---

### Post by azteech on 2006-01-25
[quote=trumsey2005]I mean the modem itself is already configured and the rtl8180 drivers are properly installed. I need to configure the wireless network connection in Ubuntu. I dont really know where to start, it is dhcp broadcast essid which the wireless card picks up, 64 bit wep, where to I enter all the values in linux?[/quote]

See if the following forum entry helps with your situation:
[http://www.ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180](http://www.ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180)

---

### Post by gpda on 2006-02-05
I have just installed ubuntu 5.04,the Hoary Hedgehog,  on an old PC 233/256.  It installs fine and synchs clock over the internet connection. 

The connection is ethernet to an actiontec modem with qwest DSL.  All lights on the modem work, network shows in ubuntu dialog box as configured/working.

This modem was previously working on the same box with Windows XP installed.  I followed the Qwest install instructions on their enclosed CD, worked fine with Internet Exploroer, then I installed Firefox on XP and that worked.

However, now with ubuntu I cannot get Firefox to work.

Possibly I am no longer logging into the Qwest/MSN premium ISP arrangement correctly? or at all?

Could someone let me know about qwest dsl specific settings for firefox and ubuntu.  Thanks.
-G

---

