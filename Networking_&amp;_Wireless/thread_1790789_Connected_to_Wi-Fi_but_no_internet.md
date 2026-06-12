---
title: "Connected to Wi-Fi but no internet?"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by jdwhite87 on 2011-06-25
I can connect to my router but no web pages will load etc... I can connect my phone to the router and USB tether it to my laptop and everything works fine. I can also connect to my neighbors router and everything works fine.

I have tried put my routers IP in /etc/resolve.conf but to no avail. I also tried putting 8.8.8.8. 

I'm really at a loss here....

Edit: Toshiba Sattelite A215 laptop (RS690 wireless card?) and a Linksys router.

---

### Post by An Sanct on 2011-06-25
There has to be something wrong with the configuration of the router, '8.8.8.8' and '8.8.4.4' resolves to Google DNS (I use them, too).

Maybe you have MAC filtering turned on, DHCP disabled or something else, that prevents Ubuntu connecting successfully.

---

### Post by jdwhite87 on 2011-06-25
> **An Sanct said:**
> There has to be something wrong with the configuration of the router, '8.8.8.8' and '8.8.4.4' resolves to Google DNS (I use them, too).

Maybe you have MAC filtering turned on, DHCP disabled or something else, that prevents Ubuntu connecting successfully.

Two other computers and 3 phones are connected to it just fine...

---

### Post by An Sanct on 2011-06-25
Well, are there any *special* settings with those other devices, that work?

- my point being, that there should not be any problems with the connectivity, because Ubuntu is installed.

---

### Post by jdwhite87 on 2011-06-25
> **An Sanct said:**
> Well, are there any *special* settings with those other devices, that work?

- my point being, that there should not be any problems with the connectivity, because Ubuntu is installed.

No nothing special. Thats why I'm at such a loss :D

---

### Post by An Sanct on 2011-06-25
That's weird ... As a last resort, you could try [wicd]("http://ubuntuforums.org/wicd.net") as your network manager. But please before doing so, get another opinion. Also please post the type of router and wireless card you are using.

---

### Post by jdwhite87 on 2011-06-25
> **An Sanct said:**
> That's weird ... As a last resort, you could try [wicd]("http://ubuntuforums.org/wicd.net") as your network manager. But please before doing so, get another opinion. Also please post the type of router and wireless card you are using.

Ok. I'll take a look at wicd and add router  and wireless card info to first post.

---

### Post by An Sanct on 2011-06-26
With this wireless card there are some problems in combination with Linux (- not just Ubuntu) There is a solution here for [interpid ibex]("http://undiff.com/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/") (8.10), but the same procedure should work in near to any version.

PS. google the name of the wifi card and Ubuntu...

---

### Post by Toz on 2011-06-26
It would help if you provided more detailed information about your wireless card. Can you open a terminal window, type in the following commands, and post back the results (in code blocks)?
```
lspci -vnn
lshw -C network
lsmod
rfkill list all
```

Reference: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices")

---

### Post by An Sanct on 2011-06-26
Toz: he edited his first post and named the card in it .... [#1]("http://ubuntuforums.org/showpost.php?p=10980802&postcount=1")

---

### Post by Toz on 2011-06-26
That's still really not enough info to help troubleshoot. He should run those commands in a terminal window and post back - for a start anyways.

---

### Post by barrenoort on 2012-02-04
I had a similar problem using Ubuntu Studio. Internet access stopped working for no apparent reason while the OS reported a valid connection to the wireless router. I finally fixed the problem (after exhausting all the power cycling tricks I could) by deleting the wireless connection to the router that wasn't working, then after a reboot I used the command...
*sudo iwlist wlan scan*
to get the routers SSID, then I manually added a connection (luckily the default settings seemed to work fine, I only had to fill in the SSID)

It worked for me at least...

---

