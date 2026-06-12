---
title: "Enabling monitor mode in Broadcom Corporation BCM4311 802.11b/g WLAN"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by webmja on 2010-03-15
Am a sort of beginner in Linux. I want to enable monitor mode to sniff packets over WLAN.

**System:** Dell Vostro 1000
**Processor:** AMD X2
**OS**: Ubuntu 9.04

**Wireless Device:** BCM4311
#lspci
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

**Interface:** wlan0
#iwconfig wlan0
Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**Things I have tried**
[I]
#airmon-ng start wlan0[/I]

Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
4434    NetworkManager
4443    wpa_supplicant
4459    avahi-daemon
4460    avahi-daemon


Interface    Chipset        Driver

wlan0        Broadcom    b43 - [phy0]
                (monitor mode enabled on mon0)
[I]
#iwconfig wlan0 mode monitor[/I]
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

# *iwpriv wlan0*
wlan0     no private ioctls.

Tried even to install madwifi, athros,..But falied...
> #cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


ath_pci
“b43&#8243;
Used the following script to install madwifi,, But now am totally messed up..Now  I have to start the modules manually using modprobe and I got the kernel recompiled to Linux  2.6.30-libre-fshoppe1 #1 SMP Tue Jun 16 13:04:16 EEST 2009 i686 GNU/Linux


> [I]#!/bin/sh

# This script will install the madwifi drivers for Atheros cards.
# The script must be run in a root terminal with 755 permission
#
# Authored by Bob Nelson  [EMAIL="admin@stchman.com"]admin@stchman.com[/EMAIL]
#

script_name="madwifi.sh"

# Script must run as root 
if [ $USER != "root" ]; then
    echo "You need to run this script as root."
    echo "Use 'sudo ./$script_name' then enter your password when prompted."
    exit 1
fi

# Install essential tools
sudo apt-get -y install build-essential bin86

# Install the sharutils package
sudo apt-get -y install sharutils

# Change to the /usr/src folder
cd /usr/src

# Get the necessary drivers from [www.stchman.com]("http://www.stchman.com")
sudo wget [http://www.stchman.com/tools/madwifi/madwifi-0.9.3.3.tar.gz](http://www.stchman.com/tools/madwifi/madwifi-0.9.3.3.tar.gz)

# unpack the tarball
sudo tar -xzf /usr/src/madwifi-0.9.3.3.tar.gz

# Change to the folder that the tarball created
cd /usr/src/madwifi-0.9.3.3

# Make the drivers
sudo make clean
sudo make
sudo make install

# Make backup of /etc/modules file
sudo cp /etc/modules /etc/modules.bak

# Append to the end of the /etc/modules file by using >>
# First insert a carriage return in to the /etc/modules file
sudo echo -e '\n' >> /etc/modules
sudo echo "ath_pci" >> /etc/modules

# Enable WEP, WPA. WPA2 via network manager
# Install wpa supplicant
sudo apt-get -y install wpasupplicant

# Install Network Manager (this will allow you to see all available wireless networks)
sudo apt-get -y install network-manager-gnome network-manager

# Make backup of the /etc/network/interfaces file
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

# Make new /etc/network/interfaces file with just "lo" entry in it.
# The single > will create a new file, >> appends to a file
sudo echo "# The loopback network interface" > /etc/network/interfaces
sudo echo "auto lo" >> /etc/network/interfaces
sudo echo "iface lo inet loopback" >> /etc/network/interfaces

# Create a file called /etc/default/wpasupplicant
# This file does not exist, but the > command will create it
sudo echo "ENABLED=0" > /etc/default/wpasupplicant

#sudo touch /etc/default/wpasupplicant

# Reboot the machine, wireless should now be enabled!!!!
sudo reboot[/I]
Help me out guys..
Thanking in advance

---

### Post by chili555 on 2010-03-16
> #iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Device or resource busy.Have you tried:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Not all driver and device combinations do all things. Some wireless devices do not do monitor mode.

Some devices, including my iwl3945, need to be brought down by sudo before a mode change, also sudo-ed.

I did notice you are running as root or sudo su:> [COLOR="Red"]#[/COLOR]iwconfig wlan0 mode monitorThat is very insecure so I assume you have nothing of any real value on this computer or the network.

---

### Post by webmja on 2010-03-18
> **chili555 said:**
> Have you tried:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Not all driver and device combinations do all things. Some wireless devices do not do monitor mode.

Some devices, including my iwl3945, need to be brought down by sudo before a mode change, also sudo-ed.

I did notice you are running as root or sudo su:That is very insecure so I assume you have nothing of any real value on this computer or the network.

Thankx 4 de help...

I did run the commands as root ( su) . I was able to bring the interface to monitor mode 1 by the following command

# sudo ifconfig wlan0 down
#sudo iwconfig mode monitor
#sudo ifconfig wlan0 up

But what I need is to enable monitor mode 2 [ with no Prism2 ]

---

### Post by chili555 on 2010-03-18
> But what I need is to enable monitor mode 2 [ with no Prism2 ]I'm sorry, I don't know what this is. I am not aware of a mode 'monitor 2.'

---

