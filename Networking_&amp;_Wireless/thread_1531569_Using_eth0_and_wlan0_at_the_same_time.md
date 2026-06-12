---
title: "Using eth0 and wlan0 at the same time"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by Guerreiro on 2010-07-15
Dear esteemed Ubuntu-users,

I have a wired connection going to my router, which is encrypted with WPA2-PSK. That works fine. I hooked up a WUSB54G v4 (Linksys USB Wireless Adapter), and used ndiswrapper to install the drivers from Vista to make it compatible with WPA2. Also configured the /etc/network/interfaces with the wpasupplicant lingo to make it all work. So if I do that, my eth0 will not work anymore. Also on a side note my network manager stops with displaying in the top panel. Not a problem I can run /etc/init.d/networking (re)start and dhclient eth0 (wlan0) and all the other commands that are necessary to make it work.

Back to the problem, so I hook up wlan0 with the settings and eth0 stops working. I want to use the wlan0 solely for the purpose of my media server. The eth0 is there for my internet and that is it :) .

How can I keep 'em separated? 

Thank you all in advance.

Have a nice day.

If you need more information, ask me please.

---

### Post by Iowan on 2010-07-15
It's easier if the two interfaces are in different subnets.
Check **man route** for some more information. :)

---

### Post by Guerreiro on 2010-07-15
You mean give them a different netmask? Or a complete different IP? These are questions I had aforehand reading the manual of route. Starting up Terminal, sudo bash and man route here i come :D

Read man route;

Do I add the PS3 as a host to the route of wlan0 ? Do i reject the default gw of wlan0? Do I do both?  :) I am still confuzzled. :S

---

### Post by capscrew on 2010-07-15
> **Guerreiro said:**
> You mean give them a different netmask? Or a complete different IP? These are questions I had aforehand reading the manual of route. Starting up Terminal, sudo bash and man route here i come :D

What it means is that you need 2 distinct networks (subnets).  For example ```

192.168.[COLOR="Red"]**[SIZE="4"]1[/SIZE]**[/COLOR].0 /24 
This has a subnet mask of 255.255.255.0

192.168.[COLOR="Blue"]**[SIZE="4"]2[/SIZE]**[/COLOR].0 /24 
This also has a subnet mask of 255.255.255.0

```

The network in both of the above examples is the 192.168.n part.  The subnet mask is also the first 3 sections (called octets).

With these 2 separate networks you would by definition be using different IP addresses even if the last section of numbers and the subnet mask was the same.  This can be seen by the following example:```
192.168.[COLOR="Red"]**1**[/COLOR].10 - s/m 255.255.255.0
192.168.[COLOR="Blue"]**2**[/COLOR].10 - s/m 255.255.255.0

```

Now you need to create a gateway or router configuration on the Ubuntu host.  The reason is the you can't have 2 interfaces (wlan0 and eth0) in the same subnet on the same host.


See [**_here _**]("https://help.ubuntu.com/community/Internet/ConnectionSharing")for ICS with Ubuntu.

---

### Post by Guerreiro on 2010-07-16
Now I got you :) All right let me try that stuff out tonight. First 8 hrs of work :(

---

### Post by Guerreiro on 2010-07-16
The solution I have in my mind is this, ICS and make my wireless an AP. So the PS3 connects to my wireless (same network so server should work) and also can connect to internet because my wireless will be directed to my eth0 (default gateway) . When and if I manage this I will post here what I did, for future people who have this problem or question. Wish me luck. :D

---

### Post by Guerreiro on 2010-07-19
Ok after a weekend of trying different solutions, I am going to go with using mediatomb. [http://mediatomb.cc/](http://mediatomb.cc/)

You can use your wireless like an AP, but my card does not support Master mode.
 ie. iwconfig wlan0 mode master

You could use airbase-mg (of the aircrack-ng suite) to broadcast a SSID, it does so by creating a tapdevice at0, but that did not do the trick for me either. 

I use mediatomb and at least my wireless only does what it needs to do and the only drawback is no subtitles. I can live with that. :D

Have a nice day.

---

