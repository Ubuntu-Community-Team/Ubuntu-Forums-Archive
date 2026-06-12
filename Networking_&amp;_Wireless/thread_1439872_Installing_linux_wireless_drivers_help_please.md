---
title: "Installing linux wireless drivers help please"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by Satchmo2 on 2010-03-26
So I posted this in the new os thread but no help yet. I'm still having the same problem with my wireless internet. I don't think it recognizes my adapter, I'm not even sure if it sees that it's plugged in, but I know the adapter works because I use it in windows.

I dled the linux drivers but I have no clue how to use them, can someone guide me? Here is the readme:

Release Date: 2008-10-31, ver 0.06
RTL8192U Linux driver version 0.06
   --This driver supports RealTek rtl8192U USB Wireless LAN NIC
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
           1.1 firmare/RTL8192U

	2. Module source code
	   2.1 ieee80211 
	   2.2 HAL/rtl8192u
	   2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
	       internet also, but it is suggested to use default package contained
	       in the distribution because there should be less compilation issue.)
	
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
            cp -rf firmware/RTL8192U /lib/firmware
          or
            cp -rf firmware/RTL8192U /lib/firmware/(KERNEL_VERSION)
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
        parameter explaination      	[parameters]    
        -----------------------     	-------------   
        Show available chan and freq	freq / channel  
        Show and Scan BSS and IBSS 	scan[ning]          
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
        Connect to AP by address    ap              	[mac_addr]
        Set the essid, join (I)BSS  essid             	[essid]
        Set operation mode          mode                {Managed|Ad-hoc}
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

For example:
	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
	iwconfig wlan0 essid "ap_name"
	iwconfig wlan0 mode Ad-hoc
	iwconfig wlan0 mode essid "name" mode Ad-hoc
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
		iwconfig wlan0 essid [name]	or
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


 	If IPW driver interface is used, it is suggested to follow the steps from 1 to 6. 
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
	
	If make error for lack of <include/md5.h>, install the openssl lib(two ways):
	 1. Install the openssl lib from corresponding installation disc:
	      Fedora Core 2/3/4/5(openssl-0.9.71x-xx), 
	      Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	      Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), 
	      Gentoo(dev-libs/openssl), etc.
	   2. Download the openssl open source package from [www.openssl.org](www.openssl.org), build and 
	      install it.
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	  For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".

	   Example 1: Configuration for WPA-PWK
	  network={
			ssid="BufAG54_Ch6"
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
		 ap_scan=2 being setted.
	      4. It is suggested setting ap_scan to 2 and mode to 1 when linking to or creating an ad-hoc. Group and pairwise
		 cipher type should also be explicit, always with group setted to TKIP or CCMP and pairwise setted
		 to NONE. Lower version wpa_supplicant may not allow setting group to CCMP with pairwise setting to NONE.
		 So if any problem, you may try to set both group and pairwise to CCMP, leaving other setting unchanged, when
	         connecting to an CCMP-encrypted ad-hoc.
	      5. More config setting option, please refer to wpa_supplicant.conf in wpa_supplicant.tar.gz that we provide.

	(6)Execute WPA supplicant (Assume rtl8192U and related modules had been
           loaded):
	  wpa_supplicant -D wext -c wpa1.conf -i wlan0  (recommended)
	  wpa_supplicant -D ipw -c wpa1.conf -i wlan0 

	   Note: At first, user sholud check Wireless Extension by typing "iwconfig -v"  
	         on the comment line. If the version of Wireless Extension is equal or 
		 larger than 18, the option of "-D wext" is suggested. If the version 
		 of Wireless extension is less than 18, the option of "-D ipw" is 
		 suggested.

I have no experience with the terminal so please explain things throughly.

---

### Post by banksj17 on 2010-03-26
1. place your driver folder into your home folder
2. go into terminal and type 
```
 cd /home/*username*/*driver folder name*
```3. Type
```
make
```4. Type
```
make install
```5. Type
```
reboot
```

---

### Post by Satchmo2 on 2010-03-26
No luck, it's just throwing these errors at me.

adam@adam-desktop:~$ cd /home/adam/rtl8192u_linux_2.6.0006.1031.2008
adam@adam-desktop:~/rtl8192u_linux_2.6.0006.1031.2008$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o
/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rsl’:
/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

---

### Post by chili555 on 2010-03-26
Please do:```
sudo apt-get install build-essential
make
sudo make install

```Reboot.

---

### Post by Satchmo2 on 2010-03-26
I'm about to reboot but I don't think it worked, the apt-get seemed fine but make and sudo make install gave me these errors.

adam@adam-desktop:~/rtl8192u_linux_2.6.0006.1031.2008$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o
/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c: In function &#8216;alloc_ieee80211_rsl&#8217;:
/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c:121: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
make[2]: *** [/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2
adam@adam-desktop:~/rtl8192u_linux_2.6.0006.1031.2008$ sudo make install
make[1]: Entering directory `/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'
make -C /lib/modules/2.6.31-20-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/adam/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'
make: *** [install] Error 2

EDT: still doesn't work after reboot.

---

### Post by chili555 on 2010-03-26
Man! I just noticed this is a 2008 version of the driver. In Linux years this is too old. Let's scare up a newer one. The exact driver you need is not evident. Please post:```
lsusb
```Thanks.

---

### Post by Satchmo2 on 2010-03-26
adam@adam-desktop:~$ lsusb
Bus 001 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Not sure if it recognizes my adapter, but I know the adapter works because I use it in windows every day. It's a d-link dwa-130 revision C. I think I have the most recent linux drivers, I grabbed them off the website, but maybe there is some homebrew drivers I can use?

---

### Post by chili555 on 2010-03-26
I believe it works with the driver r8192s_usb which may be on your system already. Please do:```
sudo modprobe r8192s_usb
iwconfig
```Do you have a wireless interface?

---

### Post by Satchmo2 on 2010-03-26
I have pretty much stock ubuntu, haven't downloaded any but I thought it came with one? I did try ndiswrapper with my card but it didn't work.

adam@adam-desktop:~$ sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipw3945, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
adam@adam-desktop:~$ ^C
adam@adam-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Still doesn't work, thanks for being so patient with me lol.

---

### Post by chili555 on 2010-03-26
Well, you do have a wireless interface, so we are getting a bit closer. 

You have been a busy little Ubuntuan, haven't you? Ndiswrapper, an Intel 3945 and, I assume, a few others, if you are up to wlan3. Still no wireless? Do you have a deeper issue that we need to solve first, or do you (like me) just love messing with wireless cards?

The 3945 ought to work like a champ. I am using one right now.

---

### Post by Satchmo2 on 2010-03-26
Hmm, I did just run from 8.04 to 9.10 , I actually hadn't used ubuntu in quite a while, for this very reason and I figured I'd try again to see if the updates would fix it, no luck, but I like karmic so much I'm determined to try. I'm not sure what you mean about the intel cards, I've only ever used two usb cards in this ubuntu, the dwa-130 rev c and wua2340(still have, doesn't work either), both d-link. I'm kind of a noob at this stuff so some terminology you use I won't understand(whats wlan3 mean?).

---

### Post by chili555 on 2010-03-26
> WARNING: All config files need .conf: /etc/modprobe.d/[COLOR="Blue"]ndiswrapper[/COLOR], it will be ignored in a future release.At one time, someone installed ndiswrapper in an attempt to get a Windows driver to drive a wireless card.> WARNING: All config files need .conf: /etc/modprobe.d/[COLOR="Blue"]ipw3945[/COLOR], it will be ignored in a future release.At some time, someone wrote a configuration file for an Intel 3945 card. It is a miniPCI card, not a USB card. Is it in your machine? It ought to be a snap to get going. Find out with:```
sudo lshw -C network
```> whats wlan3 mean?Wireless cards usually, not always, use an interface of wlan0. If a second card is inserted with a different MAC address, it will use wlan1. Now settings are retained for both. A third card will use wlan2 and so on. You are now up to wlan3 indicating that no less than four cards have been used at some time.

Now maybe the cards have been sold or lost, but it is likely that the Intel 3945 is still in there. They are usually very easy to get going. 

What can you tell me?

By the way, if the internal card is disabled in the computer's BIOS, then it will be hard to get the D-link going. The same may apply if the wireless switch is off.

---

### Post by Satchmo2 on 2010-03-26
adam@adam-desktop:~$ sudo lshw -C network
[sudo] password for adam: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:c9:59:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.101 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:ee00(size=256) memory:fdeff000-fdeff0ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: 00:e0:4c:81:92:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g


I'm the one who tried ndiswrapper, I think I tried both 32 and 64 bit drivers, none worked(they're all deleted now).

---

### Post by chili555 on 2010-03-26
Let's try to work out why it's disabled. Please post:```
dmesg | grep -e 819 -e firmware
```Thanks.

---

### Post by Satchmo2 on 2010-03-26
adam@adam-desktop:~$ dmesg | grep -e 819 -e firmware
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.188196] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[ 2315.432888] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 2315.443598] Linux kernel driver for RTL8192 based WLAN cards
[ 2315.457056] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 2315.458307] usbcore: registered new interface driver rtl819xU
[ 2315.504435] rtl819xU: --->FirmwareDownload92S()
[ 2315.504444] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.514359] rtl819xU:request firmware fail!
[ 2315.514844] rtl819xU:Firmware Download Fail!!4544
[ 2315.527689] rtl819xU: --->FirmwareDownload92S()
[ 2315.527699] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.535916] rtl819xU:request firmware fail!
[ 2315.536304] rtl819xU:Firmware Download Fail!!4544
[ 2315.536310] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2315.562321] rtl819xU: --->FirmwareDownload92S()
[ 2315.562332] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.566940] rtl819xU:request firmware fail!
[ 2315.567422] rtl819xU:Firmware Download Fail!!4544
[ 2315.582824] rtl819xU: --->FirmwareDownload92S()
[ 2315.582835] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.588929] rtl819xU:request firmware fail!
[ 2315.589257] rtl819xU:Firmware Download Fail!!4544
[ 2315.589264] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3004.176115] rtl819xU:=============>wlan driver to be removed
[ 3004.186504] rtl819xU:wlan driver removed
[ 3045.430714] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 3045.464092] rtl819xU: --->FirmwareDownload92S()
[ 3045.464102] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.469355] rtl819xU:request firmware fail!
[ 3045.469692] rtl819xU:Firmware Download Fail!!4544
[ 3045.486221] rtl819xU: --->FirmwareDownload92S()
[ 3045.486231] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.490781] rtl819xU:request firmware fail!
[ 3045.491258] rtl819xU:Firmware Download Fail!!4544
[ 3045.491264] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3045.511976] rtl819xU: --->FirmwareDownload92S()
[ 3045.511987] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.516490] rtl819xU:request firmware fail!
[ 3045.516983] rtl819xU:Firmware Download Fail!!4544
[ 3045.531729] rtl819xU: --->FirmwareDownload92S()
[ 3045.531739] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.536163] rtl819xU:request firmware fail!
[ 3045.536646] rtl819xU:Firmware Download Fail!!4544
[ 3045.536653] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3101.522198] rtl819xU: --->FirmwareDownload92S()
[ 3101.522210] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3101.527156] rtl819xU:request firmware fail!
[ 3101.527632] rtl819xU:Firmware Download Fail!!4544
[ 3101.543695] rtl819xU: --->FirmwareDownload92S()
[ 3101.543707] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3101.548201] rtl819xU:request firmware fail!
[ 3101.550215] rtl819xU:Firmware Download Fail!!4544
[ 3101.550224] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 4757.169819] integrated sync not supported
[ 4819.044913] integrated sync not supported
[ 4819.378056] integrated sync not supported
[ 4819.498385] integrated sync not supported
[ 4819.616906] integrated sync not supported
[ 4819.733398] integrated sync not supported
[ 4819.841403] integrated sync not supported
[ 4819.957397] integrated sync not supported

It looks like it says the wlan driver is removed? I'm not sure though this is all pretty cryptic to me.

---

### Post by chili555 on 2010-03-26
Well, it can't find the firmware! Please do:```
sudo updatedb
locate rtl8192sfw.bin
```You may find it in RTL9192S[COLOR="Red"]E[/COLOR]. The driver wants to find it in RTL8192S[COLOR="Red"]U[/COLOR].> usb 1-7: firmware: requesting RTL8192S[COLOR="Red"]U[/COLOR]/rtl8192sfw.binLet's see if we can trick it. Please remove the device and do:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Now reinsert the device and do:```
dmesg | grep -e 819 -e firmware
```Post any new entries *after* this: [ 3101.550224] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

In other words, after 3101.

---

### Post by Satchmo2 on 2010-03-26
[ 4757.169819] integrated sync not supported
[ 4819.044913] integrated sync not supported
[ 4819.378056] integrated sync not supported
[ 4819.498385] integrated sync not supported
[ 4819.616906] integrated sync not supported
[ 4819.733398] integrated sync not supported
[ 4819.841403] integrated sync not supported
[ 4819.957397] integrated sync not supported
[ 6716.624120] rtl819xU:=============>wlan driver to be removed
[ 6716.634698] rtl819xU:wlan driver removed
[ 6780.263244] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 6780.294748] rtl819xU: --->FirmwareDownload92S()
[ 6780.294757] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.299383] rtl819xU:request firmware fail!
[ 6780.299886] rtl819xU:Firmware Download Fail!!4544
[ 6780.316128] rtl819xU: --->FirmwareDownload92S()
[ 6780.316138] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.321629] rtl819xU:request firmware fail!
[ 6780.321967] rtl819xU:Firmware Download Fail!!4544
[ 6780.321974] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 6780.347509] rtl819xU: --->FirmwareDownload92S()
[ 6780.347520] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.352089] rtl819xU:request firmware fail!
[ 6780.352571] rtl819xU:Firmware Download Fail!!4544
[ 6780.367135] rtl819xU: --->FirmwareDownload92S()
[ 6780.367147] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.371649] rtl819xU:request firmware fail!
[ 6780.372403] rtl819xU:Firmware Download Fail!!4544
[ 6780.372410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
adam@adam-desktop:~$ 


And here's the first thing, it says it doesn't exist.

adam@adam-desktop:~$ sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
cp: cannot stat `/lib/firmware/RTL8192SE/rtl8192sfw.bin': No such file or directory

---

### Post by chili555 on 2010-03-26
Did you search for it and find it? I said you ***may*** find it there. Is it there or somewhere else or missing altogether?

```
sudo updatedb
locate rtl8192sfw.bin
```

---

### Post by Satchmo2 on 2010-03-26
locate rtl8192sfw.bin seems to do nothing, it just brings up the input again:

adam@adam-desktop:~$ sudo updatedb
adam@adam-desktop:~$ locate rtl8192sfw.bin
adam@adam-desktop:~$ locate rtl8192sfw.bin
adam@adam-desktop:~$

---

### Post by chili555 on 2010-03-26
In case we need it a bit later, here is the firmware.

---

### Post by Satchmo2 on 2010-03-26
Where do I put it?

And btw thanks for your help so far.

---

### Post by chili555 on 2010-03-26
Download the file I referenced just above. By default, downloads go to your desktop. Right-click it and select Extract Here. Now remove the device and do:```
sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Let's make sure the ownership and permissions are correct.```
sudo chown root:root /lib/firmware/RTL8192SU/*
sudo chmod 644 /lib/firmware/RTL8192SU/*
```Insert the device and run:```
dmesg | grep -e 819 -e firmware
```How does it look after 6780?> 6780.372410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by Satchmo2 on 2010-03-26
adam@adam-desktop:~$ sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
adam@adam-desktop:~$ sudo chown root:root /lib/firmware/RTL8192SU/*
adam@adam-desktop:~$ sudo chmod 644 /lib/firmware/RTL8192SU/*
adam@adam-desktop:~$ dmesg | grep -e 819 -e firmware
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.188196] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[ 2315.432888] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 2315.443598] Linux kernel driver for RTL8192 based WLAN cards
[ 2315.457056] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 2315.458307] usbcore: registered new interface driver rtl819xU
[ 2315.504435] rtl819xU: --->FirmwareDownload92S()
[ 2315.504444] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.514359] rtl819xU:request firmware fail!
[ 2315.514844] rtl819xU:Firmware Download Fail!!4544
[ 2315.527689] rtl819xU: --->FirmwareDownload92S()
[ 2315.527699] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.535916] rtl819xU:request firmware fail!
[ 2315.536304] rtl819xU:Firmware Download Fail!!4544
[ 2315.536310] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2315.562321] rtl819xU: --->FirmwareDownload92S()
[ 2315.562332] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.566940] rtl819xU:request firmware fail!
[ 2315.567422] rtl819xU:Firmware Download Fail!!4544
[ 2315.582824] rtl819xU: --->FirmwareDownload92S()
[ 2315.582835] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2315.588929] rtl819xU:request firmware fail!
[ 2315.589257] rtl819xU:Firmware Download Fail!!4544
[ 2315.589264] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3004.176115] rtl819xU:=============>wlan driver to be removed
[ 3004.186504] rtl819xU:wlan driver removed
[ 3045.430714] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 3045.464092] rtl819xU: --->FirmwareDownload92S()
[ 3045.464102] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.469355] rtl819xU:request firmware fail!
[ 3045.469692] rtl819xU:Firmware Download Fail!!4544
[ 3045.486221] rtl819xU: --->FirmwareDownload92S()
[ 3045.486231] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.490781] rtl819xU:request firmware fail!
[ 3045.491258] rtl819xU:Firmware Download Fail!!4544
[ 3045.491264] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3045.511976] rtl819xU: --->FirmwareDownload92S()
[ 3045.511987] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.516490] rtl819xU:request firmware fail!
[ 3045.516983] rtl819xU:Firmware Download Fail!!4544
[ 3045.531729] rtl819xU: --->FirmwareDownload92S()
[ 3045.531739] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3045.536163] rtl819xU:request firmware fail!
[ 3045.536646] rtl819xU:Firmware Download Fail!!4544
[ 3045.536653] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3101.522198] rtl819xU: --->FirmwareDownload92S()
[ 3101.522210] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3101.527156] rtl819xU:request firmware fail!
[ 3101.527632] rtl819xU:Firmware Download Fail!!4544
[ 3101.543695] rtl819xU: --->FirmwareDownload92S()
[ 3101.543707] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3101.548201] rtl819xU:request firmware fail!
[ 3101.550215] rtl819xU:Firmware Download Fail!!4544
[ 3101.550224] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 4757.169819] integrated sync not supported
[ 4819.044913] integrated sync not supported
[ 4819.378056] integrated sync not supported
[ 4819.498385] integrated sync not supported
[ 4819.616906] integrated sync not supported
[ 4819.733398] integrated sync not supported
[ 4819.841403] integrated sync not supported
[ 4819.957397] integrated sync not supported
[ 6716.624120] rtl819xU:=============>wlan driver to be removed
[ 6716.634698] rtl819xU:wlan driver removed
[ 6780.263244] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 6780.294748] rtl819xU: --->FirmwareDownload92S()
[ 6780.294757] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.299383] rtl819xU:request firmware fail!
[ 6780.299886] rtl819xU:Firmware Download Fail!!4544
[ 6780.316128] rtl819xU: --->FirmwareDownload92S()
[ 6780.316138] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.321629] rtl819xU:request firmware fail!
[ 6780.321967] rtl819xU:Firmware Download Fail!!4544
[ 6780.321974] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 6780.347509] rtl819xU: --->FirmwareDownload92S()
[ 6780.347520] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.352089] rtl819xU:request firmware fail!
[ 6780.352571] rtl819xU:Firmware Download Fail!!4544
[ 6780.367135] rtl819xU: --->FirmwareDownload92S()
[ 6780.367147] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 6780.371649] rtl819xU:request firmware fail!
[ 6780.372403] rtl819xU:Firmware Download Fail!!4544
[ 6780.372410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 8267.052116] rtl819xU:=============>wlan driver to be removed
[ 8267.062554] rtl819xU:wlan driver removed
[ 8392.417896] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 8392.452400] rtl819xU: --->FirmwareDownload92S()
[ 8392.452412] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 8392.458876] rtl819xU:signature:8192, version:7031, size:30, imemsize:8408, sram size:a448
[ 8392.458937] rtl819xU:--->FirmwareDownloadCode()
[ 8392.458981] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 8392.711073] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 8392.711080] rtl819xU:FirmwareDownloadCode() fail ! 
[ 8392.711314] rtl819xU:Firmware Download Fail!!4544
[ 8392.726074] rtl819xU: --->FirmwareDownload92S()
[ 8392.726080] rtl819xU:--->FirmwareDownloadCode()
[ 8392.726125] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 8392.976868] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 8392.976875] rtl819xU:FirmwareDownloadCode() fail ! 
[ 8392.977110] rtl819xU:Firmware Download Fail!!4544
[ 8392.977116] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 8393.000127] rtl819xU: --->FirmwareDownload92S()
[ 8393.000135] rtl819xU:--->FirmwareDownloadCode()
[ 8393.000174] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 8393.250918] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 8393.250924] rtl819xU:FirmwareDownloadCode() fail ! 
[ 8393.251159] rtl819xU:Firmware Download Fail!!4544
[ 8393.265667] rtl819xU: --->FirmwareDownload92S()
[ 8393.265674] rtl819xU:--->FirmwareDownloadCode()
[ 8393.265719] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 8393.516589] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 8393.516596] rtl819xU:FirmwareDownloadCode() fail ! 
[ 8393.516830] rtl819xU:Firmware Download Fail!!4544
[ 8393.516836] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
adam@adam-desktop:~$ 

Not sure what happened here.

---

### Post by chili555 on 2010-03-26
> Not sure what happened here.I don't either, yet. I will check in tomorrow.

---

### Post by chili555 on 2010-03-27
I downloaded the file rtl8192su_linux_2.6.0002.0708.2009 from the internet. I was reading this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034)

It suggests that the firmware file in it is appropriate for your device; see post #22 and #23.

I compared the md5sum of the file I attached earlier to the md5sum of the firmware file I just downloaded. Here is the result:> chili@LAPTOP60:~$ md5sum /lib/firmware/2.6.31-20-generic/RTL8192SE/rtl8192sfw.bin
**a5ad703551efb108ba012b4b8a830d93 ** /lib/firmware/2.6.31-20-generic/RTL8192SE/rtl8192sfw.bin
chili@LAPTOP60:~$ md5sum 8192su/rtl8192su_linux_2.6.0002.0708.2009/firmware/RTL8192SU/rtl8192sfw.bin 
**68533bf8078a9e00966a78c9f2da4b9b**  8192su/rtl8192su_linux_2.6.0002.0708.2009/firmware/RTL8192SU/rtl8192sfw.binThey are different. I also notice a difference in the location of the file. Here is the version from the file I downloaded.

Before you download the file I attached, remove the previous version:```
cd Desktop
rm rtl8192sfw.*
sudo rm /lib/firmware/RTL8192SU/*
```Now, the previous, not-working files are gone to heaven.

Download this file. Remove the device.

On your desktop, right-click the file and select Extract Here. Next, do:```
sudo cp ~/Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU/
sudo mkdir /lib/firmware/`uname -r`/RTL8192SU
sudo cp ~/Desktop/rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU/

```Those tickmarks are on the left on my US keyboard on the same key with ~.

Reinsert the device. Any improvement? What does this tell us?```
dmesg | grep -e 819 -e firmware
```

I have included some of the more technical details for the benefit of the searchers.

---

### Post by Satchmo2 on 2010-03-27
adam@adam-desktop:~/Desktop$ dmesg | grep -e 819 -e firmware
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.848191] brd: module loaded
[   16.343641] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   16.350188] Linux kernel driver for RTL8192 based WLAN cards
[   16.362726] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[   16.363717] usbcore: registered new interface driver rtl819xU
[   16.673139] rtl819xU: --->FirmwareDownload92S()
[   16.673149] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   16.914163] rtl819xU:signature:8192, version:7031, size:30, imemsize:8408, sram size:a448
[   16.914210] rtl819xU:--->FirmwareDownloadCode()
[   16.914249] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   17.231961] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   17.231966] rtl819xU:FirmwareDownloadCode() fail ! 
[   17.232338] rtl819xU:Firmware Download Fail!!4544
[   17.246586] rtl819xU: --->FirmwareDownload92S()
[   17.246591] rtl819xU:--->FirmwareDownloadCode()
[   17.246625] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   17.780656] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   17.780661] rtl819xU:FirmwareDownloadCode() fail ! 
[   17.780898] rtl819xU:Firmware Download Fail!!4544
[   17.780902] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   18.006309] rtl819xU: --->FirmwareDownload92S()
[   18.006316] rtl819xU:--->FirmwareDownloadCode()
[   18.006358] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   18.413860] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   18.413865] rtl819xU:FirmwareDownloadCode() fail ! 
[   18.414103] rtl819xU:Firmware Download Fail!!4544
[   18.446864] rtl819xU: --->FirmwareDownload92S()
[   18.446871] rtl819xU:--->FirmwareDownloadCode()
[   18.446911] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[   18.818663] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[   18.818668] rtl819xU:FirmwareDownloadCode() fail ! 
[   18.818904] rtl819xU:Firmware Download Fail!!4544
[   18.818909] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  304.748097] rtl819xU:=============>wlan driver to be removed
[  304.758515] rtl819xU:wlan driver removed
[  355.695410] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[  355.724939] rtl819xU: --->FirmwareDownload92S()
[  355.724950] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  355.730861] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[  355.730915] rtl819xU:--->FirmwareDownloadCode()
[  355.730959] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[  355.982724] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[  355.982731] rtl819xU:FirmwareDownloadCode() fail ! 
[  355.982965] rtl819xU:Firmware Download Fail!!4544
[  355.996847] rtl819xU: --->FirmwareDownload92S()
[  355.996853] rtl819xU:--->FirmwareDownloadCode()
[  355.996891] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[  356.247632] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[  356.247638] rtl819xU:FirmwareDownloadCode() fail ! 
[  356.247874] rtl819xU:Firmware Download Fail!!4544
[  356.247880] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  356.268137] rtl819xU: --->FirmwareDownload92S()
[  356.268145] rtl819xU:--->FirmwareDownloadCode()
[  356.268183] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[  356.519041] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[  356.519047] rtl819xU:FirmwareDownloadCode() fail ! 
[  356.519284] rtl819xU:Firmware Download Fail!!4544
[  356.533917] rtl819xU: --->FirmwareDownload92S()
[  356.533922] rtl819xU:--->FirmwareDownloadCode()
[  356.533954] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[  356.784574] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[  356.784579] rtl819xU:FirmwareDownloadCode() fail ! 
[  356.784817] rtl819xU:Firmware Download Fail!!4544
[  356.784819] 
[  356.784823] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


Hmm, I still can't connect to anything but if it counts when I rightclick the Ethernet icon it says enable wireless and enable networking. Nothing else shows up though and it says wireless device not ready.

---

### Post by Satchmo2 on 2010-03-27
Any ideas?

---

### Post by Satchmo2 on 2010-03-27
Bump.

---

### Post by chili555 on 2010-03-27
I wonder if the permissions are right. Please remove the device and do:```
sudo chmod 755 /lib/firmware/`uname -r`/RTL8192SU/*
sudo chmod 755 /lib/firmware/RTL8192SU/*
sudo chown root:root /lib/firmware/`uname -r`/RTL8192SU/*
sudo chown root:root /lib/firmware/RTL8192SU/*
```Insert the device, take a deep breath and run:```
dmesg | grep -e 819 -e firmware
```Are we seeing any improvement?

---

### Post by Satchmo2 on 2010-03-27
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[ 2718.866912] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 2718.877429] Linux kernel driver for RTL8192 based WLAN cards
[ 2718.890305] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 2718.891572] usbcore: registered new interface driver rtl819xU
[ 2718.946439] rtl819xU: --->FirmwareDownload92S()
[ 2718.946450] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2718.975452] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[ 2718.975507] rtl819xU:--->FirmwareDownloadCode()
[ 2718.975551] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 2719.227992] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 2719.227999] rtl819xU:FirmwareDownloadCode() fail ! 
[ 2719.228506] rtl819xU:Firmware Download Fail!!4544
[ 2719.242366] rtl819xU: --->FirmwareDownload92S()
[ 2719.242372] rtl819xU:--->FirmwareDownloadCode()
[ 2719.242409] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 2719.493162] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 2719.493168] rtl819xU:FirmwareDownloadCode() fail ! 
[ 2719.493404] rtl819xU:Firmware Download Fail!!4544
[ 2719.493410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2719.525543] rtl819xU: --->FirmwareDownload92S()
[ 2719.525551] rtl819xU:--->FirmwareDownloadCode()
[ 2719.525589] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 2719.776337] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 2719.776343] rtl819xU:FirmwareDownloadCode() fail ! 
[ 2719.776579] rtl819xU:Firmware Download Fail!!4544
[ 2719.791087] rtl819xU: --->FirmwareDownload92S()
[ 2719.791092] rtl819xU:--->FirmwareDownloadCode()
[ 2719.791125] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 2720.041883] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 2720.041888] rtl819xU:FirmwareDownloadCode() fail ! 
[ 2720.042125] rtl819xU:Firmware Download Fail!!4544
[ 2720.042131] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


Just failures, do you think a reinstall of ubuntu would help? Not much on here so it wouldn't be too bothersome.

EDIT: As well if I go into wifi radar(some program I downloaded) it straight out says no devices are connected. Also maybe I should have included this earlier... a long time ago when I installed ubuntu, if I plugged this card in it would show up and show my networks(I didn't install any drivers for it either), but I couldn't connect and so I gave up and went back to windows. Now it's like it doesn't even see it's plugged in, but gdiswrapper does.

---

### Post by chili555 on 2010-03-27
> do you think a reinstall of ubuntu would help?A fresh start? Yes. I will be here waiting.

---

### Post by Satchmo2 on 2010-03-27
Ubuntu has been completely reinstalled, I haven't tried anything yet so I'm currently wired and have a few options to try and get wireless working.

I have two connectors, a DLINK DWA-130 revision C, and a DLINK WUA2340, we've been working with the 130 so far(I tried both before and neither worked, hopefully now one of them might). I'm wondering whether I should go for the barely updated linux drivers, or the windows drivers with ndiswrapper, though only the 130 has linux drivers available.

---

### Post by chili555 on 2010-03-27
I read that the WUA2340 will work with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=861855&page=2](http://ubuntuforums.org/showthread.php?t=861855&page=2)  Post #16.

Here are the needed Windows drivers: [ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip](ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip)

I think ndiswrapper is installed by default. Do you want to try it, or do you need some guidance?

---

### Post by Satchmo2 on 2010-03-27
I'll try it out and report back.

---

### Post by bkratz on 2010-03-27
> **chili555 said:**
> I read that the WUA2340 will work with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=861855&page=2](http://ubuntuforums.org/showthread.php?t=861855&page=2)  Post #16.

Here are the needed Windows drivers: [ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip](ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip)

I think ndiswrapper is installed by default. Do you want to try it, or do you need some guidance?



Sorry to interrupt, but I don't think it is installed by default. I have always downloaded ndisgtk which install both the ndiswrapper files and the gui frontend through synaptic.

---

### Post by chili555 on 2010-03-27
I believe you are quite correct; however aren't the files (not the GUI) on the install CD? In any event, young Adam has ethernet access, I believe:```
sudo apt-get install ndisgtk
```

---

### Post by bkratz on 2010-03-27
Yes they are on the install disk, but ndisgtk makes it so easy!

---

### Post by Satchmo2 on 2010-03-27
I'm not incompetent lol, I realize it wasn't installed.

Anyways, seems the reformat did the trick after all, I'm connected and it's working flawlessly. Thanks so much for you help chili555, it took two days but it works. People like you are what linux is all about. 

One happy ubuntu user here :D

---

### Post by chili555 on 2010-03-27
You mean it's working out of the box? Amazing! I'm glad. Enjoy.

---

### Post by Satchmo2 on 2010-03-27
Not out of the box, I had to ndis the drivers but it DID work, however I had to disable security on my network as it cause problems with the connection(any fix for this?)

---

### Post by chili555 on 2010-03-28
> I had to disable security on my network as it cause problems with the connection(any fix for this?)What are the symptoms?

---

### Post by Satchmo2 on 2010-03-28
the network icon just keeps trying to connect, then asks for pass(which I already gave), and if it does make it on(rare), it stays connected for maybe a minute, then tries to connect again. Works great without security though.

---

### Post by chili555 on 2010-03-28
Please do:```
ls /var/log
```Find out where Network Manager stores its log; it might be in NetworkManager or network-manager or some such. Then do:```
sudo tail -n50 /var/log/<what_you_found>
```Find the place where it fails and post about ten lines up to and including that part. Let's see what's not happening correctly.

Sorry, I am not at my NM equipped computer right now, or I could identify it for you.

---

### Post by Satchmo2 on 2010-03-28
```
apparmor       dmesg           kern.log          samba
apt            dmesg.0         kern.log.1        speech-dispatcher
auth.log       dmesg.1.gz      lastlog           syslog
auth.log.1     dmesg.2.gz      lpr.log           syslog.1
boot           dmesg.3.gz      lpr.log.1         udev
bootstrap.log  dmesg.4.gz      mail.err          unattended-upgrades
btmp           dpkg.log        mail.info         user.log
ConsoleKit     faillog         mail.log          user.log.1
cups           fontconfig.log  mail.warn         wifi-radar.log
daemon.log     fsck            messages          wtmp
daemon.log.1   gdm             messages.1        Xorg.0.log
debug          installer       news              Xorg.0.log.old
debug.1        jockey.log      pm-powersave.log
dist-upgrade   jockey.log.1    pycentral.log

```

I tried wifi-radar but nothing opened, and none of these look like a network manager to me.

---

### Post by chili555 on 2010-03-28
Oops! Try this:```
sudo cat /var/log/syslog | grep -i network
```


**Note to self: Don't guess; always check.**

---

### Post by Satchmo2 on 2010-03-28
```
f 5 (IP6 Configure Get) started...
Mar 28 14:46:15 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 14:46:15 adam-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Mar 28 14:46:16 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:17 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:17 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:18 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:18 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:18 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:19 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 2 (reason 40)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1369
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  dhclient started with pid 1663
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 14:46:24 adam-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Mar 28 14:46:25 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:25 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:26 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:26 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:28 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:28 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:30 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:30 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:31 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:31 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:32 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:32 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:33 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:33 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:35 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:35 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:37 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:38 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:39 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:40 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:40 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:41 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:42 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:42 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:43 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:43 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:44 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:45 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:45 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:45 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:46 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:47 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:47 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:48 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:48 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:48 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:49 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:49 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:54 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:55 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:55 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:55 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:56 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:56 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:57 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:57 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:58 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:46:58 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:46:59 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:47:01 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:47:02 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:47:05 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:47:06 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:47:07 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:47:07 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 28 14:47:08 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1663
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  Activation (eth0) failed.
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Mar 28 14:47:09 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:47:10 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:47:11 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Mar 28 14:47:11 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Mar 28 14:47:11 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:47:12 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:47:12 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:47:12 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Mar 28 14:47:12 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Mar 28 14:47:12 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:47:13 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:47:13 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:47:13 adam-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Mar 28 14:47:13 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Mar 28 14:47:13 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 28 14:47:21 adam-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 14:47:21 adam-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  dhclient started with pid 1678
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 14:47:40 adam-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Mar 28 14:48:25 adam-desktop NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1678
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  Activation (eth0) failed.
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Mar 28 14:48:26 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Mar 28 14:49:56 adam-desktop kernel: [  238.525258] wlan0: ethernet device 00:1c:f0:1a:ee:f3 using NDIS driver: neta5agu, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 07D1:3A08.F.conf
Mar 28 14:49:56 adam-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlan1, iface: wlan1)
Mar 28 14:49:56 adam-desktop kernel: [  238.550567] udev: renamed network interface wlan0 to wlan1
Mar 28 14:49:56 adam-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): driver does not support SSID scans (scan_capa 0x00).
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper')
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): now managed
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): device state change: 1 -> 2 (reason 2)
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): bringing up device.
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): preparing device.
Mar 28 14:49:56 adam-desktop NetworkManager: <info>  (wlan1): deactivating device (reason: 2).
Mar 28 14:49:57 adam-desktop NetworkManager: <info>  (wlan1): supplicant interface state:  starting -> ready
Mar 28 14:49:57 adam-desktop NetworkManager: <info>  (wlan1): device state change: 2 -> 3 (reason 42)
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  starting...
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  Trying to start the modem-manager...
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:05.0/net/eth0, iface: eth0)
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:05.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar 28 14:50:55 adam-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 28 14:50:55 adam-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  Wireless now enabled by radio killswitch
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: (145631984) ... get_connections.
Mar 28 14:50:55 adam-desktop NetworkManager:    SCPlugin-Ifupdown: (145631984) ... get_connections (managed=false): return empty list.
Mar 28 14:50:55 adam-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): carrier is OFF
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too')
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): now managed
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): bringing up device.
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): preparing device.
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 28 14:50:55 adam-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:05.0/net/eth0
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  modem-manager is now available
Mar 28 14:50:55 adam-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 28 14:50:55 adam-desktop NetworkManager: <info>  Trying to start the supplicant...
Mar 28 14:50:55 adam-desktop avahi-daemon[789]: Network interface enumeration completed.
Mar 28 14:50:55 adam-desktop kernel: [    2.622891] type=1505 audit(1269787846.995:4): operation="profile_load" pid=399 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 28 14:50:55 adam-desktop kernel: [   11.530791] type=1505 audit(1269802255.903:14): operation="profile_replace" pid=889 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 28 14:50:56 adam-desktop kernel: [   12.554256] wlan0: ethernet device 00:1c:f0:1a:ee:f3 using NDIS driver: neta5agu, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 07D1:3A08.F.conf
Mar 28 14:50:57 adam-desktop kernel: [   12.805052] udev: renamed network interface wlan0 to wlan1
Mar 28 14:50:57 adam-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlan1, iface: wlan1)
Mar 28 14:50:57 adam-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): driver does not support SSID scans (scan_capa 0x00).
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper')
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): now managed
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): device state change: 1 -> 2 (reason 2)
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): bringing up device.
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): preparing device.
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): deactivating device (reason: 2).
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): supplicant interface state:  starting -> ready
Mar 28 14:50:57 adam-desktop NetworkManager: <info>  (wlan1): device state change: 2 -> 3 (reason 42)
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) starting connection 'Auto Beaumont'
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  (wlan1): device state change: 3 -> 4 (reason 0)
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Auto Beaumont' requires no security.  No secrets needed.
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Config: added 'ssid' value 'Beaumont'
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 28 14:51:08 adam-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Mar 28 14:51:13 adam-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Mar 28 14:51:18 adam-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> associated
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> completed
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Beaumont'.
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  (wlan1): device state change: 5 -> 7 (reason 0)
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction (timeout in 45 seconds)
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  dhclient started with pid 1691
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 14:51:20 adam-desktop NetworkManager: <info>  DHCP: device wlan1 state changed (null) -> preinit
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  DHCP: device wlan1 state changed preinit -> reboot
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Mar 28 14:51:23 adam-desktop NetworkManager: <info>    address 192.168.0.100
Mar 28 14:51:23 adam-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 28 14:51:23 adam-desktop NetworkManager: <info>    gateway 192.168.0.1
Mar 28 14:51:23 adam-desktop NetworkManager: <info>    nameserver '192.168.0.1'
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 28 14:51:23 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Mar 28 14:51:24 adam-desktop NetworkManager: <info>  (wlan1): device state change: 7 -> 8 (reason 0)
Mar 28 14:51:24 adam-desktop NetworkManager: <info>  Policy set 'Auto Beaumont' (wlan1) as default for routing and DNS.
Mar 28 14:51:24 adam-desktop NetworkManager: <info>  Activation (wlan1) successful, device activated.
Mar 28 14:51:24 adam-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.

```

I'm not sure what I'm supposed to be looking for here...

Moreover, I went out and bought a switch for the connection in the room beside me, so I could have wired, and I can't connect(It sees auto etho, but can't connect, keeps trying however)! Windows has no problems with it however, so I know it works.

---

### Post by chili555 on 2010-03-28
I was hoping we were going to see an example of the system trying and failing to connect to an encrypted network; however, you connected:> NetworkManager: <info>    address 192.168.0.100
NetworkManager: <info>    prefix 24 (255.255.255.0)
NetworkManager: <info>    gateway 192.168.0.1
NetworkManager: <info>    nameserver '192.168.0.1'Do you want to continue to troubleshoot wireless or should we switch to wired ethernet?

---

### Post by Satchmo2 on 2010-03-28
Do you want to continue to troubleshoot wireless or should we switch to wired ethernet?


Let's try getting wired working.

---

### Post by chili555 on 2010-03-28
With the ethernet cable attached, let's see:```
sudo ethtool eth0
ifconfig eth0
```Thanks.

---

### Post by Satchmo2 on 2010-03-28
Hmm, nvm it seems to be working now that I plugged it in WITH the wireless adapter, then I removed the adapter, much faster now. Thanks for your help.

---

### Post by gren12345 on 2010-09-28
I just wanted to say thanks to Chili555.  This thread got my LM Technologies lm006 usb wireless (also got the RTL8192SU chipset) up and running under Lucid 10.04 .  Specifically it was post #16 and this which did the trick for me:


```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```

---

