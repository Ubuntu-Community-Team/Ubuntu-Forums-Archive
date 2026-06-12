---
title: "Newbie - wireless not working"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by james306 on 2011-12-11
I just installed ubuntu on an Acer Aspire 9300 (9340WSMi), all up and running aside the wireless. I open network connections and no networks are found under the wireless tab. I have had a search online, but not found anything I can really work with that works.

Here's the computers details



sudo lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c3000000-c3003fff

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Any help apreciated :)

---

### Post by praseodym on 2011-12-11
Hi,

install the packages **b43-fwcutter** and **firmware-b43-installer** from the software center via cable connection and reboot.

---

### Post by bluexrider on 2011-12-11
> **praseodym said:**
> Hi,

install the packages **b43-fwcutter** and **firmware-b43-installer** from the software center via cable connection and reboot.

I fail to understand why that isn't included in the distro. For all the issues with wireless and such?

---

### Post by james306 on 2011-12-11
I have installed the above packages, however no change. It's still not finding any wireless networks.

---

### Post by bluexrider on 2011-12-11
> **james306 said:**
> I have installed the above packages, however no change. It's still not finding any wireless networks.

did the driver get picked up by the wireless

```
sudo lshw -C network
```

---

### Post by james306 on 2011-12-11
I'm not sure, here is the response to the above command

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c3000000-c3003fff

---

### Post by bluexrider on 2011-12-11
Instead of a computer restart, in a terminal issue the following commands: 
```
sudo modprobe -r b43 ssb wl 
sudo modprobe wl
```[B]

Note:[/B] Allow several seconds for the network manager to scan for available networks before attempting a connection.

---

### Post by TBABill on 2011-12-11
> **bluexrider said:**
> Instead of a computer restart, in a terminal issue the following commands: 
```
sudo modprobe -r b43 ssb wl 
sudo modprobe wl
```[B]

Note:[/B] Allow several seconds for the network manager to scan for available networks before attempting a connection.

No, that's incorrect advice. The last command should be ```
sudo modprobe b43
``` not modprobe wl. The driver installed was the b43, which is correct in current versions of Ubuntu for the BCM4311.

---

### Post by bluexrider on 2011-12-11
> **TBABill said:**
> No, that's incorrect advice. The last command should be ```
sudo modprobe b43
``` not modprobe wl. The driver installed was the b43, which is correct in current versions of Ubuntu for the BCM4311.
I stand corrected

---

### Post by james306 on 2011-12-11
I have put in the above commands and nothing in the wireless utility, also run the following with the following response

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2011-12-11
The firmware is proprietary, this is why it is not shipped by default.

Please check:

```
dmesg | grep b43
iwconfig
rfkill list
```
If there are still error messages for missing firmware files, check this posting:

[http://ubuntuforums.org/showpost.php?p=11462422&postcount=2](http://ubuntuforums.org/showpost.php?p=11462422&postcount=2)

Unpack the firmware file as described.

---

### Post by james306 on 2011-12-11
After the commands you mentioned earlier it briefly started working, connected to the wireless network. I disconnected my Wired connection and shortly after it disconnected from the wireless and has stopped working completely again.

Results to the above commands

shelby@shelby-Aspire-9300:~$ dmesg | grep b43
[ 2339.853778] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[ 2340.004857] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 2340.131619] Registered led device: b43-phy0::tx
[ 2340.131679] Registered led device: b43-phy0::rx
[ 2340.131744] Registered led device: b43-phy0::radio
[ 2340.448066] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 2437.100061] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 2761.028100] b43-phy0: Radio hardware status changed to DISABLED
[ 2766.036138] b43-phy0: Radio hardware status changed to ENABLED
[ 2911.028080] b43-phy0: Radio hardware status changed to DISABLED
[ 2916.036074] b43-phy0: Radio hardware status changed to ENABLED
shelby@shelby-Aspire-9300:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
shelby@shelby-Aspire-9300:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2011-12-11
Ok,

check again:

```
iwlist chan
sudo iwlist scan
dmesg | grep country
```

---

### Post by TBABill on 2011-12-11
Back to the basics on this one. First ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then to activate it for the current session, just ```
sudo modprobe b43
```If it works fine after this, just make sure the other driver (wl) is blacklisted by ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the list, save and exit: ```
blacklist wl
``` To make the b43 active on every restart ```
gksudo gedit /etc/modules
``` and just add "b43" without quotes to the end of the list, save and exit.

---

### Post by james306 on 2011-12-11
iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
shelby@shelby-Aspire-9300:~$ sudo iwlist scan
[sudo] password for shelby: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

shelby@shelby-Aspire-9300:~$ dmesg | grep country

---

### Post by james306 on 2011-12-11
> **TBABill said:**
> Back to the basics on this one. First ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then to activate it for the current session, just ```
sudo modprobe b43
```If it works fine after this, just make sure the other driver (wl) is blacklisted by ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the list, save and exit: ```
blacklist wl
``` To make the b43 active on every restart ```
gksudo gedit /etc/modules
``` and just add "b43" without quotes to the end of the list, save and exit.

Tried first two steps but still no luck.

---

### Post by james306 on 2011-12-11
Scrap that, I pulled my head out of the complete newbie zone and have it working again. I have also followed your steps to blacklist the other driver so hopefully it will continue to work!

Thanks for all your help people :)

---

### Post by praseodym on 2011-12-11
You can uninstall the other driver completely via
```
sudo apt-get remove --purge bcmwl-kernel-source
```
if it is not needed.

---

### Post by UltimateCat on 2011-12-11
> **james306 said:**
> I have put in the above commands and nothing in the wireless utility, also run the following with the following response

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
"Don't give up 5 minutes before the miracle is about to happen"
I am having issues close to what your having but i am not giving up.
When I find the answer : providing I do it's yours too-
Best of Luck

---

### Post by TBABill on 2011-12-11
UltimateCat, if you create your own thread with good detail of the problem and what card you have we can sure give a fix a shot for you.

---

