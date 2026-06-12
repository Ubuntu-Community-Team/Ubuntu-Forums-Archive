---
title: "Need help compiling and installing wireless driver in 11.04"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by Osalot on 2012-02-19
I am new to ubuntu and dont have much expriance with the termal and need some help compiling the driver for my Asus PCE-N15 PCIE 1x card. I got the diver from Asus and Realtek. The chip set is  		 			RTL8188CE. If you need more info let me know and Any and all help is appreciated.

---

### Post by streetjedi on 2012-02-19
Go to [http://www.asus.com/Networks/Wireless_Adapters/PCEN15/#download](http://www.asus.com/Networks/Wireless_Adapters/PCEN15/#download) and choose "Linux" under "OS". Download your driver and all instalation notes should be in readme.txt file. If not, open your terminal and navigate to folder where you downloaded driver to. Then type "sudo su make", type in your password, after that type in "make install". After installation is finished you have to reboot your PC. Click on restart with your mouse, or you can just type in "reboot" in terminal. After rebooting log in to your user account and your wireless card should work just fine.

---

### Post by Osalot on 2012-02-19
> Go to [http://www.asus.com/Networks/Wireles...EN15/#download]("http://www.asus.com/Networks/Wireless_Adapters/PCEN15/#download") and choose "Linux" under "OS". Download your driver and all instalation notes should be in readme.txt file. If not, open your terminal and navigate to folder where you downloaded driver  to. Then type "sudo su make", type in your password, after that type in  "make install". After installation is finished you have to reboot your  PC. Click on restart with your mouse, or you can just type in "reboot"  in terminal. After rebooting log in to your user account and your wireless card should work just fine.

I have the drivers from both Asus and Realtek and in the readmes there is not enough info or asks to do things I have no clue are for or what to put in the terminal:confused:  could you explain how to navigate to folder in the terminal? or what commands to use would help a lot. Just to make it clear I do not know any commands in terminal or how to use them. To do soming in windows like this does not require coding or compiling to install a driver and yes i have tried it with **ndisgtk** to use the windows driver but nothing happens or if i am doing even that incorrectly. Ubuntu is so confusing to install drivers for hardware it does not have support for yet. :confused:

---

### Post by streetjedi on 2012-02-19
to do it just use: cd "folder"

here's some newbie guide too: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by Osalot on 2012-02-19
Ok so used cd and put the file path to the files that need to be compiled in the terminal then use make but all I get Is this 

```
root@osalot-Rampage-Extreme:/home/osalot/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/2.6.38-13-generic-pae/build M=/home/osalot/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make: *** /lib/modules/2.6.38-13-generic-pae/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

Am I still missing something? or did something out of order? also heres what it says to do in the driver readme.

```
Release Date: 2011-12-30, ver 0005 
Realtek Linux mac80211 based driver: 
   --This driver supports follwing RealTek PCIE Wireless LAN NICs: 
    RTL8188CE/RTL8192CE 
    RTL8191SE/RTL8192SE 
    RTL8192DE 
 
   --This driver supports follwing Linux OS: 
     Fedora Core 
    Debian 
    Mandriva 
    Open SUSE 
    Gentoo 
    MeeGo 
    android 2.2 (froyo-x86), etc. 
 
   --This driver supports follwing kernel versions: 
    1) kernel version >=2.6.35 
       you can build & install drvier use II.  
 
 
    2) kernel version [2.6.24, 2.6.34] 
       you can build & install drvier use III.  
 
 
======================================================================================== 
        I. Component  
======================================================================================== 
The driver is composed of several parts: 
    1. Firmare to make nic work 
           1.1 firmare/rtlwifi 
 
    2. Module source code 
       2.1 ./* 
       2.2 rtl8192ce 
       2.2 rtl8192se 
       2.2 rtl8192de 
     
    3. Script to build the modules 
       3.1 Makefile  
 
    4. compat-wireless 
       4.1 compat-wireless*.tar.bz2 
       4.2 compat 
 
======================================================================================== 
        II. Compile & Installation & uninstall 
======================================================================================== 
You can enter top-level directory of driver and execute follwing command to 
Compile, Installation, or uninstall the driver: 
 
    1. Change to Super User 
       sudo su 
 
    2. Compile driver from the source code  
       make 
 
    3. Install the driver to the kernel 
       make install 
       reboot 
 
    4. uninstall driver 
       make uninstall 
 
======================================================================================== 
        III. Compile & Installation & uninstall [2.6.24, 2.6.34] 
======================================================================================== 
We don't support kernel 2.6.24-2.6.34 directly, Because there are 
lots of issues in mac80211 from kernel 2.6.24-2.6.34, 
So we suggest you to use the latest kernel >= 2.6.35. 
 
but if you want to use our driver in an old kernel, 
you can use compat-wireless. this methord can support all kernel 
versions higher than 2.6.24, and you can use all functions 
of our driver like you use it in the latest kernel version. 
 
You can get more informations of compat-wireless from: 
http://wireless.kernel.org/en/users/Download/stable 
 
you should use the following commands to Compile, Installation, or uninstall the driver: 
 
    1. Change to Super User 
       sudo su 
 
    2. install compat-wireless driver 
       ./compat/script/compat-install.sh 
          
    3. reboot 
       reboot 
 
    4. uninstall driver 
       ./compat/script/compat-uninstall.sh 
 
    5. you can get more information form follwing webset for how to use compat-wireless: 
       http://wireless.kernel.org/en/users/Download/stable 
        
NOTICE: 
    1. Maybe you can not use other vendors wireless after you install compat wireless, 
       in this situation, you can uninstall compat-wireless use step 4 to recover it. 
 
    2. This install methord can support all versions of kernel, not just 2.6.24-2.6.34, 
       you can also use it in the kernel higher than 2.6.35. 
======================================================================================== 
                IV. Start Up Wireless 
======================================================================================== 
You can use two methord to start up wireless: 
 
    1. Install driver like II. and reboot OS, Wireless will be brought  
       up by GUI, such as NetworkManager 
 
    2. If Wireless is not brought up by GUI, you can use:  
       ifconfig wlan0 up  
 
       Note: some times when you have two wireless NICs on your computer, 
         interface "wlan0" may be changed to "wlan1" or "wlan2", etc.  
         So before "ifconfig wlan0 up", you can use "iwconfig" to check 
         which interface our NIC is. 
 
       Note: Don't try to down driver by "ifconfig wlan0 down" when  
         NetworkManager id opened, because NetworkManager will up 
         driver automatically.  
 
======================================================================================== 
                V. Wireless UI & NetworkManager  
======================================================================================== 
    1. All latest distributions have UI & NetworkManager to like with AP. 
       And it's more easy to link with AP than commandline, 
       So we suggest you use UI to link with AP. 
 
    2. Don't try to like with AP use commandline with UI or NetworkManager opened. 
 
    3. If you still used commandline to link with AP, Please check if 
       NetworkManager & wpa_supplicant is killed by follwing command: 
 
        ps -x | grep NetworkManager 
        ps -x | grep wpa_supplicant 
 
    4. Follwing commandlines(V-VII) are all used under Linux without UI.  
 
======================================================================================== 
                VI. Set wireless lan MIBs   
======================================================================================== 
This driver uses Wireless Extension as an interface allowing you to set 
Wireless LAN specific parameters. 
 
    1. Current driver supports "iwlist" to show the device status of nic 
 
       iwlist wlan0 [parameters] 
 
       you can use follwing parameters: 
 
            parameter explaination          [parameters]     
               -----------------------         -------------    
            Show available chan and freq    freq / channel   
            Show and Scan BSS and IBSS     scan[ning]           
            Show supported bit-rate         rate / bit[rate]         
 
       For example: 
        iwlist wlan0 channel 
        iwlist wlan0 scan 
        iwlist wlan0 rate 
 
    2. Driver also supports "iwconfig", manipulate driver private ioctls,  
       to set MIBs. 
 
       iwconfig wlan0 [parameters] [val] 
 
       you can use follwing parameters: 
 
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
            iwconfig wlan0 key s:12345 
 
       Note: There are two types of key, "hex" code or "ascii" code. "hex" code 
            only contains hexadecimal characters, "ascii" code is consist of  
                "ascii" characters. Assume the "hex" code key is "0123456789", you  
                are suggested to use command like this "iwconfig wlan0 key 0123456789".  
                Assume the "ascii" code key is "12345", you should enter command  
                like this "iwconfig wlan0 key s:12345". 
 
           Note: Better to set these MIBS without GUI such as NetworkManager and be  
            sure that our nic has been brought up before these settings. WEP key 
            index 2-4 is not supportted by NetworkManager. 
 
======================================================================================== 
                VII. Getting IP address (For OS without UI)  
======================================================================================== 
Before transmit/receive data, you should obtain an IP address use one of 
the follwing method:  
 
    1. static IP address: 
 
        ifconfig wlan0 IP_ADDRESS 
 
    2. dynamic IP address using DHCP: 
            
        dhclient wlan0 
         
 
======================================================================================== 
                VIII. WPAPSK/WPA2PSK (For OS without UI)  
======================================================================================== 
Wpa_supplicant helps you to link with WPA/WPA2(include WPA Enterprise) AP,  
in Linux with NetworkManger & UI, UI will help you to link with AP,  
But if there is no UI & Networkmanger in your Linux, you can use  
follwing method to link with WPA/WPA2 AP.  
     
    1. we suppose that your Linux have installed wpa_supplicant &  
       kernel build with WIRELESS_EXT, In fact, lots of distributions 
       have done like this. 
 
       But if some distribution not install wpa_supplicant, 
       please download wpa_supplicant from webset and install it. 
 
    2. Edit wpa1.conf to set up SSID and its passphrase. 
       For example, the following setting in "wpa1.conf"  
       means SSID to join is "BufAG54_Ch6" and its  
       passphrase is "87654321". 
 
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
 
       You can download wpa_supplicant and read wpa_supplicant.conf  
       for more examples. 
 
    3. Execute WPA supplicant: 
 
       wpa_supplicant -D wext -c wpa1.conf -i wlan0  
 
    4. To see detailed description for driver interface and wpa_supplicant,  
       please type:  
 
       man wpa_supplicant
```

---

### Post by kevdog on 2012-02-19
Try this (it might work):

sudo apt-get install build-essentials linux-headers-`uname -r`

Then try to recompile.

---

### Post by Osalot on 2012-02-19
> Try this (it might work):

sudo apt-get install build-essentials linux-headers-`uname -r`

Then try to recompile.

ok so I put the code in to the terminal but I got this

```
osalot@osalot-Rampage-Extreme:~$ sudo apt-get install build-essentials linux-headers-`uname -r`
[sudo] password for osalot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials

```

Am I missing some packages?

---

### Post by kevdog on 2012-02-19
I typed it wrong -- build-essential, not build-essentials, sorry

---

### Post by Osalot on 2012-02-20
Ok so that got me going and got it compiled and installed reboot but still no WIFI. I used this command 

```
sudo lshw -C network 
```  


Got it fom here [https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper)

and it says that it is Unclaimed heres what it says in the terminal

 ```
osalot@osalot-Rampage-Extreme:~$ sudo lshw -C network
[sudo] password for osalot: 
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:d800(size=256) memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:23:54:65:d0:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 12
       serial: 00:23:54:65:d4:99
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:fe8fc000-fe8fffff ioport:b800(size=256) memory:fe8c0000-fe8dffff

```

I also up dated to 11.10 but still no WIFI had it working before on 11.10
on and another computer that used the 11.10 live disk:confused:

---

### Post by Osalot on 2012-02-20
Any body got any more ideas how to get it working? I been looking at some of the other posts and few are having issue with this same chip set but they are having black listing problems could I be having the same issue?

---

### Post by praseodym on 2012-02-20
Can you show now:
```
uname -a
lspci -nnk | grep -iA2 Realtek
lsmod
rfkill list
iwconfig
dmesg | egrep 'rtl8|r8'
```

---

### Post by Osalot on 2012-02-22
> Can you show now:
     Code:
     uname -a lspci -nnk | grep -iA2 Realtek lsmod rfkill list iwconfig dmesg | egrep 'rtl8|r8'

Ok so I put the commands in the the terminal and the out put I got was this but when I put in this one dmesg | egrep 'rtl8|r8' it did nothing


```
root@osalot-Rampage-Extreme:~# uname -a
Linux osalot-Rampage-Extreme 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 i686 i386 GNU/Linux
root@osalot-Rampage-Extreme:~# lspci -nnk | grep -iA2 Realtek
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
    Kernel modules: rtl8192ce
root@osalot-Rampage-Extreme:~# lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
nvidia              10390874  40 
binfmt_misc            17292  1 
snd_hda_codec_analog    75090  1 
usb_storage            44173  1 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dm_multipath           22771  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           17742  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           193669  0 
snd                    55902  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x38_edac               12932  0 
edac_core              46858  2 x38_edac
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_marvell           12763  0 
ahci                   21634  0 
libahci                25761  1 ahci
sky2                   49304  0 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
root@osalot-Rampage-Extreme:~# rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@osalot-Rampage-Extreme:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
root@osalot-Rampage-Extreme:~# dmesg | egrep 'rtl8|r8'
root@osalot-Rampage-Extreme:~# 


```I hope this helps find out why is not working.

---

### Post by Osalot on 2012-02-23
OK I got my wirless card working by fallowing some of the steps in the is thread
[http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta](http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta)

so far so good I am going to restart to see if is still works:)

---

### Post by Osalot on 2012-02-23
Well it sort of worked I have to run this command  sudo modprobe rtl8192ce to make it show up in the gui  and connect to the network with the other connections:confused: did I miss a step? How do I get it to work every time I turn on or restart my computer? I add in to the driver to /etc/modules but its not working:(

---

### Post by chili555 on 2012-02-23
> **Osalot said:**
> Well it sort of worked I have to run this command  sudo modprobe rtl8192ce to make it show up in the gui  and connect to the network with the other connections:confused: did I miss a step? How do I get it to work every time I turn on or restart my computer? I add in to the driver to /etc/modules but its not working:(Please let us see:```
cat /etc/modules
```Thanks.

---

### Post by praseodym on 2012-02-23
You need to uninstall ndiswrapper:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
sudo depmod -a
sudo update-initramfs -u
```
Reboot.

---

### Post by Osalot on 2012-02-23
> Please let us see: 	Code:
 	cat /etc/modules 
Thanks.

Heres whats in /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtl8192ce.ko

```



> You need to uninstall ndiswrapper:

 	Code:
 	sudo modprobe -rf ndiswrapper sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk sudo rm /etc/modprobe.d/ndiswrapper.conf sudo rm -r /etc/ndiswrapper/* sudo depmod -a sudo update-initramfs -u 
Reboot.

Done and removed will reboot

---

### Post by Osalot on 2012-02-23
Well removing ndiswrapper seem to have worked as far as it showing up after a reboot will try to reboot once more and do a cold boot to see if it is working after doing that

OK! It finally works and shows up in the connections menu thanks to all that helped and posted info to resolve my issue with the wireless card and will add a little how to for beginners who have issues with this chip set and new to the terminal as I could not find one.

---

