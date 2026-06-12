---
title: "HOWTO: TrueMobile 1300 USB PRISM54 chipset"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by opt1k on 2009-11-25
The Linux p54usb driver is a little flaky still. 

So heres how you get it to work right.

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

