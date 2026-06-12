---
title: "Getting Getnet GN621-U to work.  Reinstall my faith in Ubuntu!"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by elsmandino on 2010-02-08
Warning - absolute beginner here.  Close to throwing in the towell and returning to windows but striving to try and get to grips with Linux.

Hi I have set up Ubuntu 9.10 and have bought a Getnet 300N GN-621U on the basis that it is Linux compliant.

The problem is everytime I plug the adaptor in, the network manager keeps saying no connection, thus leading me to believe that the adaptor is not ready to go and I shall have to install some bits from the CD that came with it.

I have opened the "Linux Driver" folder on the CD and opened the readme file to be presented with this:

Sorry - very long!

[B]Release Date: 2009-0825, ver 0003 
RTL8192SU Linux driver
   --This driver supports RealTek rtl8192SU USB Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04, etc.
     2.4 kernel:
     Redhat 9.0/9.1

===============================================================================
                Component 
===============================================================================
The driver is composed of several parts:
    1. Firmare to make nic work
           1.1 firmare/RTL8192SU

    2. Module source code
       2.1 ieee80211 
       2.2 HAL/rtl8192u
       2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
           internet also, but it is suggested to use default package contained
           in the distribution because there should less compilation issue.)
    
    3. Script to build the modules
       3.1 Makefile 

    4. Script to load/unload modules
       4.1 wlan0up 
       4.2 wlan0down 

    5. Script and configuration for DHCP
        5.1 wlan0dhcp
       5.2 ifcfg-wlan0

    6. Example of supplicant configuration file:
       6.1 wpa1.conf

    7. Script to run wpa_supplicant
       7.1 runwpa

===============================================================================
                Installation 
===============================================================================
<<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
    1. Build up the drivers from the source code
      make

    2. Install the driver to the kernel
          make install
          reboot

    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
      ifconfig wlan0 up 
      Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
     1. Build up the drivers from the source code
      make
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
            cp -rf firmware/RTL8192SU /lib/firmware
          or
            cp -rf firmware/RTL8192SU /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware

     3. Load driver module to kernel and start up nic.
      ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..
      Note: If you see the message of "unkown symbol" during ./wlan0up, it
        is suggested to build driver by <<Method 1>>.

===============================================================================
                Set wireless lan MIBs 
===============================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic
        iwlist wlan0 [parameters]
where
        parameter explaination          [parameters]    
        -----------------------         -------------   
        Show available chan and freq    freq / channel  
        Show and Scan BSS and IBSS     scan[ning]          
        Show supported bit-rate         rate / bit[rate]        

For example:
    iwlist wlan0 channel
    iwlist wlan0 scan
    iwlist wlan0 rate

Driver also supports "iwconfig", manipulate driver private ioctls, to set
MIBs.

    iwconfig wlan0 [parameters] [val]
where
    parameter explaination      [parameters]        [val] constraints
        -----------------------     -------------        ------------------
        Connect to AP by address    ap                  [mac_addr]
        Set the essid, join (I)BSS  essid                 [essid]
        Set operation mode          mode                {Managed|Ad-hoc}
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

For example:
    iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
    iwconfig wlan0 essid "ap_name"
    iwconfig wlan0 mode Ad-hoc
    iwconfig wlan0 essid "name" mode Ad-hoc
    iwconfig wlan0 key 0123456789 [2] open
    iwconfig wlan0 key off
    iwconfig wlan0 key restricted [3] 0123456789
        Note: Better to set these MIBS without GUI such as NetworkManager and be sure that our
              nic has been brought up before these settings. WEP key index 2-4 is not supportted by
              NetworkManager.

===============================================================================
                Getting IP address
===============================================================================
After start up the nic, the network needs to obtain an IP address before
transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"
command, or using DHCP.

If using DHCP, setting steps is as below:
    (1)connect to an AP via "iwconfig" settings
        iwconfig wlan0 essid [name]    or
        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

    (2)run the script which run the dhclient
        ./wlan0dhcp
           or 
        dhcpcd wlan0
                  (Some network admins require that you use the
                  hostname and domainname provided by the DHCP server.
                  In that case, use 
        dhcpcd -HD wlan0)
        

===============================================================================
            WPAPSK/WPA2PSK 
===============================================================================
    Wpa_supplicant helps to secure wireless connection with the protection of 
WPAPSK/WPA2PSK mechanism. 

    If the version of Wireless Extension in your system is equal or larger than 18, 
WEXT driver interface is recommended. Otherwise, IPW driver interface is advised.  
    Note: Wireless Extension is defined us "#define WIRELESS_EXT" in Kernel
    Note: To check the version of wireless extension, please type "iwconfig -v"


     If IPW driver interface is used, it us suggested to follow the steps from 1 to 6. 
If wpa_supplicant has been installed in your system, only steps 5 and 6 are required 
to be executed for WEXT driver interface.

    To see detailed description for driver interface and wpa_supplicant, please type
"man wpa_supplicant".  
    
    (1)Download latetest source code for wpa supplicant or use wpa_supplicant-0.5.10 
       attached in this package. (It is suggested to use default package contained
           in the distribution because there should less compilation issue.)

       Unpack source code of WPA supplicant:

      tar -zxvf wpa_supplicant-0.5.10.tar.gz (e.g.) 
      cd wpa_supplicant-0.5.10
    
    (2)Create .config file:
      cp defconfig .config
    
    (3)Edit .config file, uncomment the following line if ipw driver interface 
       will be applied:
      #CONFIG_DRIVER_IPW=y.
        
    (4)Build and install WPA supplicant:
      make
      cp wpa_cli wpa_supplicant /usr/local/bin    
    
    NOTE:
     1. If make error for lack of <include/md5.h>, install the openssl lib(two ways):
      (1) Install the openssl lib from corresponding installation disc:
          Fedora Core 2/3/4/5(openssl-0.9.71x-xx), 
          Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
          Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), 
          Gentoo(dev-libs/openssl), etc.
      (2) Download the openssl open source package from [www.openssl.org]("http://www.openssl.org"), build and 
          install it.
     2. If make errors happen in RedHat(and also Fedora Core) for kssl.h,
please add lines below into Makefile
          CPPFLAGS+=-I/usr/kerboros/include
     
    (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
      For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".

       Example 1: Configuration for WPA-PWK
      network={
            ssid="BufAG54_Ch6"
            #scan_ssid=1 //see note 3
            proto=WPA
            key_mgmt=WPA-PSK
            pairwise=CCMP TKIP
            group=CCMP TKIP WEP104 WEP40
            psk="87654321"
            priority=2
          }
    
        Example 2: Configuration for LEAP
        network={
            ssid="BufAG54_Ch6"
            key_mgmt=IEEE8021X
            group=WEP40 WEP104
            eap=LEAP
            identity="user1"
            password="1111"
          }
        Example 3: Linking to hidden ssid given AP's security policy exactly.(see note 3 below)
            ap_scan=2
        network={
        ssid="Hidden_ssid"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        psk="12345678"
          }
        
        Example 4: Linking to ad-hoc (see note 4 below)
        ap_scan=2
        network={
        ssid="Ad-hoc"
                mode=1
        proto=WPA
        key_mgmt=WPA-NONE
        pairwise=NONE
        group=TKIP
        psk="12345678"
        }
    Note: 1. proto=WPA for WPA, proto=RSN for WPA2. 
          2. If user needs to connect an AP with WPA or WPA2 mixed mode, it is suggested 
         to set the cipher of pairwise and group to both CCMP and TKIP unless you 
         know exactly which cipher type AP is configured.
          3. When connecting to hidden ssid, explicit security policy should be given with 
         ap_scan=2 being setting.
          4. It is suggested setting ap_scan to 2 and mode to 1 when linking to or creating an ad-hoc. Group and pairwise
         cipher type should also be explicit, always with group setting to TKIP or CCMP and pairwise setting
         to NONE. Lower version wpa_supplicant may not allow setting group to CCMP with pairwise setting to NONE.
         So if any problem, you may try to set both group and pairwise to CCMP, leaving other setting unchanged, when
             connecting to an CCMP-encrypted ad-hoc.
          5. More config setting option, please refer to wpa_supplicant.conf in wpa_supplicant.tar.gz that we provide.

    (6)Execute WPA supplicant (Assume rtl8192E and related modules had been
           loaded):
           ./runwpa

           Note: The script runwpa will check Wireless Extension version automatically.
                 If the version of Wireless Extension is equal or larger than 18, the
                 option of "-D wext" is selected. If the version of Wireless extension
                 is less than 18, the option of "-D ipw" is selected.
[/B]
As I said, despite having had a mess around with a few distros before, I never really got to grips with Linux, but would really like to give Ubuntu a try - like everything, it is bound to become better once I start undertstanding some of the basics.  I really have no idea what I am doing and would appreciate a dribbling idiot's walkthrough as to what to do next.

Thanks v much.

A

---

### Post by chili555 on 2010-02-08
Well, compiling from source would be a lot of fun for both of us, but maybe there is another way. Please open Applications -> Accessories -> Terminal and do:```
modinfo 8192s_usb
```If it is on your system, you should see lots of confusing output including this little gem:> $ modinfo r8192s_usb 
filename:       /lib/modules/2.6.31-19-generic/kernel/drivers/staging/[COLOR="Red"]rtl8192su[/COLOR]/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cardsYou might get lucky and try to load the driver with:```
sudo modprobe r8192s_usb
```Did it create a wireless interface? Check with:```
iwconfig
```If not, please post:```
lsusb
```Thanks.

---

### Post by elsmandino on 2010-02-08
Thanks very much for your reply.  The following happend:

[I]"Well, compiling from source would be a lot of fun for both of us, but maybe there is another way. Please open Applications -> Accessories -> Terminal and do:
Code:

modinfo 8192s_usb"[/I]

[B]ERROR: modinfo: could not find module 8192s_usb
alex@alex-desktop:~$ 
[/B]
[I]"You might get lucky and try to load the driver with:
Code:

sudo modprobe r8192s_usb"[/I]

**Nothing happened**

[I]"Did it create a wireless interface? Check with:
Code:

iwconfig[/I]"

[B]alex@alex-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

[I]"If not, please post:
Code:

lsusb"[/I]

[B]alex@alex-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/B]

Unfortunately, no connection to my router.

A

---

### Post by chili555 on 2010-02-08
> wlan0 802.11b/g Mode:Managed Access Point: Not-Associated You *do* have a wireless interface! If you find the Network Manager icon at the top right of your desktop and click it, can you see your network, select it and connect?

---

### Post by Highlanddark on 2010-04-22
> **elsmandino said:**
> Warning - absolute beginner here.  Close to throwing in the towell and returning to windows but striving to try and get to grips with Linux.

Hi I have set up Ubuntu 9.10 and have bought a Getnet 300N GN-621U on the basis that it is Linux compliant.

The problem is everytime I plug the adaptor in, the network manager keeps saying no connection, thus leading me to believe that the adaptor is not ready to go and I shall have to install some bits from the CD that came with it.

I have opened the "Linux Driver" folder on the CD and opened the readme file to be presented with this:

Sorry - very long!

[B]Release Date: 2009-0825, ver 0003 
RTL8192SU Linux driver
   --This driver supports RealTek rtl8192SU USB Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04, etc.
     2.4 kernel:
     Redhat 9.0/9.1

===============================================================================
                Component 
===============================================================================
The driver is composed of several parts:
    1. Firmare to make nic work
           1.1 firmare/RTL8192SU

    2. Module source code
       2.1 ieee80211 
       2.2 HAL/rtl8192u
       2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
           internet also, but it is suggested to use default package contained
           in the distribution because there should less compilation issue.)
    
    3. Script to build the modules
       3.1 Makefile 

    4. Script to load/unload modules
       4.1 wlan0up 
       4.2 wlan0down 

    5. Script and configuration for DHCP
        5.1 wlan0dhcp
       5.2 ifcfg-wlan0

    6. Example of supplicant configuration file:
       6.1 wpa1.conf

    7. Script to run wpa_supplicant
       7.1 runwpa

===============================================================================
                Installation 
===============================================================================
<<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
    1. Build up the drivers from the source code
      make

    2. Install the driver to the kernel
          make install
          reboot

    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
      ifconfig wlan0 up 
      Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
     1. Build up the drivers from the source code
      make
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
            cp -rf firmware/RTL8192SU /lib/firmware
          or
            cp -rf firmware/RTL8192SU /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware

     3. Load driver module to kernel and start up nic.
      ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..
      Note: If you see the message of "unkown symbol" during ./wlan0up, it
        is suggested to build driver by <<Method 1>>.

===============================================================================
                Set wireless lan MIBs 
===============================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic
        iwlist wlan0 [parameters]
where
        parameter explaination          [parameters]    
        -----------------------         -------------   
        Show available chan and freq    freq / channel  
        Show and Scan BSS and IBSS     scan[ning]          
        Show supported bit-rate         rate / bit[rate]        

For example:
    iwlist wlan0 channel
    iwlist wlan0 scan
    iwlist wlan0 rate

Driver also supports "iwconfig", manipulate driver private ioctls, to set
MIBs.

    iwconfig wlan0 [parameters] [val]
where
    parameter explaination      [parameters]        [val] constraints
        -----------------------     -------------        ------------------
        Connect to AP by address    ap                  [mac_addr]
        Set the essid, join (I)BSS  essid                 [essid]
        Set operation mode          mode                {Managed|Ad-hoc}
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

For example:
    iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
    iwconfig wlan0 essid "ap_name"
    iwconfig wlan0 mode Ad-hoc
    iwconfig wlan0 essid "name" mode Ad-hoc
    iwconfig wlan0 key 0123456789 [2] open
    iwconfig wlan0 key off
    iwconfig wlan0 key restricted [3] 0123456789
        Note: Better to set these MIBS without GUI such as NetworkManager and be sure that our
              nic has been brought up before these settings. WEP key index 2-4 is not supportted by
              NetworkManager.

===============================================================================
                Getting IP address
===============================================================================
After start up the nic, the network needs to obtain an IP address before
transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"
command, or using DHCP.

If using DHCP, setting steps is as below:
    (1)connect to an AP via "iwconfig" settings
        iwconfig wlan0 essid [name]    or
        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

    (2)run the script which run the dhclient
        ./wlan0dhcp
           or 
        dhcpcd wlan0
                  (Some network admins require that you use the
                  hostname and domainname provided by the DHCP server.
                  In that case, use 
        dhcpcd -HD wlan0)
        

===============================================================================
            WPAPSK/WPA2PSK 
===============================================================================
    Wpa_supplicant helps to secure wireless connection with the protection of 
WPAPSK/WPA2PSK mechanism. 

    If the version of Wireless Extension in your system is equal or larger than 18, 
WEXT driver interface is recommended. Otherwise, IPW driver interface is advised.  
    Note: Wireless Extension is defined us "#define WIRELESS_EXT" in Kernel
    Note: To check the version of wireless extension, please type "iwconfig -v"


     If IPW driver interface is used, it us suggested to follow the steps from 1 to 6. 
If wpa_supplicant has been installed in your system, only steps 5 and 6 are required 
to be executed for WEXT driver interface.

    To see detailed description for driver interface and wpa_supplicant, please type
"man wpa_supplicant".  
    
    (1)Download latetest source code for wpa supplicant or use wpa_supplicant-0.5.10 
       attached in this package. (It is suggested to use default package contained
           in the distribution because there should less compilation issue.)

       Unpack source code of WPA supplicant:

      tar -zxvf wpa_supplicant-0.5.10.tar.gz (e.g.) 
      cd wpa_supplicant-0.5.10
    
    (2)Create .config file:
      cp defconfig .config
    
    (3)Edit .config file, uncomment the following line if ipw driver interface 
       will be applied:
      #CONFIG_DRIVER_IPW=y.
        
    (4)Build and install WPA supplicant:
      make
      cp wpa_cli wpa_supplicant /usr/local/bin    
    
    NOTE:
     1. If make error for lack of <include/md5.h>, install the openssl lib(two ways):
      (1) Install the openssl lib from corresponding installation disc:
          Fedora Core 2/3/4/5(openssl-0.9.71x-xx), 
          Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
          Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), 
          Gentoo(dev-libs/openssl), etc.
      (2) Download the openssl open source package from [www.openssl.org]("http://www.openssl.org"), build and 
          install it.
     2. If make errors happen in RedHat(and also Fedora Core) for kssl.h,
please add lines below into Makefile
          CPPFLAGS+=-I/usr/kerboros/include
     
    (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
      For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".

       Example 1: Configuration for WPA-PWK
      network={
            ssid="BufAG54_Ch6"
            #scan_ssid=1 //see note 3
            proto=WPA
            key_mgmt=WPA-PSK
            pairwise=CCMP TKIP
            group=CCMP TKIP WEP104 WEP40
            psk="87654321"
            priority=2
          }
    
        Example 2: Configuration for LEAP
        network={
            ssid="BufAG54_Ch6"
            key_mgmt=IEEE8021X
            group=WEP40 WEP104
            eap=LEAP
            identity="user1"
            password="1111"
          }
        Example 3: Linking to hidden ssid given AP's security policy exactly.(see note 3 below)
            ap_scan=2
        network={
        ssid="Hidden_ssid"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        psk="12345678"
          }
        
        Example 4: Linking to ad-hoc (see note 4 below)
        ap_scan=2
        network={
        ssid="Ad-hoc"
                mode=1
        proto=WPA
        key_mgmt=WPA-NONE
        pairwise=NONE
        group=TKIP
        psk="12345678"
        }
    Note: 1. proto=WPA for WPA, proto=RSN for WPA2. 
          2. If user needs to connect an AP with WPA or WPA2 mixed mode, it is suggested 
         to set the cipher of pairwise and group to both CCMP and TKIP unless you 
         know exactly which cipher type AP is configured.
          3. When connecting to hidden ssid, explicit security policy should be given with 
         ap_scan=2 being setting.
          4. It is suggested setting ap_scan to 2 and mode to 1 when linking to or creating an ad-hoc. Group and pairwise
         cipher type should also be explicit, always with group setting to TKIP or CCMP and pairwise setting
         to NONE. Lower version wpa_supplicant may not allow setting group to CCMP with pairwise setting to NONE.
         So if any problem, you may try to set both group and pairwise to CCMP, leaving other setting unchanged, when
             connecting to an CCMP-encrypted ad-hoc.
          5. More config setting option, please refer to wpa_supplicant.conf in wpa_supplicant.tar.gz that we provide.

    (6)Execute WPA supplicant (Assume rtl8192E and related modules had been
           loaded):
           ./runwpa

           Note: The script runwpa will check Wireless Extension version automatically.
                 If the version of Wireless Extension is equal or larger than 18, the
                 option of "-D wext" is selected. If the version of Wireless extension
                 is less than 18, the option of "-D ipw" is selected.
[/B]
As I said, despite having had a mess around with a few distros before, I never really got to grips with Linux, but would really like to give Ubuntu a try - like everything, it is bound to become better once I start undertstanding some of the basics.  I really have no idea what I am doing and would appreciate a dribbling idiot's walkthrough as to what to do next.

Thanks v much.

A

I have similar problem, same new gn621u device, same driver disc version, but just upgraded to Lucid Lynx.

i have been following this thread

george@george-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

george@george-desktop:~$ 

george@george-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05e3:0760 Genesys Logic, Inc. USB 2.0 Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
george@george-desktop:~$

My network connections manager states Wireless Networks ¨Device not ready¨

checked user privilages.

Any guidance appreciated, and sorry for big post and being a noob.

---

### Post by chili555 on 2010-04-22
> wlan0 802.11b/g Mode:Managed Access Point: Not-Associated
Bit Rate:0 kb/s Please try:```
sudo iwconfig wlan0 rate 54M
iwconfig
```Now is the rate 0 kb/s? Is the 'Device not ready' message still there? How about this:```
sudo iwlist wlan0 scan
dmesg | grep wlan
```Thanks.

---

### Post by Highlanddark on 2010-04-22
> **chili555 said:**
> Please try:```
sudo iwconfig wlan0 rate 54M
iwconfig
```Now is the rate 0 kb/s? Is the 'Device not ready' message still there? How about this:```
sudo iwlist wlan0 scan
dmesg | grep wlan
```Thanks.


george@george-desktop:~$ sudo iwconfig wlan0 rate 54M
george@george-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

george@george-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

george@george-desktop:~$ dmesg | grep wlan
[ 7374.690025] rtl819xU:=============>wlan driver to be removed
[ 7374.700428] rtl819xU:wlan driver removed
george@george-desktop:~$

---

### Post by Highlanddark on 2010-04-22
*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:1f:a3:9a:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

---

### Post by chili555 on 2010-04-22
> rtl819xU:=============>wlan driver to be removed
rtl819xU:wlan driver removedThat's interesting. Let's see if there is more to learn:```
dmesg | grep rtl8
```Thanks.

PS - There is no need to flood the forum with information about your CDROM and video card, etc. This would be sufficient:> *-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:1f:1f:a3:9a:2e
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=802.11b/g


---

### Post by Highlanddark on 2010-04-22
Very Sorry.

george@george-desktop:~$ dmesg | grep rtl8
[   27.815336] usbcore: registered new interface driver rtl819xU
[   27.884280] rtl819xU: --->FirmwareDownload92S()
[   27.884286] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   27.980207] rtl819xU:request firmware fail!
[   27.981124] rtl819xU:Firmware Download Fail!!a
[   28.006796] rtl819xU: --->FirmwareDownload92S()
[   28.006804] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   28.012688] rtl819xU:request firmware fail!
[   28.013081] rtl819xU:Firmware Download Fail!!a
[   28.013085] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   28.041526] rtl819xU: --->FirmwareDownload92S()
[   28.041535] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   28.052148] rtl819xU:request firmware fail!
[   28.052564] rtl819xU:Firmware Download Fail!!a
[   28.061523] rtl819xU: --->FirmwareDownload92S()
[   28.061533] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   28.069058] rtl819xU:request firmware fail!
[   28.069457] rtl819xU:Firmware Download Fail!!a
[   28.069462] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 7374.690025] rtl819xU:=============>wlan driver to be removed
[ 7374.700428] rtl819xU:wlan driver removed
[ 7391.331474] rtl819xU: --->FirmwareDownload92S()
[ 7391.331483] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 7391.377269] rtl819xU:request firmware fail!
[ 7391.377735] rtl819xU:Firmware Download Fail!!a
[ 7391.387849] rtl819xU: --->FirmwareDownload92S()
[ 7391.387857] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 7391.389874] rtl819xU:request firmware fail!
[ 7391.390751] rtl819xU:Firmware Download Fail!!a
[ 7391.390758] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 7391.442845] rtl819xU: --->FirmwareDownload92S()
[ 7391.442857] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 7391.459387] rtl819xU:request firmware fail!
[ 7391.459697] rtl819xU:Firmware Download Fail!!a
[ 7391.470224] rtl819xU: --->FirmwareDownload92S()
[ 7391.470235] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 7391.482047] rtl819xU:request firmware fail!
[ 7391.482365] rtl819xU:Firmware Download Fail!!a
[ 7391.482370] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
george@george-desktop:~$

---

### Post by chili555 on 2010-04-22
Ah, ha!> firmware: requesting RTL8192SU/rtl8192sfw.binYou may have the firmware, but in the wrong location. Let's check:```
ls /lib/firmware/`uname -r` | grep RTL
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

On my system, there is only a file called RTL8192[COLOR="Red"]SE[/COLOR]. The driver wants the firmware in [COLOR="Red"]SU[/COLOR]. Let's cheat a bit.```
sudo mkdir /lib/firmware/`uname -r`/RTL8192SU
sudo cp /lib/firmware/`uname -r`/RTL8192SE/rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU
```Now reboot and see if it's working. If not, let's see, again:```
dmesg | grep rtl8
```

---

### Post by Highlanddark on 2010-04-23
my Firmware folder is in different directory, so changed to
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU

not sure if that´s where its meant to be.

Anyway I rebooted and... result!

george@george-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  li  ESSID:"BTHomeHub2-Q7C5"  
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:24:2C:9F:54:FB   
          Bit Rate=130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-55 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Its working :-)the Lucid Lynx Droopy dongle is cured haha

Thank you so much chili555 you have made me happy again.

---

### Post by chili555 on 2010-04-23
Great work. I'm glad it's working. Have fun!

---

