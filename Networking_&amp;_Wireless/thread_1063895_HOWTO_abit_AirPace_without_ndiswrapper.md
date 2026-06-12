---
title: "HOWTO: abit AirPace without ndiswrapper"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by canoemoose on 2009-02-08
Right!  By reading until my eyes went square, I've found a way to use the abit AirPace PCI-e WiFi card under Linux with native drivers.
Standard disclaimer: I'm not a genius, just lucky.  Don't take my word as law.  This may break your system.  That's not my fault.

Big thanks to luks911 who started me down the right track!

This HowTo assumes ethernet internet access and an otherwise working installation of any flavour of Ubuntu 8.10 Intrepid Ibex.  I've used it on Mythbuntu 64 bit and Ubuntu.
If you've been playing with Wicd, remove it and reinstall the standard network manager through Synaptic Package Manager.

It ought work for any card with an Atheros AR242x chipset, but is untested.

1)  First thing to do is disable the suggested drivers; go to the Restricted Drivers Manager wherever it is on your system (Applications>System>Hardware Drivers on Mythbuntu) and disable "Support for Atheros 802.11 wireless LAN cards".  There may be something else relating to HAL and Atheros based cards, but I didn't have it.
Reboot.

2)  We need to blacklist the usual drivers, so open up your editor of choice (I use nano):
```
sudo nano /etc/modprobe.d/blacklist
```

We need to add the suggested driver to this list to prevent it being loaded. Add the following to the bottom of this file:
```
# This is the wrong driver for the AirPace WiFi card
blacklist ath9k
```
If you've been mucking about with MadWifi and/or ndiswrapper then add the relevant lines also:
```
blacklist ath_pci
blacklist ndiswrapper
```
Save the file and exit the editor (<Control-x>, <y>, <Enter> in nano)

3)  Now, we can find and install the driver which works.
Install the backported modules:
```
sudo apt-get install linux-backports-modules-intrepid
```

Go back to the Restricted Drivers Manager and "Support for 5xxx series of Atheros 802.11 wireless LAN cards" should be "Activated but not in use" if you click on it.

4)  We can now load the driver.
Check that none of the blacklisted drivers are running:
```
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ndiswrapper
```
Load the new driver:
```
sudo modprobe ath5k
```
Right-click on the network manager applet in the notification area, disable wireless, enable it again.  If you now left-click on it, your network should show up on the list.  Click your network and if it connects, then we've just got to make it permanent.  If it doesn't, sorry but I can't help :(

5)  Time to make it permanent.
Add it to the list of kernel modules loaded at boot:
```
sudo nano /etc/modules
```
Delete any line which is one of the modules blacklisted earlier (ndiswrapper, ath9k or ath_pci) and add the following line to the bottom:
```
ath5k
```
Save and exit.
Reboot and check your WiFi still works!

---

### Post by Conorm1 on 2009-03-07
Hi Canoemoose,

Worked a treat - thank you for the clear instructions as I am very new to linux!

One point for anyone else usng this is that before finding this post I had tried Wicd to see if that worked (it didn't) and had to uninstall wicd and reinstall the standard network manager from synaptic.

C

---

### Post by canoemoose on 2009-03-09
> **Conorm1 said:**
> 
One point for anyone else usng this is that before finding this post I had tried Wicd to see if that worked (it didn't) and had to uninstall wicd and reinstall the standard network manager from synaptic.
Yes, that's a good point.  I'd forgotten that bit - funny really since I had also been playing with Wicd!  I'll edit the HowTo to reflect this.

EDIT 1: HowTo changed.

EDIT 2: Woo! 50 posts!

---

### Post by literocola on 2009-03-16
Thank you very much.  Worked exactly as described.

---

### Post by Gryphon-ni on 2009-03-25
Worked a treat for me, ubuntu newbie. I do think I needed a reboot in their somewhere.

One other thing and I may be off the mark on this, but it seems to use US standards, because I could not see networks in the higher channel range that's available in Europe. I dropped my wireless router down 2 channels and all was happy.

---

### Post by canoemoose on 2009-03-25
[quote=Gryphon-ni]One other thing and I may be off the mark on this, but it seems to use US standards, because I could not see networks in the higher channel range that's available in Europe. I dropped my wireless router down 2 channels and all was happy.[/quote]

I dunno! I'm in Europe and had no problems!  I can't remember what channel I run my access point on though - may be 11?

---

### Post by TheCrook on 2009-05-09
I have just installed Kubuntu 9.04 and put the AirPace in after the system was up and running. My WLAN with WPA2 encryption and hidden SSID works right out of the box, nothing to install, nothing to remove. :)

---

### Post by canoemoose on 2009-05-11
> **TheCrook said:**
> I have just installed Kubuntu 9.04 and put the AirPace in after the system was up and running. My WLAN with WPA2 encryption and hidden SSID works right out of the box, nothing to install, nothing to remove. :)
Just out of interest, what driver is kubuntu automatically loading for you?
If we can find it out, I'll add it to the top of the HowTo and it can be archived.

---

