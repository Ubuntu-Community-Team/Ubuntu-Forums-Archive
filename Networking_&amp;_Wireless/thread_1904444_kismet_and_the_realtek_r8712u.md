---
title: "kismet and the realtek r8712u"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by thelastboyscout on 2012-01-04
Hello all,
I have an older dell precision laptop who's intel wireless card stopped working, I bought a belkin card and although wireless is working, kismet will not run, here are a few dumps:

 airmon-ng


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 - [phy0]
wlan0		Unknown 		r8712u

lsusb -v | grep -i belkin -A 15
Bus 001 Device 003: ID 050d:945a Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x945a 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer Realtek 
  iProduct                2 Basic Wireless USB Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)

iwconfig
wlan0     IEEE 802.11bg  ESSID:"PPLD-W"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:CF:26:9C:A0   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=91/100  Signal level=59/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



from dmesg:
[   61.683606] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   62.404612] r8712u: 1 RCR=0x153f00e
[   62.405355] r8712u: 2 RCR=0x553f00e


and finally the source line from kismet.conf
source=rt8180,wlan0,ATHEROS
#source=rt2500,ra0,ATHEROS
# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
 enablesources=prismsource,ciscosource,ATHEROS 


this is the error message
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ATHEROS): Enabling monitor mode for rt8180 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.



Any help would be greatly appreciated.

Thanks

---

### Post by josephmills on 2012-01-04
try ```
sudo airmon-ng start wlan0 
``` then paste ```
airmon-ng 
```
thanks

---

### Post by thelastboyscout on 2012-01-04
Note I am running all these commands as root, so no need for the sudo


airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
583	avahi-daemon
584	avahi-daemon
586	NetworkManager
1797	wpa_supplicant
5141	dhclient
Process with PID 5141 (dhclient) is running on interface wlan0


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 - [phy0]
wlan0		Unknown 		r8712u (monitor mode enabled)

---

### Post by josephmills on 2012-01-04
> **thelastboyscout said:**
> Note I am running all these commands as root, so no need for the sudo


airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
583	avahi-daemon
584	avahi-daemon
586	NetworkManager
1797	wpa_supplicant
5141	dhclient
Process with PID 5141 (dhclient) is running on interface wlan0


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 - [phy0]
wlan0		Unknown 		r8712u (monitor mode enabled)

ok I see that oyu ran one of the commands could we see a ```
airmon-ng
``` to make sure that the card is in monitor mode

---

### Post by thelastboyscout on 2012-01-04
begin dump:


airmon-ng


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 - [phy0]
wlan0		Unknown 		r8712u

---

