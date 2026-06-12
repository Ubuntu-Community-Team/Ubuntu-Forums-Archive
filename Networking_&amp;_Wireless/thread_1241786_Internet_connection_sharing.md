---
title: "Internet connection sharing"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by snotplop on 2009-08-16
Using Ubuntu to share one wireless internet connection to other machines on a network


I've searched quite a bit and there are few, sparse and terse howtos on internet connection sharing in Ubuntu.
I managed to work out a reliable method that turns the whole tedious process into three easy steps, and I thought this would be a great starting point for many.

For those interested, I am running Ubuntu 9.04 (Jaunty) with all the current patches.
In my setup I am sharing the internet connection connected through my wifi adapter (wlan0). The connection is being shared on my ethernet port (eth0). I'm already connected to the wireless network I intend to share.
[B]
==Initial Configuration==[/B][INDENT][INDENT]$ sudo apt-get install dhcp3-server firestarter
$ sudo ln -sf /etc/init.d/dhcp3-server /etc/init.d/dhcpd
$ sudo nano -w /etc/default/dhcp3-server
[/INDENT]Change the line[INDENT]INTERFACES=""
[/INDENT]to[INDENT]INTERFACES="eth0"
[/INDENT](I am going to be supplying ip addresses to every machine connected to the ethernet port [eth0]. NOTE:The connected machines will be in an entirely different subnet than the wireless point's pool. If you don't want this, look into "network interface bridging")

Right click on Network-Manager in the panel and select "Edit Connections..."[INDENT][ Wired ] > [Add]
Connection name: Shared internet connection
[ IPv4 Settings ] > Method: Manual > [Add]
Address: 10.0.0.1 > Netmask: 255.255.255.0 > Gateway: 0.0.0.0
[x] Available to all users > [Apply]
[/INDENT]Attach the ethernet cable to (eth0). Click on the Network-Manager and select "Shared internet connection" under the "Wired Networks" heading[INDENT]$ sudo firestarter
[/INDENT]The first time running firestarter, you will be presented with the Firewall Wizard.[INDENT][Forward] > Please select your Internet connected network device: (wlan0) > [  ] Start the firewall on dial-out > [x] IP address is assigned by DHCP
[Forward] > [x] Enable internet connection sharing > Local area network device: (eth0)
[Forward] >[  ] Start firewall now
[Save]
[/INDENT][INDENT][Preferences] >  Firewall/Network Settings > [x] Enable DHCP for the local network >  (> DHCP server details
[x] Create new DHCP configuration > Lowest IP address to assign: 10.0.0.2 > Highest IP address to assign: 10.0.0.200 > Name server: <dynamic>
[Accept]
[/INDENT]Test if the DHCP server is functioning by enabling the firewall: [Start Firewall]
If the firewall status changes from "Disabled" to "Active" without any error messages you're good to go!
[/INDENT]**==Usage==**[INDENT]
[LIST=1]
[*]Ensure you're connected to the wireless network you intend to share. Plug in the ethernet cord you intend to act as a gateway for.
[*]Click Network-Manager and select "Shared internet connection" under the "Wired Networks" heading. (There will be a notification when the card is fully reconfigured
[*]ubuntu menu > Internet > Firestarter
[/LIST]

As long as Firestarter starts up without any error messages and the status is "Active", the gateway is set up and the other machines should be able to use dhcp to obtain addresses and ultimately internet connectivity.
[/INDENT]**==Notes==**

[LIST]
[*]Since we didn't set up "Shared internet connection" as the default profile to be used with eth0, every time the ethernet cord is removed from the port the connection will be reset. Simply close firestarter if you have it open and repeat the 3 connection steps.
[*]Why didn't we make "Shared internet connection" the default profile for (eth0)? This is to ensure that if your machine ever comes across an ethernet connection used for internet connectivity, you should still be able to just plug it in and Network-Manager will do the rest. Internet connection sharing is probably going to be a more rare, specialized occurance than internet connectivity in a foreign place.
[*]To refresh IP addresses on machines that were already on the network before it was uplinked through your gateway DON'T just reconnect the connection! The entire process will reset and you'll have to start over. 

Just either use Network-Manager > "auto eth0" under the "Wired Networks" heading [Ubuntu]  or "repair..." or whatever the daily equivalent is in M$ Windoz.
[/LIST]

Hope this helps some fellow travelers out there...

---

### Post by quixote on 2009-08-18
Interesting!  Thanks for that!

---

### Post by tuahaa on 2009-08-18
I might use this for connecting to Xbox live via my laptop since the official guide doesn't work.

---

### Post by potrick on 2009-09-06
This guide is fantastic, and I'm so close...but for whatever reason DHCP isn't setting up properly. I get the message 

"No subnet declaration for eth0 (10.0.0.1)."

How can I get this working?

---

### Post by potrick on 2009-09-06
Hey guys, nevermind, I figured it out. This is fantastic! Thanks so much for providing such a workable solution...

---

### Post by snotplop on 2009-09-17
Glad to hear it worked out for you :)

---

### Post by snotplop on 2010-07-16
Oh wow I always know where to find this

(Still working in Lucid)

---

### Post by Gerrit Bijlsma on 2010-07-18
Hi,
I have been struggling with Internet sharing, with Windows, OS X and Ubuntu.
In Windows XP Vista and 7, only windows PC's could share the internet with the windows sharing host. No OS X, no Ubuntu and not even my Nokia E90
On OS X it is very simple to set it up and everything works.
On Ubuntu (up until 9.10) I tried with dhcp3, firestarter, etc... Nothing worked.
After a fresh install of Ubuntu 10.04 x64 on my HP-TX2, I started again to try to share the internet connection.
I use a USB CDMA modem to access the internet because I live on a boat
and I want to use my E90 and other PC's to share that CDMA connection.

I first downloaded Wicd network manager, but it did not do the job. (again)
I did not install DHCP or Firestarter.
Then I did something that is too simple to believe:
I opened the network connection manager and edited the the wired ethernet adapter settings: IPv4 method set to "Shared to other computers"
I connected the Windows 7 PC with an ethernet cable and it received an IP adress from the Ubuntu 10.04 PC and it worked!!
All to my amazement but as simple as that!

Then I created an ad-hoc network and set the IPv4 method to "Shared with other computers"
To my surprise it worked too!
After rebooting the Ubuntu machine, I only have to click "create a new Wireless Network" but selecting the same SSID as I did the first time and all PC's can share my ad-hoc internet connection! Even both using an ad-hoc and wired connections!

I hope this will help you all.

When I want to use a wifi hotspot I simply set the method back to DHCP.

---

