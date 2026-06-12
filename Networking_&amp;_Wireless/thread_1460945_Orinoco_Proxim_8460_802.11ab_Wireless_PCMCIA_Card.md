---
title: "Orinoco Proxim 8460 802.11a/b Wireless PCMCIA Card"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by horsechoker on 2010-04-23
Here are some specs...

HP Compaq nx6110 laptop
built in wireless NIC: Intel Corp PRO/Wireless 2915ABG (Calexico2)
PCMCIA wireless NIC: Orinoco 802.11a/b Proxim 8460

I'd like to use the Orinoco card instead of the onboard intel wireless NIC. The problem I'm having is both cards are disabled and I can't seem to enable either of them. There is a button on my laptop to turn the antenna one but it does not work. 

I don't care about the onboard intel card AT ALL. I only want to use the Orinoco card. 

Ubuntu recognizes the Orinoco card. With the card plugged it, the card is assigned to wlan0, but disabled. 
sudo ifconfig wlan0 up doesn't seem to do anythingl've been using the following guide to troubleshoot:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Any help would be greatly appreciated...

---

### Post by horsechoker on 2010-04-24
Any help available? :confused:

---

### Post by horsechoker on 2010-04-24
To further troubleshoot...

I tried installing NetworkManager..

running nm-applet i get the error 'No connections defined'

To attempt to fix this, I edited the nm-system-settings.conf file to the following:

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=[COLOR=DarkRed]true

[COLOR=Black]This didn't help - no connections defined error still. 

Any ideas?
[/COLOR][/COLOR]

---

