---
title: "Disable wireless card"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by gregorus on 2009-04-23
Hello!
I've upgraded today to 9.04 and I'm havng a major problem with my d-link DWL-520+ wifi card. It's crashing my ubuntu right after loading Gnome, in 8.04 it was crashing it as well, but only when I was trying to connect to a network, so I could easily work on other wifi card. I can't remove the DWL520+ because I need it in Windows, where my other wifi card isn't working too well. I've read that you can blacklist the card drivers from loading, but I have no idea how to do it. If someone could tell how to blacklist my wifi card from console, I would gladly appreciate it:)

---

### Post by utnubuuser on 2009-04-23
Hi - Try:> [http://ubuntuforums.org/showthread.php?t=1040096](http://ubuntuforums.org/showthread.php?t=1040096)

PS  Did this card work at all under 8.04lts?  I've the same card, and in 8.04 it recognizes the network, but I've not been able to get it to connect.   Thanks

---

### Post by chili555 on 2009-04-23
This card has at least five versions and there are three different chipsets! The driver depends on the chipset. Let's ask the computer what we have. Open a terminal and do:```
sudo lshw -C network
```You will get both ethernet and wireless data. If you check the details, you will see something like this:```
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       ---snip---
 [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.108 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```Then do:```
sudo nano /etc/modprobe.d/blacklist.conf
```The nano window will open and show the file along with the key combinations to save (Ctrl+O) and exit (Ctrl+X). Scroll down to the end and type in:```
blacklist <whatever_driver_you_found>
```Proofread twice, save and close.

Upon reboot, it will not load unless it is dependent on other modules that invite it to the party despite it being blacklisted! You can see what depends on what with:```
modinfo <whatever_driver_you_found>
```Post back so the searchers will know what worked...or not.

---

### Post by gregorus on 2009-04-24
Unfortunately, I can't even check if your solution works, because every time I try to do something in console session when this card is plugged in, I'm getting a total crash after a short while. Maybe there's a way to blacklist all the dwl520+ drivers after unplugging the card-that's the only way I can do anything without 9.04 crashing.
On 8.04 it wasn't working as well, but it was crashing the system only after attempting to connect to a network.

---

### Post by gregorus on 2009-04-24
I'm still fighting with this dwl520+. Now, I've plugged it to another pc with 9.04 installed and I've been able to check the driver it's using. It says the driver is acx_pci, but after I've blacklisted it there was no difference. Also I've discoveried something interesting-when plugging in the fatal dwl520+ without the antenna and with another card connected to an internet, system doesn't crash, but your connection is getting painfully slow:confused:. The other thing is, that after checking the acx_pci driver with modinfo it says that the module cannot be found.Is there a way to check if the device is really blacklisted?

---

### Post by chili555 on 2009-04-24
I think the module is really *acx.* According to modinfo, it has no 'depends.' I'd try blacklisting it. Also, let's try to figure out the instability. I suggest you do:```
sudo cat /var/log/messages | grep acx > acx.txt
sudo cat /var/log/messages | grep wlan0 > wlan.txt
```Substitute your wireless interface if it's not wlan0. Two text files will be created in your user directory that you can transfer on a USB stick, for example, to another computer and post here.

I wonder if the D-Link is dead.

---

