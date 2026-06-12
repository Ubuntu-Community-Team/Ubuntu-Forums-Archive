---
title: "Nic Problem"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by M3nta on 2011-09-25
Hi there,
I have installed Ubuntu 64bit Gnome.
I bought a GSKY GS-20USB-50 from DealExtreame.com.
In the GSKY box writes its Linux support.
I have been downloaded drivers and follow the manual(ReadMe file).
Here the manual:

Release Date: 2008-12-05, ver 1037 
RTL8187L Linux driver version 1037 
 
   --This driver supports RealTek RTL8187L Wireless LAN NIC for 
     2.6 kernel: 
     Fedora Core 2/3/4/5/6/7, Debian 3.1, Mandrake 10.2/Mandriva 2006,  
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc, Ubuntu8.04/8.10. 
     2.4 kernel: 
     Redhat 9.2, etc 
   - Support Client mode for either infrastructure or adhoc mode 
   - Support WEP, WPAPSK and WPA2PSK connection 
 
======================================================================================
                                Component
======================================================================================
The driver is composed of several parts:
        1. Module source code
           ieee80211
           rtl8187

        2. Script ot build the modules
           Makefile

        3. Script to load/unload modules
           wlan0up
           wlan0down

        4. Script and configuration for DHCP
           wlan0dhcp
           ifcfg-wlan0
 
    5. Supplicant source code: 
       wpa_supplicant-0.5.5.tar.gz 
 
    6. Example of supplicant configuration file: 
       wpa1.conf 
 
======================================================================================
                                Installation
======================================================================================
<<Method 1>>
Runing the scripts can finish all operations of building up modules
from the source code, installing driver to the kernel and starting up the nic.
        1. Build up the drivers from the source code
           make

        2. Install the driver to the kernel
           make install
           reboot
    
        3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
           ifconfig wlan0 up
           Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to 
           check your wlan interface name,since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
        1. Build up the drivers from the source code
           make

        2. Load driver module to kernel and start up nic.
           ./wlan0up

           Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                 after run ./wlan0up, please run ./wlan0down first, then it should
                 be ok..
           Note: If you see the message of "unkown symbol" during ./wlan0up, it
                 is suggested to build driver by <<Method 1>>.

I did all the process and when I plugged the Nic again it was blinking.
I entered ifconfig on the terminal for find my interface and I found only 2 interfaces(l0, eth0)

Please help,

thank you very much

---

### Post by M3nta on 2011-09-25
Somebody help please!

---

### Post by docbop on 2011-09-25
This might help.

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

the Realtek is good stuff, but from what I've not always supported out of the box.  The Atheros chip is what typically works out of the box.

---

### Post by M3nta on 2011-09-25
I entered the command "lsusb" and I didnt found any Realitek devices on it.
The Nic connected!

---

### Post by bkratz on 2011-09-25
> **M3nta said:**
> I entered the command "lsusb" and I didnt found any Realitek devices on it.
The Nic connected!


By the Nic connected I guess you mean you have wireless?? Please keep in mind that whenever you have a kernel update (not just regular ones) you will probably have to rebuild again following the same procedure. Please also go to the thread tools and mark as solved in case it helps someone else with the same device.

---

### Post by M3nta on 2011-09-26
I am on my leptop which have a built-in NIC.
My Ubuntu located on a virtual machine in brige-mode.
I currently have a problem with my new NIC(GSKY).

---

