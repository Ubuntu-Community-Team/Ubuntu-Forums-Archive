---
title: "Wifi Card Help Please"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by Z-09 on 2011-03-31
Hello everyone. Thank you for taking the time to read my request. I am very new to Ubuntu and Linux. I just got Ubuntu 10.10 and am using the Ubuntu Desktop Server/Version. I have been trying for weeks to find a solution to a FREE way to turn my laptop into a wireless router to connect my game consoles or my brother's laptop (he has the exact same as I do). I honestly don't care how I manage to find a way (obviously as long as it is legal). I have spent endless hours looking on all the forums i could find for my answer, but I am terrible at searching through forums. If someone would please tell me, or show me, a step-by-step guide to solve my problem, that would greatly be appreciated.

Now for my laptop information. I currently have an** MSI S6000**, pre-installed with Windows 7 Home Premium (I tried finding a way for my Windows 7 but could not find a way that was free. I have NO spare cash on me and won't be able to get some till I get a job in the summer. Right now I am too busy with my college classes). I am dual-booting it with my Ubuntu 10.10. My only source of Internet is with a WIRED LAN cord. I am unable to find and tamper with an IP address because I am connected to my college's internet server, which means that THIS INTERNET AND IP ADDRESS DOES _**NOT**_ BELONG TO ME. IT BELONGS TO THE SCHOOL. Sorry, but I had to point that out. I came across some people who didn't understand that I could change or find the IP address. With that out of the way, here is a link my computer I purchased online:

[http://www.officedepot.com/a/products/541572/MSI-S6000-017US-Laptop-Computer-With/](http://www.officedepot.com/a/products/541572/MSI-S6000-017US-Laptop-Computer-With/)

And this is the information I found using the sudo command.
__________________________________________________________________________

_**sudo lspci**_

[I]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)[/I]

_**sudo iwconfig**_

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
_**sudo iwconfig wlan0 mode master**_
zach@ubuntu:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.[/I]
[U][B]
sudo iwconfig off/any mode master[/B][/U]
[I]zach@ubuntu:~$ sudo iwconfig off/any mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device off/any ; No such device.
[/I]__________________________________________________________________________

Unfortunately I have no idea what all the information means from the **sudo lspci** command. I don't even know which one shows the type of wireless adapter card I have on my laptop. And as you can see, me being the ubuntu/linux nub that I am, I typed in "wlan0" as the adapter name. Since that didn't work, I tried the **"off/any" from the ESSID** (which I thought had to be the name of the adapter).

This is all the information I have to offer for my situation. If anyone can please help me or point me in the right direction, I will be very grateful. Also, if anyone needs more information, just tell me how to (in a nub step-by-step guide preferably :P ) and I'll gladly give the information. Thank you everyone and have a great day.

---

### Post by bkratz on 2011-03-31
This is your wireless card

 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

It looks like you are just about there, 

**Power Management:on**

This is the "sleep mode" for the wireless (can't think of a better term!?)

You will probably need to go to the terminal (it looks like you have already been there) and put in

sudo iwconfig wlan0 power off

To fix that, then try to connect again, the ESSID is the name of what you are trying to connect to, not your card (unless I missunderstood whatyou said above.

---

### Post by Z-09 on 2011-03-31
Thanks for you reply :D . I did as you suggested and got this:

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
         ** Power Management:off**
          
zach@ubuntu:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.[/I]

For some reason, I cannot seem to get it to work still.  Does this mean I cannot change my adapter card into master mode? If not, I could have sworn that I saw someone got his set...

If there is no way for me to do this, I would like to ask another favor. Does anyone know of a virtual router software that supports WEP? I don't know if SoftAP (I don't even know what it does or how to set it up) or bridging connections would work. I am open to any solutions. I see that there are many ways to support WPA but not for WEP. I have a PS3 and a Nintendo DS Lite I would like to connect. If WEP is not possible, please let me know. Once again, thank you for your reply :D .

---

### Post by vlaar on 2011-03-31
> For some reason, I cannot seem to get it to work still.  Does this mean I cannot change my adapter card into master mode? If not, I could have sworn that I saw someone got his set...

You might try this : [http://www.linuxquestions.org/questions/showthread.php?t=464069](http://www.linuxquestions.org/questions/showthread.php?t=464069)

7th post in particular

---

### Post by Z-09 on 2011-03-31
Thanks for the reply. I tried what you said and got the following:

[I]zach@ubuntu:~$ #wlanconfig ath1 create wlandev ath1 wlanmode master
zach@ubuntu:~$ wlanconfig ath1 create wlandev ath1 wlanmode master
wlanconfig: command not found
zach@ubuntu:~$ sudo wlanconfig ath1 create wlandev ath1 wlanmode master
[sudo] password for zach: 
sudo: wlanconfig: command not found
zach@ubuntu:~$ sudo wlanconfig ath1 create wlandev ath1 wlanmode master
sudo: wlanconfig: command not found
zach@ubuntu:~$ sudo wlanconfig wlan0 create wlandev wlan0 wlanmode master
sudo: wlanconfig: command not found
[/I]
Did I do something wrong? :confused:

---

### Post by bkratz on 2011-03-31
Never tried to use master mode, but went to the terminal and typed in

man iwconfig

(man gives you manual) and it refers to various modes and alway capitalizes the first letter. I know it is sensitive to capitalization, but don't know if it is required in this case, Anyway, try

sudo iwconfig <interface> mode Master

where interface in your case is wlan0.

---

### Post by vlaar on 2011-03-31
> **Z-09 said:**
> Did I do something wrong? :confused:

No, i'm sorry my mistake completely. I just assumed you had madwifi drivers installed.

Back to the problem, could you post the output of "lshw -c network"

---

### Post by Z-09 on 2011-03-31
it's ok. here you go:

[I]zach@ubuntu:~$ lshw -c network
**WARNING: you should run this program as super-user.**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:af:d8:e8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=138.47.107.174 latency=0 multicast=yes
       resources: irq:47 ioport:d000(size=256) memory:f6824000-f6824fff memory:f6820000-f6823fff memory:f6800000-f681ffff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:33:12:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f2c00000-f2c0ffff
[/I]
The warning made me nervous :w

---

### Post by Rakeshvijayan on 2011-03-31
mac@mac-System-Product-Name:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 20:cf:30:c9:10:f3
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half ip=192.168.1.2 latency=0 link=yes  multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.56.1 multicast=yes
m
ac@mac-System-Product-Name:~$
same issue In my experience ,I am using dlink DWA510. I will became mad I started to follow this issue before three days give help

---

### Post by vlaar on 2011-04-01
> **Z-09 said:**
> The warning made me nervous :w

Nothing to worry about. I dug up an old thread with exactly the same problem : [http://art.ubuntuforums.org/showthread.php?t=1549021](http://art.ubuntuforums.org/showthread.php?t=1549021)

I hope you have more luck on that one.

---

### Post by Z-09 on 2011-04-05
Sorry for the late response. I have not been able to have access to same connection.

Thanks for the help. I followed your advice on the old threads and ended up on this page:
[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)
Some of these steps were rather frustrating. Through trial and error, I finally got to "make" step listed below:

**Now find this line: **

*#CONFIG_DRIVER_NL80211=y*[B] and  uncomment it by removing the '#' sign.  Repeat for other settings that  you may be interested in.  The basic configuration, with only this line  uncommented is enough to get hostapd up and running with WPA/WPA2  authentication and encryption. 
[/B] [B]Next, compile hostapd: 

[/B]*make* 

[B]if this fails with errors like: 
[/B] 
[I]driver_nl80211.c:21:31: warning: netlink/genl/genl.h: No such file or directory
driver_nl80211.c:22:33: warning: netlink/genl/family.h: No such file or directory
driver_nl80211.c:23:31: warning: netlink/genl/ctrl.h: No such file or directory
driver_nl80211.c:24:25: warning: netlink/msg.h: No such file or directory
driver_nl80211.c:25:26: warning: netlink/attr.h: No such file or directory
[/I]**you  need to install/update libnl-1.0pre8 (or later).  If all goes well and  the compilation finishes, try the minimal hostapd again.  I'd recommend  creating a seperate hostapd.conf file with this configuration in it  called hostapd-minimal.conf, for testing use. **

However, when I did the "make" step, I ended up getting this **(SORRY i COULD NOT FIND A WAY TO WRAP THIS TEXT IN A SPOILER. I DIDN'T KNOW WHICH WAS IMPORTANT. I KNEW THE BOTTOM WAS AT LEAST)**: 
__________________________________________________________________________

[I]zach@ubuntu:~/hostapd-0.6.8/hostapd$ make
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o hostapd.o hostapd.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ieee802_1x.o ieee802_1x.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o eapol_sm.o eapol_sm.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ieee802_11.o ieee802_11.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o config.o config.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ieee802_11_auth.o ieee802_11_auth.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o accounting.o accounting.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o sta_info.o sta_info.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o wpa.o wpa.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ctrl_iface.o ctrl_iface.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o drivers.o drivers.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o preauth.o preauth.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o pmksa_cache.o pmksa_cache.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o beacon.o beacon.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o hw_features.o hw_features.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o wme.o wme.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ap_list.o ap_list.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o mlme.o mlme.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o vlan_init.o vlan_init.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o wpa_auth_ie.o wpa_auth_ie.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/eloop.o ../src/utils/eloop.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/common.o ../src/utils/common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/wpa_debug.o ../src/utils/wpa_debug.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/wpabuf.o ../src/utils/wpabuf.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/os_unix.o ../src/utils/os_unix.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/utils/ip_addr.o ../src/utils/ip_addr.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/common/ieee802_11_common.o ../src/common/ieee802_11_common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/common/wpa_common.o ../src/common/wpa_common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/radius/radius.o ../src/radius/radius.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/radius/radius_client.o ../src/radius/radius_client.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/md5.o ../src/crypto/md5.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/rc4.o ../src/crypto/rc4.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/md4.o ../src/crypto/md4.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/sha1.o ../src/crypto/sha1.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/des.o ../src/crypto/des.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/aes_wrap.o ../src/crypto/aes_wrap.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/aes.o ../src/crypto/aes.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o iapp.o iapp.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o peerkey.o peerkey.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o driver_hostap.o driver_hostap.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o driver_nl80211.o driver_nl80211.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o radiotap.o radiotap.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/l2_packet/l2_packet_linux.o ../src/l2_packet/l2_packet_linux.c
../src/l2_packet/l2_packet_linux.c: In function ‘l2_packet_get_ip_addr’:
../src/l2_packet/l2_packet_linux.c:190: warning: dereferencing pointer ‘saddr’ does break strict-aliasing rules
../src/l2_packet/l2_packet_linux.c:187: note: initialized from here
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_md5.o ../src/eap_server/eap_md5.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_tls.o ../src/eap_server/eap_tls.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_peap.o ../src/eap_server/eap_peap.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_common/eap_peap_common.o ../src/eap_common/eap_peap_common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_ttls.o ../src/eap_server/eap_ttls.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_mschapv2.o ../src/eap_server/eap_mschapv2.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_gtc.o ../src/eap_server/eap_gtc.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap.o ../src/eap_server/eap.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_common/eap_common.o ../src/eap_common/eap_common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_methods.o ../src/eap_server/eap_methods.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_identity.o ../src/eap_server/eap_identity.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/eap_server/eap_tls_common.o ../src/eap_server/eap_tls_common.c
cc -MMD -O2 -Wall -g -DHOSTAPD_DUMP_STATE -I../src -I../src/crypto -I../src/utils -I../src/common -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_IAPP -DCONFIG_RSN_PREAUTH -DCONFIG_PEERKEY -DCONFIG_DRIVER_HOSTAP -DCONFIG_DRIVER_NL80211 -DEAP_MD5 -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_SERVER -DEAP_TLS_FUNCS -DPKCS12_FUNCS -DINTERNAL_SHA256 -DCONFIG_NO_FIPS186_2_PRF -DCONFIG_NO_T_PRF -DCONFIG_IPV6   -c -o ../src/crypto/tls_openssl.o ../src/crypto/tls_openssl.c
[B]../src/crypto/tls_openssl.c:23: fatal error: openssl/ssl.h: No such file or directory
compilation terminated.
make: *** [../src/crypto/tls_openssl.o] Error 1[/B][/I]
__________________________________________________________________________

As you can see, I get that error at the end. If someone could give me a step-by-step guide to fix this error, I would be grateful. I tried searching for this error. The only sites webs offered solutions were from other languages ( :lolflag: ). Also, I tried to install/update libnl-1.0pre8, but got this:
__________________________________________________________________________

[I]zach@ubuntu:~$ sudo apt-get update libnl-1.0pre8
[sudo] password for zach: 
E: The update command takes no arguments
zach@ubuntu:~$ sudo apt-get install libnl-1.0pre8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libnl-1.0pre8
E: Couldn't find any package by regex 'libnl-1.0pre8'[/I]
__________________________________________________________________________

Thanks again.

---

### Post by Z-09 on 2011-04-07
Anyone able to help?

---

