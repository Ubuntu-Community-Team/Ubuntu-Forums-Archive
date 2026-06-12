---
title: "Newbie Wireless question?"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by rjpear on 2006-05-03
Ok...I have been reading and reading..and using different laptops and PCMCIA cards trying to get wireless working but no luck...   Until today I think...   I did a new install of Ubuntu 5.10 on a Dell D800 Laptop..  This has the MiniPC Broadcom Wireless card (not the intel) installed.       Just for Giggles I Looked at the Device Manager upon first boot to see what I had to work with and this is what I see:
    BCM4309 802.11a/b/g   Vendor Broadcom
    Status: Status
    Bus Type: PCI
    Device Type: Unknown
    Capabilities: Unknown
   OEM Vendor: Dell
   OEM Product: Truemobile 1400
 ..And the Advanced tab is populated full of Strings...   

In the Network tab I do not see the Wireless car as available though.. Just my eth0 (wired Gigabit) interface.     
  How can I go about Populating the DEVICE TYPE and the Capabilites..and getting this baddie to be displayed in the Networking Tab...
   I know this is a worn out subject and topic but I go to linux for it's very good wireless Tools..     
Thanks for reading this mess!..
Rob

---

### Post by towsonu2003 on 2006-05-03
did you try ndiswrapper for this card? 

also check out the instructions at [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?highlight=%28bcm43xx%29](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?highlight=%28bcm43xx%29) for an alternative driver to use with your wireless card.

---

### Post by rjpear on 2006-05-03
Thanks.. I was kinda hoping not to NDISwrap it ...  I was thinking maybe this build had everything up and running install..    But I am giving the NDIS a shot now..Thanks..

Rob

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=rjpear]Thanks.. I was kinda hoping not to NDISwrap it ...  I was thinking maybe this build had everything up and running install..    But I am giving the NDIS a shot now..Thanks..

Rob[/QUOTE]
try the wiki link in my previous post if you'd like to avoid ndis. Was very easy to make my broadcom work with bcm43xx, in Dapper though. may be it's the case for you too, in breezy.

---

### Post by rjpear on 2006-05-03
Using the GUI for NDISWRAPPER and the Drivers (BCMWl5.sys) it says the Hardware is Present...  but Network Tab Only shows the Wired Ethernet and the Modem..    I have also rebooted after install to see if that made a difference but no go...  
   Doing this lapci I get : 0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
  ndiswrapper -l   = Hardware and Driver both Present  

any ideas?

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=rjpear]Using the GUI for NDISWRAPPER and the Drivers (BCMWl5.sys) it says the Hardware is Present...  but Network Tab Only shows the Wired Ethernet and the Modem..    I have also rebooted after install to see if that made a difference but no go...  
   Doing this lapci I get : 0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
  ndiswrapper -l   = Hardware and Driver both Present  

any ideas?[/QUOTE]


did you modprobe ndsiwrapper?
```
sudo modprobe ndiswrapper
```this will not give you any output.

what's the output of 
```
sudo ifconfig -a
sudo iwconfig

``` after modprobing?

---

### Post by rjpear on 2006-05-03
all after sudo modprobe ndiswrapper

sudo ifconfig -a
     eth0      Link encap:Ethernet  HWaddr 00:0D:56:EB:C8:3D
          inet addr:112.64.227.125  Bcast:147.64.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feeb:c83d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:142660 (139.3 KiB)  TX bytes:17329 (16.9 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2655973 (2.5 MiB)  TX bytes:2655973 (2.5 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


sudo iwconfig
  sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


YUK!  
Thanks for the Help...

---

### Post by towsonu2003 on 2006-05-03
output of 
```
lsmod | grep ndis
```?

---

### Post by rjpear on 2006-05-03
ndiswrapper           114376  0
usbcore               104316  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

---

### Post by towsonu2003 on 2006-05-03
> **rjpear]ndiswrapper           114376  0
usbcore               104316  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd[/QUOTE]
to be honest, I was hoping you forgot to load the module  said:**
> http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page[/url]
List of cards (check this one): [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
Use these instructions to locate what file to download for your specific card (using the list above):
> Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry List. To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the List, find out an entry for the same PCI ID and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension).
If there are multiple INF/SYS files, you may look in the List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory.
Remove one .inf (windows driver) before adding the next one you wanna try: 
[quote]
1. Make sure you unload your current ndiswrapper module with 'sudo modprobe -r ndiswrapper'
2. ndiswrapper installs Windows drivers under /etc/ndiswrapper directory. If you want to uninstall just a specific Windows driver, first list the drivers installed with "ndiswrapper -l". If you then want to remove, say, driver "bcmwl5", then remove it with ndiswrapper itself with "ndiswrapper -e bcmwl5". If that doesn't work, just remove the directory /etc/ndiswrapper/bcmcwl5 (e.g., with '/bin/rm -rf /etc/ndiswrapper/bcmwl5').
this was from Uninstallaton guide: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall)[/quote]

Everytime you try a new driver, make sure your other network interfaces (modem, eth0, whatever you have) are deactivated, than load the module.

---

### Post by rjpear on 2006-05-03
You Did it Towsonu!!  Here was the issue  WRONG DRIVER!!
  I was using BCMWl5.sys and it all looked good,  but nothing ..   I removed those ans tried the BCMWl5a.sys drivers and the WLAN0 showed up right away in the Networking tool!!     The Only Issue I had from there was how to make WLAN0 my default gateway....    I had to use the Networking Tool to Disable the eth0 adapter and WLAN0 took over!!..  
  wow...This is like Christmas in May!    Thanks for all your work/suggestions...   

Now I am off to see what Ubuntu can really do!!

 Thanks again!!

 Rob
:KS

---

### Post by towsonu2003 on 2006-05-03
great news :) enjoy ;)

---

