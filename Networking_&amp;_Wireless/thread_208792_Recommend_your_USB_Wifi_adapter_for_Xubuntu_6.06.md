---
title: "Recommend your USB Wifi adapter for Xubuntu 6.06?"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by asktoby on 2006-07-04
My friend would like to put his Xubuntu box onto the wireless network. I
tried connecting my Belkin USB wireless dongle to his PC
('F5D7050' [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211))
but attempting to configure it in the GUI locked the whole O/S.

Can anyone recommend a USB wireless dongle which they have had success
configuring on a Ubuntu O/S?

This thread says a Conceptronic C54RU USB (Ralink 2500) will also hang the OS:
[http://www.ubuntuforums.org/showthread.php?t=199501](http://www.ubuntuforums.org/showthread.php?t=199501)
This thread recommends a Netgear WG111v2 USB wireless adapter as working 'out of the box'.
[http://www.ubuntuforums.org/showthread.php?t=188849](http://www.ubuntuforums.org/showthread.php?t=188849)

I wonder: What other makes of USB adapter have people had success using on Xubuntu 6.06?

---

### Post by asktoby on 2006-09-24
If no-one here successfully uses a USB WiFi dongle with Xubuntu I wonder if, at least, someone uses a PCI WiFi card?

Does anyone have WiFi working *at all* in Xubuntu?

---

### Post by KingArthur10 on 2006-09-24
The only WiFi solutions I've worked on in (X)Ubuntu are the Intel IPW2100/2200 cards and an old DWL-650+ PCMCIA card.  I've also been wondering about various USB or PCI wifi cards for my Sis-in-law's old Ubuntu box.

---

### Post by neildarlow on 2006-09-25
I have a Belkin Wireless G USB Network Adapter working with Ubuntu 6.06.

I use the vendor-supplied Windows XP driver/ndiswrapper/network-manager-gnome combination and there are a few requirements.

1) Add to /etc/modprobe.d/blacklist:
   blacklist rt2570
   blacklist islsm_usb

2) Create /etc/default/wpasupplicant with:
   ENABLED=0

3) Add to /etc/modules:
   ndiswrapper

4) Remove all rausb0 or wlan0 configuration from /etc/network/interfaces

Use Synaptic or another method to add the ndiswrapper-utils package. Insert your USB dongle's Windows driver disk and do something like:

   sudo ndiswrapper -i /media/cdrom0/drivers/rt2500usb.inf

Now restart your system and login. In a shell console iwconfig should show the presence of the wlan0 device.

GNOME will automatically start nm-applet at login. nm-applet will start wpa_supplicant by itself.

You should now be able to click the nm-applet icon and select the Connect to Other Wireless Network... option.

In Network Name: enter your Access Point's SSID
From Wireless Security: select WPA Personal

Insert passphrase information into the expanded dialogue box and supply a passphrase for gnome-keyring, if requested.

Network-Manager should now connect to your access point, which you can verify by right-clicking the nm-applet icon and selecting Connection Information.

All of the GUI instructions are targetted at Ubuntu but I'm sure they can be adapted for network-manager and Xubuntu.

Note: A number of posts related to this topic have mentioned the use of older hardware with USB wireless dongles. It is likely that USB 1.x ports will work reliably with them. This might rule out their on such systems.

Regards,
Neil Darlow

---

