---
title: "Lenove R500 wireless not working with 9.04"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by jgmillr1 on 2009-06-09
I just got my R500, partly based on user comments and reviews that the wireless worked out of the box. Not sure if Lenovo swapped in a different wireless card, but I'm having trouble getting to work.

The laptop has a switch to enable/disable the wireless. It is switched "on" and at least the bluetooth led lights and Ubuntu toggles the bluetooth icon when I switch off and on. The wireless led never lights up though. I've tried the switch and the Fn-F5 combo but that only toggles the bluetooth again. So, I'm not sure if it is an issue with the device being off or not recognized. Either way, any help is appreciated.

I can't tell what kind of wireless card is installed. Here are some relevant outputs that may help:

jgmillr1@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

jgmillr1@john-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 17ef:1003 Lenovo 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 17ef:1004 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 010: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jgmillr1@john-laptop:~$ dmesg | grep iwl
jgmillr1@john-laptop:~$

---

### Post by shanix on 2009-06-10
Can you provide the lspci -vv & the dmesg file?

Thanks,

---

### Post by w00tstock on 2009-06-11
I also am having this problem with my w500. I am gona go out on a limb and say you got the new lenovo branded bgn card.

Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device e020
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: I/O ports at 3000 [size=256]
    Region 1: Memory at f4200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>

There is also a thread on this card on the lenovo linux forums
[http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&message.id=1196](http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&message.id=1196)

---

### Post by Spicewood on 2009-06-12
I too have this exact same problem.  I did get the new lenovo branded wireless card.  Clearly I should have gotten the intel one.

From what I can tell, the new card a Realtek 8172 chip that uses the 8192se driver on vista.  I went to the Lenovo website and they did not have any realtek drivers there.  All their drivers were for some other company.  I tried to install them and they did not work (under windows).  And of course the vista drivers that came preinstalled on my machine do not work with ndiswrapper.

My next goal is to try and find some realtek drivers for XP and try them with ndiswrapper.  But I have not found any.

A pointer to some working drivers would be a great help.

---

### Post by Spicewood on 2009-06-12
I got XP drivers from the lenovo post - thanks.  I installed them with ndiswrapper and they recognize the card and everything looked good.  Unfortunately after installing/loading ndiswrapper itself no wlan0 appeared.  At this point I am at a loss.  Ndiswrapper seems to be working, but the card does not turn on and there is no network interface for it.

---

### Post by shanix on 2009-06-12
Can you provide the link for the XP driver that you found?
Also, Have you checked with the 

ifconfig -a

command? Perhaps it is just not turn on...

---

### Post by mrvklaw on 2009-06-15
I have exactly this problem with my new T500.  I was under the impression that the Thinkpad branded wireless was an Atheros chp, but they seem to have recently changed that.  

There is a discussion over at the Lenovo forums as well:  

[http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&thread.id=1195](http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&thread.id=1195)

I tried installing both the XP and Vista drivers with ndiswrapper, but it fails with some unknown symbols in the log file.

If anyone has any ideas about getting this to work, I would really appreciate it.

Output from ndiswrapper:
```
Jun 15 16:26:56 daneel kernel: [66358.875840] ndiswrapper (ntoskernel_exit:2671): object f6282220(2) was not freed, freeing it now
Jun 15 16:27:00 daneel kernel: [66363.749396] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Jun 15 16:27:01 daneel loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192se 
Jun 15 16:27:01 daneel kernel: [66363.833260] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIQueryAllData'
Jun 15 16:27:01 daneel kernel: [66363.833278] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIOpenBlock'
Jun 15 16:27:01 daneel kernel: [66363.833788] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192se'
Jun 15 16:27:01 daneel kernel: [66363.834505] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192se; check system log for messages from 'loadndisdriver'
Jun 15 16:27:01 daneel kernel: [66363.840546] usbcore: registered new interface driver ndiswrapper
```lspci -vv:

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. Device e020
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 3000 [size=256]
        Region 1: Memory at f4200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88
```

---

### Post by 1caras on 2009-07-08
I have the same chipset, Realtek 8172 on a Lenovo T400. After some tinkering trying to ndiswrapper in a winXP driver, I'm getting conflicting messages: the driver seems to have installed correctly, but it doesn't actually load.

I started by using the generic [ndiswrapper guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing Windows driver using ndisgtk (ndiswrapper graphical interface)") using the inf and sys drivers found [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72700"). Punching in ```
sudo modprobe ndiswrapper
``` gives me 

"net8192se : driver installed
device (10EC:8172) present"

but after loading, ndisgtk gives me an "Unable to see if hardware is present" message, even though it lists the driver as installed, with hardware present. iwconfig and ifconfig don't see it either.

Any ideas would of course be appreciated, or if someone can build upon this. Also, does anyone know if this chipset is to get official support in the future?

Thanks in advance...

---

### Post by mrvklaw on 2009-07-09
> **1caras said:**
> 

Any ideas would of course be appreciated, or if someone can build upon this. Also, does anyone know if this chipset is to get official support in the future?

Thanks in advance...


In your syslog, do you see any errors?  I see the following whenever I load that driver with ndiswrapper:

```
Jul  9 09:46:05 daneel loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192se 
Jul  9 09:46:05 daneel kernel: [72894.293895] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIQueryAllData'
Jul  9 09:46:05 daneel kernel: [72894.293901] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIOpenBlock'
Jul  9 09:46:05 daneel kernel: [72894.294054] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192se'
Jul  9 09:46:05 daneel kernel: [72894.294249] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192se; check system log for messages from 'loadndisdriver'
Jul  9 09:46:05 daneel kernel: [72894.296045] usbcore: registered new interface driver ndiswrapper

```

---

### Post by _az_ on 2009-07-14
I had the same error message when using the WinXP(32-Bit) drivers. The Win2k Drivers work except for Encryption.

---

### Post by 1cewolf on 2009-07-14
> **_az_ said:**
> I had the same error message when using the WinXP(32-Bit) drivers. The Win2k Drivers work except for Encryption.

Link?

---

### Post by 1caras on 2009-07-20
> **mrvklaw said:**
> In your syslog, do you see any errors?  I see the following whenever I load that driver with ndiswrapper:

```
Jul  9 09:46:05 daneel loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192se 
Jul  9 09:46:05 daneel kernel: [72894.293895] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIQueryAllData'
Jul  9 09:46:05 daneel kernel: [72894.293901] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoWMIOpenBlock'
Jul  9 09:46:05 daneel kernel: [72894.294054] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192se'
Jul  9 09:46:05 daneel kernel: [72894.294249] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192se; check system log for messages from 'loadndisdriver'
Jul  9 09:46:05 daneel kernel: [72894.296045] usbcore: registered new interface driver ndiswrapper

```

Exact same errors as you've had. Still no luck getting this to work...

> **1cewolf said:**
> Link?

I second that. Does this mean you got wireless to work with this specific chipset? And where did you pull the drivers from?

---

### Post by mjdavis on 2009-07-31
> **1caras said:**
> Exact same errors as you've had. Still no luck getting this to work...



I second that. Does this mean you got wireless to work with this specific chipset? And where did you pull the drivers from?

I just confirmed this worked as _az_  said.
The driver link is here: [http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520(www.station-drivers.com).exe]("http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520%28www.station-drivers.com%29.exe")

I used wine to extract the exe directly in linux as i didn't have a usbkey handy to copy it over.

Same ndiswrapper commands as before, brought up wlan0 (not using Ubuntu, but the latest OpenSUSE milestone).  Looks like encryption does not work, but I'll tinker a bit.

Lenovo TP T400

uname -a
Linux linux-cijc 2.6.30.2-1-default #1 SMP 2009-07-20 20:31:16 +0200 i686 i686 i386 GNU/Linux

lspci:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

ndiswrapper -l
net8192se : driver installed
        device (10EC:8172) present

[ 8433.024724] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 8433.040021] ndiswrapper: driver net8192se (Realtek Semiconductor Corp.,05/20/2009,1080.7.0520.2009) loaded
[ 8433.040604] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8433.041406] ndiswrapper 0000:03:00.0: setting latency timer to 64
[ 8433.376098] ndiswrapper: using IRQ 17
[ 8433.752147] wlan0 (ndiswrapper): not using net_device_ops yet
[ 8433.754259] wlan0: ethernet device 00:24:2c:e7:24:5a using NDIS driver: net8192se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8192SE Wireless LAN PCI-E NIC                                     ', 10EC:8172.5.conf
[ 8433.754304] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mrvklaw on 2009-07-31
> **mjdavis said:**
> I just confirmed this worked as _az_  said.
The driver link is here: [http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520(www.station-drivers.com).exe]("http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520%28www.station-drivers.com%29.exe")



Worked like a charm for me.  WPA encryption also seems to work without a hitch using network manager in Ubuntu 9.04.

Thanks so much for that link!

Sloan

---

### Post by AltF4 on 2009-07-31
I'm going to give that solution a shot on my Gentoo installation, hopefully with some kind of success.

I'll try it when I get home and I'll report back here.

If I get to the same stage as you guys I will start tinkering with the encryption as well.

---

### Post by mjdavis on 2009-07-31
> **mrvklaw said:**
> Worked like a charm for me.  WPA encryption also seems to work without a hitch using network manager in Ubuntu 9.04.

Thanks so much for that link!

Sloan

Yup, I just disabled network manager in opensuse and used the traditional ifup/ifdown setup and wpa is working for me as well.

Would like for network manager to work because I have a few locations that would like to autodetect, but I am satisfied as is.  Will try using network manager again.

---

### Post by AltF4 on 2009-07-31
I can confirm that this solution works, however I was not able to connect to my WPA personal TKIP network (this is without network manager)

I will test it on some other encrypted networks when I get the chance.

---

### Post by AltF4 on 2009-08-01
Another interesting point, it appears your out of luck if you want to use a 64 bit version of linux. The 64 bit windows drivers don't work through ndiswrapper.

---

### Post by tomth43 on 2009-08-26
Any news about the 64 bit version?

---

### Post by rubax on 2009-09-29
Any news regarding the encryption tinkering? I'm connecting to a WEP network at uni and then connecting to a PPTP VPN, which was all very easy on my old Thinkpad using network manager with the appropriate plugins, but with my new T400 I can't get it to work. Following the ndiswrapper instructions I get the card to appear in network manager, and it shows all the available networks, but it can't connect to the WEP network. The tray icon just keeps turning around with the green lights on for a while and then returns to where you have to put in the WEP key (and yes, I have tested the key elsewhere and it works on a old Thinkpad R51 with Ubuntu 9.04).

Some of you report that encryption works for you in network manager - is there any tweaking I need to do? I'm running Ubuntu 9.04 with kernel 2.6.30.5.

Any help is greatly appreciated.

---

### Post by npallett on 2009-10-22
> **tomth43 said:**
> Any news about the 64 bit version?

2. You need to download, compile and install the native Linux Realtek 8192Se 64Bit driver from the following location:

[http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)


The 32Bit version is available from here:

[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

---

### Post by mulder5_uk on 2009-10-23
has anyone been able to sort out the wireless problems. If so can you tell me because  my wireless card makes a contact with the router but it when I click on firefox it does not connect to the internet.

---

### Post by npallett on 2009-10-23
> **mulder5_uk said:**
> has anyone been able to sort out the wireless problems. If so can you tell me because  my wireless card makes a contact with the router but it when I click on firefox it does not connect to the internet.

Which method of wireless support are you using - ndiswrapper or the native rtl8192se driver ?

---

### Post by mulder5_uk on 2009-10-25
I think it's ndiswrapper

---

### Post by jubxie on 2009-11-05
I can confirm this method worked for me on my new toshiba t115-s1105 with the rtl8192se driver downloaded from the realtek website(win2000 version).:D

---

### Post by howdoesitmatter on 2009-12-01
System: Lenovo R500. Ubuntu version: 9.10 

I migrated to ubuntu from Vista a week ago. The wireless doesnt work. Ubuntu recognizes bluetooth but not the wireless. The following are the details. Hope someone can help me with what to do.

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. Device e020
Flags: bus master, fast devsel, latency 0, IRQ 11
I/O ports at 2000 [size=256]
Memory at f4300000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Subsystem: Lenovo Device 20d5
Flags: bus master, fast devsel, latency 0, IRQ 31
Memory at f4800000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: <access denied>
Kernel driver in use: tg3
Kernel modules: tg3

iwconfig gives me these results

lo no wireless extensions.

eth0 no wireless extensions.

sudo lshw -C network gave the following results:

*-network UNCLAIMED 
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:2000(size=256) memory:f4300000-f4303fff
*-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 02
serial: 00:22:68:16:29:43
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.13 ip=192.168.15.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:31 memory:f4800000-f480ffff

What I did:
I downloaded driver for 8192 from Realtek site. Located the .inf file and installed it through windows wireless drivers. Still, the wireless doesnt work.

---

### Post by howdoesitmatter on 2009-12-02
Problem solved. I used a linux 8192 driver and it worked for my realtek 8172 card.

Thanks to everyone on this thread.

---

