---
title: "WNA3100 Support"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by cybpabeofm on 2012-03-25
*hyperlinks are inserted into the word guide*
I recently followed this [guide]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100") to install a netgear WNA3100 (v1) USB wireless adapter. The only step I didnt use was the first one were I am supposed to mod a file, instead I compiled NDISWRAPPER 1.57 (according to the guide the 1.57 version doesnt require modding). I compiled it with the following steps:
extracted in terminal
cd /home/user/Desktop/ndiswrapper-1.57
sudo make uninstall
sudo make
sudo make install

after that I typed in NDISWRAPPER and got the standard command list so I ASSUMED that it had installed correctly.
Then I followed the guide up until ndiswrapper -l. I typed this in and it only showed the driver, not any hardware (in this case my WNA3100) that was supposed to be coupled with it. So I entered the command:
ndiswrapper -a 0846:9020 bcmwlhigh5
no errors. clicked on the little wireless thing in the top right corner and nothing. typed in IWCONFIG and both eth0 and link0 showed up with NO hardware, even though I have ethernet on the motherboard and I also have the WNA3100. When I type in lsusb the WNA3100 shows up. So a little while after browsing the web I ran into this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). I read through it and decided to blacklist all of the free drivers (step 3). That didnt work either. This is the output from ndiswrapper -l
WARNING: All config files need .conf /etc/modprobe.d/blacklist, it will be ignored in a future release
bcmwlhigh5: driver install
          device (0846:9020) present

My build is custom:
Rosewill thor case
fx 8120
gigabyte 990fxa-ud3
gtx 550 ti (have to use nouveau.nomodeset=0 when booting up)
8 gigabytes of PNY RAM
600W PSU
PS/2 connected vaio keyboard
Dynex USB mouse
Speakers
Envision display
Netgear WNA3100 v1 USB adapter
but the WNA3100 DOESNT work, am I missing something?

---

### Post by chili555 on 2012-03-25
> Then I followed the guide up until ndiswrapper -l. I typed this in and it only showed the driver, not any hardware That suggests the .inf is incorrect for your device. Here is a better package that might work better.

I'd remove the current .inf:```
sudo ndiswrapper -e bcmwlhigh5
```Wipe out all the vestiges of the old incorrect .inf:```
sudo rm -rf /etc/ndiswrapper/*
```Download this file to your desktop and then right-click it and select *Extract Here*. Now do:```
sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
ndiswrapper -l
iwconfig
```Any improvement?

---

### Post by chili555 on 2012-03-25
Note to searchers: You can actually read the .inf file to see if it drives your device and that it's an XP file:> ;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9020[/COLOR]

;-----------------------------------------------------------------
If it isn't, keep looking.

---

### Post by cybpabeofm on 2012-03-25
Thank you!! :-D

---

### Post by cybpabeofm on 2012-03-25
When I type in ndiswrapper -l it'll show that the device is in fact present, but iwconfig says the exact opposite. It appears to me as if one clearly recognizes the adapter and the other doesnt, when I click on the wireless icon in the top right it shows no sign of the adapter. I am thoroughly puzzled :/

---

### Post by chili555 on 2012-03-25
What does this tell us?```
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by cybpabeofm on 2012-03-26
user@user-GA-990FXA-UD3:~$ sudo su

[sudo] password for user: 

root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
root@user-GA-990FXA-UD3:/home/user# exit
exit
user@user-GA-990FXA-UD3:~$ dmesg | grep ndis
user@user-GA-990FXA-UD3:~$


I would just type it in the it would display what account I was logged in under, under both sudo and normal powers.? :confused:

---

### Post by chili555 on 2012-03-26
The command:```
dmesg | grep ndis
```...should tell us if there are any kernel messages with 'ndis' in the name. Obviously, so far, there isn't. It does no good to repeat this or any command repeatedly. Let's try again:```
sudo modprobe ndiswrapper
iwconfig
dmesg | grep ndis
```Just once, please, as a normal user.

---

### Post by cybpabeofm on 2012-03-26
user@user-GA-990FXA-UD3:~$ sudo su
[sudo] password for user: 
root@user-GA-990FXA-UD3:/home/user# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
root@user-GA-990FXA-UD3:/home/user# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@user-GA-990FXA-UD3:/home/user# dmesg | grep ndis
[   53.775324] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   54.083882] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   54.084039] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   54.678001] usbcore: registered new interface driver ndiswrapper



That is the output from the commands you gave me. Now I do have networking but I cant connect to my WPA2 AES encrypted network, I checked to make sure that I used the right password (5x), and reset my modem, and rebooted 2x. However, I still cannot connect, but I am very glad I have your technical expertise.

---

### Post by cybpabeofm on 2012-03-26
My bad I did it as a normal user, but, I am still not able to connect to my WPA2 AES encrypted network. These are the outputs for the commands you gave me:




user@user-GA-990FXA-UD3:~$ sudo modprobe ndiswrapper
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
user@user-GA-990FXA-UD3:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-GA-990FXA-UD3:~$ dmesg | grep ndis
[   50.175952] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   50.476206] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   50.476337] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   51.069873] usbcore: registered new interface driver ndiswrapper
user@user-GA-990FXA-UD3:~$

---

### Post by chili555 on 2012-03-26
> ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'I'm conflicted. This doesn't appear to be an error; it may simply be a harmless warning. When you Google this, *every* hit is for WNA3100 and bcmwlhigh5.inf! 

The reason I suspect it isn't an actual error is that a wireless interface wlan0 is created, it sees your network and at least tries to connect.

Before we delve deep into the C code and recompile ndiswrapper, let's see if we can diagnose a bit. Please post:```
sudo iwlist wlan0 scan
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

---

### Post by cybpabeofm on 2012-03-26
The output:

user@user-GA-990FXA-UD3:~$ sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     Interface doesn't support scanning.

user@user-GA-990FXA-UD3:~$ sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]:    SCPlugin-Ifupdown: (144507592) ... get_connections.
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]:    SCPlugin-Ifupdown: (144507592) ... get_connections (managed=false): return empty list.
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]:    Ifupdown: get unmanaged devices count: 0
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> modem-manager is now available
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> WiFi enabled by radio killswitch; enabled by state file
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> WWAN enabled by radio killswitch; enabled by state file
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> WiMAX enabled by radio killswitch; enabled by state file
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> Networking is enabled by state file
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): carrier is OFF
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): now managed
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): bringing up device.
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): preparing device.
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/eth0
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 26 08:08:36 user-GA-990FXA-UD3 NetworkManager[852]: <warn> bluez error getting default adapter: No such adapter
user@user-GA-990FXA-UD3:~$ 



However I **_didnt_** run the commands:
dmesg | grep ndis
sudo modprobe ndiswrapper
iwconfig
dmesg | grep ndis

Do you want me to run these first? Wireless was down, according to the icon in the top right corner.

---

### Post by cybpabeofm on 2012-03-26
Does this have any use here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435119](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435119)

I'm currently running the ubuntu 11.10 i386 (32bit) OS

---

### Post by chili555 on 2012-03-26
> **cybpabeofm said:**
> Does this have any use here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435119](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435119)

I'm currently running the ubuntu 11.10 i386 (32bit) OSThat has to do with bluetooth; not significant here.

There is almost nothing here about wireless, wlan0. Please try again:```
sudo modprobe ndiswrapper
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Please leave the ethernet disconnected while you run the tests.

---

### Post by cybpabeofm on 2012-03-27
My ethernet was disconnected for ALL of them. Wireless is my only way to acquire internet, Im dual booting with windows

---

### Post by cybpabeofm on 2012-03-28
> **chili555 said:**
> That has to do with bluetooth; not significant here.

There is almost nothing here about wireless, wlan0. Please try again:```
sudo modprobe ndiswrapper
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Please leave the ethernet disconnected while you run the tests.

Here is the output for the commands you gave me:

user@user-GA-990FXA-UD3:~$ sudo modprobe ndiswrapper
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
user@user-GA-990FXA-UD3:~$ sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Mar 28 03:21:12 user-GA-990FXA-UD3 NetworkManager[826]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 28 03:21:12 user-GA-990FXA-UD3 NetworkManager[826]: <warn> bluez error getting default adapter: No such adapter
Mar 28 03:21:51 user-GA-990FXA-UD3 kernel: [   50.697548] wlan0: ethernet device e0:46:9a:bc:9e:3e using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
Mar 28 03:21:51 user-GA-990FXA-UD3 kernel: [   50.700688] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0)
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <error> [1332919311.320096] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): now managed
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): bringing up device.
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): preparing device.
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 28 03:21:51 user-GA-990FXA-UD3 kernel: [   50.752593] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> wpa_supplicant started
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 28 03:21:51 user-GA-990FXA-UD3 NetworkManager[826]: <info> (wlan0): supplicant interface state: ready -> inactive
user@user-GA-990FXA-UD3:~$

---

### Post by cybpabeofm on 2012-03-28
bump

---

### Post by chili555 on 2012-03-28
We're getting closer! I am studying this:> [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)Does the interface scan?```
sudo iwlist wlan0 scan
```Is your access point/router/network set up with a hidden SSID?

---

### Post by cybpabeofm on 2012-03-28
The output:


sudo modprobe ndiswrapper
sudo iwlist wlan0 scan

user@user-GA-990FXA-UD3:~$ sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:B7:89:39
                    ESSID:"mtdnens"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 58:6D:8F:B7:89:3B
                    ESSID:"mtdnens-guest"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:26:62:E8: D6: D4
                    ESSID:"A44N1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:1F:90:EE:7F:F2
                    ESSID:"QHQJ2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1F:90:E9:69: DC
                    ESSID:"J9WL1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: A0:21:B7:B7:65: 0A
                    ESSID:"ragdolls"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

user@user-GA-990FXA-UD3:~$

---

### Post by cybpabeofm on 2012-03-28
My access point/SSID isnt hidden. It is mtdnens, its WPA2 AES encrypted.

---

### Post by cybpabeofm on 2012-03-29
thanks

---

### Post by cybpabeofm on 2012-03-29
this is a working guide anyone looking for a comprenhensive way to install the driver for a Netgear N300 WNA3100 USB wifi adapter can follow these steps.
Install NDISWRAPPER
Download the latest NDISWRAPPER source code
browse to it in terminal: cd /path/to/source/code
Once your in the directory: 
make uninstall
make
sudo make install
Installing the driver:
The wna3100 driver can be found on page 1
Browse to the directory with the wna3100 driver: cd /path/to/driver
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows that the USB device is scanning then you have installed the driver correctly and will have wireless capabilities with a minute, if not you either dont have the correct driver or its not installed correctly.
This guide wouldnt be possible without the help of chili555

---

### Post by Nuster on 2012-05-02
Hello to all!
All new to Ubuntu Forums and with little to no experience on Ubuntu...
I follow the guide posted on the last post and when I type "sudo modprobe ndiswrapper" my terminal freezes as if trying to load something. 
Any suggestions?

---

### Post by chili555 on 2012-05-02
Do you have the exact same device? Please open a terminal and run and post:```
lsusb
arch
```Thanks. Welcome to the exciting world of Ubuntu!

---

### Post by Nuster on 2012-05-02
Thanks for your reply! 

Yes I've got the exact same device, N300 Wireless USB Adapter - WNA3100.

Here's the output:
```
user@PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04fc:0801 Sunplus Technology Co., Ltd 
Bus 001 Device 004: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 006: ID 18d1:4e24 Google Inc. Nexus S (tether)
user@PC:~$ arch
x86_64
```

---

### Post by chili555 on 2012-05-02
Please see post #14 here: [http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2](http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2)

---

### Post by Nuster on 2012-05-02
I see. 
The commands seem to have made some progress with the device though (it's built-in light is on now :) ).

So that's why I can't run the following command on my terminal? 
```
sudo modprobe ndiswrapper
```I've read somewhere that it was a kernel problem but it was a really old post referring to an older Ubuntu version. 
I am using 12.04.

---

### Post by chili555 on 2012-05-02
I don't know how I could have made myself any clearer. I know of *no way* to get this device to work correctly in 64-bit. Sure, you can download and try different .inf and .sys files; there is a post somewhere outlining modifying the .inf file; there is a post around where some guy got it to work but not with encryption. There are dozens of posts around about freezes and not ever seeing networks and everything else except smoke and sparks. I have not seen *any* posts where someone said it works, it connects and it does WPA2 perfectly.

You can chase your tail for a few weeks and probably still not be successful. You can install 32-bit. You can buy a different device. But I know of *no way* to get this device to work correctly in 64-bit.

---

### Post by Nuster on 2012-05-02
You were completely clear from your previous post. 
I just wasn't sure about the command I mentioned, thinking it had nothing to do with the compatibility of the device.
I am relatively new to Ubuntu and, therefore, UNIX commands.
Thanks for your time.

---

### Post by glendavee on 2012-05-21
chili555
Been reading through this thread as I'm having a problem with same netgear usb adaptor, and I'm running 64bit 12.04. I have ndiswrapper-1.57 installed, and bcmn43xx64.inf
My problem is that the adaptor works, but every now and then, drops the internet connection. Interesting bit is that when connection is down, everything in my system tells me that internet is ok - ie network manager shows connection ok, iwconfig shows no problem.
Solution is either to reboot, or unplug usb adaptor and replug.
Judging from your comments, is this something I just have to put up with?
Alternatively, can you recomment any device which is know to work with 64bit system?

---

### Post by chili555 on 2012-05-21
In view of my comments above about 64-bit, I'm quite amazed that it works at all. Did you do anything special? Did you simply follow the usual ndiswrapper instructions?

I would start troubleshooting by turning off N speeds in the router. I'd also make sure it's set for WPA2 only and not WPA and WPA2 mixed mode. I'd also try different channels in the router, especially 1 and 11. I'd look at the signal strength from the router; is there any way to improve it?> iwconfig

wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx  
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=61/70[/COLOR]  Signal level=-49 dBm  

Finally, although I don't hold out much hope, I'd look for clues in syslog.```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by kurt18947 on 2012-05-21
> **glendavee said:**
> 
Alternatively, can you recomment any device which is know to work with 64bit system?

Not Chili555 but I think you'll find a Netgear WNA1100 is plug 'n' play.  Be aware that it's not dual band thus N150 only.  The trick with WiFi devices and Linux is pay attention to the ***chipset****, *not the manufacturer.  I've had quite good luck with Atheros ath9k devices - the Netgear WNA 110 is one - and pretty good luck with RealTek RTL8192SU.  The Dlink DWA-131 is an adapter that usese the RealTek RTL8192SU chip and is plug - n - play in my experience.

There are a lot of vendors on Ebay offering nano WiFi adapters.  Many of these use RealTek's RTL8188 Cus chipset.  My experience is that chipset will work if used with RealTek's driver.  The driver that is used by default in 12.04  will recognize the device but I've never had a decent connection, the 'enter network password' message keeps repeating.  The driver from RealTek has a bash script which has worked perfectly on 3 different machines.

Edit:  Another gotcha is version numbers of a given model.  Device ABC v.1 may use one chip set, device ABC v.2 will use another chipset which may or may not be compatible.

---

### Post by chili555 on 2012-05-21
Excellent, kurt18947. Thanks!

---

### Post by glendavee on 2012-05-21
Thanks guys. I followed the standard ndiswrapper instructions. I will have a play around with the router as you suggest, though the signal strength is good. I'll post again if I find anything.

---

### Post by peterdtm on 2012-06-07
Thanks 

I followed post #22 - thank you from a newbie - it was in plain English and easy to follow (I had seen many references to 'recompile ndiswrapper' but no explanation of what to actually do) so many thanks 

One point 

sudo modprobe ndiswrapper returns nothing at all but it works ... 

got to try a re-boot ....thanks again !:p

--> well the re-boot worked a treat. Ubuntu box back on the net - thanks guys wish I'd found this one last weekend !

---

### Post by chili555 on 2012-06-07
> sudo modprobe ndiswrapper returns nothing at all but it works ... Correct. When a command returns nothing at all, it means, roughly, 'command executed and there are no errors or warnings to report.' That's exactly what you want to see.

---

### Post by nismo9132 on 2012-06-15
What if I followed all of the instructions from:
> **cybpabeofm said:**
> this is a working guide anyone looking for a  comprenhensive way to install the driver for a Netgear N300 WNA3100 USB  wifi adapter can follow these steps.
Install NDISWRAPPER
Download the latest NDISWRAPPER source code
browse to it in terminal: cd /path/to/source/code
Once your in the directory: 
make uninstall
make
sudo make install
Installing the driver:
The wna3100 driver can be found on page 1
Browse to the directory with the wna3100 driver: cd /path/to/driver
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows that the USB device is scanning then you have  installed the driver correctly and will have wireless capabilities with a  minute, if not you either dont have the correct driver or its not  installed correctly.
This guide wouldnt be possible without the help of chili555

but when I type:
```
 sudo modprobe ndiswrapper 
```
my terminal does nothing. I don't believe I have a 64 bit version of Ubuntu.
Not sure what to do... I'm currently running sharing the internet through an ethernet switch from one of my laptops right now lol

---

### Post by chili555 on 2012-06-15
> I don't believe I have a 64 bit version of Ubuntu.Let's see. Please run and post:```
arch
```Let's do some diagnostics:```
dmesg | grep ndis
iwconfig
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by kian128 on 2012-07-26
Concerning 64 bit support, I'm running Ubuntu 12.04 64 bit with the WNA3100, and it's working perfectly :D I followed guides on this thread and others but with no success, and was about to give up until I found this post: [http://forums.linuxmint.com/viewtopic.php?f=197&t=92044](http://forums.linuxmint.com/viewtopic.php?f=197&t=92044)

It also has a small section at the end about improving connection stability, which might be worth checking out.

---

### Post by Elkster on 2012-09-10
I am having trouble with netgear. Same one as mentoned here.

danielehlke@ubuntu:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub

Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser

Bus 001 Device 005: ID 1058:1110 Western Digital Technologies, Inc. 

Bus 002 Device 003: ID 18e3:9106 Fitipower Integrated Technology Inc 

Bus 002 Device 004: ID 413c:5233 Dell Computer Corp. 

Bus 001 Device 006: ID 06a3:075c Saitek PLC X52 Flight Controller

Bus 001 Device 007: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

danielehlke@ubuntu:~$ dmesg | grep ndis

danielehlke@ubuntu:~$ sudo modprobe ndiswrapper

[sudo] password for danielehlke: 

danielehlke@ubuntu:~$ iwconfig

lo        no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"belkin.63c"  

          Mode:Managed  Frequency:2.422 GHz  Access Point: 08:86:3B:73:96:3C   

          Bit Rate=300 Mb/s   Tx-Power:32 dBm   

          RTS thr:2347 B   Fragment thr:2346 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



eth0      no wireless extensions.



danielehlke@ubuntu:~$ dmesg | grep ndis

[  187.634297] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)

[  187.859663] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded

[  188.391483] usbcore: registered new interface driver ndiswrapper

danielehlke@ubuntu:~$ 

The authentication required window keeps popping up. I've checked the password and it is entered correctly. 

When I switch back to Windows 7, I have to reinstall the driver for Windows. What is going on?????

---

### Post by dizzylizard on 2012-11-03
> **cybpabeofm said:**
> this is a working guide anyone looking for a comprenhensive way to install the driver for a Netgear N300 WNA3100 USB wifi adapter can follow these steps.
Install NDISWRAPPER
Download the latest NDISWRAPPER source code
browse to it in terminal: cd /path/to/source/code
Once your in the directory: 
make uninstall
make
sudo make install
Installing the driver:
The wna3100 driver can be found on page 1
Browse to the directory with the wna3100 driver: cd /path/to/driver
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows that the USB device is scanning then you have installed the driver correctly and will have wireless capabilities with a minute, if not you either dont have the correct driver or its not installed correctly.
This guide wouldnt be possible without the help of chili555

I did the above, and got the following output:
```
root@TedzBox:/home/damien# cd wna3100-drivers
root@TedzBox:/home/damien/wna3100-drivers# sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@TedzBox:/home/damien/wna3100-drivers#  sudo modprobe ndiswrapper
root@TedzBox:/home/damien/wna3100-drivers# iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.


```

What next?

---

### Post by chili555 on 2012-11-03
> **dizzylizard said:**
> 
What next?Look for interesting messages:```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by dizzylizard on 2012-11-04
> **chili555 said:**
> Look for interesting messages:```
ndiswrapper -l
dmesg | grep ndis
```

```

damien@TedzBox:~$ sudo -s
[sudo] password for damien: 
root@TedzBox:~# sudo iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.

root@TedzBox:~# sudo ndiswrapper -l
bcmn43xx32 : driver installed
	device (0846:9020) present
root@TedzBox:~# dmesg | grep ndis
[  266.158359] rndis_host 1-9:1.0: usb0: register 'rndis_host' at usb-0000:00:02.1-9, RNDIS device, 02:3a:0f:33:92:63
[  266.160203] usbcore: registered new interface driver rndis_host
[  266.215519] usbcore: registered new interface driver rndis_wlan

root@TedzBox:~# sudo modprobe ndiswrapper
root@TedzBox:~# iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

root@TedzBox:~# dmesg | grep ndis
[  266.158359] rndis_host 1-9:1.0: usb0: register 'rndis_host' at usb-0000:00:02.1-9, RNDIS device, 02:3a:0f:33:92:63
[  266.160203] usbcore: registered new interface driver rndis_host
[  266.215519] usbcore: registered new interface driver rndis_wlan
[  892.996919] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[  893.302690] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  893.834893] usbcore: registered new interface driver ndiswrapper 
```

That's with the usb tethered cellphone attached and connected.  with it off, I get the following from :
```

root@TedzBox:~# sudo modprobe ndiswrapper
root@TedzBox:~# sudo ndiswrapper -l
bcmn43xx32 : driver installed
	device (0846:9020) present
root@TedzBox:~# dmesg | grep ndis
[  266.158359] rndis_host 1-9:1.0: usb0: register 'rndis_host' at usb-0000:00:02.1-9, RNDIS device, 02:3a:0f:33:92:63
[  266.160203] usbcore: registered new interface driver rndis_host
[  266.215519] usbcore: registered new interface driver rndis_wlan
[  892.996919] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[  893.302690] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  893.834893] usbcore: registered new interface driver ndiswrapper
[ 1088.413568] rndis_host 1-9:1.0: usb0: unregister 'rndis_host' usb-0000:00:02.1-9, RNDIS device
[ 1125.919060] rndis_host 1-9:1.0: usb0: register 'rndis_host' at usb-0000:00:02.1-9, RNDIS device, 02:3a:0f:33:92:63
[ 1771.877497] rndis_host 1-9:1.0: usb0: unregister 'rndis_host' usb-0000:00:02.1-9, RNDIS device

```

I posted this on the wireless...gonna reboot and see if it comes back up on its own...

---

### Post by dizzylizard on 2012-11-04
So I rebooted, and after a false start, I got wireless after doing this:
```
sudo modprobe ndiswrapper
root@TedzBox:~# sudo modprobe ndiswrapper
root@TedzBox:~# sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Teddly33"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 88:30:8A:1A:7B:10   
          Bit Rate=58.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:86B6-B238-D8A8-B672-5EDB-40DF-243D-0D8B   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

root@TedzBox:~# sudo dmesg |  grep ndis
[   81.351343] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   81.657610] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   82.181497] usbcore: registered new interface driver ndiswrapper

```

Which script do I have to edit in 12.04 to do this at boot?

---

### Post by dizzylizard on 2012-11-04
Think I got it...I checked this post [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) and entered this into terminal

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

It takes it a few seconds to connect, and it's not connecting automatically (I have to open the network widget and click the connection two or three times to connect), but I think I have it working...anything I need to check to make sure I didn't FUBAR anything?  Or how to get it to connect automatically (I checked the box on the network manager, but it still won't connect automatically)...I'm setting up this box for a total n00b b/c he can't stop getting viruses on his windows systems, and I need to make it as idiotproof as possible...

---

### Post by chili555 on 2012-11-04
> anything I need to check to make sure I didn't FUBAR anything?All your readings look perfect to me.

Please boot and don't click the icon and see if it connects. If not, run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Let's see what Network Manager is doing or not under the hood.

I assume the boxes you checked in NM are 'Connect automatically' and 'Available to all users.'

---

### Post by dizzylizard on 2012-11-04
> **chili555 said:**
> All your readings look perfect to me.

Please boot and don't click the icon and see if it connects. If not, run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Let's see what Network Manager is doing or not under the hood.

I assume the boxes you checked in NM are 'Connect automatically' and 'Available to all users.'

yep...seems to be working,  Takes a few minutes to connect, but I think that's just the box giving me time to roll a joint...:)

heres the output you asked for...
```

 sudo cat /var/log/syslog | grep etwork | tail -n20
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info>   address 192.168.43.244
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info>   prefix 24 (255.255.255.0)
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info>   gateway 192.168.43.1
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info>   hostname 'TedzBox'
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info>   nameserver '192.168.43.1'
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov  4 15:55:10 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov  4 15:55:11 TedzBox NetworkManager[1036]: <info> DNS: starting dnsmasq...
Nov  4 15:55:11 TedzBox NetworkManager[1036]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  4 15:55:12 TedzBox NetworkManager[1036]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  4 15:55:12 TedzBox NetworkManager[1036]: <info> Policy set 'Teddly33' (wlan0) as default for IPv4 routing and DNS.
Nov  4 15:55:12 TedzBox NetworkManager[1036]: <info> Activation (wlan0) successful, device activated.
Nov  4 15:55:12 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  4 15:55:30 TedzBox NetworkManager[1036]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov  4 15:55:30 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov  4 15:55:30 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov  4 15:55:30 TedzBox NetworkManager[1036]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```
Everything look right?  if so, I'd love to call this question done and move to my next one...[http://ubuntuforums.org/showthread.php?p=12337141#post12337141](http://ubuntuforums.org/showthread.php?p=12337141#post12337141)
thanks for all the help!!

---

### Post by chili555 on 2012-11-04
> Everything look right? if so, I'd love to call this question doneLooks very fine to me.

I'm sure you'll get an answer in General Help. That is not my area of (???) expertise. They only let me fool with the simple stuff here on Wireless.

---

### Post by mnk0 on 2012-11-07
dmesg | grep ndis


gives me blank.

---

### Post by chili555 on 2012-11-07
> **mnk0 said:**
> dmesg | grep ndis


gives me blank.That indicates that the module *ndiswrapper* isn't loaded. What have you done so far to install the driver?

---

### Post by DarkAii on 2013-04-27
> **cybpabeofm said:**
> [COLOR=#0000cd]this is a working guide anyone looking for a comprenhensive way to install the driver for a Netgear N300 WNA3100 USB wifi adapter can follow these steps.
Install NDISWRAPPER
Download the latest NDISWRAPPER source code
browse to it in terminal: cd /path/to/source/code
Once your in the directory: 
make uninstall
make
sudo make install
Installing the driver:
The wna3100 driver can be found on page 1
Browse to the directory with the wna3100 driver: cd /path/to/driver
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows that the USB device is scanning then you have installed the driver correctly and will have wireless capabilities with a minute, if not you either dont have the correct driver or its not installed correctly.
This guide wouldnt be possible without the help of chili555[/COLOR]

Hello everyone, I'm having a hard time trying to understand this methode.

I'm new on Linux, from France (=n00b), and I installed the 12.04 (64bits) on my computer because I didn't want to use Windows 8 anymore.
But I can't understand things like go inside a folder(eg: browse in Desktop) in the Terminal.

So far, I managed to download _ndiswrapper-1.58.tar.gz_ & _wna3100-drivers.zip_.

Could anyone give me a help... The solution seems to be already given, but my understanding isn't the same.

Thanks to anyone who can help. (I took 30min to write this little message, my English is really low).

---

### Post by chili555 on 2013-04-27
> **DarkAii said:**
> Hello everyone, I'm having a hard time trying to understand this methode.

I'm new on Linux, from France (=n00b), and I installed the 12.04 (64bits) on my computer because I didn't want to use Windows 8 anymore.
But I can't understand things like go inside a folder(eg: browse in Desktop) in the Terminal.

So far, I managed to download _ndiswrapper-1.58.tar.gz_ & _wna3100-drivers.zip_.

Could anyone give me a help... The solution seems to be already given, but my understanding isn't the same.

Thanks to anyone who can help. (I took 30min to write this little message, my English is really low).This thread is becoming very long with lots of different users. Would you please start your own new thread and I'll be very happy to help you alone. Either leave the link here or send me a private message with the link to your thread.

---

### Post by DarkAii on 2013-04-28
:) Ok, and I'm very sorry to have posted a message requesting help while this actual post is known as **[Resolved]**.

If it is possible to block any new message, then thank you very much.

---

### Post by chili555 on 2013-04-28
> **DarkAii said:**
> :) Ok, and I'm very sorry to have posted a message requesting help while this actual post is known as **[Resolved]**.

If it is possible to block any new message, then thank you very much.I am very happy to help you if you'll start a thread and give us a link.

---

### Post by JoeBearPA on 2013-05-07
This DID work for me, thank you for posting... a question though... Will it continue to be available upon each reboot (will it be persistent?) or do I have to type sudo modprobe ndiswrapper each time I reboot?

Joe

---

### Post by chili555 on 2013-05-07
> **JoeBearPA said:**
> This DID work for me, thank you for posting... a question though... Will it continue to be available upon each reboot (will it be persistent?) or do I have to type sudo modprobe ndiswrapper each time I reboot?

JoeIf it isn't persistent, make it so:```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
```You should be all set.

---

### Post by als2 on 2014-01-28
Thanks for posting this!!! Worked perfectly.

---

