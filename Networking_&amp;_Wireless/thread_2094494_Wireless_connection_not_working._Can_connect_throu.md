---
title: "Wireless connection not working. Can connect through ethernet cable. Using Lenovo."
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by KISLAYRAKESH on 2012-12-13
[B]Hii! I am new to Ubuntu
My wireless connection worked very well on Windows and Ubuntu 9.04
But it is not working now.
I am using Ubuntu 12.04 LTE on the Lenovo G Series laptop.
I tried the codes given on the forum. [/B]

rakesh@rakesh-C-Notebook-XXXX:~$** lspci -nn | grep 0280**
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
rakesh@rakesh-C-Notebook-XXXX:~$ **rfkill list all**
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
rakesh@rakesh-C-Notebook-XXXX:~$ **lsmod | grep -e brcmsmac -e wl**
wl                   2646601  0 
lib80211               14040  1 wl
rakesh@rakesh-C-Notebook-XXXX:~$ **sudo modprobe -r wl**
[sudo] password for rakesh: 
rakesh@rakesh-C-Notebook-XXXX:~$** lsmod | grep -e brcmsmac -e wl**
**(showed nothing)**
rakesh@rakesh-C-Notebook-XXXX:~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

rakesh@rakesh-C-Notebook-XXXX:~$ **sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning.

rakesh@rakesh-C-Notebook-XXXX:~$[B] sudo modprobe brcmsmac
(showed nothing)
[/B]rakesh@rakesh-C-Notebook-XXXX:~$ 

[B]I can only connect through ethernet cable. 
Please help me so that I dont have to shift back to Windows.[/B]

---

### Post by chili555 on 2012-12-14
Please see here. You have the same device and require the same fix.

[http://askubuntu.com/questions/228821/wireless-not-working-with-drivers-installed/](http://askubuntu.com/questions/228821/wireless-not-working-with-drivers-installed/)

---

### Post by KISLAYRAKESH on 2012-12-14
Thanks for quick response. It did not work. 
I tried the codes that you recommended.
sudo apt-get remove --purge bcmwl-kernel-source sudo apt-get install linux-firmware-nonfree sudo modprobe b43 
this is what I got.
rakesh@rakesh-C-Notebook-XXXX:~$ [B]sudo apt-get remove --purge bcmwl-kernel-source
[/B][sudo] password for rakesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 170903 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae

rakesh@rakesh-C-Notebook-XXXX:~$** sudo apt-get install linux-firmware-nonfree**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

rakesh@rakesh-C-Notebook-XXXX:~$ **sudo modprobe b43**
**(showed nothing)**
rakesh@rakesh-C-Notebook-XXXX:~$ 

Please Help.

---

### Post by chili555 on 2012-12-14
Do you have a wireless interface, ideally wlan0?```
iwconfig
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```Is the wireless switch on or off?```
rfkill list all
```

---

### Post by KISLAYRAKESH on 2012-12-14
YOU ARE GREAT CHILI! I think all it needed was a restart. After the restart now I am replying through wireless connection. 

The codes that you wanted me to run:-

rakesh@rakesh-C-Notebook-XXXX:~$** iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:29:68:05:52   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:90   Missed beacon:0

rakesh@rakesh-C-Notebook-XXXX:~$** sudo iwlist wlan0 scan**
[sudo] password for rakesh: 
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:68:05:52
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000092ba7cf8b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C

rakesh@rakesh-C-Notebook-XXXX:~$** rfkill list all**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
rakesh@rakesh-C-Notebook-XXXX:~$

---

### Post by KISLAYRAKESH on 2012-12-14
Thanks a lot Chili.

---

### Post by chili555 on 2012-12-14
Great job. Please use thread tools at the top to mark Solved.

---

