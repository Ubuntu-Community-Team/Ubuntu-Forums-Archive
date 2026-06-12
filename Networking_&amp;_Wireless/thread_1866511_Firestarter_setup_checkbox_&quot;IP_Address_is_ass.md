---
title: "Firestarter setup checkbox &quot;IP Address is assigned via DHCP&quot; question!"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by Rytron on 2011-10-21
Hi.

I have a query about setting up Firestarter. On setup there is a checkbox with "IP Address is assigned via DHCP". How do I know if I am assigned my IP address from DHCP? Does this refer to my public IP address? i.e. When someone goes to a place like [www.ip-adress.com/ipaddresstolocation/](www.ip-adress.com/ipaddresstolocation/)

[http://imagecdn.maketecheasier.com/2009/03/firestarter_wiz2.jpg](http://imagecdn.maketecheasier.com/2009/03/firestarter_wiz2.jpg)

---

### Post by lightwarrior on 2011-10-21
If your computer is accessing the internet behind a modem or router, then your IP address is assigned by the modem/router and it is an LAN IP, usually these are 192.168.x.x, it is DHCP.

Your ISP will issue an IP to your link (modem), this IP is on the WAN, and is probably DHCP.

Unless your setup needs to login and password from your PC directly to your ISP and you paid for a fixed IP address.

---

### Post by Rytron on 2011-10-21
> **lightwarrior said:**
> If your computer is accessing the internet via a modem or router, then your IP address is assigned by the modem/router and it is an LAN IP, usually these are 192.168.x.x

Your ISP will issue an IP to your link (modem), this IP is on the WAN.

So I am assigned an IP Address from DHCP so I should check that box @ [ATTACH]205073[/ATTACH]

---

### Post by lightwarrior on 2011-10-21
Yes.

---

### Post by lightwarrior on 2011-10-21
Since it is a firewall, if you have several computers behind it, you will need a second ethernet card and configure your own DHCP server to issue IPs inside your LAN (eth1).

[http://www.fs-security.com/docs/dhcp.php](http://www.fs-security.com/docs/dhcp.php)

If you do this, just make sure your eth0 is the only one device connecting to the internet modem.

---

### Post by Rytron on 2011-10-21
Thanks. I connect to my wireless modem/router to access the internet and it usually has a different IP address at [www.ip-adress.com/ipaddresstolocation/](www.ip-adress.com/ipaddresstolocation/) each time the modem/router is powered on.

I saw a YT video somewhere where they setup Firestarter but did not check that DHCP box. What kind of setup did they have since they did not get their IP address from a DHCP server?

---

### Post by SparTacux on 2011-10-21
The IP address your modem gets from your ISP is NOT the same as the IP address your computer gets from your modem.  Your modem will give a different IP address to every computer connected to it. You can configure the modem to give out IP addresses to your computers via DHCP or set them up statically so that the same computer gets the same ip address each time it connects to your modem. You also have to configure Ubuntu Network Connections on each computer to set up static ip's. By default Ubuntu is configured to get it's IP address from the modem via DHCP.

---

### Post by Rytron on 2011-10-22
Thank you SparTacux for helping me out.

So just to confirm -- I do mark the box "IP Address is assigned via DHCP" in Firestarter?

---

### Post by SparTacux on 2011-10-22
I've not used Firestarter in ages and opted to use GUFW instead. The die hards on here set-up their firewalls using ip-tables directly as you can do more with them by doing it manually. 

To answer your question I would say YES. If you don't set  DHCP on Firestarter then Firestarter will probably BLOCK the DHCP traffic so your computer can't get an IP address from your modem. That's my guess as to what will happen if you don't tick the DHCP 'button'.

You can always run the Firestarter wizard a second time if you get it wrong.

---

### Post by Rytron on 2011-10-23
Cheers again.

Do I need to add Firestarter to 'Startup applications' with **sudo /usr/sbin/firestarter** or **sudo /usr/firestarter**?
How can I tell if Firestarter is running in the background? I don't see it in 'System Monitor'.

---

### Post by SparTacux on 2011-10-23
> **Rytron said:**
> Cheers again.

Do I need to add Firestarter to 'Startup applications' with **sudo /usr/sbin/firestarter** or **sudo /usr/firestarter**?
How can I tell if Firestarter is running in the background? I don't see it in 'System Monitor'.


Dunno - give both a try :-)
I wouldn't have it running myself and just start Firestarter if I need to make changes to the Firewall for whatever reason.

Having it running on your desktop looks pretty since it shows BLOCKED traffic and gives you some basic network info but in reality you don't need it running for it to protect your computer. Once you set your Firewall rules in Firestarter it should write those rules to linux ip-tables which will be loaded every time you re-start your computer.

You can verify this by running terminal and typing sudo iptables -L

---

### Post by Rytron on 2011-10-23
> **SparTacux said:**
> Dunno - give both a try :-)
I wouldn't have it running myself and just start Firestarter if I need to make changes to the Firewall for whatever reason.

Having it running on your desktop looks pretty since it shows BLOCKED traffic and gives you some basic network info but in reality you don't need it running for it to protect your computer. Once you set your Firewall rules in Firestarter it should write those rules to linux ip-tables which will be loaded every time you re-start your computer.

You can verify this by running terminal and typing sudo iptables -L

Ah, your explanation re the IP Tables clears that up. So really Firestarter or any IP Tables frontend for that matter would only be required to make settings. Gotcha. Thanks again my friend.

---

