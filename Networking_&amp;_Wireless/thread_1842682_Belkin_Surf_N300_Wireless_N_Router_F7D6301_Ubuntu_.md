---
title: "Belkin Surf N300 Wireless N Router F7D6301/ Ubuntu 11.04/ Lenovo Z575 - Not working"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by SyncMr on 2011-09-11
Hi,
I recently installed Ubuntu11.04. I am having trouble in connecting to my wireless internet connection. Below are the details I got from various commands which might be helpful.  [B]

1 ) Machine Brand and Model (PC/Laptop)[/B]:
     ```

     Lenovo Ideapad Laptop Z575 with AMD A6 processor 
```**2 ) Wireless Brand, Model and Wireless Chipset:**
     ```
  $ lspci
  00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
  00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647
  00:01.1 Audio device: ATI Technologies Inc Device 1714
  00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
  00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
  00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
  00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
  00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
  00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
  00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
  00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
  00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
  00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
  00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
  00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
  00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
  00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
  00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
  00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
  00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
  00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
  00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
  01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
  02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
```[B]

3 ) check interface:[/B]
```

**New**
[B] $ ifconfig
  eth0      Link encap:Ethernet  HWaddr f0:de:f1:77:55:1d  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:40 Base address:0xe000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:388 errors:0 dropped:0 overruns:0 frame:0
            TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:29392 (29.3 KB)  TX bytes:29392 (29.3 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 38:59:f9:ab:f3:13  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
  [FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/B]


**Old:**~$ ifconfig
  eth0      Link encap:Ethernet  HWaddr f0:de:f1:77:55:1d  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:40 Base address:0xc000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
            TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:144432 (144.4 KB)  TX bytes:144432 (144.4 KB)
   
  iwconfig
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  wlan0     IEEE 802.11bgn  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
```[B]

4 ) Check for modules:[/B]```

 $ lsmod
  Module                  Size  Used by
  parport_pc             36959  0
  ppdev                  17113  0
  vesafb                 13761  1
  joydev                 17606  0
  binfmt_misc            17565  1
  snd_hda_codec_realtek   336693  1
  rt2860sta             543010  0
  arc4                   12529  2
  acer_wmi               23771  0
  rt2800pci              18535  0
  snd_hda_codec_hdmi     28103  1
  rt2800lib              45181  1 rt2800pci
  crc_ccitt              12667  2 rt2860sta,rt2800lib
  rt2x00pci              14322  1 rt2800pci
  rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
  snd_seq_midi           13324  0
  snd_hda_intel          33211  2
  snd_hda_codec         103804  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
  snd_hwdep              13604  1 snd_hda_codec
  psmouse                73535  0
  mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
  snd_rawmidi            30486  1 snd_seq_midi
  uvcvideo               72195  0
  snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
  snd_seq_midi_event     14899  1 snd_seq_midi
  serio_raw              13166  0
  videodev               82052  1 uvcvideo
  v4l2_compat_ioctl32    17078  1 videodev
  snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
  k10temp                13119  0
  i2c_piix4              13303  0
  snd_timer              29602  2 snd_pcm,snd_seq
  cfg80211              178528  2 rt2x00lib,mac80211
  snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
  snd                    67382  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
  eeprom_93cx6           12725  1 rt2800pci
  soundcore              12680  1 snd
  snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
  ideapad_laptop         13494  0
  sparse_keymap          13898  2 acer_wmi,ideapad_laptop
  video                  19438  0
  lp                     17825  0
  parport                46458  3 parport_pc,ppdev,lp
  ahci                   25951  3
  libahci                26642  1 ahci
  r8169                  48022  0
```[B]

5) Network configuration[/B]:```

[B]New:

  sudo lshw -C network
    *-network               
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: eth0
         version: 05
         serial: f0:de:f1:77:55:1d
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:40 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
    *-network
         description: Wireless interface
         product: RT3090 Wireless 802.11n 1T/1R PCIe
         vendor: Ralink corp.
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: wlan0
         version: 00
         serial: 38:59:f9:ab:f3:13
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
  [FONT=&quot]       resources: irq:18 memory:f0100000-f010ffff[/FONT][/B]  


**Old:**
sudo lshw -C network
  [sudo] password for prag:
    *-network               
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: eth0
         version: 05
         serial: f0:de:f1:77:55:1d
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:40 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
    *-network DISABLED
         description: Wireless interface
         product: RT3090 Wireless 802.11n 1T/1R PCIe
         vendor: Ralink corp.
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: wlan0
         version: 00
         serial: 38:59:f9:ab:f3:13
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
         resources: irq:18 memory:f0100000-f010ffff
```**6) Scan for networks:**```

 iwlist scan
   
  wlan0     Failed to read scan data : Network is down
```[B]
7) Ubuntu Version: [/B]```

 lsb_release -d
  Description:     Ubuntu 11.04
```[B]
  
8. Kernel/architecture (including 32 vs. 64 bit): [/B]
```
uname -mr
  2.6.38-8-generic x86_64
```[B]

9) Restarting the network:[/B]```

  sudo /etc/init.d/networking restart
   * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
   * Reconfiguring network interfaces...

```But my internet works fine with Windows 7 which is the other OS in my laptop. Kindly help me in solving this problem. Thanks in advance.

---

### Post by SyncMr on 2011-09-13
gentle bounce...

---

### Post by psrdotcom on 2011-09-13
I think you need to install the drivers manually.

---

### Post by pdc on 2011-09-13
have a read at this guide;

it seems the most detailed around

[http://www.techytalk.info/ralink-rt3090-ubuntu-driver-ppa/](http://www.techytalk.info/ralink-rt3090-ubuntu-driver-ppa/)

(I understand that from 2.6.38 version, the driver is included in the kernel)

let us know how it goes;

---

### Post by fdrake on 2011-09-13
before playing around with the drivers can youn please post the results of:

```

sudo ifconfig wlan0 up 
rfkill list all
nm-tool

```

from the following results that you posted it looks like your card is switched in "OFF" mode.
> 
  [COLOR="Red"]_**  *-network DISABLED**_[/COLOR]
         description: Wireless interface
         product: RT3090 Wireless 802.11n 1T/1R PCIe

......
  wlan0     Failed to read scan data : [COLOR="Red"]**_Network is down_**[/COLOR]



---

### Post by praseodym on 2011-09-13
There are two drivers loaded rt2860sta and rt2800pci, the latter is in better development right now. Unload both, reload the right one, and blacklist the wrong one:

```
echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf rt2860sta rt2800pci
sudo modprobe -v rt2800pci
```
This
> ```
wlan0     IEEE 802.11bgn  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]off[/COLOR]   
```
means, that there is a button/switch, etc, the card is "off". Also check the BIOS settings.

Please show:

```
rfkill list
```

---

### Post by SyncMr on 2011-09-13
Thanks a lot for your reply. Unfortunately my wireless was off. Sorry for not checking that. 



I have edited my original post(ifconfig and sudo lshw -C network) with updated results after ensuring that the wireless is On.Here are the outputs of few other commands. Kindly help me in fixing this.  

**iwlist scan:**

```
$ iwlist scan
  lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     No scan results
```

**ifconfigand rfkill**
```
sudo ifconfig wlan0 up
  unnamed:~$
  unnamed:~$ rfkill list all
  0: ideapad_wlan: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  1: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  2: acer-wireless: Wireless LAN
              Soft blocked: yes
              Hard blocked: no

```

**nm-tool**

```
nm-tool
   
  NetworkManager Tool
   
  State: disconnected
   
  - Device: eth0 -----------------------------------------------------------------
    Type:              Wired
    Driver:            r8169
    State:             unavailable
    Default:           no
    HW Address:        F0:DE:F1:77:55:1D
   
    Capabilities:
      Carrier Detect:  yes
      Speed:           10 Mb/s
   
    Wired Properties
      Carrier:         off
   
   
  - Device: wlan0 ----------------------------------------------------------------
    Type:              802.11 WiFi
    Driver:            rt2800pci
    State:             unavailable
    Default:           no
    HW Address:        38:59:F9:AB:F3:13
   
    Capabilities:
   
    Wireless Properties
      WEP Encryption:  yes
      WPA Encryption:  yes
      WPA2 Encryption: yes
   
    Wireless Access Points
```

---

### Post by fdrake on 2011-09-13
cab you try:
```

sudo rfkill unblock all

```
and see if there is any improvement. you may need to reboot. if nothing happens try to follow praseodym steps.

---

### Post by praseodym on 2011-09-13
Try

```
sudo rfkill unblock all
```
You may unload the module acer_wmi:

```
sudo rmmod acer_wmi
```

---

### Post by SyncMr on 2011-09-13
Thanks for your quick replies. Even after trying these steps, the problem remains. After executing the commands, i rebooted to machine and still unable to connect to internet. 

I am yet to try post 4 and post 6 by pdc and praseodym. Just want to update you with the results after turning on the wireless.

---

### Post by pdc on 2011-09-13
praseodym is right: **do as he says**: 

you have two drivers available;

**You will not have wireless with two drivers competing**.........

.....do as prasedym told you to do: blacklist rt2860sta as he said below

> echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf rt2860sta rt2800pci
sudo modprobe -v rt2800pci



and after doing that, I think you should again tell the forum what you get with 

> rfkill list all

if all is unblocked, you should be able to configure;

if not repeat the commands and copy and paste the results back to the forum

---

### Post by SyncMr on 2011-09-14
Here are the results
```

**echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf**
blacklist rt2860sta

**sudo modprobe -rf rt2860sta rt2800pci**
network disconnected you are offline
    
 **sudo modprobe -v rt2800pci**
  insmod /lib/modules/2.6.38-8-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/net/wireless/cfg80211.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/net/mac80211/mac80211.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/lib/crc-ccitt.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
  insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
  

   
  **rfkill list all**
  0: ideapad_wlan: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  2: acer-wireless: Wireless LAN
              Soft blocked: yes
              Hard blocked: no
  3: phy0: Wireless LAN
              Soft blocked: no
  [FONT=&quot]            Hard blocked: no[/FONT]


```

But acer wireless is softblocked..

---

### Post by praseodym on 2011-09-15
Try 

```
sudo rfkill unblock all
```
If it doesnt work, unload the module

```
sudo rmmod acer_wmi
```

---

### Post by fdrake on 2011-09-15
after you have done the commands in the previous post (you may need to reboot for the last one to take effect) in case of negative results, can you post the outputs of

```

less /etc/modprobe.d/blacklist.conf | grep rt28
more /var/log/* | grep rfkill | tail -100

```

---

### Post by SyncMr on 2011-09-15
even after rebooting everything seems the same. :( 
```

 **$ less /etc/modprobe.d/blacklist.conf | grep rt28**
  blacklist rt2860
  blacklist rt2860sta

**prag@prag-Ideapad-Z575:~$ more /var/log/* | grep rfkill | tail -100**
  Sep 15 11:53:09 prag-Ideapad-Z575 sudo:     prag : TTY=pts/0 ; PWD=/home/prag ; USER=root ; COMMAND=/usr/sbin/rfkill unblock all
  2011-04-25 23:00:15 install rfkill <none> 0.4-1
  2011-04-25 23:00:15 status half-installed rfkill 0.4-1
  2011-04-25 23:00:15 status unpacked rfkill 0.4-1
  2011-04-25 23:00:15 status unpacked rfkill 0.4-1
  2011-04-25 23:05:48 configure rfkill 0.4-1 <none>
  2011-04-25 23:05:48 status unpacked rfkill 0.4-1
  2011-04-25 23:05:48 status half-configured rfkill 0.4-1
  2011-04-25 23:05:48 status installed rfkill 0.4-1
  Sep 14 18:18:51 prag-Ideapad-Z575 NetworkManager[535]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 14 18:18:51 prag-Ideapad-Z575 NetworkManager[535]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 14 18:18:52 prag-Ideapad-Z575 NetworkManager[535]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 14 18:20:55 prag-Ideapad-Z575 NetworkManager[535]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1 disappeared
  Sep 14 18:21:40 prag-Ideapad-Z575 NetworkManager[535]: <info> found WiFi radio killswitch rfkill3 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill3) (driver <unknown>)
  Sep 14 18:31:59 prag-Ideapad-Z575 NetworkManager[671]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 14 18:31:59 prag-Ideapad-Z575 NetworkManager[671]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 14 18:31:59 prag-Ideapad-Z575 NetworkManager[671]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 15 11:17:31 prag-Ideapad-Z575 NetworkManager[577]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 15 11:17:32 prag-Ideapad-Z575 NetworkManager[577]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 15 11:17:32 prag-Ideapad-Z575 NetworkManager[577]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 15 11:53:20 prag-Ideapad-Z575 NetworkManager[577]: <info> radio killswitch /sys/devices/platform/acer-wmi/rfkill/rfkill2 disappeared
  Sep 15 11:54:30 prag-Ideapad-Z575 NetworkManager[609]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 15 11:54:30 prag-Ideapad-Z575 NetworkManager[609]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 15 11:54:30 prag-Ideapad-Z575 NetworkManager[609]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 11 09:35:19 prag-Ideapad-Z575 NetworkManager[796]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 11 09:35:19 prag-Ideapad-Z575 NetworkManager[796]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 11 09:35:19 prag-Ideapad-Z575 NetworkManager[796]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 11 18:30:27 prag-Ideapad-Z575 NetworkManager[713]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 11 18:30:27 prag-Ideapad-Z575 NetworkManager[713]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 11 18:30:27 prag-Ideapad-Z575 NetworkManager[713]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 13 08:38:50 prag-Ideapad-Z575 NetworkManager[595]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 13 08:38:50 prag-Ideapad-Z575 NetworkManager[595]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 13 08:38:50 prag-Ideapad-Z575 NetworkManager[595]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 13 10:04:37 prag-Ideapad-Z575 NetworkManager[785]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill1) (driver ideapad_acpi)
  Sep 13 10:04:37 prag-Ideapad-Z575 NetworkManager[785]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
  Sep 13 10:04:37 prag-Ideapad-Z575 NetworkManager[785]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 13 10:12:38 prag-Ideapad-Z575 NetworkManager[711]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 13 10:12:38 prag-Ideapad-Z575 NetworkManager[711]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 13 10:12:38 prag-Ideapad-Z575 NetworkManager[711]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 13 11:04:52 prag-Ideapad-Z575 NetworkManager[606]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 13 11:04:52 prag-Ideapad-Z575 NetworkManager[606]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  Sep 13 11:04:52 prag-Ideapad-Z575 NetworkManager[606]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 13 12:03:10 prag-Ideapad-Z575 NetworkManager[606]: <info> radio killswitch /sys/devices/platform/acer-wmi/rfkill/rfkill2 disappeared
  Sep 13 12:04:45 prag-Ideapad-Z575 NetworkManager[617]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 13 12:04:45 prag-Ideapad-Z575 NetworkManager[617]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 13 12:04:45 prag-Ideapad-Z575 NetworkManager[617]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 14 07:43:21 prag-Ideapad-Z575 NetworkManager[721]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 14 07:43:21 prag-Ideapad-Z575 NetworkManager[721]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
  Sep 14 07:43:21 prag-Ideapad-Z575 NetworkManager[721]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
  Sep 14 17:50:09 prag-Ideapad-Z575 NetworkManager[696]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
  Sep 14 17:50:09 prag-Ideapad-Z575 NetworkManager[696]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
  Sep 14 17:50:09 prag-Ideapad-Z575 NetworkManager[696]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (driver acer-wmi)
  KERNEL[1316112869.719014] add      /devices/virtual/misc/rfkill (misc)
  DEVPATH=/devices/virtual/misc/rfkill
  DEVNAME=rfkill
  KERNEL[1316112869.863841] add      /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  KERNEL[1316112869.864299] change   /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  UDEV  [1316112869.965043] add      /devices/virtual/misc/rfkill (misc)
  DEVPATH=/devices/virtual/misc/rfkill
  DEVNAME=/dev/rfkill
  UDEV  [1316112870.090416] add      /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  UDEV  [1316112870.091035] change   /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  KERNEL[1316112870.149170] add      /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
  DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
  SUBSYSTEM=rfkill
  KERNEL[1316112870.149638] change   /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  UDEV  [1316112870.158273] change   /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0 (rfkill)
  DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/PNP0C09:00/VPC2004:00/rfkill/rfkill0
  SUBSYSTEM=rfkill
  UDEV  [1316112870.158297] add      /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
  DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
  SUBSYSTEM=rfkill
  KERNEL[1316112870.194680] change   /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
  DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
  SUBSYSTEM=rfkill
  UDEV  [1316112870.195199] change   /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
  DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
  SUBSYSTEM=rfkill
  KERNEL[1316112870.213237] add      /devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2 (rfkill)
  DEVPATH=/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2
  SUBSYSTEM=rfkill
  KERNEL[1316112870.213374] change   /devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2 (rfkill)
  DEVPATH=/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2
  SUBSYSTEM=rfkill
  UDEV  [1316112870.242973] add      /devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2 (rfkill)
  DEVPATH=/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2
  SUBSYSTEM=rfkill
  UDEV  [1316112870.243383] change   /devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2 (rfkill)
  DEVPATH=/devices/pci0000:00/0000:00:06.0/0000:02:00.0/ieee80211/phy0/rfkill2
  [FONT=&quot]SUBSYSTEM=rfkill[/FONT] 
```

---

### Post by fdrake on 2011-09-15
can you run this :
```

sudo modprobe -r acer-wmi
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rm -R /sys/devices/platform/acer-wmi/*
sudo modprobe -r ideapad_laptop
sudo modprobe -v ideapad_laptop

```
reboot
```

sudo rfkill unblock all

```
if the problem still persists post results for 
```

rfkill list all
lsmod
less /etc/modprobe.d/blacklist.conf

```

---

### Post by SyncMr on 2011-09-15
Here are the resutls.
```

 sudo modprobe -r acer-wmi
  [sudo] password for prag:
  prag@prag-Ideapad-Z575:~$
  prag@prag-Ideapad-Z575:~$ echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
  blacklist acer-wmi
  prag@prag-Ideapad-Z575:~$
  prag@prag-Ideapad-Z575:~$ sudo rm -R /devices/platform/acer-wmi/*
  rm: cannot remove `/devices/platform/acer-wmi/*': No such file or directory
  prag@prag-Ideapad-Z575:~$
  prag@prag-Ideapad-Z575:~$ sudo modprobe -r ideapad_acpi
  FATAL: Module ideapad_acpi not found.
  prag@prag-Ideapad-Z575:~$ sudo modprobe -v ideapad_acpi
  FATAL: Module ideapad_acpi not found.
  

```

And I am unable to find devices folder. Should I try some different commands as ideapad_acpi is not found. Would you like to see results of any other commands.?

---

### Post by fdrake on 2011-09-15
i checked my commands and i found that there was typo error. i have already fixed the path and names, can you try again.

---

### Post by SyncMr on 2011-09-15
I did a kernel upgrade by following the link, [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

The kernel upgrade ended up with Black screen. [IMG]http://www.thinkdigit.com/forum/images/smilies/icon_sad.gif[/IMG]  I installed Linux 3.0 kernel image, module init tools and procps. Then  did a reboot and chose ubuntu in bootloader. After that am stuck with  black screen.

So I logged into the earlier kernel version of ubuntu to recover from the blackscreen and found that **Wireless network works**. [IMG]http://www.thinkdigit.com/forum/images/smilies/icon_smile.gif[/IMG]

Now shall I proceed with removing the older kernel (as internet is working  here).? Will the wireless connection work in the upgraded kernel too.?

---

### Post by fdrake on 2011-09-15
> **SyncMr said:**
> I did a kernel upgrade by following the link, [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

The kernel upgrade ended up with Black screen. [IMG]http://www.thinkdigit.com/forum/images/smilies/icon_sad.gif[/IMG]  I installed Linux 3.0 kernel image, module init tools and procps. Then  did a reboot and chose ubuntu in bootloader. After that am stuck with  black screen.

So I logged into the earlier kernel version of ubuntu to recover from the blackscreen and found that **Wireless network works**. [IMG]http://www.thinkdigit.com/forum/images/smilies/icon_smile.gif[/IMG]

Now shall I proceed with removing the older kernel (as internet is working  here).? Will the wireless connection work in the upgraded kernel too.?
make sure you install backposrts package first this should prevent the kernel upgrade from editing your wireless modules
```

sudo apt-get install --reinstall linux-backports-modules-wireless-generic

```

i am a little bit confused how did you exactly managed to fix the problem? what did you do?

---

### Post by SyncMr on 2011-09-15
But I have already done the kernel upgrade. I thought of upgrading the kernel and giving it a try. After that when I logged into the older kernel version, my wireless popped up stating that wireless connection are available. I was able to connect successfully. 

But the internet is very very slow. It is proceeding in bytes per second. And frequently am getting Problem loading page. 

And I am still unable to log into the upgraded kernel. Wondering if I should remove the earlier kernel version as internet works fine here.

---

### Post by fdrake on 2011-09-15
i don't think the problem has nothing to do with the old kernel but you can try this
login into your old kernel and run
```

sudo aptitude purge linux-image-3.0-1-generic linux-headers-3 linux-image-3 
echo "deb http://archive.ubuntu.com/ubuntu natty-backports main universe multiverse restricted" |tee >> /etc/apt/sources.list
sudo aptitude update && sudo aptitude upgrade

```
then upgrade again the kernel to 3 if you wish. This time you should be able to login normally.

---

### Post by SyncMr on 2011-09-15
Now am not able to connect to internet. i.e.Am able to see the wireless connections. On giving connect, the wifi icon on the top right keeps connecting and prompts for password. I am giving the exact password but in vain. And not able to browse internet.

---

### Post by fdrake on 2011-09-15
> **SyncMr said:**
> Now am able to connect to internet. i.e.Am able to see the wireless connections. But not able to browse internet.

are you using the new kernel, right?
edit: i edited after seeing your edit... so there is a problem with the password. are you able to connect to an open network?
can you post the result for

```

nm-tool
sudo iwlist scan 
less /var/log/syslog | grep -i network | tail -100

```

also with a wire connection can you install the following package
```

sudo aptitude install wpasupplicant

```

---

