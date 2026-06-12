---
title: "Ubuntu wireless does not work. Win7 can work"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by pspencil on 2013-01-25
It is quite a strange situation. 

In school, with school wifi, both OS can work pretty well. In hostel, with hostel wifi(seems more unstable), Win7 can still access internet quite easily while ubuntu sometimes cannot access internet. It just cannot connect to the wifi. But there are also times when ubuntu can also connect to the hostel wifi, but most of the time, ubuntu wireless does not work. 

My Laptop is Thinkpad e40 0578B32 Ubuntu 12.10

in windows device manager, the wireless adapter shows "11b/g/n wireless LAN Mini-PCI Express Adapter II" Google tells me it is actually RTL8192SE(If i am not wrong)

I know there should be something more detailed but I am not sure about the command(iwconfig?)

Thank you.

---

### Post by meteorrock on 2013-01-25
Did you try to update your software on ubuntu? Find the software updater in the menu options of Ubuntu and see if that could help first.

Sometimes just a simple solution is all you need to fix something. ;)

~~~~~~~~~~~
:KS Help develop up in XDA forums at this link here.

---

### Post by pspencil on 2013-01-25
> **meteorrock said:**
> Did you try to update your software on ubuntu? Find the software updater in the menu options of Ubuntu and see if that could help first.

Sometimes just a simple solution is all you need to fix something. ;)

~~~~~~~~~~~
:KS Help develop up in XDA forums at this link here.
I have tried these below

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

The problem persists

---

### Post by Yellow Pasque on 2013-01-25
Nvm.

---

### Post by meteorrock on 2013-01-25
Try the settings in Ubuntu for the wireless in there :) 

Go to systems settings, then network.

This other thread here in the forums could help you get your drivers up and going. Here is the link for that thread. [http://ubuntuforums.org/showthread.php?t=2108603](http://ubuntuforums.org/showthread.php?t=2108603)

---

### Post by elgordodude on 2013-01-25
> In school, with school wifi, both OS can work pretty well. This is key, and should make you happy, cause if it works well in one area, but not in another then your configuration is likely good, and there's something else going on. Unfortunately it's been my experience that intermittent connections are the worst to diagnose and repair, so keep that in mind.

*iwconfig *will show you information about any wireless networks you're currently connected to, *lspci *will list all pci devices and should show the realtek card you listed, as well as all other pci devices. Also note that realtek drivers tend to be well supported by ubuntu and linux, with some newer exceptions. Can you take a little walk around the hostel? If you move closer to the router does the connection solidify?

---

### Post by pspencil on 2013-01-26
> **elgordodude said:**
> This is key, and should make you happy, cause if it works well in one area, but not in another then your configuration is likely good, and there's something else going on. Unfortunately it's been my experience that intermittent connections are the worst to diagnose and repair, so keep that in mind.

*iwconfig *will show you information about any wireless networks you're currently connected to, *lspci *will list all pci devices and should show the realtek card you listed, as well as all other pci devices. Also note that realtek drivers tend to be well supported by ubuntu and linux, with some newer exceptions. Can you take a little walk around the hostel? If you move closer to the router does the connection solidify?
The problem is I don't know when it will just die. Like at 2am, when not many people are using it, it works fine. 
does that help?

---

### Post by elgordodude on 2013-01-26
Sure, it points to a cheap and/or poor and/or overloaded router. That's  fairly common nowadays, but there isn't much anyone can do about it. I would guess that one of two things is going on, First Windows has the exact driver designed for your laptop installed, because it came that way out of the factory, while ubuntu has defauled to a driver that "works". You can check this by running ```
sudo lshw -C network
``` in ubuntu and comparing it to the driver installed in Windows, should be shown in device manager (? could be wrong haven't troubleshot win for awhile now)

OR, ubuntu is running at peak times, and thus falling off the grid while win is running late night. Best way to check this is to switch rapidly from one OS to the other 3 or 4 times and see if there's a noticeable difference in connectivity, if there is see option 1 and post, else, your configuration is okay, but you can tell the landlord to buy some decent kit ;)

---

### Post by pspencil on 2013-01-26
Just not I tried Ubuntu, it is not working. I switched back to Win now, and so I can post...  The 'OR' option is eliminated. now i shall try to see the result of lshw..

---

### Post by pspencil on 2013-01-26
> **elgordodude said:**
> Sure, it points to a cheap and/or poor and/or overloaded router. That's  fairly common nowadays, but there isn't much anyone can do about it. I would guess that one of two things is going on, First Windows has the exact driver designed for your laptop installed, because it came that way out of the factory, while ubuntu has defauled to a driver that "works". You can check this by running ```
sudo lshw -C network
``` in ubuntu and comparing it to the driver installed in Windows, should be shown in device manager (? could be wrong haven't troubleshot win for awhile now)

OR, ubuntu is running at peak times, and thus falling off the grid while win is running late night. Best way to check this is to switch rapidly from one OS to the other 3 or 4 times and see if there's a noticeable difference in connectivity, if there is see option 1 and post, else, your configuration is okay, but you can tell the landlord to buy some decent kit ;)
In Ubuntu, it tells that my wireless card is "product: **RTL8191SE**vB Wireless LAN Controller" but in windows it is **rtl8192se**

Actually I have thought of the driver problem and downloaded a driver (.tar.gz) from RTL website. But I seem to encounter problems when I "make install"
..

---

### Post by pspencil on 2013-01-26
Actually, the version we see in device manager in windows is just the driver installed, not necessarily the version of the wireless cardh. I am going to download the driver for windows from thinkpad centre again and try to see the version of the driver after installing it. That should be the correct version. 

But after that, how could i install the correct driver for my ubuntu?

---

### Post by sdowney717 on 2013-01-26
> **In school, with school wifi, both OS can work pretty well. **In hostel, with hostel wifi(seems more unstable), Win7 can still access internet quite easily while ubuntu sometimes cannot access internet. It just cannot connect to the wifi. But there are also times when ubuntu can also connect to the hostel wifi, but most of the time, ubuntu wireless does not work. 

it is working, maybe a signal strength issue which you can adjust.
[http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/](http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/)

I simply bought this and it works well for me when I use it.
[http://www.ebay.com/itm/150Mbps-150M-Mini-USB-WiFi-Wireless-Card-Adapter-Network-LAN-Card-802-11n-g-b-/320917992695?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item4ab833f4f7](http://www.ebay.com/itm/150Mbps-150M-Mini-USB-WiFi-Wireless-Card-Adapter-Network-LAN-Card-802-11n-g-b-/320917992695?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item4ab833f4f7)

shows up as

```
scott@scott-P5QC:~$ lsusb
Bus 002 Device 005: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

```

---

### Post by pspencil on 2013-01-26
> **sdowney717 said:**
> it is working, maybe a signal strength issue which you can adjust.
[http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/](http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/)

I simply bought this and it works well for me when I use it.
[http://www.ebay.com/itm/150Mbps-150M-Mini-USB-WiFi-Wireless-Card-Adapter-Network-LAN-Card-802-11n-g-b-/320917992695?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item4ab833f4f7](http://www.ebay.com/itm/150Mbps-150M-Mini-USB-WiFi-Wireless-Card-Adapter-Network-LAN-Card-802-11n-g-b-/320917992695?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item4ab833f4f7)

shows up as

```
scott@scott-P5QC:~$ lsusb
Bus 002 Device 005: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

```
The passage does mention about 'illegal'.. which i am quite concerned. Do you know more details about this?

---

### Post by asg1290 on 2013-01-26
Try using the latest upstream drivers

[http://ubuntuforums.org/showpost.php?p=12475322&postcount=8]("http://ubuntuforums.org/showpost.php?p=12475322&postcount=8")

---

### Post by elgordodude on 2013-01-26
> **pspencil said:**
> But after that, how could i install the correct driver for my ubuntu? With ndiswrapper / ndisgtk extract the .inf file from the windows .exe file with archive manager than install it in ndiswrapper.

---

### Post by pspencil on 2013-01-26
I tried. The link quality shown becomes better but the real speed does not increase much. 

By the way, is there anything else I need to do after installing, say, load the driver? I did a reboot.

---

### Post by pspencil on 2013-01-27
> **asg1290 said:**
> Try using the latest upstream drivers

[http://ubuntuforums.org/showpost.php?p=12475322&postcount=8]("http://ubuntuforums.org/showpost.php?p=12475322&postcount=8")
After I loaded the driver, the speed is good when the link quality is 70/70. but when the signal strength suddenly drops, I cannot connect, again.

---

### Post by pspencil on 2013-01-27
After I did some research, this seems to be an 'intermittent DNS resolution' problem (bear with me if i make some mistake in the term) and i seem to get my computer to work by 

editting
/etc/NetworkManager/NetworkManager.conf

comment out the line dns=dnsmasq

---

### Post by pspencil on 2013-01-28
> **elgordodude said:**
> With ndiswrapper / ndisgtk extract the .inf file from the windows .exe file with archive manager than install it in ndiswrapper.
Thank you. I solved my question using ndiswrapper 1.58 and xp driver. Previously I use 1.57 and win7 drivers and failed. Not it turns out quite ok, although still a bit slow, but that is bearable.

---

