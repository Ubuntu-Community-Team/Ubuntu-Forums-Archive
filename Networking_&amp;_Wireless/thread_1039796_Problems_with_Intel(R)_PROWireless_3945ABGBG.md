---
title: "Problems with Intel(R) PRO/Wireless 3945ABG/BG"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Filipe C on 2009-01-14
Hello, 
I have a problem with my notebook, 
I use a Packard Bell MX65-004 but my wireless doesn´t work,
when i used Ubuntu 7.10 the wireless worked fine e could connect to any wireless network even the button on/of worked just great!!
Now i have installed Ubuntu 8.10 Intrepid works fine, but the wireless doesn´t work. 

[COLOR="Red"][U]**I don´t now if is a problem or if is the little experience that i have with Ubuntu**
[/U][/COLOR]
The wireless networks is detected but i can´t enter the wireless network, if it´s open when i click in the network it doesn´t enter,
after a wile says: could not enter the network, 
if i use a network with WPA2 after i click to enter in the wireless network after a while shows the dialog box
to enter the password i do that and after a time it appears the same dialog box again, 
and the password doesn´t stay memorized in the wireless network that i created.

Sorry about my english :)


This is the result of some commmands:

> lipec@bell-laptop:~$ uname -a

Linux bell-laptop 2.6.27-11-generic i686 GNU/Linux 

> lipec@bell-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
[COLOR="Red"][B]03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
[/B][/COLOR]06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 

> lipec@bell-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:56:3a:db:80
                    ESSID:"PT-WIFI"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=96/100  Signal level:-30 dBm  Noise level=-127 dBm
                    Encryption key: off
                    IE: Unknown: 000750542D57494649
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 050400020000
                    IE: Unknown: 0706505420010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 32023048
                    IE: Unknown: DD1600409604000706A4000022A400004143000061320000
                    IE: Unknown: DD050040960301

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:tsf=0000001db4957181
                    Extra: Last beacon: 204ms ago

pan0      Interface doesn't support scanning. 

> lipec@bell-laptop:~$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:13:02:de:9b:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


> lipec@bell-laptop:~$ dmesg | grep Network

[19.689544] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks 


> lipec@bell-laptop:~$ dmesg | grep iwl

[   19.998069] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.998081] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.998258] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.998279] iwl3945 0000:03:00.0: setting latency timer to 64
[   20.060412] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   20.060424] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   20.126017] iwl3945 0000:03:00.0: PCI INT A disabled
[   20.148707] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   37.240647] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.240797] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   37.241089] firmware: requesting iwlwifi-3945-2.ucode
[   37.955414] iwl3945 0000:03:00.0: iwlwifi-3945-2.ucode firmware file req failed: -2
[   37.955418] firmware: requesting iwlwifi-3945-1.ucode
[   38.001037] iwl3945 0000:03:00.0: Loaded firmware iwlwifi-3945-1.ucode, which is deprecated.  Please use API v2 instead.
[   38.001042] iwl3945 0000:03:00.0: Firmware has old API version. Expected 2, got 1. New firmware can be obtained from [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org).
[   38.001046] iwl3945 0000:03:00.0: loaded firmware version 2.14.1.5
[   38.050482] Registered led device: iwl-phy0:radio
[   38.050507] Registered led device: iwl-phy0:assoc
[   38.050574] Registered led device: iwl-phy0:RX
[   38.050595] Registered led device: iwl-phy0:TX 


> lipec@bell-laptop:~$ dmesg | grep iwl3945

[   19.689544] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.689555] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.689719] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.689741] iwl3945 0000:03:00.0: setting latency timer to 64
[   19.750466] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.750479] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.751858] iwl3945 0000:03:00.0: PCI INT A disabled
[   36.589661] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   36.589810] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   36.666989] iwl3945 0000:03:00.0: iwlwifi-3945-2.ucode firmware file req failed: -2
[   36.702594] iwl3945 0000:03:00.0: Loaded firmware iwlwifi-3945-1.ucode, which is deprecated.  Please use API v2 instead.
[   36.702605] iwl3945 0000:03:00.0: Firmware has old API version. Expected 2, got 1. New firmware can be obtained from [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org).
[   36.702613] iwl3945 0000:03:00.0: loaded firmware version 2.14.1.5 


> lipec@bell-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:de:9b:6f
       width: 32 bits

       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg 


I appreciate any help that anyone can give me

Thanks........

---

### Post by utnubuuser on 2009-01-15
Hi -- Not sure as to a solution for ya,  but it sounds like a key-ring issue rather than the network-manager.
Had a similar problem for a while in 7.04.  If you click on the network icon, then select the network you want to connect to,  does it accept your password/key?

---

### Post by Filipe C on 2009-01-15
> **utnubuuser said:**
> Hi -- Not sure as to a solution for ya,  but it sounds like a key-ring issue rather than the network-manager.
Had a similar problem for a while in 7.04.  If you click on the network icon, then select the network you want to connect to,  does it accept your password/key?

Hello, thanks for help me,
I have created in network-manager my network with the name e password and the type of password, and when i click it start to connect after a few time shows the dialog box to write the password again i do that, but a few time later appears again the same dialog box always the same thing, i don´t now what to do and i use wireless networks most of the time and i don´t want to continuing using Winxp to access the wireless i realy prefer ubuntu.

I can´t use the driver of ubuntu 7.10 for my intel? I think that the driver was ipw3945 not iwl3945
When i useded it appears on the restricted drivers along with the Nvidia and it worked just fine whithout any problems.

---

### Post by utnubuuser on 2009-01-15
If you're getting a wireless symbol in your top panel, the little blue bars, then you wireless driver is probably ok, and you've got one of your settings wrong, ie. wrong type of network,(wep instead of wap), maybe a spelling error.
have a look through System>>Administration>>Authorizations.

I had this axact same problem some while ago, but in my case it was a simple matter of having changed passwords, and then forgot that I'd made a change. Are you seeing the password when you enter it, to make sure you're using the right password?

---

### Post by Filipe C on 2009-01-15
Yes, i see the password when the dialog box open i see a pass that has nothing to the one i have. i clean the same and i put mine, but when the dialog box open again the pass that appears is diferent i don't know why but the pass doesn't memorize.

---

### Post by Noccy on 2010-04-25
My apologies for the gravedigging but I believe I just sorted this issue on a Packard Bell EasyNote. The WiFi led doesn't light up any more, but I am at last able to connect to my wireless.

The solution was in that "asus_laptop" was loaded. Adding it to the modprobe.d blacklist and restarting did the trick.

Just thought I'd share this, as I've been looking for this solution myself for days, and all I've found is more people with the same problem.

---

