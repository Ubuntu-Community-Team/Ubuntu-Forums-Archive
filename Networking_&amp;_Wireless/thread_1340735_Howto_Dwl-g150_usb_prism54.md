---
title: "Howto: Dwl-g150 usb prism54"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by opt1k on 2009-11-28
Tested on kernel 2.6.30 
This card operates best with the Linux p54usb driver, although ndiswrapper does work, but it limits the range of the card.
Install Instructions for DWL-G120 USB with kernel p54usb module
1. sudo modprobe p54usb
2. sudo echo p54usb >> /etc/modules
Thats all.

usb 1-1: firmware: requesting isl3886usb
phy1: p54 detected a LM86 firmware
p54: rx_mtu reduced from 3240 to 2392
phy1: FW rev 2.13.1.0 - Softmac protocol 5.5
phy1: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
phy1: hwaddr 00:0f:3d:0c:e6:5e, MAC:isl3886 RF:Frisbee
phy1: Selected rate control algorithm 'minstrel'
Registered led device: p54-phy1::assoc
Registered led device: p54-phy1::tx
usb 1-1: is registered as 'phy1'
usbcore: registered new interface driver p54usb
udev: renamed network interface wlan0 to wlan2
ADDRCONF(NETDEV_UP): wlan2: link is not ready
ADDRCONF(NETDEV_UP): wlan2: link is not ready
wlan2: authenticate with AP ************
wlan2: authenticated


Alternate Install Instructions for NDISWRAPPER:

open terminal

# Install ndisgtk + ndiswrapper
1. sudo apt-get install ndisgtk

# Download Drivers
2. Download the attached Windows Drivers and extract them somewhere.

# Start Driver installer
3. sudo ndiskgtk (or via:System - Administration - Windows Wireless Drivers.)

#Follow the instructions for installing the Windows Drivers. Browse to and locate the PRISMA02.inf file.

# Load drivers and unload p54usb
5. sudo rmmod p54usb ; sudo modprobe ndiswrapper

# Make ndiswrapper module load on start and blacklist p54usb
6. sudo echo ndiswrapper >> /etc/modules ; sudo echo blacklist p54usb >> /etc/modprobe.d/blacklist.conf

7. Connect to your wireless network through the connection manager.


Lazy ndiswrapper install

sudo apt-get install ndisgtk
sudo ndiskgtk 
##Install PRISMA02.inf driver from attached file.
sudo rmmod p54usb ; sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules ; sudo echo blacklist p54usb >> /etc/modprobe.d/blacklist.conf

---

