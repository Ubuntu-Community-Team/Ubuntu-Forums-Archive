---
title: "Broadcom BCM4306 can't find wireless networks"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by mikeee99 on 2010-05-23
I am new to Ubuntu and have just installed Ubuntu 10.04 on a Dell D600. My wired network is working perfectly however, my wireless card is unable to detect wireless networks. I am using a Broadcom Corporation BCM4306 wireless card. I have updated the drivers and it is installed correctly as far as I can tell. 

My card seems to be working, but it doesn't detect any wireless networks. I know that my wireless is functioning, because I can log on successfully with a windows laptop. In addition there are 5 or 6 other networks available, so it should be able to detect something.

I am new, so please let me know what information you need and, if possible, how to find it. 

Here is the results of "lshw -C network" from the terminal below:

mikee@mikee-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a6:d0:29
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5705-v3.16 ip=192.168.1.3 latency=32 mingnt=64 multicast=yes
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:06:af:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
mikee@mikee-laptop:~$ 


Thanks!

---

### Post by mikeee99 on 2010-05-23
I think this information may help:

mikee@mikee-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
mikee@mikee-laptop:~$ 


------------------------------------------------------------------------------------------------------



mikee@mikee-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mikee@mikee-laptop:~$ 



-------------------------------------------------------------------------------------------------------


mikee@mikee-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mikee@mikee-laptop:~$ 




-------------------------------------------------------------------------------------------------------



Let me know if I need to post any more information. Thanks!

---

### Post by mikeee99 on 2010-05-24
I have been unable to resolve this issue. If someone could help me I would really appreciate it. I have posted all the info I can think of, but I am new to Ubuntu, so if you need more info, please tell me where I can find it.

Thanks in advance!

---

### Post by bkratz on 2010-05-25
> **mikeee99 said:**
> I have been unable to resolve this issue. If someone could help me I would really appreciate it. I have posted all the info I can think of, but I am new to Ubuntu, so if you need more info, please tell me where I can find it.

Thanks in advance!

If you look at this site, you will see your device mentioned as using the b43 driver.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Look under the section titled Ubuntu/Debian

Good luck

---

### Post by db654 on 2010-05-25
I've just had a similar problem with this card running ubuntu server, I've managed to get it working now. I've wrote up my steps here ([http://ubuntuforums.org/showthread.php?p=9356977#post9356977](http://ubuntuforums.org/showthread.php?p=9356977#post9356977))  

Hope it is of some use!

---

### Post by mikeee99 on 2010-05-25
I tried installing the new b43 driver, but I was already running the correct version:

mikee@mikee-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for mikee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mikee@mikee-laptop:~$


I also tried to remove the drivers and reinstall, but it had no effect.

---

### Post by mikeee99 on 2010-05-25
Thanks for the help, but I tried following the directions (skipping the server steps) and I couldn't connect to the wireless still. Here are the results:



 mikee@mikee-laptop:~$ sudo b43-fwcutter -w /lib/firmware ./broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
mikee@mikee-laptop:~$ sudo ifconfig wlan0 up
mikee@mikee-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

mikee@mikee-laptop:~$ dmesg | grep b4
[    0.122280] pci 0000:00:1f.6: reg 10 io port: [0xb400-0xb4ff]
[    0.425786] usb usb4: configuration #1 chosen from 1 choice
[    1.418580] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   22.369196] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   23.649016] Registered led device: b43-phy0::tx
[   23.649040] Registered led device: b43-phy0::rx
[   23.649063] Registered led device: b43-phy0::radio
[   23.712104] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.714507] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   23.726992] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   23.738137] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   23.960273] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
mikee@mikee-laptop:~$ 


I really appreciate you guys trying to help, but I'm at a loss as to what to do now, does any one have any ideas?

---

### Post by pdc on 2010-05-26
here is a diagnostic script for wireless

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

download it; run it; see what it tells you to do;

post back here if it does not provide answers

_____________

and in this thread

[http://ubuntuforums.org/showthread.php?t=1490717](http://ubuntuforums.org/showthread.php?t=1490717)

post #3 a guy is also talking about the 4306 and firmware

---

### Post by mikeee99 on 2010-05-27
> **pdc said:**
> here is a diagnostic script for wireless

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

download it; run it; see what it tells you to do;

post back here if it does not provide answers

_____________

and in this thread

[http://ubuntuforums.org/showthread.php?t=1490717](http://ubuntuforums.org/showthread.php?t=1490717)

post #3 a guy is also talking about the 4306 and firmware


I downloaded the script and ran it. I had a few errors, but I wasn't able to fix any of them.

                                 !!! CND0120E: Network card wlan0 has no IP address  [COLOR=Red]
[/COLOR]
[COLOR=Red]The fix for this was for SUSE and I wasn't sure how to convert it for Ubuntu[/COLOR]
 
!!! CND0490E: No access point with your SSID detected on interface wlan0
 [COLOR=Red]It told me I needed to get the updated drivers, but I already have the drivers installed.[/COLOR]
 
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually
 [COLOR=Red]There is a lot of data in the output file and I was unable to find any visible WLAN keys. In addition, I don't know how to to masquerade them manually.[/COLOR]
 

 Thanks for all the help for this Luddite newb, I am definitely learning a lot!
 

 Here is the entire output of the script: 


--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card wlan0 has no IP address
!!! CND0490E: No access point with your SSID detected on interface wlan0
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux mikee-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver 192.168.1.1
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mikee-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de]("http://www.suse.de")
Ping of [www.suse.de]("http://www.suse.de") failed
==================================================================================================================
*** lspci
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
==================================================================================================================
*** lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ac97_bus        | agpgart         | arc4            | b43             | binfmt_misc      |
| bitblit         | cfg80211        | crc_ccitt       | dcdbas          | dell_wmi         |
| drm             | drm_kms_helper  | fbcon           | font            | i2c_algo_bit     |
| intel_agp       | irda            | led_class       | lp              | mac80211         |
| output          | pcmcia_core     | ppdev           | radeon          | rsrc_nonstatic   |
| serio_raw       | shpchp          | snd_ac97_codec  | snd_intel8x0    | snd_rawmidi      |
| snd_seq_device  | snd_seq_dummy   | snd_seq_midi    | snd_seq_oss     | softcursor       |
| ssb             | tg3             | tileblit        | ttm             | vga16fb          |
| vgastate        | video           | yenta_socket    |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
==================================================================================================================
*** Actual date for bias of following greps
18:51:46 2010-05-27
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages.1:May 22 14:35:42 mikee-laptop kernel: [ 1440.582295] Registered led device: b43-phy1::radio
/var/log/messages.1:May 22 14:47:52 mikee-laptop kernel: [   22.823709] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:02:30 mikee-laptop kernel: [   22.287927] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:11:27 mikee-laptop kernel: [   22.050482] Registered led device: b43-phy0::radio
/var/log/messages.1:May 23 12:13:07 mikee-laptop kernel: [   20.955454] Registered led device: b43-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   27.829538] Registered led device: b43-phy0::radio
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May 23 12:13:51 mikee-laptop kernel: [   64.772233] b43 ssb0:0: firmware: requesting b43/ucode5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.805547] b43 ssb0:0: firmware: requesting b43/pcm5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.820222] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.834230] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.956053] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | b43                      |
| b43legacy               | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw |
| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw       |
| v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw       |
| v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                    |
| whiteheat.fw            | whiteheat_loader.fw     | yam                     | yamaha                   |
| zd1201-ap.fw            | zd1201.fw               | zd1211                  |
--- /lib/firmware
| a0g0bsinitvals5.fw      | a0g0bsinitvals9.fw      | a0g0initvals5.fw        | a0g0initvals9.fw         |
| a0g1bsinitvals13.fw     | a0g1bsinitvals5.fw      | a0g1bsinitvals9.fw      | a0g1initvals13.fw        |
| a0g1initvals5.fw        | a0g1initvals9.fw        | b0g0bsinitvals13.fw     | b0g0bsinitvals5.fw       |
| b0g0bsinitvals9.fw      | b0g0initvals13.fw       | b0g0initvals5.fw        | b0g0initvals9.fw         |
| lp0bsinitvals13.fw      | lp0bsinitvals14.fw      | lp0bsinitvals15.fw      | lp0initvals13.fw         |
| lp0initvals14.fw        | lp0initvals15.fw        | n0absinitvals11.fw      | n0bsinitvals11.fw        |
| n0initvals11.fw         | pcm5.fw                 | ucode11.fw              | ucode13.fw               |
| ucode14.fw              | ucode15.fw              | ucode5.fw               | ucode9.fw                |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
IF:wlan0 IM:2 DI:1 AP:0 FALON:1 NIC:1 cNiC:1:1 NI:1 cNI:1 NDIS:0 IP6:0 WLW:0 RTDT:debian 
[/code]

---

### Post by pdc on 2010-05-28
according to this

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

you need b43 and I see it loaded

I don't know what the problem is 

If chili555 sees this, he may be able to advise if a bug report is indicated

If you are desperate for wireless, you might be best to download another linux distro and try that: they are all free as you know; opensuse has good wireless support

---

### Post by mikeee99 on 2010-05-28
Thanks for the advice pdc. I had 9.04 installed previously, but it kept freezing. I also installed openSUSE 11.2, but the support (i.e. you awesome, helpful people:-) for Ubuntu was a lot better. So I installed Ubuntu 10.04. If I can't figure it out soon, I'll try a different one. If I don't have wireless, there's not much point in the laptop, my desktop (also with Ubuntu!) is much faster and I've been running Ubuntu on it for six months, so I'm sure it's working. 

Question though, how do I make a bug report? D600s are pretty common. I can't be the only person with this problem.

Thanks!

---

### Post by bkratz on 2010-05-28
Although a year old, there may be some help in posts 6 and 7 here.

[http://ubuntuforums.org/showthread.php?t=1134762](http://ubuntuforums.org/showthread.php?t=1134762)

---

### Post by mikeee99 on 2010-05-28
> **bkratz said:**
> Although a year old, there may be some help in posts 6 and 7 here.

[http://ubuntuforums.org/showthread.php?t=1134762](http://ubuntuforums.org/showthread.php?t=1134762)

Thanks Bkratz! that was very helpful, but it's a good news bad news situation. Now that I turned on the card with fn-f2 (I cannot believe it was just turned off all this time, I am definitely wearing my dunce cap today!) 

I am able to find all the wireless networks around including my own. But when I try to connect, even without security, I get the message:

                                 "Connection Failed: Unable to get IP address" 



I ran the script to test my wireless again from earlier and some of the errors are gone, but 2 remain. Here they are, with my problems solving them. I will paste the entire script below. Thanks for the help!



!!! CND0120E: Network card wlan0 has no IP address
[COLOR=Red]I tried following the directions, but when I entered their commands I got an error message:[/COLOR]
[COLOR=Red]
[/COLOR]
[COLOR=Red]"mikee@mikee-laptop:~/Desktop$ dhcpcd-test wlan
dhcpcd-test: command not found"[/COLOR]
[COLOR=Red]
[/COLOR]
[COLOR=Red]So I'm not sure what to do now.[/COLOR]


!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually


[COLOR=Red]I'm not sure this is really a problem I think most of the error is the IP issue.[/COLOR]


Here is the entire script output:



--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card wlan0 has no IP address
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux mikee-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mikee-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1048 (1.0 KB)  TX bytes:1048 (1.0 KB)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:fafee000-faff0000 
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de]("http://www.suse.de")
Ping of [www.suse.de]("http://www.suse.de") failed
==================================================================================================================
*** lspci
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
==================================================================================================================
*** lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ac97_bus        | agpgart         | binfmt_misc     | bitblit         | crc_ccitt        |
| dcdbas          | dell_wmi        | drm             | drm_kms_helper  | fbcon            |
| font            | i2c_algo_bit    | intel_agp       | irda            | lp               |
| ndiswrapper     | output          | pcmcia_core     | ppdev           | radeon           |
| rsrc_nonstatic  | serio_raw       | shpchp          | snd_ac97_codec  | snd_intel8x0     |
| snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi    | snd_seq_oss      |
| softcursor      | tg3             | tileblit        | ttm             | vga16fb          |
| vgastate        | video           | yenta_socket    |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
13:41:11 2010-05-28
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages.1:May 22 14:35:42 mikee-laptop kernel: [ 1440.582295] Registered led device: b43-phy1::radio
/var/log/messages.1:May 22 14:47:52 mikee-laptop kernel: [   22.823709] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:02:30 mikee-laptop kernel: [   22.287927] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:11:27 mikee-laptop kernel: [   22.050482] Registered led device: b43-phy0::radio
/var/log/messages.1:May 23 12:13:07 mikee-laptop kernel: [   20.955454] Registered led device: b43-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May 23 12:13:51 mikee-laptop kernel: [   64.772233] b43 ssb0:0: firmware: requesting b43/ucode5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.805547] b43 ssb0:0: firmware: requesting b43/pcm5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.820222] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.834230] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.956053] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | b43                      |
| b43legacy               | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| updates                 | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
--- /lib/firmware
| a0g0bsinitvals5.fw      | a0g0bsinitvals9.fw      | a0g0initvals5.fw        | a0g0initvals9.fw         |
| a0g1bsinitvals13.fw     | a0g1bsinitvals5.fw      | a0g1bsinitvals9.fw      | a0g1initvals13.fw        |
| a0g1initvals5.fw        | a0g1initvals9.fw        | b0g0bsinitvals13.fw     | b0g0bsinitvals5.fw       |
| b0g0bsinitvals9.fw      | b0g0initvals13.fw       | b0g0initvals5.fw        | b0g0initvals9.fw         |
| lp0bsinitvals13.fw      | lp0bsinitvals14.fw      | lp0bsinitvals15.fw      | lp0initvals13.fw         |
| lp0initvals14.fw        | lp0initvals15.fw        | n0absinitvals11.fw      | n0bsinitvals11.fw        |
| n0initvals11.fw         | pcm5.fw                 | ucode11.fw              | ucode13.fw               |
| ucode14.fw              | ucode15.fw              | ucode5.fw               | ucode9.fw                |
==================================================================================================================
*** ndiswrapper -l
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    ESSID:"§§§§§§§§1"
                    Quality:100/100  Signal level:-28 dBm  Noise level:-96 dBm
                    Encryption key:off
                    ESSID:"§§§§§§§§2"
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"§§§§§§§§3"
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    IE: WPA Version 1
                    ESSID:"§§§§§§§§4"
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    IE: WPA Version 1
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 FALON:1 NIC:1 cNiC:2:1 NI:1 cNI:1 NDIS:0 IP6:0 WLW:0 RTDT:debian 
[/code]

---

### Post by bkratz on 2010-05-28
A bit confused. The earlier lsmod showed b43 loaded, now I see ndiswrapper and no b43 in the latest lsmod. Did you try ndiswrapper and if so what driver did you use?

What is the output of 

ndiswrapper -l
(that is an L in lowercase)

---

### Post by mikeee99 on 2010-05-28
> **bkratz said:**
> A bit confused. The earlier lsmod showed b43 loaded, now I see ndiswrapper and no b43 in the latest lsmod. Did you try ndiswrapper and if so what driver did you use?

What is the output of 

ndiswrapper -l
(that is an L in lowercase)

When I first ran the script to test for wireless errors, it said I was running both b43 and ndiswrapper drivers in parallel and I had to un-install one of them. So I uninstalled b43 and the error was gone on the next test. Should I remove ndiswrapper and re-install b43?

I tried to run ndiswrapper -l, but it didn't do anything, nothing at all no error no script, nothing. Here is the result:

mikee@mikee-laptop:~/Desktop$ ndiswrapper -l
mikee@mikee-laptop:~/Desktop$

That's it...

I will try switching back to b43 and post the results.

---

### Post by brantney on 2010-05-28
I have an Inspiron 1525 with a similar issue.  lspci shows "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01.

I could see my wireless network, but couldn't connect.  I  changed security  from WEP to none this morning, and have been able to connect several times since then.

I don't want to run my network with no security, but there doesn't seem to be a choice right now.

---

### Post by mikeee99 on 2010-05-28
> **mikeee99 said:**
> When I first ran the script to test for wireless errors, it said I was running both b43 and ndiswrapper drivers in parallel and I had to un-install one of them. So I uninstalled b43 and the error was gone on the next test. Should I remove ndiswrapper and re-install b43?

I tried to run ndiswrapper -l, but it didn't do anything, nothing at all no error no script, nothing. Here is the result:

mikee@mikee-laptop:~/Desktop$ ndiswrapper -l
mikee@mikee-laptop:~/Desktop$

That's it...

I will try switching back to b43 and post the results.

I removed ndiswrapper and used ndiswrapper -l again. this time the results were:

mikee@mikee-laptop:~$ ndiswrapper -l
Error: ndiswrapper-utils-1.9 not installed!
mikee@mikee-laptop:~$ 

I also ran the test again and I think I am back to using b43 driver, but the other errors remain. Here is the entire script. Thanks!

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card wlan0 has no IP address
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux mikee-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mikee-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8372 (8.3 KB)  TX bytes:8372 (8.3 KB)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:fafee000-faff0000 
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de]("http://www.suse.de")
Ping of [www.suse.de]("http://www.suse.de") failed
==================================================================================================================
*** lspci
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
==================================================================================================================
*** lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ac97_bus        | agpgart         | binfmt_misc     | bitblit         | crc_ccitt        |
| dcdbas          | dell_wmi        | drm             | drm_kms_helper  | fbcon            |
| font            | i2c_algo_bit    | intel_agp       | irda            | lp               |
| ndiswrapper     | output          | pcmcia_core     | ppdev           | radeon           |
| rsrc_nonstatic  | serio_raw       | shpchp          | snd_ac97_codec  | snd_intel8x0     |
| snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi    | snd_seq_oss      |
| softcursor      | tg3             | tileblit        | ttm             | vga16fb          |
| vgastate        | video           | yenta_socket    |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
15:14:05 2010-05-28
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages.1:May 22 14:35:42 mikee-laptop kernel: [ 1440.582295] Registered led device: b43-phy1::radio
/var/log/messages.1:May 22 14:47:52 mikee-laptop kernel: [   22.823709] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:02:30 mikee-laptop kernel: [   22.287927] Registered led device: b43-phy0::radio
/var/log/messages.1:May 22 15:11:27 mikee-laptop kernel: [   22.050482] Registered led device: b43-phy0::radio
/var/log/messages.1:May 23 12:13:07 mikee-laptop kernel: [   20.955454] Registered led device: b43-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May 23 12:13:51 mikee-laptop kernel: [   64.772233] b43 ssb0:0: firmware: requesting b43/ucode5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.805547] b43 ssb0:0: firmware: requesting b43/pcm5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.820222] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.834230] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
May 23 12:13:51 mikee-laptop kernel: [   64.956053] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | b43                      |
| b43legacy               | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| updates                 | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
--- /lib/firmware
| a0g0bsinitvals5.fw      | a0g0bsinitvals9.fw      | a0g0initvals5.fw        | a0g0initvals9.fw         |
| a0g1bsinitvals13.fw     | a0g1bsinitvals5.fw      | a0g1bsinitvals9.fw      | a0g1initvals13.fw        |
| a0g1initvals5.fw        | a0g1initvals9.fw        | b0g0bsinitvals13.fw     | b0g0bsinitvals5.fw       |
| b0g0bsinitvals9.fw      | b0g0initvals13.fw       | b0g0initvals5.fw        | b0g0initvals9.fw         |
| lp0bsinitvals13.fw      | lp0bsinitvals14.fw      | lp0bsinitvals15.fw      | lp0initvals13.fw         |
| lp0initvals14.fw        | lp0initvals15.fw        | n0absinitvals11.fw      | n0bsinitvals11.fw        |
| n0initvals11.fw         | pcm5.fw                 | ucode11.fw              | ucode13.fw               |
| ucode14.fw              | ucode15.fw              | ucode5.fw               | ucode9.fw                |
==================================================================================================================
*** ndiswrapper -l
Error: ndiswrapper-utils-1.9 not installed!
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    ESSID:"§§§§§§§§1"
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"§§§§§§§§2"
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"§§§§§§§§3"
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    IE: WPA Version 1
                    ESSID:"§§§§§§§§4"
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    IE: WPA Version 1
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 FALON:1 NIC:1 cNiC:2:1 NI:1 cNI:1 NDIS:0 IP6:0 WLW:0 RTDT:debian 
[/code]

---

### Post by mikeee99 on 2010-05-28
> **brantney said:**
> I have an Inspiron 1525 with a similar issue.  lspci shows "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01.

I could see my wireless network, but couldn't connect.  I  changed security  from WEP to none this morning, and have been able to connect several times since then.

I don't want to run my network with no security, but there doesn't seem to be a choice right now.

I tried without security, but it still wouldn't connect...

---

### Post by mikeee99 on 2010-05-29
Ok, so I think we're getting closer. I am able to find the available wireless networks, but I am not able to find an IP address when I try to connect. I ran "dmesg|grep b43" and it told me that I was missing some firmware (I"ll post the whole script below. It is quite long). I followed the directions, but I found that I was already using the correct firmware, When I ran "dmesg|grep b43" I got the same result; it still told me that I was missing firmware. 

I will also post the results of the wireless test script in another post right after this, it is also very long and I want to make it easier to read.

I really appreciate you guys trying to help, I think it's getting closer. Thanks!

Here is the entire result of  "dmesg|grep b43":

mikee@mikee-laptop:~$ dmesg|grep b43
[    1.414447] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   12.294393] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   12.633401] Registered led device: b43-phy0::tx
[   12.633425] Registered led device: b43-phy0::rx
[   12.633451] Registered led device: b43-phy0::radio
[   18.596051] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.598360] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   18.609321] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   18.609411] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   18.609487] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   19.305017] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.307334] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   19.314468] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.314559] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   19.314635] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  354.637266] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  354.645859] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  354.654313] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  354.654320] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  354.654324] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  356.326884] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  356.339467] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  356.349265] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  356.349272] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  356.349277] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  369.053643] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  369.055725] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  369.064214] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  369.064221] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  369.064225] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  369.106352] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  369.114173] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  369.126790] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  369.126797] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  369.126801] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  665.530266] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  665.536299] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  665.542654] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  665.542662] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  665.542666] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  668.818508] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  668.827944] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  668.837302] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  668.837309] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  668.837313] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1341.937364] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 1341.943709] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[ 1341.955194] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[ 1341.962811] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[ 1342.088083] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1575.956286] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1576.928271] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1577.196270] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1652.620104] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1662.740116] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1957.964082] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2253.384071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2262.556283] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2263.668281] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2340.360297] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
mikee@mikee-laptop:~$

---

### Post by mikeee99 on 2010-05-29
Here is the result of my latest wireless test script:

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card wlan0 has no IP address
!!! CND0510W: Channel 4 used by your accespoint interferes with 3 adjacent access points
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux mikee-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mikee-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180448 (180.4 KB)  TX bytes:180448 (180.4 KB)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:108 (108.0 B)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de](www.suse.de)
Ping of [www.suse.de](www.suse.de) failed
==================================================================================================================
*** lspci
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
==================================================================================================================
*** lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ac97_bus        | agpgart         | arc4            | b43             | binfmt_misc      |
| bitblit         | cfg80211        | crc_ccitt       | dcdbas          | dell_wmi         |
| drm             | drm_kms_helper  | fbcon           | font            | i2c_algo_bit     |
| intel_agp       | irda            | led_class       | lp              | mac80211         |
| output          | pcmcia_core     | ppdev           | radeon          | rsrc_nonstatic   |
| serio_raw       | shpchp          | snd_ac97_codec  | snd_intel8x0    | snd_rawmidi      |
| snd_seq_device  | snd_seq_dummy   | snd_seq_midi    | snd_seq_oss     | softcursor       |
| ssb             | tg3             | tileblit        | ttm             | vga16fb          |
| vgastate        | video           | yenta_socket    |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
==================================================================================================================
*** Actual date for bias of following greps
12:59:56 2010-05-29
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
May 29 11:49:05 mikee-laptop kernel: [    9.246396] Registered led device: b43-phy0::radio
May 29 11:50:30 mikee-laptop kernel: [    9.010520] Registered led device: b43-phy0::radio
May 29 12:19:58 mikee-laptop kernel: [   12.633451] Registered led device: b43-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   12.633451] Registered led device: b43-phy0::radio
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May 29 12:52:24 mikee-laptop kernel: [ 1957.964082] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 29 12:57:19 mikee-laptop kernel: [ 2253.384071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 29 12:57:29 mikee-laptop kernel: [ 2262.556283] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 29 12:57:30 mikee-laptop kernel: [ 2263.668281] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
May 29 12:58:46 mikee-laptop kernel: [ 2340.360297] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | b43                      |
| b43legacy               | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw |
| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw       |
| v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw       |
| v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                    |
| whiteheat.fw            | whiteheat_loader.fw     | yam                     | yamaha                   |
| zd1201-ap.fw            | zd1201.fw               | zd1211                  |
--- /lib/firmware
| a0g0bsinitvals5.fw      | a0g0bsinitvals9.fw      | a0g0initvals5.fw        | a0g0initvals9.fw         |
| a0g1bsinitvals13.fw     | a0g1bsinitvals5.fw      | a0g1bsinitvals9.fw      | a0g1initvals13.fw        |
| a0g1initvals5.fw        | a0g1initvals9.fw        | b0g0bsinitvals13.fw     | b0g0bsinitvals5.fw       |
| b0g0bsinitvals9.fw      | b0g0initvals13.fw       | b0g0initvals5.fw        | b0g0initvals9.fw         |
| lp0bsinitvals13.fw      | lp0bsinitvals14.fw      | lp0bsinitvals15.fw      | lp0initvals13.fw         |
| lp0initvals14.fw        | lp0initvals15.fw        | n0absinitvals11.fw      | n0bsinitvals11.fw        |
| n0initvals11.fw         | pcm5.fw                 | ucode11.fw              | ucode13.fw               |
| ucode14.fw              | ucode15.fw              | ucode5.fw               | ucode9.fw                |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    Channel:1
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§2"
                    IE: WPA Version 1
                    Channel:1
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§3"
                    IE: WPA Version 1
                    Channel:11
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§4"
                    Channel:9
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§5"
                    Channel:4
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"§§§§§§§§1"
                    Channel:3
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§6"
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 FALON:1 NIC:1 cNiC:2:1 NI:1 cNI:1 NDIS:0 IP6:0 WLW:0 RTDT:debian 
[/code]

---

### Post by mikeee99 on 2010-05-29
Ok, one more quick update. Another good news bad news situation. I was able to actually get it to connect to my wireless network after refreshing and taking WEP off, but it worked for about 15 minutes until it started flickering and then fully disconnected. I have tried to connect again and I just get the same "Connection Failure: Unable to get IP address" message I've been getting all along. 

The thing is I didn't change anything to make it work, and when it stopped working I hadn't done anything either. I just don't understand what happened. Is there something I can check to find out what happened? Some sort of script I can run or something...

---

### Post by mikeee99 on 2010-05-30
I still haven't been able to resolve this problem. Does anyone have any ideas or know a script to run to figure out why it was working earlier, but not now?

Thanks!

---

### Post by pdc on 2010-05-31
I saw this in an earlier post you did

> 668.837313] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

so is there still a firmware problem?

I am not a wireless expert 

doubtless

[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

you have already done this

> sudo apt-get install b43-fwcutter

as I can see b43 and b43 legacy ..........??

---

### Post by mikeee99 on 2010-05-31
> **pdc said:**
> I saw this in an earlier post you did



so is there still a firmware problem?

I am not a wireless expert 

doubtless

[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

you have already done this



as I can see b43 and b43 legacy ..........??

Thanks pdc. I installed the new firmware, but it still can't get an IP address. I have already installed the b43 drivers and b43-fwcutte.

Anyone got any ideas?

Here is the script from the firmware install:

mikee@mikee-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
[sudo] password for mikee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-backports-modules-wireless-2.6.32-22-generic
The following NEW packages will be installed:
  linux-backports-modules-wireless-2.6.32-22-generic linux-backports-modules-wireless-lucid-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,956kB of archives.
After this operation, 6,009kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-backports-modules-wireless-2.6.32-22-generic 2.6.32-22.13 [1,952kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-backports-modules-wireless-lucid-generic 2.6.32.22.23 [4,024B]
Fetched 1,956kB in 5s (344kB/s)                                    
Selecting previously deselected package linux-backports-modules-wireless-2.6.32-22-generic.
(Reading database ... 146019 files and directories currently installed.)
Unpacking linux-backports-modules-wireless-2.6.32-22-generic (from .../linux-backports-modules-wireless-2.6.32-22-generic_2.6.32-22.13_i386.deb) ...
Selecting previously deselected package linux-backports-modules-wireless-lucid-generic.
Unpacking linux-backports-modules-wireless-lucid-generic (from .../linux-backports-modules-wireless-lucid-generic_2.6.32.22.23_i386.deb) ...
Setting up linux-backports-modules-wireless-2.6.32-22-generic (2.6.32-22.13) ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic

Setting up linux-backports-modules-wireless-lucid-generic (2.6.32.22.23) ...
mikee@mikee-laptop:~$

---

### Post by pdc on 2010-05-31
I wonder what the framp script says now ........

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

---

### Post by mikeee99 on 2010-06-03
> **pdc said:**
> I wonder what the framp script says now ........

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

Thanks pdc.I tried the script again, but I got exactly the same result.I tried openSUSE, but I didn't really like it. Program and function locations didn't seem to make any sense and it wasn't able to connect to my wireless either. 

What I really don't understand is that I had it working for about 15 minutes and I didn't change anything. Then it stopped and I haven't been able to get it back since. I can see not only mine, but all the wireless networks in the building and nothing works. I even took it to the coffee shop to try their wireless, but nothing...I am really at a loss.

---

### Post by JimmieC on 2010-06-04
Mikeee,

Did you manually assign an ip address to your wireless adapter? Also, are you connected to a router? You may have already answered these questions but I did not see that you manually edited your connection assigning an ip address, gateway, etc. to your wireless adapter. 

Jim

---

### Post by mikeee99 on 2010-06-05
> **JimmieC said:**
> Mikeee,

Did you manually assign an ip address to your wireless adapter? Also, are you connected to a router? You may have already answered these questions but I did not see that you manually edited your connection assigning an ip address, gateway, etc. to your wireless adapter. 

Jim

Hi Jim, I am using a Netgear WGR614v6 router for the wired and wireless network. I have not edited the IP address, because the router uses a dhcp and it works on the ethernet cable. 

If I was going to use a static IP address, how would I find out what address I should use? I don't know how to set up a static IP.

---

### Post by mikeee99 on 2010-06-13
I've got it working! There was an update installed this morning and when I tried the wireless again, it connected :-) 

There are still 2 odd things. First it won't save my WEP key, I have to enter it every time I turn the computer on. The other is that it asks me for a keyring password after I enter the WEP key; I've never entered or been asked for this password before so I have no idea what it is. I tried my sudo password, but that didn't work. I can click cancel though and it will still connect to the network anyway. 

Not a big deal really because it works now, but it is kinda weird. 

:D :D Thanks everybody for helping out. I couldn't have done it without you! :D :D

---

