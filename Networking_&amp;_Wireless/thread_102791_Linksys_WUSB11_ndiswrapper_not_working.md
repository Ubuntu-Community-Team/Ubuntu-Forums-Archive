---
title: "Linksys WUSB11 ndiswrapper not working"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by rabidsnail on 2005-12-12
Here is what I did to install this so far:
     1. Installed ndiswrapper-utils
     2. ndiswrapper -i 'd both .inf files
     3. ndiswrapper -l showed drivers present for both, hardware present for the first one
     4. sudo modprobe ndiswrapper seemed succesful (dmesg shows proper install)
     5. Network Settings does not see the adapter
     6. Noticed that the link light is on
     7. iwconfig returns the following:
             lo          no wireless extensions
             wlan0     no wireleess extensions
             sit0        no wireless extensions

Any suggestions?

---

### Post by az on 2005-12-12
Use the log too to see /var/log/messages when you plug in the device.  That will show the chipset.

---

### Post by rabidsnail on 2005-12-13
Prism_2

---

### Post by az on 2005-12-13
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

The device should be useable to the networking tool after you install the linux-wlan-ng package.  It appears that this does not work for everybody.

I must run a script to get the device to work.  See the bug report and the mailling list thread referenced there for more details.

I save this to /etc/hotplug/usb/prism2_usb:



wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0

wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="(mysecretWEPkey)"

wlanctl-ng wlan0 lnxreq_autojoin ssid="(myssid)" authtype="sharedkey"

sleep 2

dhclient wlan0



If you want to use ndiswrapper, you need to blacklist the prism2_usb module from loading (hotplug) by putting it`s name in /etc/hotplug/blacklist

Ndiswrapper cannot use it if the prism2_usb module already takes ownership of the hardware.

Good luck.

---

### Post by rabidsnail on 2005-12-13
Thanks for the tip.

I decided not to bother with the wlan-ng driver and delete it, installed the Linksys driver with ndiswrapper, and now it works great!

---

### Post by az on 2005-12-13
What revision is your device?  There can be different chipsets for the same linksys device.  There is a wiki page about the WUSB11, but it is for another chipset.  I want to add to that page.

---

