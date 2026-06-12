---
title: "ndiswrapper and Netgear MA111 - wlan0 not found"
date: 2005-03-08
forum: Networking &amp; Wireless
---

### Post by fritzk3 on 2005-03-08
Hi all,

I was trying to get my Netgear MA111 USB wireless NIC working under Warty.  I plugged in the NIC, installed the ndiswrapper package, did ndiswrapper -i <inffile>.inf, ndiswrapper -l (hardware present, drivers present) and modprobe ndiswrapper.

After all of that, though, iwconfig shows no extensions on wlan0.  Any suggestions?  Does linux-wlan-ng work more successfully here?

My dilemma is that the computer on which Ubuntu and the wireless NIC are installed does not have a tethered ethernet connection, so I am sneaker-netting everything with a flash drive.

Thanks in advance for any help you can provide.

---

### Post by Q4U on 2005-04-13
The MA111 works with Warty using the wlan-ng packages (as long as you have the MA111 version with the prism2 chip in it):

1. download the wlan-ng packages from the universe repositories

2. go to the top-bar menu and navigate through Computer -> System Configuration-> Networking. Push the "add" button and configure the new connection (call it "wlan0" or anything you like and type in your SSID etc...).

3. open the terminal and type in:

sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=1
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=[YourSSID] authtype=opensystem
sudo iwconfig wlan0
sudo dhclient wlan0

Sometimes, a few errors fly around, but they are sort of harmelss (in my experience).

If you use the dongle a lot, consider writing this in a little script which can be fired up as needed.

Hope this helps.  

Q4U

PS I am still in the hair-pulling stage re: getting this to work in Hoary, but this is another story...

---

