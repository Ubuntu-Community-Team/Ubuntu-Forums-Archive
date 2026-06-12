---
title: "I can't connect to internet"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by BitaCookie on 2009-08-03
I am new at Linux, and my friend helped me to install kubuntu on my computer. Now I have both kubuntu and windows in the same computer (partition).  

I lived in another city, and I was happily using internet in kubuntu. Then, when I changed my city I couldn't connect to internet with kubuntu, so I guess my problem is with the detection of my wireless card. I can connect with windows, but with kubuntu I can't. 

When I am in kubuntu the "Network Management" can detect router, but when I put the password says: "Connection on Network interface wlan0 failed".

Sincerely, I have been struggling for some weeks without any result. I have been reading, but I can't figure out where the problem is :confused:

Thank you in advance!
[U]
This is some of the information on my current setup:[/U]

> lspci -nn

```
user@user:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```

> lshw -C Network

```
user@user:~$ lshw -C Network                                                                                                  
WARNING: you should run this program as super-user.                                                                                    
  *-network
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:f5:86:da
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:5e:7d:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0a:18:eb:19:37:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

> uname -rm

```
user@user:~$ uname -rm
2.6.28-11-generic i686
```


> sudo iwlist scan

```
user@user:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:F2:3E:D9
                    ESSID:"INFINITUM9968"     
                    Mode:Master               
                    Channel:4                 
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/100  Signal level:-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 000D494E46494E4954554D39393638
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000009b0613f181
                    Extra: Last beacon: 456ms ago
          Cell 02 - Address: 00:1D:5A:3A:B3:21
                    ESSID:"INFINITUM3846"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=76/100  Signal level:-46 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 000D494E46494E4954554D33383436
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000001f1bf7181
                    Extra: Last beacon: 708ms ago

pan0      Interface doesn't support scanning.
```

> dmesg | grep -e ath -e wlan

```
user@user:~$ dmesg | grep -e ath -e wlan
[    3.632330] device-mapper: multipath: version 1.0.5 loaded
[    3.632332] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.164748] ath9k: 0.1
[   11.164806] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.164817] ath9k 0000:03:00.0: setting latency timer to 64
[   11.596696] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.745887] Registered led device: ath9k-phy0:radio
[   11.745904] Registered led device: ath9k-phy0:assoc
[   11.745919] Registered led device: ath9k-phy0:tx
[   11.745935] Registered led device: ath9k-phy0:rx
[   20.158195] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by pytheas22 on 2009-08-03
My first suggestion is to try to connect using wicd instead of NetworkManager.  wicd is an alternative connection manager that sometimes works better.  To install it, type:
```

sudo apt-get install wicd
```

Then launch it (I'm not sure exactly where it is in the KDE menu, but probably under "Internet" somewhere) and try connecting.  If at first you can't see any wireless networks, press the "Preferences" button and make sure the wireless interface is set to 'wlan0'.

Note that you will need to enter your wireless password *before* attempting to connect--there is no prompt for it like with NetworkManager--by clicking the "Advanced Settings" drop-down menu in wicd for the network you want to connect to.

Please give this a try and let me know if it helps.

Also, note that installing wicd will require NM to be uninstalled.  If you want NM back later for some reason, just type:
```

sudo apt-get install network-manager-kde
```

---

### Post by BitaCookie on 2009-08-03
Hello pytheas22,
I tryied to install wicd and I couldn't, so I will try to download the wicd files from internet (not in kubuntu because my problem is with connection). Then I will install them on kubuntu. I will let you know about how this is working...

I am reading, and it says that I need this files to install wicd:

[LIST]
[*]python-cairo
[*]libglade2-0
[*]python-gtk2
[*]python-glade2
[*]wicd
[/LIST]
If you have any other sugestion, I will be happy to try. Thank you!

> user@user:~$ sudo apt-get install wicd
[sudo] password for user:                                   
Reading package lists... Done                  
Building dependency tree                       
Reading state information... Done              
The following extra packages will be installed:
  libglade2-0 python-cairo python-glade2 python-gtk2
Suggested packages:                                 
  python-gtk2-doc python-numpy                      
The following packages will be REMOVED:             
  network-manager plasma-widget-network-manager     
The following NEW packages will be installed:       
  libglade2-0 python-cairo python-glade2 python-gtk2 wicd
0 upgraded, 5 newly installed, 2 to remove and 92 not upgraded.
Need to get 1813kB of archives.                                
After this operation, 4010kB of additional disk space will be used.
Do you want to continue [Y/n]? y                                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libglade2-0 1:2.6.4-1 
  Could not resolve 'us.archive.ubuntu.com'                        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-cairo 1.4.12-1.2ubuntu1
  Could not resolve 'us.archive.ubuntu.com'                                
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-gtk2 2.14.1-1ubuntu1   
  Could not resolve 'us.archive.ubuntu.com'                                
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-glade2 2.14.1-1ubuntu1 
  Could not resolve 'us.archive.ubuntu.com'                                
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe wicd 1.5.9-2              
  Could not resolve 'us.archive.ubuntu.com'                                
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libglade2/libglade2-0_2.6.4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libglade2/libglade2-0_2.6.4-1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pycairo/python-cairo_1.4.12-1.2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pycairo/python-cairo_1.4.12-1.2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-gtk2_2.14.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-gtk2_2.14.1-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'     
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-glade2_2.14.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-glade2_2.14.1-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'   
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'                  
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?                                                                     
user@user:~$ sudo apt-get update wicd                                                                                                            
E: The update command takes no arguments

---

### Post by pytheas22 on 2009-08-03
You need to have an Internet connection to install wicd using the "apt-get install wicd" command--sorry for not pointing that out.  If you don't have any way of getting connected without the wireless, you can download the wicd installer from [http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb](http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb).  Then just transfer it to your Ubuntu computer and double-click to install.

You should not need to worry about any of the other packages you mentioned; I believe all of wicd's dependencies are already installed on a default Ubuntu/Kubuntu system.

Let me know how this goes.

---

### Post by BitaCookie on 2009-08-03
Thank you pytheas22,

I eliminated the network-manger, and now I have the wicd installed, but I can't connect. It says: "validaiting authentication", and then stays for a long saying "obtaining IP", but finally it can't be connected.

Preferences/General Settings in the Manager Wicd:

WPA supplicant driver: wext
wireless interface: wlan0
wired interface: eth0
Automatically reconnect on connection loss (able)
Wired Autoconnect settings: Use default profile on wired autoconnect


Preferences/External Programs in the Manager Wicd:
DHCP Client: Automatic
Wired Link Detection: Automatic
Route Table Flushing: Automatic

In Advanced settings in Manager Wicd:
Use statics IP (disable)
Use static DNS (disable)
Encryption (abled)  -WEP Hex-

---

### Post by pytheas22 on 2009-08-04
Sorry wicd didn't help.  The next thing to try is compiling an updated version of the wireless driver using the latest code.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop on Ubuntu.  Then run these commands:
```

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

(If possible, you should be connected to the Internet while running these commands so you can download the "build-essential" package; if that's impossible, make sure your Ubuntu live CD is in the drive and the system should be able to find the packages it needs on that.)

Then reboot and let me know if the wireless works better.  You can continue to use wicd, or you can switch back to NetworkManager if you prefer--it shouldn't matter.

---

### Post by BitaCookie on 2009-08-04
Hi pytheas22,

I connected my computer to a wired network in order to download the "build essential package". After the "sudo make install", I reboot the wicd without positive results. Maybe I did something wrong. Do you see something wrong in the code I am showing you?

Thank you for all :D

user@user:~/Desktop/compat-wireless-2009-08-04$ make  
```

make: Nothing to be done for `all'.  
```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make unload  
```

Unloading ipw2100...                                                                                                                            
Unloading ipw2200...                                                                                                                            
Unloading libertas_cs...                                                                                                                        
Unloading usb8xxx...                                                                                                                            
Unloading adm8211...                                                                                                                            
Unloading zd1211rw...                                                                                                                           
Unloading b43...                                                                                                                                
Unloading b43legacy...                                                                                                                          
Unloading iwl3945...                                                                                                                            
Unloading iwlagn...                                                                                                                             
Unloading ath9k...                                                                                                                              
Unloading ath5k...                                                                                                                              
Unloading ar9170usb...                                                                                                                          
Unloading p54pci...                                                                                                                             
Unloading p54usb...                                                                                                                             
Unloading rt2400pci...                                                                                                                          
Unloading rt2500pci...                                                                                                                          
Unloading rt61pci...                                                                                                                            
Unloading rt2500usb...                                                                                                                          
Unloading rt73usb...                                                                                                                            
Unloading rtl8180...                                                                                                                            
Unloading rtl8187...                                                                                                                            
Unloading mwl8k...                                                                                                                              
Unloading mac80211_hwsim...                                                                                                                     
Unloading at76c50x_usb...                                                                                                                       
Unloading at76_usb...                                                                                                                           
Unloading rndis_wlan... 

```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make load 
```

Loading ipw2100...                                                                                                                              
Loading ipw2200...                                                                                                                              
Loading libertas_cs...                                                                                                                          
Loading usb8xxx...                                                                                                                              
Loading p54pci...                                                                                                                               
Loading p54usb...                                                                                                                               
Loading adm8211...                                                                                                                              
Loading zd1211rw...                                                                                                                             
Loading rtl8180...                                                                                                                              
Loading rtl8187...                                                                                                                              
Loading p54pci...                                                                                                                               
Loading p54usb...                                                                                                                               
Loading iwl3945...                                                                                                                              
Loading iwlagn...                                                                                                                               
Loading ath...                                                                                                                                  
Loading ar9170usb...                                                                                                                            
Loading rtl8180...                                                                                                                              
Loading rtl8187...                                                                                                                              
Loading rt2400pci...                                                                                                                            
Loading rt2500pci...                                                                                                                            
Loading rt61pci...                                                                                                                              
Loading rt2500usb...                                                                                                                            
Loading rt73usb...                                                                                                                              
Loading rndis_wlan...                                                                                                                           
Loading at76_usb...                                                                                                                             
Loading mwl8k...                                                                                                                                
Loading mac80211_hwsim...                                                                                                                       
Loading at76c50x_usb...                                                                                                                         
Module ath_pci not detected -- this is fine                                                                                                     
ath5k loaded successfully                                                                                                                       
ath9k loaded successfully                                                                                                                       
Module bcm43xx not detected -- this is fine                                                                                                     
Module wl not detected -- this is fine                                                                                                          
b43 loaded successfully                                                                                                                         
b43legacy loaded successfully 
```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make install
```

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko    
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko                         
kernel/drivers/net/usb/cdc_ether.ko               
kernel/drivers/misc/eeprom_93cx6.ko               
kernel/drivers/net/wireless/ipw2100.ko            
kernel/drivers/net/wireless/ipw2200.ko            
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko    
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko     
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko    
kernel/drivers/net/wireless/libertas/libertas.ko  
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/p54/p54common.ko              
kernel/drivers/net/wireless/p54/p54pci.ko                 
kernel/drivers/net/wireless/p54/p54usb.ko                 
kernel/drivers/net/usb/rndis_host.ko                      
kernel/drivers/net/wireless/rndis_wlan.ko                 
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko           
kernel/drivers/net/wireless/rt2x00/rt61pci.ko             
kernel/drivers/net/wireless/rt2x00/rt73usb.ko             
kernel/drivers/net/wireless/rtl8180.ko                    
kernel/drivers/net/wireless/rtl8187.ko                    
kernel/drivers/ssb/ssb.ko                                 
kernel/drivers/net/wireless/libertas/usb8xxx.ko           
kernel/drivers/net/usb/usbnet.ko                          
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko          

make -C /lib/modules/2.6.28-11-generic/build M=/home/user/Desktop/compat-wireless-2009-08-04 "INSTALL_MOD_DIR=updates"  \
                modules_install                                                                                             
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'                                                      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.ko                              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/b44.ko                                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.ko                                     
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/rndis_host.ko                                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/usbnet.ko                                        
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/adm8211.ko                                  
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.ko                             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170usb.ko                     
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath.ko                                  
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.ko                                  
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.ko                      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlagn.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlcore.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas.ko                        
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_cs.ko                     
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_sdio.ko                   
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_spi.ko                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/usb8xxx.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.ko                  
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.ko                                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54common.ko                            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.ko                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.ko                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.ko                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.ko                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.ko                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.ko                            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd1211rw.ko                        
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/ssb.ko                                               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mac80211.ko                                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/rfkill_backport.ko                                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/cfg80211.ko                                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211.ko                                         
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.ko                              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.ko                              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.ko                               
  DEPMOD  2.6.28-11-generic                                                                                                 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'                                                       
[: 9: missing ]                                                                                                             
[: 9: missing ]                                                                                                             
depmod will prefer updates/ over kernel/ -- OK!                                                                             

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko        
updates/drivers/net/wireless/ath/ath.ko             
updates/drivers/net/wireless/ath/ath5k/ath5k.ko     
updates/drivers/net/wireless/ath/ath9k/ath9k.ko     
updates/drivers/net/wireless/b43/b43.ko             
updates/drivers/net/wireless/b43legacy/b43legacy.ko 
updates/drivers/net/b44.ko                          
updates/drivers/net/usb/cdc_ether.ko                
updates/drivers/misc/eeprom/eeprom_93cx6.ko         
updates/drivers/net/wireless/ipw2x00/ipw2100.ko     
updates/drivers/net/wireless/ipw2x00/ipw2200.ko     
updates/drivers/net/wireless/iwlwifi/iwl3945.ko     
updates/drivers/net/wireless/iwlwifi/iwlagn.ko      
updates/drivers/net/wireless/iwlwifi/iwlcore.ko     
updates/net/wireless/lib80211_crypt_ccmp.ko         
updates/net/wireless/lib80211_crypt_tkip.ko         
updates/net/wireless/lib80211_crypt_wep.ko          
updates/drivers/net/wireless/libertas/libertas.ko   
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.
```

---

### Post by pytheas22 on 2009-08-04
hmmm, it looks like you didn't actually compile anything, but I'm not what when wrong.  Could you please try deleting all the files on your desktop whose names start with 'compat-wireless', then running the commands from my last post again?  The command 'make' should produce more than just a 'Nothing to be done for `all'' message.

---

### Post by BitaCookie on 2009-08-05
The command "make" produced more than "Nothing to be done for `all" the first time I used. In the last post I only showed the result for the second time I run again all the commands you recommend me. I run the commands again because I saw that there was no result the first time. I am sorry, I didn't tell you.

I did it again:

user@user:~/Desktop/compat-wireless-2009-08-04$ make

(just a part of the code because I didn't see where the other part went)

```
compat-wireless-2009-08-04/include/net/ieee80211_radiotap.h             
compat-wireless-2009-08-04/include/net/mac80211.h                       
compat-wireless-2009-08-04/include/net/compat-2.6.23.h                  
compat-wireless-2009-08-04/include/linux/                               
compat-wireless-2009-08-04/include/linux/ieee80211.h                    
compat-wireless-2009-08-04/include/linux/nl80211.h                      
compat-wireless-2009-08-04/include/linux/pm_qos_params.h                
compat-wireless-2009-08-04/include/linux/ssb/                           
compat-wireless-2009-08-04/include/linux/ssb/ssb_regs.h                 
compat-wireless-2009-08-04/include/linux/ssb/ssb_driver_gige.h          
compat-wireless-2009-08-04/include/linux/ssb/ssb_driver_extif.h         
compat-wireless-2009-08-04/include/linux/ssb/ssb_driver_mips.h          
compat-wireless-2009-08-04/include/linux/ssb/ssb_driver_pci.h           
compat-wireless-2009-08-04/include/linux/ssb/ssb_driver_chipcommon.h    
compat-wireless-2009-08-04/include/linux/ssb/ssb_embedded.h             
compat-wireless-2009-08-04/include/linux/ssb/ssb.h                      
compat-wireless-2009-08-04/include/linux/rfkill_backport.h              
compat-wireless-2009-08-04/include/linux/spi/                           
compat-wireless-2009-08-04/include/linux/spi/wl12xx.h                   
compat-wireless-2009-08-04/include/linux/spi/libertas_spi.h             
compat-wireless-2009-08-04/include/linux/ath9k_platform.h               
compat-wireless-2009-08-04/include/linux/usb/                           
compat-wireless-2009-08-04/include/linux/usb/rndis_host.h               
compat-wireless-2009-08-04/include/linux/usb/usbnet.h                   
compat-wireless-2009-08-04/include/linux/bitops.h                       
compat-wireless-2009-08-04/include/linux/unaligned/                     
compat-wireless-2009-08-04/include/linux/unaligned/generic.h            
compat-wireless-2009-08-04/include/linux/unaligned/le_byteshift.h       
compat-wireless-2009-08-04/include/linux/unaligned/be_byteshift.h       
compat-wireless-2009-08-04/include/linux/unaligned/packed_struct.h      
compat-wireless-2009-08-04/include/linux/unaligned/le_struct.h          
compat-wireless-2009-08-04/include/linux/unaligned/be_memmove.h         
compat-wireless-2009-08-04/include/linux/unaligned/be_struct.h          
compat-wireless-2009-08-04/include/linux/unaligned/access_ok.h          
compat-wireless-2009-08-04/include/linux/unaligned/le_memmove.h         
compat-wireless-2009-08-04/include/linux/unaligned/memmove.h            
compat-wireless-2009-08-04/include/linux/pci_ids.h                      
compat-wireless-2009-08-04/include/linux/wireless.h                     
compat-wireless-2009-08-04/include/linux/eeprom_93cx6.h                 
compat-wireless-2009-08-04/compat/                                      
compat-wireless-2009-08-04/compat/compat-2.6.26.c                       
compat-wireless-2009-08-04/compat/compat-2.6.24.c                       
compat-wireless-2009-08-04/compat/compat-2.6.27.h                       
compat-wireless-2009-08-04/compat/compat-2.6.31.h                       
compat-wireless-2009-08-04/compat/compat-2.6.22.h                       
compat-wireless-2009-08-04/compat/compat-2.6.32.h                       
compat-wireless-2009-08-04/compat/compat-2.6.25.c                       
compat-wireless-2009-08-04/compat/compat.h                              
compat-wireless-2009-08-04/compat/compat-2.6.24.h                       
compat-wireless-2009-08-04/compat/compat-2.6.27.c                       
compat-wireless-2009-08-04/compat/compat-2.6.25.h                       
compat-wireless-2009-08-04/compat/compat-2.6.29.c                       
compat-wireless-2009-08-04/compat/compat-2.6.30.h                       
compat-wireless-2009-08-04/compat/compat-2.6.30.c                       
compat-wireless-2009-08-04/compat/compat-2.6.32.c                       
compat-wireless-2009-08-04/compat/compat-2.6.22.c                       
compat-wireless-2009-08-04/compat/compat-2.6.28.h                       
compat-wireless-2009-08-04/compat/compat-2.6.28.c                       
compat-wireless-2009-08-04/compat/compat-2.6.29.h                       
compat-wireless-2009-08-04/compat/compat-2.6.26.h                       
compat-wireless-2009-08-04/compat/compat-2.6.23.c                       
compat-wireless-2009-08-04/compat/compat.diff                           
compat-wireless-2009-08-04/compat/compat-2.6.31.c                       
compat-wireless-2009-08-04/compat/compat-2.6.23.h                       
compat-wireless-2009-08-04/net/                                         
compat-wireless-2009-08-04/net/wireless/                                
compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.c           
compat-wireless-2009-08-04/net/wireless/reg.c                           
compat-wireless-2009-08-04/net/wireless/compat-2.6.26.c                 
compat-wireless-2009-08-04/net/wireless/Makefile                        
compat-wireless-2009-08-04/net/wireless/nl80211.c                       
compat-wireless-2009-08-04/net/wireless/sysfs.c                         
compat-wireless-2009-08-04/net/wireless/compat-2.6.24.c                 
compat-wireless-2009-08-04/net/wireless/scan.c                          
compat-wireless-2009-08-04/net/wireless/debugfs.c                       
compat-wireless-2009-08-04/net/wireless/nl80211.h                       
compat-wireless-2009-08-04/net/wireless/mlme.c                          
compat-wireless-2009-08-04/net/wireless/debugfs.h                       
compat-wireless-2009-08-04/net/wireless/compat-2.6.25.c                 
compat-wireless-2009-08-04/net/wireless/wext.c                          
compat-wireless-2009-08-04/net/wireless/scan.c.orig                     
compat-wireless-2009-08-04/net/wireless/compat-2.6.27.c                 
compat-wireless-2009-08-04/net/wireless/radiotap.c                      
compat-wireless-2009-08-04/net/wireless/compat-2.6.29.c                 
compat-wireless-2009-08-04/net/wireless/sysfs.h                         
compat-wireless-2009-08-04/net/wireless/compat-2.6.30.c                 
compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.c            
compat-wireless-2009-08-04/net/wireless/compat-2.6.32.c                 
compat-wireless-2009-08-04/net/wireless/core.h                          
compat-wireless-2009-08-04/net/wireless/wext.c.orig                     
compat-wireless-2009-08-04/net/wireless/compat-2.6.22.c                 
compat-wireless-2009-08-04/net/wireless/core.c                          
compat-wireless-2009-08-04/net/wireless/compat-2.6.28.c                 
compat-wireless-2009-08-04/net/wireless/reg.h                           
compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.c           
compat-wireless-2009-08-04/net/wireless/compat-2.6.23.c                 
compat-wireless-2009-08-04/net/wireless/util.c                          
compat-wireless-2009-08-04/net/wireless/wext-compat.c                   
compat-wireless-2009-08-04/net/wireless/wext-sme.c                      
compat-wireless-2009-08-04/net/wireless/wext-compat.h                   
compat-wireless-2009-08-04/net/wireless/compat-2.6.31.c                 
compat-wireless-2009-08-04/net/wireless/lib80211.c                      
compat-wireless-2009-08-04/net/wireless/ibss.c                          
compat-wireless-2009-08-04/net/wireless/sme.c                           
compat-wireless-2009-08-04/net/mac80211/                                
compat-wireless-2009-08-04/net/mac80211/Makefile                        
compat-wireless-2009-08-04/net/mac80211/debugfs_sta.c                   
compat-wireless-2009-08-04/net/mac80211/driver-trace.c                  
compat-wireless-2009-08-04/net/mac80211/rate.h                          
compat-wireless-2009-08-04/net/mac80211/debugfs_key.c                   
compat-wireless-2009-08-04/net/mac80211/scan.c                          
compat-wireless-2009-08-04/net/mac80211/debugfs.c                       
compat-wireless-2009-08-04/net/mac80211/debugfs_sta.h                   
compat-wireless-2009-08-04/net/mac80211/aes_ccm.h                       
compat-wireless-2009-08-04/net/mac80211/agg-rx.c                        
compat-wireless-2009-08-04/net/mac80211/wme.h                           
compat-wireless-2009-08-04/net/mac80211/mesh_pathtbl.c                  
compat-wireless-2009-08-04/net/mac80211/mlme.c                          
compat-wireless-2009-08-04/net/mac80211/rc80211_pid.h                   
compat-wireless-2009-08-04/net/mac80211/wpa.h                           
compat-wireless-2009-08-04/net/mac80211/debugfs.h                       
compat-wireless-2009-08-04/net/mac80211/debugfs_key.h                   
compat-wireless-2009-08-04/net/mac80211/cfg.h                           
compat-wireless-2009-08-04/net/mac80211/pm.c                            
compat-wireless-2009-08-04/net/mac80211/aes_cmac.c                      
compat-wireless-2009-08-04/net/mac80211/rc80211_pid_debugfs.c           
compat-wireless-2009-08-04/net/mac80211/driver-ops.h                    
compat-wireless-2009-08-04/net/mac80211/cfg.c                           
compat-wireless-2009-08-04/net/mac80211/debugfs_netdev.h                
compat-wireless-2009-08-04/net/mac80211/iface.c.orig                    
compat-wireless-2009-08-04/net/mac80211/wpa.c                           
compat-wireless-2009-08-04/net/mac80211/aes_cmac.h                      
compat-wireless-2009-08-04/net/mac80211/ht.c                            
compat-wireless-2009-08-04/net/mac80211/rate.c                          
compat-wireless-2009-08-04/net/mac80211/rc80211_minstrel_debugfs.c      
compat-wireless-2009-08-04/net/mac80211/led.c                           
compat-wireless-2009-08-04/net/mac80211/wme.c                           
compat-wireless-2009-08-04/net/mac80211/driver-trace.h                  
compat-wireless-2009-08-04/net/mac80211/sta_info.c                      
compat-wireless-2009-08-04/net/mac80211/wep.h                           
compat-wireless-2009-08-04/net/mac80211/ieee80211_i.h                   
compat-wireless-2009-08-04/net/mac80211/agg-tx.c                        
compat-wireless-2009-08-04/net/mac80211/main.c                          
compat-wireless-2009-08-04/net/mac80211/rx.c                            
compat-wireless-2009-08-04/net/mac80211/tx.c                            
compat-wireless-2009-08-04/net/mac80211/aes_ccm.c                       
compat-wireless-2009-08-04/net/mac80211/key.c                           
compat-wireless-2009-08-04/net/mac80211/mesh.h                          
compat-wireless-2009-08-04/net/mac80211/tkip.h                          
compat-wireless-2009-08-04/net/mac80211/key.h                           
compat-wireless-2009-08-04/net/mac80211/led.h                           
compat-wireless-2009-08-04/net/mac80211/event.c                         
compat-wireless-2009-08-04/net/mac80211/rc80211_minstrel.h              
compat-wireless-2009-08-04/net/mac80211/debugfs_netdev.c                
compat-wireless-2009-08-04/net/mac80211/spectmgmt.c                     
compat-wireless-2009-08-04/net/mac80211/mesh.c                          
compat-wireless-2009-08-04/net/mac80211/wep.c                           
compat-wireless-2009-08-04/net/mac80211/rc80211_minstrel.c              
compat-wireless-2009-08-04/net/mac80211/sta_info.h                      
compat-wireless-2009-08-04/net/mac80211/tkip.c                          
compat-wireless-2009-08-04/net/mac80211/util.c                          
compat-wireless-2009-08-04/net/mac80211/mesh_plink.c                    
compat-wireless-2009-08-04/net/mac80211/michael.c                       
compat-wireless-2009-08-04/net/mac80211/iface.c                         
compat-wireless-2009-08-04/net/mac80211/rc80211_pid_algo.c              
compat-wireless-2009-08-04/net/mac80211/michael.h                       
compat-wireless-2009-08-04/net/mac80211/mesh_hwmp.c                     
compat-wireless-2009-08-04/net/mac80211/ibss.c                          
compat-wireless-2009-08-04/net/rfkill/                                  
compat-wireless-2009-08-04/net/rfkill/Makefile                          
compat-wireless-2009-08-04/net/rfkill/rfkill.h                          
compat-wireless-2009-08-04/net/rfkill/core.c                            
compat-wireless-2009-08-04/net/rfkill/input.c                           
compat-wireless-2009-08-04/drivers/                                     
compat-wireless-2009-08-04/drivers/ssb/                                 
compat-wireless-2009-08-04/drivers/ssb/Makefile                         
compat-wireless-2009-08-04/drivers/ssb/scan.c                           
compat-wireless-2009-08-04/drivers/ssb/sprom.c                          
compat-wireless-2009-08-04/drivers/ssb/embedded.c                       
compat-wireless-2009-08-04/drivers/ssb/ssb_private.h                    
compat-wireless-2009-08-04/drivers/ssb/b43_pci_bridge.c                 
compat-wireless-2009-08-04/drivers/ssb/driver_chipcommon.c              
compat-wireless-2009-08-04/drivers/ssb/pci.c                            
compat-wireless-2009-08-04/drivers/ssb/driver_gige.c                    
compat-wireless-2009-08-04/drivers/ssb/driver_chipcommon_pmu.c          
compat-wireless-2009-08-04/drivers/ssb/driver_mipscore.c                
compat-wireless-2009-08-04/drivers/ssb/driver_pcicore.c                 
compat-wireless-2009-08-04/drivers/ssb/main.c                           
compat-wireless-2009-08-04/drivers/ssb/driver_extif.c                   
compat-wireless-2009-08-04/drivers/ssb/pcihost_wrapper.c                
compat-wireless-2009-08-04/drivers/ssb/pcmcia.c                         
compat-wireless-2009-08-04/drivers/net/                                 
compat-wireless-2009-08-04/drivers/net/wireless/                        
compat-wireless-2009-08-04/drivers/net/wireless/Makefile                
compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.c        
compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.h          
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/                
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_dev.c   
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/Makefile        
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_rtl8225.h
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_leds.h   
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_grf5101.h
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.h        
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_rtl8225.h
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.h        
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_rtl8225.c
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_dev.c    
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_rtl8225.c
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_max2820.h
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_max2820.c
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_leds.c   
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl818x.h        
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_sa2400.h 
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_grf5101.c
compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_sa2400.c 
compat-wireless-2009-08-04/drivers/net/wireless/ath/                     
compat-wireless-2009-08-04/drivers/net/wireless/ath/Makefile             
compat-wireless-2009-08-04/drivers/net/wireless/ath/regd.c               
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/               
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/eeprom.h       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/Makefile       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/dma.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/reset.c        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/rfgain.h       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/caps.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/initvals.c     
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/eeprom.c       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/base.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/rfbuffer.h     
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/base.h         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/led.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/attach.c       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/gpio.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/reg.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/qcu.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/rfkill.c       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/desc.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/debug.c        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/desc.h         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/pcu.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/phy.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/debug.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/regd.h               
compat-wireless-2009-08-04/drivers/net/wireless/ath/regd_common.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/               
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/eeprom.h       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/Makefile       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/hw.c.orig      
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/hw.h           
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ani.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ani.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/mac.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/eeprom.c       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/phy.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/xmit.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/virtual.c      
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/calib.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/pci.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/calib.c        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/rc.h           
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/rc.c           
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/beacon.c       
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/main.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/reg.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/mac.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/debug.c        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/initvals.h     
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/hw.c           
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/recv.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ahb.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/phy.c          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/debug.h        
compat-wireless-2009-08-04/drivers/net/wireless/ath/main.c               
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/              
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/eeprom.h      
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/Makefile      
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/usb.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/hw.h          
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/mac.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/cmd.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/led.c         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170.h      
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/usb.h         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/main.c        
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/cmd.h         
compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/phy.c         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/               
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/Makefile       
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/sysfs.c        
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/dma.c          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/pio.h          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/radio.c        
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/debugfs.c      
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/rfkill.h       
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/debugfs.h      
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/phy.h          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/xmit.c         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/sysfs.h        
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/radio.h        
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/main.h         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/pio.c          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/main.c         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/ilt.c          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/rfkill.c       
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/xmit.h         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/dma.h          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/leds.h         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/ilt.h          
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.h    
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/leds.c         
compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/phy.c          
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/             
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/Makefile     
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.h
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/if_usb.c     
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/cmd.c        
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/if_usb.h     
compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/main.c       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/                  
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_init.h     
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/Makefile          
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_acx.c      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_acx.h      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_boot.c     
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_spi.c      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_debugfs.h  
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_event.h    
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_netlink.h  
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_event.c    
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ops.c      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_debugfs.c  
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_rx.c       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_cmd.h      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_main.c     
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_rx.h       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ps.c       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_boot.h     
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_init.c     
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_tx.h       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.h          
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/reg.h             
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_spi.h      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ps.h       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_cmd.c      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ops.h      
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_tx.c       
compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl12xx_80211.h    
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/                
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/Makefile        
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_uw2453.c  
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_rf2959.c  
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_al2230.c  
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_usb.h        
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_al7230b.c 
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_usb.c        
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf.c         
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf.h         
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_chip.h       
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_def.h        
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_chip.c       
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_mac.c        
compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_mac.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/            
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/eeprom.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/Makefile    
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/cfg80211.c  
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/debugfs.c   
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/rx.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/cfg80211.h  
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/commands.c  
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/eeprom.c    
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/hal.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/netdev.c    
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/lmac.h      
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/fw.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/bus.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/hal.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/fw.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/iwm.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/main.c      
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/rx.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/tx.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/commands.h  
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/sdio.h      
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/sdio.c      
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/umac.h      
compat-wireless-2009-08-04/drivers/net/wireless/iwmc3200wifi/debug.h     
compat-wireless-2009-08-04/drivers/net/wireless/adm8211.h                
compat-wireless-2009-08-04/drivers/net/wireless/libertas/                
compat-wireless-2009-08-04/drivers/net/wireless/libertas/hostcmd.h       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/Makefile        
compat-wireless-2009-08-04/drivers/net/wireless/libertas/scan.c          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/debugfs.c       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_sdio.h       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_usb.c        
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_spi.h        
compat-wireless-2009-08-04/drivers/net/wireless/libertas/debugfs.h       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/dev.h           
compat-wireless-2009-08-04/drivers/net/wireless/libertas/persistcfg.c    
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_sdio.c       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/wext.c          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/types.h         
compat-wireless-2009-08-04/drivers/net/wireless/libertas/cmd.c           
compat-wireless-2009-08-04/drivers/net/wireless/libertas/wext.h          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_usb.h        
compat-wireless-2009-08-04/drivers/net/wireless/libertas/cmdresp.c       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/11d.h           
compat-wireless-2009-08-04/drivers/net/wireless/libertas/main.c          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/rx.c            
compat-wireless-2009-08-04/drivers/net/wireless/libertas/tx.c            
compat-wireless-2009-08-04/drivers/net/wireless/libertas/ethtool.c       
compat-wireless-2009-08-04/drivers/net/wireless/libertas/host.h          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/scan.h          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/cmd.h           
compat-wireless-2009-08-04/drivers/net/wireless/libertas/assoc.h         
compat-wireless-2009-08-04/drivers/net/wireless/libertas/radiotap.h      
compat-wireless-2009-08-04/drivers/net/wireless/libertas/11d.c           
compat-wireless-2009-08-04/drivers/net/wireless/libertas/defs.h          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/assoc.c         
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_spi.c        
compat-wireless-2009-08-04/drivers/net/wireless/libertas/decl.h          
compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_cs.c         
compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.c             
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/                  
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/Makefile          
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.c         
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00dev.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00debug.c     
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00queue.h     
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00leds.h      
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00ht.c        
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00leds.c      
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00debug.h     
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00config.c    
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00firmware.c  
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00queue.c     
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00link.c      
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00dump.h      
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.c         
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00.h          
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00mac.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.h         
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00crypto.c    
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00reg.h       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.h         
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.c       
compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/                 
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-agn-rs.c     
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/Makefile         
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-core.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-hw.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-csr.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-6000.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-led.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-spectrum.h   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-debugfs.c    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-fh.h         
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-sta.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-agn-rs.h     
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-power.c      
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-eeprom.h     
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-commands.h   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-1000.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-dev.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-4965-hw.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-hcmd.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-scan.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-calib.h      
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-5000.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-tx.c         
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-4965.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-eeprom.c     
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-power.h      
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-io.h         
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-led.h   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-led.c   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-led.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945-base.c   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-core.c       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-prph.h       
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-rs.c    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-agn.c        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-calib.c      
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-6000-hw.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-5000-hw.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-rx.c         
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-helpers.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-sta.h        
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-spectrum.c   
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-fh.h    
compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-debug.h      
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/                 
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/Makefile         
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ieee80211.h      
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_wx.c      
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_tx.c      
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.h        
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_module.c  
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_rx.c      
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_geo.c     
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.c        
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.c        
compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.h        
compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.c           
compat-wireless-2009-08-04/drivers/net/wireless/adm8211.c                
compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.c                  
compat-wireless-2009-08-04/drivers/net/wireless/p54/                     
compat-wireless-2009-08-04/drivers/net/wireless/p54/eeprom.h             
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.c             
compat-wireless-2009-08-04/drivers/net/wireless/p54/Makefile             
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.h             
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54.h                
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.h             
compat-wireless-2009-08-04/drivers/net/wireless/p54/eeprom.c             
compat-wireless-2009-08-04/drivers/net/wireless/p54/lmac.h               
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi_eeprom.h      
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.c             
compat-wireless-2009-08-04/drivers/net/wireless/p54/led.c                
compat-wireless-2009-08-04/drivers/net/wireless/p54/fwio.c               
compat-wireless-2009-08-04/drivers/net/wireless/p54/main.c               
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.c             
compat-wireless-2009-08-04/drivers/net/wireless/p54/txrx.c               
compat-wireless-2009-08-04/drivers/net/wireless/p54/net2280.h            
compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.h             
compat-wireless-2009-08-04/drivers/net/wireless/b43/                     
compat-wireless-2009-08-04/drivers/net/wireless/b43/Makefile             
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables.c             
compat-wireless-2009-08-04/drivers/net/wireless/b43/sysfs.c              
compat-wireless-2009-08-04/drivers/net/wireless/b43/dma.c                
compat-wireless-2009-08-04/drivers/net/wireless/b43/pio.h                
compat-wireless-2009-08-04/drivers/net/wireless/b43/debugfs.c            
compat-wireless-2009-08-04/drivers/net/wireless/b43/rfkill.h             
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables_nphy.h        
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_lp.h             
compat-wireless-2009-08-04/drivers/net/wireless/b43/debugfs.h            
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_common.c         
compat-wireless-2009-08-04/drivers/net/wireless/b43/xmit.c               
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_n.h              
compat-wireless-2009-08-04/drivers/net/wireless/b43/sysfs.h              
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables_lpphy.h       
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_lp.c             
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_g.h              
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_n.c              
compat-wireless-2009-08-04/drivers/net/wireless/b43/main.h               
compat-wireless-2009-08-04/drivers/net/wireless/b43/pio.c                
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_common.h         
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_g.c              
compat-wireless-2009-08-04/drivers/net/wireless/b43/main.c               
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables_lpphy.c       
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables.h             
compat-wireless-2009-08-04/drivers/net/wireless/b43/pcmcia.h             
compat-wireless-2009-08-04/drivers/net/wireless/b43/rfkill.c             
compat-wireless-2009-08-04/drivers/net/wireless/b43/xmit.h               
compat-wireless-2009-08-04/drivers/net/wireless/b43/dma.h                
compat-wireless-2009-08-04/drivers/net/wireless/b43/tables_nphy.c        
compat-wireless-2009-08-04/drivers/net/wireless/b43/leds.h               
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_a.c              
compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.h                
compat-wireless-2009-08-04/drivers/net/wireless/b43/lo.c                 
compat-wireless-2009-08-04/drivers/net/wireless/b43/pcmcia.c             
compat-wireless-2009-08-04/drivers/net/wireless/b43/leds.c               
compat-wireless-2009-08-04/drivers/net/wireless/b43/wa.c                 
compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_a.h              
compat-wireless-2009-08-04/drivers/net/wireless/b43/wa.h                 
compat-wireless-2009-08-04/drivers/net/wireless/b43/lo.h                 
compat-wireless-2009-08-04/drivers/net/usb/                              
compat-wireless-2009-08-04/drivers/net/usb/Makefile                      
compat-wireless-2009-08-04/drivers/net/usb/rndis_host.c                  
compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.c                   
compat-wireless-2009-08-04/drivers/net/usb/usbnet.c                      
compat-wireless-2009-08-04/drivers/net/b44.c                             
compat-wireless-2009-08-04/drivers/net/b44.h                             
compat-wireless-2009-08-04/drivers/misc/                                 
compat-wireless-2009-08-04/drivers/misc/eeprom/                          
compat-wireless-2009-08-04/drivers/misc/eeprom/Makefile                  
compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.c            
compat-wireless-2009-08-04/.gitignore                                    
compat-wireless-2009-08-04/scripts/                                      
compat-wireless-2009-08-04/scripts/b43enable                             
compat-wireless-2009-08-04/scripts/admin-clean.sh                        
compat-wireless-2009-08-04/scripts/gen-stable-release.sh                 
compat-wireless-2009-08-04/scripts/check_depmod                          
compat-wireless-2009-08-04/scripts/b43load                               
compat-wireless-2009-08-04/scripts/load.sh                               
compat-wireless-2009-08-04/scripts/athenable                             
compat-wireless-2009-08-04/scripts/check_config.sh                       
compat-wireless-2009-08-04/scripts/iwl-load                              
compat-wireless-2009-08-04/scripts/athload                               
compat-wireless-2009-08-04/scripts/madwifi-unload                        
compat-wireless-2009-08-04/scripts/gen-compat-autoconf.sh                
compat-wireless-2009-08-04/scripts/modlib.sh                             
compat-wireless-2009-08-04/scripts/iwl-enable                            
compat-wireless-2009-08-04/scripts/compress_modules                      
compat-wireless-2009-08-04/scripts/admin-refresh.sh                      
compat-wireless-2009-08-04/scripts/admin-update.sh                       
compat-wireless-2009-08-04/scripts/unload.sh  
```user@user:~/Desktop$ cd compat-wireless*
                        
user@user:~/Desktop/compat-wireless-2009-08-04$ make
```
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.28-11-generic/build M=/home/user/Desktop/compat-wireless-2009-08-04 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'                                 
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/built-in.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.o          
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/built-in.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.o                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/rndis_host.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/usbnet.o                    
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/built-in.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/main.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/regd.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath.o              
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/built-in.o  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/usb.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/main.o      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/cmd.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/mac.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/phy.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/led.o       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170usb.o 
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/built-in.o   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/caps.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/initvals.o   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/eeprom.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/gpio.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/desc.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/dma.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/qcu.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/pcu.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/phy.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/reset.o      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/attach.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/base.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/led.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/rfkill.o     
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.o      
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/built-in.o   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/hw.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/eeprom.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/mac.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/calib.o      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ani.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/phy.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/beacon.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/main.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/recv.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/xmit.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/virtual.o    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/rc.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/pci.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.o      
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/built-in.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/main.o             
/home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/main.c: In function â€˜b43_request_firmwareâ€™:                                                                                                       
/home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/main.c:2215: warning: format not a string literal and no format arguments                                                                         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/tables.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_common.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_g.o                   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/phy_a.o                   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/sysfs.o                   
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/xmit.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/lo.o                      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/wa.o                      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/dma.o                     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/pio.o                     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/rfkill.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/leds.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/pcmcia.o                  
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.o                     
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/built-in.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/main.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/ilt.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/phy.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/radio.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/sysfs.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/xmit.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/rfkill.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/leds.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/debugfs.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/dma.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/pio.o               
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.o         
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/built-in.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_module.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_tx.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_rx.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_wx.o           
/home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_wx.c: In function â€˜ieee80211_wx_set_encodeextâ€™:                                                                                        
/home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_wx.c:622: warning: format not a string literal and no format arguments                                                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw_geo.o          
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw.o              
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/built-in.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945-base.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-rs.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-3945-led.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-agn.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-agn-rs.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-4965.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-5000.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-6000.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-1000.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-core.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-eeprom.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-hcmd.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-power.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-rx.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-tx.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-sta.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-calib.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-scan.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-led.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl-spectrum.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlcore.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlagn.o              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945.o             
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/built-in.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/main.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/wext.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/rx.o                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/tx.o                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/cmd.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/cmdresp.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/scan.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/11d.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/debugfs.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/persistcfg.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/ethtool.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/assoc.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_cs.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_sdio.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_spi.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/if_usb.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas.o           
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/usb8xxx.o            
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_cs.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_sdio.o      
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_spi.o       
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/built-in.o        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/main.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/cmd.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/if_usb.o          
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.o     
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf_usb.o 
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/built-in.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/eeprom.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/fwio.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/txrx.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/main.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/led.o                     
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54common.o               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.o                  
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/built-in.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00dev.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00mac.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00config.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00queue.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00link.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00crypto.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00firmware.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00leds.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00ht.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.o            
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/built-in.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_dev.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_rtl8225.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_sa2400.o      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_max2820.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180_grf5101.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_dev.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_rtl8225.o     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187_leds.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.o             
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/built-in.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_main.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_spi.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_event.o         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_tx.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_rx.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ps.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_cmd.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_acx.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_boot.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_init.o          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_ops.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251_debugfs.o       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.o               
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/built-in.o           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_chip.o            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_mac.o             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_al2230.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_rf.o              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd_usb.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd1211rw.o           
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/built-in.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/adm8211.o                     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.o              
  LD      /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/built-in.o                             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/main.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/scan.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/sprom.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/pci.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/pcihost_wrapper.o                      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/pcmcia.o                               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/driver_chipcommon.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/driver_chipcommon_pmu.o                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/driver_pcicore.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/b43_pci_bridge.o                       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/ssb.o                                  
  LD      /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/built-in.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/main.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/sta_info.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/wep.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/wpa.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/scan.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/ht.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/agg-tx.o                              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/agg-rx.o                              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/ibss.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mlme.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/iface.o                               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rate.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/michael.o                             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/tkip.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/aes_ccm.o                             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/aes_cmac.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/cfg.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rx.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/spectmgmt.o                           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/tx.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/key.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/util.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/wme.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/event.o                               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/led.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/debugfs.o                             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/debugfs_sta.o                         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/debugfs_netdev.o                      
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/debugfs_key.o                         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mesh.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mesh_pathtbl.o                        
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mesh_plink.o                          
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mesh_hwmp.o                           
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/pm.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rc80211_pid_algo.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rc80211_pid_debugfs.o                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rc80211_minstrel.o                    
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/rc80211_minstrel_debugfs.o            
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mac80211.o                            
  LD      /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/built-in.o                              
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/core.o                                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/input.o                                 
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/rfkill_backport.o                       
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/wext.o                                
  LD      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/built-in.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/core.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/sysfs.o                               
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/radiotap.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/util.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/reg.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/scan.o                                
/home/user/Desktop/compat-wireless-2009-08-04/net/wireless/scan.c: In function â€˜cfg80211_bss_updateâ€™:      
/home/user/Desktop/compat-wireless-2009-08-04/net/wireless/scan.c:401: warning: unused variable â€˜usedâ€™     
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/nl80211.o                             
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/mlme.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/ibss.o                                
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/sme.o                                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/wext-compat.o                         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/wext-sme.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.27.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.28.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.29.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.30.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.31.o                       
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/compat-2.6.32.o                       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/cfg80211.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211.o                            
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.o                  
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.o                 
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.o                 
  LD      /home/user/Desktop/compat-wireless-2009-08-04/built-in.o                                         
  CC [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/b44.o                                  
  Building modules, stage 2.                                                                                  
  MODPOST 54 modules                                                                                          
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.mod.o             
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.ko                
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/b44.mod.o                              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/b44.ko                                 
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.mod.o                    
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.ko                       
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/rndis_host.mod.o                   
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/rndis_host.ko                      
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/usbnet.mod.o                       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/usbnet.ko                          
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/adm8211.mod.o                 
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/adm8211.ko                    
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.mod.o            
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.ko               
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170usb.mod.o    
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170usb.ko       
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath.mod.o                 
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath.ko                    
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.mod.o                 
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.ko                    
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.mod.o     
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.ko        
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw.mod.o          
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw.ko             
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlagn.mod.o          
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlagn.ko             
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlcore.mod.o         
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlcore.ko            
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas.mod.o       
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas.ko          
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_cs.mod.o    
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_cs.ko       
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_sdio.mod.o  
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_sdio.ko     
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_spi.mod.o   
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_spi.ko      
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/usb8xxx.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/usb8xxx.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.mod.o 
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.ko    
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf_usb.mod.o                                                                                                           
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.mod.o          
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.ko             
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.mod.o                   
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.ko                      
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54common.mod.o           
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54common.ko              
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.mod.o              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.ko                 
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.mod.o              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.ko                 
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.mod.o              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.ko                 
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.mod.o              
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.ko                 
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.ko           
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.mod.o        
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/ssb.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/ssb.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mac80211.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mac80211.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/rfkill_backport.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/rfkill_backport.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/cfg80211.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/cfg80211.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.ko
  CC      /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.mod.o
  LD [M]  /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make unload
```
Unloading ath9k...   
```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make load  
```
Loading ipw2100...                                                       
Loading ipw2200...                                                       
Loading libertas_cs...                                                   
Loading usb8xxx...                                                       
Loading p54pci...                                                        
Loading p54usb...                                                        
Loading adm8211...                                                       
Loading zd1211rw...                                                      
Loading rtl8180...                                                       
Loading rtl8187...                                                       
Loading p54pci...                                                        
Loading p54usb...                                                        
Loading iwl3945...                                                       
Loading iwlagn...                                                        
Loading ath...                                                           
Loading ar9170usb...                                                     
Loading rtl8180...                                                       
Loading rtl8187...                                                       
Loading rt2400pci...                                                     
Loading rt2500pci...                                                     
Loading rt61pci...                                                       
Loading rt2500usb...                                                     
Loading rt73usb...                                                       
Loading rndis_wlan...                                                    
Loading at76_usb...                                                      
Loading mwl8k...                                                         
Loading mac80211_hwsim...                                                
Loading at76c50x_usb...                                                  
Module ath_pci not detected -- this is fine                              
ath5k loaded successfully                                                
ath9k loaded successfully                                                
Module bcm43xx not detected -- this is fine                              
Module wl not detected -- this is fine                                   
b43 loaded successfully                                                  
b43legacy loaded successfully  

```user@user:~/Desktop/compat-wireless-2009-08-04$ sudo make install
```
Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko    
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko                         
kernel/drivers/net/usb/cdc_ether.ko               
kernel/drivers/misc/eeprom_93cx6.ko               
kernel/drivers/net/wireless/ipw2100.ko            
kernel/drivers/net/wireless/ipw2200.ko            
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko    
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko     
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko    
kernel/drivers/net/wireless/libertas/libertas.ko  
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/p54/p54common.ko              
kernel/drivers/net/wireless/p54/p54pci.ko                 
kernel/drivers/net/wireless/p54/p54usb.ko                 
kernel/drivers/net/usb/rndis_host.ko                      
kernel/drivers/net/wireless/rndis_wlan.ko                 
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko           
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko           
kernel/drivers/net/wireless/rt2x00/rt61pci.ko             
kernel/drivers/net/wireless/rt2x00/rt73usb.ko             
kernel/drivers/net/wireless/rtl8180.ko                    
kernel/drivers/net/wireless/rtl8187.ko                    
kernel/drivers/ssb/ssb.ko                                 
kernel/drivers/net/wireless/libertas/usb8xxx.ko           
kernel/drivers/net/usb/usbnet.ko                          
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko          

make -C /lib/modules/2.6.28-11-generic/build M=/home/user/Desktop/compat-wireless-2009-08-04 "INSTALL_MOD_DIR=updates"  \                                                                                                
                modules_install                                                                               
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'                                        
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/misc/eeprom/eeprom_93cx6.ko                
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/b44.ko                                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/cdc_ether.ko                       
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/rndis_host.ko                      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/usb/usbnet.ko                          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/adm8211.ko                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/at76c50x-usb.ko               
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ar9170/ar9170usb.ko       
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath.ko                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath5k/ath5k.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ath/ath9k/ath9k.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43/b43.ko                    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/b43legacy/b43legacy.ko        
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2100.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/ipw2200.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/ipw2x00/libipw.ko             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwl3945.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlagn.ko             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/iwlwifi/iwlcore.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas.ko          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_cs.ko       
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_sdio.ko     
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/libertas_spi.ko      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas/usb8xxx.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf.ko    
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mac80211_hwsim.ko             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/mwl8k.ko                      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54common.ko              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54pci.ko                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54spi.ko                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/p54/p54usb.ko                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rndis_wlan.ko                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2400pci.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500pci.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2500usb.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2800usb.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00lib.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00pci.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt2x00usb.ko           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt61pci.ko             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rt2x00/rt73usb.ko             
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8180.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/rtl818x/rtl8187.ko            
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/wl12xx/wl1251.ko              
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/net/wireless/zd1211rw/zd1211rw.ko          
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/drivers/ssb/ssb.ko                                 
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/mac80211/mac80211.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/rfkill/rfkill_backport.ko                      
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/cfg80211.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211.ko                           
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_ccmp.ko                
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_tkip.ko                
  INSTALL /home/user/Desktop/compat-wireless-2009-08-04/net/wireless/lib80211_crypt_wep.ko                 
  DEPMOD  2.6.28-11-generic                                                                                   
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'                                         
[: 9: missing ]                                                                                               
[: 9: missing ]                                                                                               
depmod will prefer updates/ over kernel/ -- OK!                                                               

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko        
updates/drivers/net/wireless/ath/ath.ko             
updates/drivers/net/wireless/ath/ath5k/ath5k.ko     
updates/drivers/net/wireless/ath/ath9k/ath9k.ko     
updates/drivers/net/wireless/b43/b43.ko             
updates/drivers/net/wireless/b43legacy/b43legacy.ko 
updates/drivers/net/b44.ko                          
updates/drivers/net/usb/cdc_ether.ko                
updates/drivers/misc/eeprom/eeprom_93cx6.ko         
updates/drivers/net/wireless/ipw2x00/ipw2100.ko     
updates/drivers/net/wireless/ipw2x00/ipw2200.ko     
updates/drivers/net/wireless/iwlwifi/iwl3945.ko     
updates/drivers/net/wireless/iwlwifi/iwlagn.ko      
updates/drivers/net/wireless/iwlwifi/iwlcore.ko     
updates/net/wireless/lib80211_crypt_ccmp.ko         
updates/net/wireless/lib80211_crypt_tkip.ko         
updates/net/wireless/lib80211_crypt_wep.ko          
updates/drivers/net/wireless/libertas/libertas.ko   
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko 
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

```

---

### Post by pytheas22 on 2009-08-05
It looks like the new driver was successfully compiled--it makes sense now that you received the "Nothing to be done for `all" when running the commands the second time; that's normal.

The next thing that I'd do to figure out why you can't connect is to disable the security on your router temporarily, then try connecting.  Please give this a try and let me know if it helps.

If that doesn't help, another thing to try is using the ath_pci driver instead of ath9k (which you're currently using).  To switch temporarily to ath_pci, type:
```

sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up
```

Then wait a few seconds and try connecting again.  (To go back to the original settings, just reboot and the changes applied by the commands above will be erased.)

---

### Post by BitaCookie on 2009-08-10
Hello pytheas,

First, I disabled the security on my router, but  I couldn't connect. I saw that the computer of the router didn't detect any computer (neither my computer with kubuntu).

Then, I run the commands you told me, and this is the result:

```
user@user:~$ sudo rmmod ath9k
[sudo] password for user:
ERROR: Module ath9k does not exist in /proc/modules
user@user:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
user@user:~$ sudo modprobe ath_pci
user@user:~$ ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
user@user:~$
```

---

### Post by BitaCookie on 2009-08-10
I rebooted the computer, and I obtained this (like the first time when I run the commands):

```
user@user:~$ sudo rmmod ath9k
[sudo] password for user:
user@user:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
user@user:~$ sudo modprobe ath_pci
user@user:~$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
user@user:~$
```

---

### Post by pytheas22 on 2009-08-11
hmmmm, that's strange that ath_pci is not bringing the device up.  Could you please post the output of these commands, in this order:
```

sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lsmod | grep ath
lshw -C Network
```

---

### Post by BitaCookie on 2009-08-12
After run the commands the wicd says: "No wireless networks found"
Then I used ethernet and I was connected to internet (wired). 

```
sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lsmod | grep ath
lshw -C Network

user@user:~$ sudo rmmod ath9k
[sudo] password for user:          
user@user:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
user@user:~$ sudo modprobe ath_pci
user@user:~$ dmesg | grep -e ath -e wlan
[    3.721327] device-mapper: multipath: version 1.0.5 loaded
[    3.721329] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.265213] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.265225] ath9k 0000:03:00.0: setting latency timer to 64               
[   11.695051] ath: EEPROM regdomain: 0x65                                   
[   11.695054] ath: EEPROM indicates we should expect a direct regpair map   
[   11.695057] ath: Country alpha2 being used: 00                            
[   11.695059] ath: Regpair used: 0x65                                       
[   11.805147] phy0: Selected rate control algorithm 'ath9k_rate_control'    
[   11.805913] Registered led device: ath9k-phy0::radio                      
[   11.805953] Registered led device: ath9k-phy0::assoc                      
[   11.805991] Registered led device: ath9k-phy0::tx                         
[   11.806029] Registered led device: ath9k-phy0::rx                         
[   16.116766] ADDRCONF(NETDEV_UP): wlan0: link is not ready                 
[  542.891969] ath9k 0000:03:00.0: PCI INT A disabled                        
[  542.892039] ath9k: Driver unloaded                                        
[  574.341912] ath_hal: module license 'Proprietary' taints kernel.          
[  574.343960] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  574.361963] wlan: 0.9.4                                                               
[  574.371366] ath_pci: 0.9.4                                                            
user@user:~$ lsmod | grep ath
ath_pci                99224  0       
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
ath                    16128  0        
cfg80211              131236  2 mac80211,ath
user@user:~$ lsh -C Network        
The program 'lsh' is currently not installed.  You can install it by typing:
sudo apt-get install lsh-client                                             
bash: lsh: command not found                                                
user@user:~$ lshw -C Network                                       
WARNING: you should run this program as super-user.                         
  *-network                                                                 
       description: Ethernet interface                                      
       product: 88E8071 PCI-E Gigabit Ethernet Controller                   
       vendor: Marvell Technology Group Ltd.                                
       physical id: 0                                                       
       bus info: pci@0000:02:00.0                                           
       logical name: eth0                                                   
       version: 16                                                          
       serial: 00:1d:72:f5:86:da                                            
       width: 64 bits                                                       
       clock: 33MHz                                                         
       capabilities: bus_master cap_list ethernet physical                  
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 7a:d5:6e:16:b1:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
```

---

### Post by pytheas22 on 2009-08-13
Ah, I think I know what's going on.  What happens if you type (please post all output):
```

sudo rmmod ath9k
sudo rmmod ath_hal
sudo rmmod ath_pci
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lshw -C Network
```

Sorry this is not going as quickly as you probably would like, but thanks for your patience.  We'll figure it out eventually.

---

### Post by BitaCookie on 2009-08-13
Hi pytheas22,
Here is the result.

user@user:~$ sudo rmmod ath9k
```
[sudo] password for user: 
```user@user:~$ sudo rmmod ath_hal
```
ERROR: Module ath_hal does not exist in /proc/modules
```user@user:~$ sudo rmmod ath_pci 
```
ERROR: Module ath_pci does not exist in /proc/modules
```user@user:~$ sudo modprobe ath_pci          
user@user:~$ dmesg | grep -e ath -e wlan 
```
[    3.729326] device-mapper: multipath: version 1.0.5 loaded
[    3.729328] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.741574] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.741585] ath9k 0000:03:00.0: setting latency timer to 64               
[   12.171486] ath: EEPROM regdomain: 0x65                                   
[   12.171489] ath: EEPROM indicates we should expect a direct regpair map   
[   12.171492] ath: Country alpha2 being used: 00                            
[   12.171493] ath: Regpair used: 0x65                                       
[   12.272155] phy0: Selected rate control algorithm 'ath9k_rate_control'    
[   12.272899] Registered led device: ath9k-phy0::radio                      
[   12.272940] Registered led device: ath9k-phy0::assoc                      
[   12.272979] Registered led device: ath9k-phy0::tx                         
[   12.273021] Registered led device: ath9k-phy0::rx                         
[   16.840237] ADDRCONF(NETDEV_UP): wlan0: link is not ready                 
[  118.310210] ath9k 0000:03:00.0: PCI INT A disabled                        
[  118.310254] ath9k: Driver unloaded                                        
[  167.316699] ath_hal: module license 'Proprietary' taints kernel.          
[  167.318776] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  167.336631] wlan: 0.9.4                                                               
[  167.346060] ath_pci: 0.9.4
```user@user:~$ lshw -C Network
```
WARNING: you should run this program as super-user.                                      
  *-network                                                                              
       description: Ethernet interface                                                   
       product: 88E8071 PCI-E Gigabit Ethernet Controller                                
       vendor: Marvell Technology Group Ltd.                                             
       physical id: 0                                                                    
       bus info: pci@0000:02:00.0                                                        
       logical name: eth0                                                                
       version: 16                                                                       
       serial: 00:1d:72:f5:86:da                                                         
       width: 64 bits                                                                    
       clock: 33MHz                                                                      
       capabilities: bus_master cap_list ethernet physical                               
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes                                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ce:ef:83:81:e2:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
user@user:~$

```

Thanks to you! :KS

---

### Post by pytheas22 on 2009-08-13
hmmm, I'm still not sure why ath_pci won't claim your wireless device.  But I think that recompiling it using madwifi's code (rather than compat-wireless) might help.  To do that, run these commands:

```
sudo apt-get update
sudo apt-get install subversion build-essential
svn co https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
```

At this step, you will be asked about accepting a certificate.  Press 'p' to accept it permanently.  Then let it download its stuff.  When it's finished, continue with:
```

cd madwifi-hal-0.10.5.6/
make
sudo make install
echo blacklist ath9k | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ath_pci /etc/modules

```

Then reboot and see if it works.  If it still doesn't, please post the output of:
```

lsmod | grep ath
lshw -C Network
dmesg | grep -e ath -e wlan
modinfo ath_pci
```

---

### Post by BitaCookie on 2009-08-13
After recompaling ath_pci using madwifi's code and rebooting, the wicd sayd: "no wireless networks found"

user@user:~$ lsmod | grep ath
user@user:~$ lshw -C Network
```
 
WARNING: you should run this program as super-user.
  *-network                                        
       description: Ethernet interface             
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.             
       physical id: 0                                    
       bus info: pci@0000:02:00.0                        
       logical name: eth0                                
       version: 16                                       
       serial: 00:1d:72:f5:86:da                         
       width: 64 bits                                    
       clock: 33MHz                                      
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller                                                                        
       product: AR928X Wireless Network Adapter (PCI-Express)                                                 
       vendor: Atheros Communications Inc.                                                                    
       physical id: 0                                                                                         
       bus info: pci@0000:03:00.0                                                                             
       version: 01                                                                                            
       width: 64 bits                                                                                         
       clock: 33MHz                                                                                           
       capabilities: bus_master cap_list                                                                      
       configuration: latency=0                                                                               
  *-network DISABLED                                                                                          
       description: Ethernet interface                                                                        
       physical id: 2                                                                                         
       logical name: pan0                                                                                     
       serial: 62:0f:38:79:46:28                                                                              
       capabilities: ethernet physical                                                                        
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```user@user:~$ dmesg | grep -e ath -e wlan
```
[    5.264323] device-mapper: multipath: version 1.0.5 loaded                                                 
[    5.264325] device-mapper: multipath round-robin: version 1.0.0 loaded
```user@user:~$ modinfo ath_pci 
```
filename:       /lib/modules/2.6.28-11-generic/net/ath_pci.ko                                                 
license:        Dual BSD/GPL                                                                                  
version:        svn r4068                                                                                     
description:    Support for Atheros 802.11 wireless LAN cards.                                                
author:         Errno Consulting, Sam Leffler                                                                 
srcversion:     5179E97F52752C9A394F7FE                                                                       
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*                                                          
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
user@user:~$
```

---

### Post by pytheas22 on 2009-08-14
Alright, please try this:
```

rm -r madwifi-hal-0.10.5.6*
wget http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz
tar -xzvf madwifi-hal-0.10.5.6.tar.gz
cd madwifi-hal-0.10.5.6
make
sudo make install
```

Now reboot and let me know the output of:
```

lshw -C Network
modinfo ath_pci
```

I modified the source code for the driver in order to force it to claim your card.  Hopefully this will finally do the trick.

---

### Post by BitaCookie on 2009-08-14
I have an answer when I type "rm -r madwifi-hal-0.10.5.6*"

```
user@user:~$ rm -r madwifi-hal-0.10.5.6*
rm: remove write-protected regular file `madwifi-hal-0.10.5.6/net80211/.svn/dir-prop-base'?

```

I should say: Y to all?

---

### Post by pytheas22 on 2009-08-14
Yes, say Y to all, or just type:
```

rm -rf madwifi-hal-0.10.5.6*
```

(note the '-rf' instead of just '-r') to remove all the files without asking your permission first.

This command removes the old source code that you downloaded a few days ago, so that you can download an updated copy in its place.

---

### Post by BitaCookie on 2009-08-14
Hi!!!

lshw -C Network
```
user@user:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network                                        
       description: Ethernet interface             
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.             
       physical id: 0                                    
       bus info: pci@0000:02:00.0                        
       logical name: eth0                                
       version: 16                                       
       serial: 00:1d:72:f5:86:da                         
       width: 64 bits                                    
       clock: 33MHz                                      
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller                                                                        
       product: AR928X Wireless Network Adapter (PCI-Express)                                                 
       vendor: Atheros Communications Inc.                                                                    
       physical id: 0                                                                                         
       bus info: pci@0000:03:00.0                                                                             
       version: 01                                                                                            
       width: 64 bits                                                                                         
       clock: 33MHz                                                                                           
       capabilities: bus_master cap_list                                                                      
       configuration: latency=0                                                                               
  *-network DISABLED                                                                                          
       description: Ethernet interface                                                                        
       physical id: 3                                                                                         
       logical name: pan0                                                                                     
       serial: 26:df:50:f5:c4:83                                                                              
       capabilities: ethernet physical                                                                        
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```modinfo ath_pci
```
user@user:~$ modinfo ath_pci                                                                         
filename:       /lib/modules/2.6.28-11-generic/net/ath_pci.ko                                                 
license:        Dual BSD/GPL                                                                                  
version:        svn r4068                                                                                     
description:    Support for Atheros 802.11 wireless LAN cards.                                                
author:         Errno Consulting, Sam Leffler                                                                 
srcversion:     5179E97F52752C9A394F7FE                                                                       
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*                                                          
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*                                                          
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
user@user:~$

```

---

### Post by pytheas22 on 2009-08-14
Ah, I'm sorry all this has failed to yield any positive results.

I think the next thing to attempt is to use ndiswrapper, which will allow you to drive the card using Windows drivers.  In order to get ndiswrapper setup, therefore, you will need the driver that you use in Windows for this device.  If you could please post a link to where you downloaded the Windows driver from, or upload the driver here if it came on a CD, that would be helpful.  I'll then extract the necessary parts of the driver so you can install them into ndiswrapper.

---

### Post by BitaCookie on 2009-08-19
The computer had installed all drivers and everything, but I will try to find the driver for the card. 
---
Why with the other router (I mentioned in the first post), I could use wireless connection?

---

### Post by pytheas22 on 2009-08-19
> Why with the other router (I mentioned in the first post), I could use wireless connection?

I'm not sure exactly why, but the problem seems to be that the driver for your wireless card in Linux has trouble communicating properly with your new router.  Sometimes things like this happen, due to various settings on the new router being different from on the old one.

If we can find a Windows driver for your card, we can use ndiswrapper, which will be entirely different from the current driver and will hopefully work better with your new router.

---

### Post by BigCityCat on 2009-08-19
I'm not an expert, but I had a problem very similar to this. Let me make a suggestion. I had a problem with the ssb driver loading even after it was blacklisted. A friend helped me and we added

rmmod wl ssb
sleep 3
modprobe wl 

to

sudo kate /etc/rc.local

at the end before exit 0 

Not saying your set up is exactly like mine but maybe the solution is similar.

---

### Post by pytheas22 on 2009-08-20
BigCityCat: thanks for your suggestion.  The ssb problem actually only applies to Broadcom-based wireless cards, while BitaCookie's is Atheros, so your solution should not work here.  But thanks for pointing it out; it might help someone else who does have a Broadcom device.

---

### Post by BitaCookie on 2009-08-21
Atheros AR5B91 Wireless Network Adapter
Date of the driver: 04/11/2008
Version: 7.6.1.162 built by WinDDK

The driver of the adpater in my PC is in: C:\Windows\System32\drivers\athr.sys
I uploaded the driver here:  [http://rapidshare.com/files/269850595/athr.rar](http://rapidshare.com/files/269850595/athr.rar)

Tell me if that is what we need. Thank you pytheas22!

---

### Post by pytheas22 on 2009-08-21
That's half of what I need...there should also be a file associated with athr.sys whose extension ends in .inf.  ndiswrapper needs both the .sys and .inf files.  Do you see any .inf files anywhere?

---

### Post by BitaCookie on 2009-08-22
Hi pytheas,

I think I found it: [http://rapidshare.com/files/270089018/WinXP.rar](http://rapidshare.com/files/270089018/WinXP.rar)

It was here: C:\Program Files\IAR Systems\Embedded Workbench 4.0\430\drivers\TIUSBFET\WinXP

---

### Post by pytheas22 on 2009-08-22
Ah, that looks like a driver for something else.  I'm sorry.  I think the .inf file for your wireless card should be named something like netath.inf or athr.inf.  Do you see anything that looks like that?

You could also try uninstalling your wireless driver in Windows, then installing it again, and searching for .inf files by date to find the most recently added one.

Sorry--I know this is a hassle--but it's the only remaining option I can think of to try.

---

### Post by BitaCookie on 2009-08-22
Hi pytheas22,

I din't uninstall the driver of the card. I just searched and included all the files with netath.inf
[http://rapidshare.com/files/270268960/netath.inf.rar](http://rapidshare.com/files/270268960/netath.inf.rar)

There are some files that have the same name, but they are in different paths. Tell me if it is better to uninstall the driver, and I will do it.

---

### Post by pytheas22 on 2009-08-23
Thanks, finally found what we were looking for!  In that .rar archive, there's a file named "netathr (2).inf".  That looks like the one.  To get ndiswrapper working, you should save that file to your desktop, along with the athr.sys file that you uploaded a couple days ago.  Then run these commands:

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd ~/Desktop
sudo ndiswrapper -i "netathr (2).inf"
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot, and hopefully it will work.  If not, please post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by BitaCookie on 2009-08-23
It seems like the driver was not correct.

lshw -C Network
```
user@user:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network                                        
       description: Ethernet interface             
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.             
       physical id: 0                                    
       bus info: pci@0000:02:00.0                        
       logical name: eth0                                
       version: 16                                       
       serial: 00:1d:72:f5:86:da                         
       width: 64 bits                                    
       clock: 33MHz                                      
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller                                                                        
       product: AR928X Wireless Network Adapter (PCI-Express)                                                 
       vendor: Atheros Communications Inc.                                                                    
       physical id: 0                                                                                         
       bus info: pci@0000:03:00.0                                                                             
       version: 01                                                                                            
       width: 64 bits                                                                                         
       clock: 33MHz                                                                                           
       capabilities: bus_master cap_list                                                                      
       configuration: latency=0                                                                               
  *-network DISABLED                                                                                          
       description: Ethernet interface                                                                        
       physical id: 3                                                                                         
       logical name: pan0
       serial: ce:f4:27:e8:28:e6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```dmesg | grep -e ndis -e wlan
```
user@user:~$ dmesg | grep -e ndis -e wlan
[   12.222714] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.278198] usbcore: registered new interface driver ndiswrappe
```ndiswrapper -l
```
user@user:~$ ndiswrapper -|
>
>
>
> ndiswrapper -l
sh: Syntax error: "(" unexpected
netathr (2) : invalid driver!
user@user:~$ ndiswrapper -l
sh: Syntax error: "(" unexpected
netathr (2) : invalid driver!
user@user:~$
```

---

### Post by BitaCookie on 2009-08-23
I thought it was the name of the .inf file, so I did the same with the name changed, but it didn't work because maybe I should have uninstalled the first ndiswrapper:
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd ~/Desktop
sudo ndiswrapper -i "netathr.inf"
echo ndiswrapper | sudo tee -a /etc/modules
```

The output of the commands you told me:

lshw -C Network
```
user@user:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network                                        
       description: Ethernet interface             
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.             
       physical id: 0                                    
       bus info: pci@0000:02:00.0                        
       logical name: eth0                                
       version: 16                                       
       serial: 00:1d:72:f5:86:da                         
       width: 64 bits                                    
       clock: 33MHz                                      
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes                                                                                         
  *-network UNCLAIMED                                                                                         
       description: Network controller                                                                        
       product: AR928X Wireless Network Adapter (PCI-Express)                                                 
       vendor: Atheros Communications Inc.                                                                    
       physical id: 0                                                                                         
       bus info: pci@0000:03:00.0                                                                             
       version: 01                                                                                            
       width: 64 bits                                                                                         
       clock: 33MHz                                                                                           
       capabilities: bus_master cap_list                                                                      
       configuration: latency=0                                                                               
  *-network DISABLED                                                                                          
       description: Ethernet interface                                                                        
       physical id: 3                                                                                         
       logical name: pan0                                                                                     
       serial: 6a:4c:7b:fc:7b:2c                                                                              
       capabilities: ethernet physical                                                                        
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes  
```
dmesg | grep -e ndis -e wlan
```
user@user:~$ dmesg | grep -e ndis -e wlan
[   12.219315] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.333754] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[   12.333769] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'        
[   12.333776] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'           
[   12.333782] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'           
[   12.333844] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'                     
[   12.333855] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'                     
[   12.333863] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'       
[   12.333870] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'       
[   12.333878] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'                         
[   12.333885] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'                     
[   12.333896] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'             
[   12.333910] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.333918] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'         
[   12.333925] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'             
[   12.333947] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'      
[   12.333970] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'    
[   12.333984] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'      
[   12.333991] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'                   
[   12.333999] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'               
[   12.334013] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'             
[   12.334020] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'                   
[   12.334047] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'          
[   12.334055] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'        
[   12.334063] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'                  
[   12.334070] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'           
[   12.334080] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'           
[   12.334090] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'                
[   12.334098] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'              
[   12.334105] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'                
[   12.334113] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'            
[   12.334120] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'                
[   12.334130] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'                    
[   12.334138] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   12.334148] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   12.334156] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.334163] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   12.334171] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.334179] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.334187] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   12.334194] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   12.334197] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   12.334707] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   12.334770] usbcore: registered new interface driver ndiswrapper
```
ndiswrapper -l
```
user@user:~$ ndiswrapper -l
netathr : driver installed
        device (168C:002A) present (alternate driver: ath9k)
sh: Syntax error: "(" unexpected
netathr (2) : invalid driver!
user@user:~$
 
```

---

### Post by pytheas22 on 2009-08-24
This looks bad...it looks like ndiswrapper is not going to work, and I'm not sure what else to try at this point...

It's late now and I don't have time to go through the thread again and think about anything else we might try, but I'll do that tomorrow.  If I don't respond within twenty-four hours, please bump the thread to remind me.

---

### Post by pytheas22 on 2009-08-25
I finally had time to reread the thread and think through this again.  Since everything we've tried with regards to changing the wireless drivers  in Ubuntu has been fruitless, and since you say this same system was able to connect before you moved, I think it would be worth investigating the settings of your router, and seeing changing those would help.

I know you've already tried disabling security, but have you tried switching to a different channel or a different mode (e.g., 802.11g vs. 802.11n)?

Also, if you're unable to see any wireless networks at all, try running these commands:
```

sudo rmmod ath9k
sudo rmmod ndiswrapper
sudo modprobe ath9k
```

and this should solve the problem.

It could also be worth the trouble to create a live CD of [Ubuntu 9.10 alpha 4]("http://cdimage.ubuntu.com/releases/karmic/alpha-4/") and see if the wireless works there...the problem may be fixed in this latest version.

---

