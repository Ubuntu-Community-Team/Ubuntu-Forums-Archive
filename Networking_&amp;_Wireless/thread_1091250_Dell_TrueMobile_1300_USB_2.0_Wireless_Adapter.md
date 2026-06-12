---
title: "Dell TrueMobile 1300 USB 2.0 Wireless Adapter"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by lmart on 2009-03-09
Has anyone successfully installed this device under xubuntu?  If so, need a detailed howto.  Thanks.

---

### Post by opt1k on 2009-11-25
If its the prism54 version it will work flawlessly with ndiswrapper.

Install Instructions:

open terminal

# Install ndisgtk + ndiswrapper
1. sudo apt-get install ndisgtk

# Download Drivers
2. Download the attached Windows Drivers and extract them somewhere.

# Start Driver installer
3. sudo ndiskgtk (or via:System - Administration - Windows Wireless Drivers.)

#Follow the instructions for installing the Windows Drivers. Browse to and locate the oem15.inf file.

# Load drivers and unload p54usb
5. sudo rmmod p54usb ; sudo modprobe ndiswrapper

# Make ndiswrapper module load on start and blacklist p54usb
6. sudo echo ndiswrapper >> /etc/modules ; sudo echo blacklist p54usb >> /etc/modprobe.d/blacklist.conf

7. Connect to your wireless network through the connection  manager.


Lazy

sudo apt-get install ndisgtk
sudo ndiskgtk  
##Install oem15.inf driver from attached file.
sudo rmmod p54usb ; sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules ; sudo echo blacklist p54usb >> /etc/modprobe.d/blacklist.conf

---

