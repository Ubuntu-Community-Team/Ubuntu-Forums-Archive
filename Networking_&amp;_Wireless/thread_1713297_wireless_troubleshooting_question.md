---
title: "wireless troubleshooting question"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by breemiller on 2011-03-23
okay so I'm running 10.10.. and have been having some issues getting my wireless to work. was following the troubleshooting steps posted at [https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html)     for device recognition 

apparently after running "sudo lshw -C networ" command in terminal your supposed to have and output and also with word say "CLAIMED", "DISCLAIMED" "ENABLED" or "DISABLED"... that was a no go I took a screenshot of my results but don't really know what's going on.

[https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html)


Much thanks in advanced for any help any of you can offer :)

---

### Post by PCNetSpec on 2011-03-23
you missed the "k" .. Open a terminal and enter:

```
sudo lshw -C network
```

hit enter, and your password when asked

And remember Linux commands ARE case sensitive, so that's a capital C

Then post the output.

---

### Post by genemerritt on 2011-03-23
Try this, I had pretty much the same thing and bought a USB wireless card. I tried to purchase a new wireless card today and I am so glad that I didn't. I worked on this for over a month.

Goto the system drop down tab top left of screen. Choose control panel, choose additional drivers and let in search until you get a list of hardware devices. My wireless card was listed but wasn't active. Choose your card and click activate it. You will need to be plugged into a network or a USB wireless card. Let it down load the drivers and see what happens. Let me know if it works.

---

### Post by breemiller on 2011-03-24
screenshot of terminal [http://i1219.photobucket.com/albums/dd436/breemiller1/lshw-Cnetwork-1.png](http://i1219.photobucket.com/albums/dd436/breemiller1/lshw-Cnetwork-1.png)

--also, i went to system drop down menu and there was no control panel, ,but there was an "Additional Drivers" option under the "Administration" option.. but the machine is not recognising ne drivers via that outlet atm... apparently because of my lack of connectivity.

---

### Post by glimmer on 2011-03-24
go to your control panel and make sure your device is connected and working properly. Make sure you can see the name of your device or else you won't be able to fix it. Maybe you should disconnect other wires first just to make sure your device is visible. Okay? Here's a good note about it wifibsd(dot)org..it helped me too when I got stuck. Well actually, I spent alot of money first before i figure it out.

---

### Post by PCNetSpec on 2011-03-24
The correct drivers seem to be loaded... what do:

```
ifconfig
```
and
```
iwlist wlan0 scanning
```

return ?

---

### Post by breemiller on 2011-03-24
okay so here is what there the first screen looks like: [http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigX2.png](http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigX2.png)

and then when I do the wlan0 scan.  "wlan0   No Scan Results"

---

### Post by PCNetSpec on 2011-03-24
It appears to be transmitting and receiving... does it list your network when you left click the networkmanager icon in the top panel (by the clock/date)... or ANY available networks.

Things to check...

is your router broadcasting its SSID  **<-- my guess is it's set not to**

does your router have MAC address filtering enabled

is your router acting as a DHCP server, or have you entered a static IP in your wireless settings.

Have you entered the correct WEP/WPA(2) key

is this an issue with security... try disabling wireless security in the router, and see if you can connect... if so, try using WEP rather than WPA

Are you sure this isn't an issue with your router?

From what I've seen so far

---

