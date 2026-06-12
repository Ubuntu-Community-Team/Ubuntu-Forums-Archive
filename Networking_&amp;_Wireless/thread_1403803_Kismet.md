---
title: "Kismet"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by andru183 on 2010-02-10
Can some one please help me set up kismet? When I try to run kismet I get: kismet will not function if no packet sources are defined in kismet.config but I don't know what info to give it to set it up, I'm using a sitecom w171 wireless card if that info is needed

---

### Post by chili555 on 2010-02-10
You will need to edit /etc/kismet/kismet.conf. Please see:```
less /usr/share/doc/kismet/README.gz
```Especially, sections 9 and 12.

Here is the relevant section of my kismet.conf:> --- snip ---
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel
--- snip ---You can find the information in:```
sudo lshw -C network
```> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: [COLOR="Red"]Intel[/COLOR] Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 02
       serial: 99:19:d2:92:1b:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR]
--- snip ---You must change these settings to match your wireless card and driver. Not all cards are supported. Have fun and post back if you get stuck.

---

### Post by andru183 on 2010-02-10
Man thanx so much for for helping me and that realy did but I don't think my wireless card will work with it so it's give up time, thanx tho

---

### Post by chili555 on 2010-02-10
Which card is it? What driver does it use?

---

### Post by andru183 on 2010-02-11
It's a sitecom w171 and I don't know what driver it uses to be honest....

---

### Post by andru183 on 2010-02-11
Oh rite you told me how to get it, I'm using internets on my phone so it's kinda hard to read some things
product: rt2561/rt61 802.11 pci
vendor Ralink
driver:rt61pci

the vendor is in the list but not the driver, I'll add this info and see if it works but I wouldn't be too sure

---

### Post by chili555 on 2010-02-11
You should certainly try; you never know until you try. I found this, but, in Linux years, it's a bit old:  [http://www.kismetwireless.net/Forum/Equipment/Messages/1201483210.8162](http://www.kismetwireless.net/Forum/Equipment/Messages/1201483210.8162)

It says:```
Your card is not supported. It contains the RT2561/RT61 PCI chipset. It might work with the RT2500 capturesource
```You might try the capture source *rt2500*.

---

### Post by andru183 on 2010-02-11
Nope the 2400 or the 2500 didn't work, a new wireless card maybe?

---

### Post by chili555 on 2010-02-11
If you want Kismet, yes, indeed. Please look over the README to be sure the one you buy is fully supported.

---

### Post by andru183 on 2010-02-11
Will do! Thanks for everything!

---

### Post by mark bower on 2010-04-09
1) hardware is Netgear PCI WPN311 with ath5k driver (AR5001X+) and Linksys WRT54g router.

2) i have not modified kismet.conf capture sources.  section 12, "Capture Sources" calls for "source = sourcetype, interface, name".  clearly, "source type" for my setup is "ath5k", and my "interface" is wlan3.  but what do i enter for "name"?

3) kismet (2008-05 R1) launched from command line begins to work, save for the packet source msg.  so it looks like i am close to getting it to work.

mark

---

### Post by chili555 on 2010-04-09
> what do i enter for "name"?I am not sure it actually matters; you might try Atheros. After you make that change and start as sudo, are there any errors or warnings?

---

### Post by mark bower on 2010-04-09
@chilli555 - figured you would rtn as you keep a close eye on this site and lots of help to many.

on the unconfigured line in kismet.conf, it says "source=none, none, addme".  so i decided from your previous post and some other reading to take a shot that "addme" could be any text - and it appears to be true.  i entered "wlan3source" for addme (based on your model), and all works great.  i have already achieved my goal of seeing a neighbors hidden SSID, more importantly _the channel used_, so that I could adjust my router ch as far away from surrounding chs, broadcast and hidden.

but two questions if i may:  1)when i exited out of kismet, i tried to estab reconnection via network manager, all looked o.k., but could not access the web.  iwlist scan showed access points.  so i rebooted to reset.  how might reset be reestablished without rebooting? and 2) the list of APs at the top had my neighbors ch listed as "<no ssid>", but never posted the ch detected.  instead i spotted the ch in the slow, incremental scrolling of data in the STATUS window at the bottome of the screen.  is there a way once the hidden ssid, and its channel, is discovered, to see this info as static data in kismet versus a temporary observance at the bottom of the screen.

mark

---

### Post by chili555 on 2010-04-09
> how might reset be reestablished without rebooting?Some wireless cards have difficulty emerging from Monitor mode. I do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Then Network Manager takes over and I can connect.> is there a way once the hidden ssid, and its channel, is discovered, to see this info as static data in kismet versus a temporary observance at the bottom of the screen.I am not sure; I never actually encountered a hidden network in the wild. You might sort by pressing 's' and highlight the network you are watching and press Enter. That will show the network's details statically and may give you the information you are seeking.

---

### Post by alexelprogramador on 2010-04-09
> **andru183 said:**
> Can some one please help me set up kismet? When I try to run kismet I get: kismet will not function if no packet sources are defined in kismet.config but I don't know what info to give it to set it up, I'm using a sitecom w171 wireless card if that info is needed
hello

the most important thing to use any of the auditory tools is the chipset who has the card.


> sitecom w171

I dont know exactly what chipset it has, and It depends of to be on mode monitor and the efficiency of auditory tools

this sitecom device is not so famous.

The best solition is to buy a card with some atheros chipset, theare not too much expensive and you'll have lot of possibilities whith auditory toos.

---

### Post by mark bower on 2010-04-09
o.k.

method which avoided need for reboot after exiting kismet.  i used Ctrl-C which took me back to the terminal that i started from.  then i went to the wireless icon, rtclicked and unchecked "enable", then checked "enable".   web access was available.

apparently the reason the static display of the hidden SSID did not show, is that after the initial opening display and pop-up msg, one must close out the pop-up window (with the space bar). then the list of SSIDs updates.  neat, but i guess i should have tried closing out the pop-up.

in summary, i purchased the Netgear WPN311 PCI card for its linux native capability (driver in kernel), simpler to rebuild a hard drive when redoing.  i wanted kismet to determine surrounding channels, and i can. 

and i have ordered 2 more WPN311s for my other 2 linux boxes.  no big deal, at about $14 each plus shipping, that comes to less than "6 hamburgers" equivalent expense.  now maybe to read just a little more on kismet features.

mark

---

