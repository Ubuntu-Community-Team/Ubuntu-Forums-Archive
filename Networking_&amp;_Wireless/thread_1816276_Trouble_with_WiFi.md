---
title: "Trouble with WiFi"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by doylerules23 on 2011-08-01
Just to start off, this is my first time using ubuntu, so i'm not really sure what i'm doing. I just installed ubuntu 11.04 on a Dell Inspiron 1150 (old crappy computer so i figured i would try ubuntu on it) and i'm having difficulty connecting with wireless. When i go to select a wireless network, it says "device not ready (firmware missing). When i was running windows, it would connect fine with wireless so anyone have any ideas?

Thanks!

---

### Post by bkratz on 2011-08-01
> **doylerules23 said:**
> Just to start off, this is my first time using ubuntu, so i'm not really sure what i'm doing. I just installed ubuntu 11.04 on a Dell Inspiron 1150 (old crappy computer so i figured i would try ubuntu on it) and i'm having difficulty connecting with wireless. When i go to select a wireless network, it says "device not ready (firmware missing). When i was running windows, it would connect fine with wireless so anyone have any ideas?

Thanks!



First we need to find out what wireless card you have in order to find a direction.  find the terminal in 11.04 and enter the following one at a time. copy/paste the outputs back here by clicking on new reply and click # and paste the information between the brackets.

lspci -nn | grep 0280

lsmod

iwconfig

rfkill list all

By the way those a L's lowercase not 1'S!

---

### Post by doylerules23 on 2011-08-01
```
 
matt@matt-Inspiron-1150:~$ lspci -nn | grep 0280
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
matt@matt-Inspiron-1150:~$ 
matt@matt-Inspiron-1150:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   296610  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
joydev                 17322  0 
i915                  450944  2 
drm_kms_helper         40745  1 i915
drm                   180037  2 i915,drm_kms_helper
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
lp                     13349  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                36746  3 parport_pc,ppdev,lp
dcdbas                 14054  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
b44                    35301  0 
ssb                    45942  2 b43,b44
matt@matt-Inspiron-1150:~$ 
matt@matt-Inspiron-1150:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
matt@matt-Inspiron-1150:~$ 
matt@matt-Inspiron-1150:~$ rfkill list all


```

---

### Post by nm_geo on 2011-08-01
Hi,

bkratz does not seem to be around right now.

You can go to Synaptic in the search box type_ bcm_ and install b43-fwcutter and firmware-b43-installer. (all you need is those two).

Or open a terminal Ctrl-Alt-T

```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```Reboot without ethernet cable .. Assign your wireless   Let us know how it goes.

---

### Post by bkratz on 2011-08-02
> **nm_geo said:**
> Hi,

bkratz does not seem to be around right now.

You can go to Synaptic in the search box type_ bcm_ and install b43-fwcutter and firmware-b43-installer. (all you need is those two).

Or open a terminal Ctrl-Alt-T

```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```Reboot without ethernet cable .. Assign your wireless   Let us know how it goes.



No, went to bed!  Thanks for taking care of it for me. To the OP, it should work, when it does, be sure to return and mark the thread as solved in case it helps someone else.

---

### Post by doylerules23 on 2011-08-02
I did that but it didn't work. Here is what it said: 
```

matt@matt-Inspiron-1150:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter


```

---

### Post by bkratz on 2011-08-02
> **doylerules23 said:**
> I did that but it didn't work. Here is what it said: 
```

matt@matt-Inspiron-1150:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter


```


Were you plugged into a wired connection when you tried?

---

### Post by doylerules23 on 2011-08-02
I tried with a wired connection and without a wired connection. It didn't work both times.

---

### Post by bkratz on 2011-08-03
> **doylerules23 said:**
> I tried with a wired connection and without a wired connection. It didn't work both times.



If you can access synaptic package manager, you can install them there.

---

### Post by doylerules23 on 2011-08-03
Sorry for the inconvenience and my stupidity, but could you give me detailed instructions on how to do that?

---

### Post by bkratz on 2011-08-03
> **doylerules23 said:**
> Sorry for the inconvenience and my stupidity, but could you give me detailed instructions on how to do that?

Copied this from someone elses post since I run 10.04 and mine would look different. Anyway, this is what you should see--just put a tick in the ones previously mentioned and then Apply.  Don't mark any others and remove any that are not correct.

Just look at the first and third ignore any of the ones that are not related to bcm or b43.

---

### Post by westie457 on 2011-08-03
If bkratz advice does not work for you I would be very surprised because it is correct.

Only sticking my 2 cents in with an alternative.

Boot into your normal system stick the cd in the tray. Open the File Browser > name of cd > pool > main > b > b43-fwcutter

Double click on the .deb package in the folder and the Software Centre will install it for you.

---

### Post by nm_geo on 2011-08-03
> **doylerules23 said:**
> Sorry for the inconvenience and my stupidity, but could you give me detailed instructions on how to do that?

Can we assume that you are responding to this thread with wired connection on the Dell Laptop you mentioned running Ubuntu 11.04?  
If so, you might need to do the following:

```
sudo apt-get update && sudo apt-get upgrade
```

You will have a large number of updates.. so be patient.

Then you are ready to install the 
b43-fwcutter & firmware-b43-installer

---

### Post by westie457 on 2011-08-04
> **bkratz said:**
> Copied this from someone elses post since I run 10.04 and mine would look different. Anyway, this is what you should see--just put a tick in the ones previously mentioned and then Apply.  Don't mark any others and remove any that are not correct.

Just look at the first and third ignore any of the ones that are not related to bcm or b43.

The screenshot that bkratz posted is really one of mine, thanks for the plug.

For the OP look carefully at the screenshot. The mouse pointer is resting on the package you need. You do not need the firmware-b43-installer for your card. You actually need to install firmware-b43legacy-installer.

```
sudo apt-get install firmware-b43legacy-installer
```

---

### Post by nm_geo on 2011-08-04
> **westie457 said:**
> The screenshot that bkratz posted is really one of mine, thanks for the plug.
 
For the OP look carefully at the screenshot. The mouse pointer is resting on the package you need. You do not need the firmware-b43-installer for your card. You actually need to install firmware-b43legacy-installer.
 
```
sudo apt-get install firmware-b43legacy-installer
```
 
Please visit this link westie.
 
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 
The firmware for the BCM4306 is depent on the Rev (2) or Rev (3)
 
The 
 firmware-b43-installer 
is correct for his revision and chipset.

---

### Post by doylerules23 on 2011-08-04
I tried typing "bcm" into synaptic manager and nothing seemed to be showing up.
I installed b43-fwcutter from the cd like you said, restarted the computer, but it still didn't work.
I also did all of the updates and still no luck.

---

### Post by lkjoel on 2011-08-05
Could you give us the output of these Terminal commands?
```
nm-tool
uname -a
lspci -vvnn
lsb_release -a

```

---

### Post by doylerules23 on 2011-08-07
```
 
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:0F:1F:28:0E:3B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             68.237.161.12


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:0B:7D:08:FB:C1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


matt@matt-Inspiron-1150:~$ uname -a
Linux matt-Inspiron-1150 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
matt@matt-Inspiron-1150:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at c000 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at f6f00000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: i915

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 4: I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 11
    Region 4: I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 11
    Region 4: I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 11
    Region 0: Memory at f6effc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 0000d000-0000efff
    Memory behind bridge: f8000000-fdffffff
    Prefetchable memory behind bridge: 20000000-23ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at bfa0 [size=16]
    Region 5: Memory at 24000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 7
    Region 0: I/O ports at c800 [size=256]
    Region 1: I/O ports at cc40 [size=64]
    Region 2: Memory at f6eff800 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at f6eff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) (prog-if 00 [Generic])
    Subsystem: Broadcom Corporation Device [14e4:4d64]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 7
    Region 0: I/O ports at c400 [size=256]
    Region 1: I/O ports at c080 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 7
    Region 0: Memory at fcffe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at fd000000 [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: f8000000-fbfff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

matt@matt-Inspiron-1150:~$ lsb_release -anm-tool
Usage: lsb_release [options]

lsb_release: error: no such option: -n
matt@matt-Inspiron-1150:~$ uname -a
Linux matt-Inspiron-1150 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
matt@matt-Inspiron-1150:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at c000 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at f6f00000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: i915

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 4: I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 11
    Region 4: I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 11
    Region 4: I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 11
    Region 0: Memory at f6effc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 0000d000-0000efff
    Memory behind bridge: f8000000-fdffffff
    Prefetchable memory behind bridge: 20000000-23ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at bfa0 [size=16]
    Region 5: Memory at 24000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 7
    Region 0: I/O ports at c800 [size=256]
    Region 1: I/O ports at cc40 [size=64]
    Region 2: Memory at f6eff800 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at f6eff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) (prog-if 00 [Generic])
    Subsystem: Broadcom Corporation Device [14e4:4d64]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 7
    Region 0: I/O ports at c400 [size=256]
    Region 1: I/O ports at c080 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:017f]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 7
    Region 0: Memory at fcffe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at fd000000 [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
    Subsystem: Dell Device [1028:017f]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: f8000000-fbfff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

matt@matt-Inspiron-1150:~$ lsb_release -a


```

---

### Post by lkjoel on 2011-08-07
Could you give us the output of these commands?
```
lsb_release -a
sudo modprobe b43
sudo nm-tool

```

---

### Post by doylerules23 on 2011-08-08
```

matt@matt-Inspiron-1150:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
matt@matt-Inspiron-1150:~$ sudo modprobe b43


```

---

### Post by lkjoel on 2011-08-08
Could you give me the output of all three commands?

---

### Post by nm_geo on 2011-08-08
doylerules.
 
I still believe since you have an ethernet connection. If you will do 
```
 
sudo apt-get update && sudo apt-get upgrade 

```
 
 
You can then get your firmware through Synaptic or in terminal.
 
```
 
sudo apt-get install firmware-b43-installer

```

---

### Post by wildmanne39 on 2011-08-08
Hi, open synaptic click on settings, then repositories and put a check by multiverse then close synaptic and then run these commands please.
```
sudo apt-get update && sudo apt-get upgrade
```
let it install all updates it may take a while, then run this command
```
sudo apt-get install firmware-b43-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

---

### Post by doylerules23 on 2011-08-09
thanks [nm_geo]("http://ubuntuforums.org/member.php?u=1182725")!

that worked! my wireless internet is now working! thank you everyone.

---

### Post by montana68 on 2011-08-10
Hello All
Let me say I'm sorry for asking this question in this way. I tried to post a question but can't find it. Maybe I tried to post it incorrectly and it wasn't posted.
I'm a newbie to Ubuntu using 10.04 on a Lenovo B560. On Ubuntu the icon which looks like radio waves with a red exclamation point. 
At this time I'm on line at the library using win7. If I need to install a package it will be necessary to download on win and then transfer it to Ubuntu. If it has to be installed I'll need to be told how to install it.
Thank you all for your help in advance.

---

### Post by chili555 on 2011-08-10
> **montana68 said:**
> Hello All
Let me say I'm sorry for asking this question in this way. I tried to post a question but can't find it. Maybe I tried to post it incorrectly and it wasn't posted.
I'm a newbie to Ubuntu using 10.04 on a Lenovo B560. On Ubuntu the icon which looks like radio waves with a red exclamation point. 
At this time I'm on line at the library using win7. If I need to install a package it will be necessary to download on win and then transfer it to Ubuntu. If it has to be installed I'll need to be told how to install it.
Thank you all for your help in advance.Your thread is here: [http://ubuntuforums.org/showthread.php?t=1821890](http://ubuntuforums.org/showthread.php?t=1821890)

I have responded there.

---

### Post by damarusama on 2011-08-18
i am running into simlar problem but I think i following the wrong path - 

i got the


subprocess installed post-installation script retuned with error exit status 1

when I do lspci i get :(for the network part) 

Broadcom Corporation BCM4312 802.11/g LP-PHY (rev01)

---

### Post by damarusama on 2011-08-18
I am using the additional driver for broadcom sta - and the card seems to work, it does scan for wireless network, but it doesn't seems able to connect to a wpa password protected network, it takes the password in and then ask for the password 2 minutes lates

iwconfig

eth1 IEEE 802.11 Access Point: Not Associated
       Link quality:5 Signal level:0 Noise Level:199
       Rx invalid nwid:0 invalid crypt:0 invalid misc:0


rfkill list all

0; brcmwl-0: Wireless LAN
    Soft Blocked: no
    Hard blocked: no

---

### Post by lkjoel on 2011-08-18
Please use the Network Info script (in my signature), and attach the generated file.

---

### Post by im.saravanan on 2011-08-18
hello friend. To update those drivers you need to have an internet connection. Without which you will get uid same results. Try update drivers by first connecting to internet by wired connection or gprs.

---

### Post by xXkanfirXx on 2011-08-19
I'm also having a wireless problem, with my Dell Latitude D620's wireless. I had Ubuntu 10.04 and the wireless was working. Then after I upgraded to 11.04 it stopped working. When I turn on my wireless switch the light doesn't come on and it doesn't detect any signals. The wireless card is a Broadcom BCM4312 it says in additional drivers that the Broadcom STA driver is installed and working properly.

---

### Post by bkratz on 2011-08-19
> **xXkanfirXx said:**
> I'm also having a wireless problem, with my Dell Latitude D620's wireless. I had Ubuntu 10.04 and the wireless was working. Then after I upgraded to 11.04 it stopped working. When I turn on my wireless switch the light doesn't come on and it doesn't detect any signals. The wireless card is a Broadcom BCM4312 it says in additional drivers that the Broadcom STA driver is installed and working properly.



You might want to go to the terminal and post the output of

```
rfkill list all
```

perhaps there is a clue there.

---

### Post by lkjoel on 2011-08-19
> **xXkanfirXx said:**
> I'm also having a wireless problem, with my Dell Latitude D620's wireless. I had Ubuntu 10.04 and the wireless was working. Then after I upgraded to 11.04 it stopped working. When I turn on my wireless switch the light doesn't come on and it doesn't detect any signals. The wireless card is a Broadcom BCM4312 it says in additional drivers that the Broadcom STA driver is installed and working properly.
Use the Network Info script in my signature, and attach the generated file.

---

### Post by nm_geo on 2011-08-19
> **xXkanfirXx said:**
> I'm also having a wireless problem, with my Dell Latitude D620's wireless. I had Ubuntu 10.04 and the wireless was working. Then after I upgraded to 11.04 it stopped working. When I turn on my wireless switch the light doesn't come on and it doesn't detect any signals. The wireless card is a Broadcom BCM4312 it says in additional drivers that the Broadcom STA driver is installed and working properly.

This one I know rather well. I also have a D620 and probably the same chip or one close to it.

Mine is 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

"I showed you mine  :)  let see yours" to be sure. Copy and paste (less typos) this in terminal then copy results here in the thread.

```
lspci -nn | grep 0280

```I firmly believe you can resolve this by deactivating and uninstalling the STA (wl) driver.
Then installing the b43-fwcutter and some firmware determined by your chip information.

---

### Post by xXkanfirXx on 2011-08-19
> **nm_geo said:**
> This one I know rather well. I also have a D620 and probably the same chip or one close to it.

Mine is 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

"I showed you mine  :)  let see yours" to be sure. Copy and paste (less typos) this in terminal then copy results here in the thread.

```
lspci -nn | grep 0280

```I firmly believe you can resolve this by deactivating and uninstalling the STA (wl) driver.
Then installing the b43-fwcutter and some firmware determined by your chip information.
anthony@anthony-Latitude-D620:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by bkratz on 2011-08-19
This should give you everything you need.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

just noticed the id is slightly different you should probably follow nm_geo's advice.

---

### Post by xXkanfirXx on 2011-08-19
> **bkratz said:**
> You might want to go to the terminal and post the output of

```
rfkill list all
```perhaps there is a clue there.
anthony@anthony-Latitude-D620:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

---

### Post by nm_geo on 2011-08-19
Your Switch on left side of laptop slide that baby back towards you.

Let look at 
```
rfkill list all 
```after you slide that baby back..

Then 

```
sudo lshw -C network
``````
lsmod
```I never could get STA (wl) working in Natty and believe me I tried.. Turn it off in Synaptic.. de-activate in Additional driver ..just get rid of it for now.  Insert an ethernet cable and do these.

```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install b43-fwcutter
``````

sudo apt-get install firmware-b43-installer
```reboot without ethernet cable and wifi will be ready to setup.

---

### Post by nm_geo on 2011-08-19
> **bkratz said:**
> This should give you everything you need.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

just noticed the id is slightly different you should probably follow nm_geo's advice.

+1 bkratz that will work too

That is a good link too LOL chili555 and I wrote that baby...

Excellent

---

### Post by xXkanfirXx on 2011-08-19
> **nm_geo said:**
> Your Switch on left side of laptop slide that baby back towards you.

Let look at 
```
rfkill list all 
```after you slide that baby back..

Then 

```
sudo lshw -C network
``````
lsmod
```I never could get STA (wl) working in Natty and believe me I tried.. Turn it off in Synaptic.. de-activate in Additional driver ..just get rid of it for now.  Insert an ethernet cable and do these.

```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install b43-fwcutter
``````

sudo apt-get install firmware-b43-installer
```reboot without ethernet cable and wifi will be ready to setup.
anthony@anthony-Latitude-D620:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
anthony@anthony-Latitude-D620:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ac:16:7a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=192.168.200.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:efcf0000-efcfffff
anthony@anthony-Latitude-D620:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  451033  3 
psmouse                73312  0 
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
dell_laptop            13515  0 
dell_wmi               12601  0 
drm                   184164  4 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
lp                     13349  0 
i2c_algo_bit           13184  1 i915
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18951  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
sparse_keymap          13666  1 dell_wmi
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
dcdbas                 14054  1 dell_laptop
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 
anthony@anthony-Latitude-D620:~$

---

### Post by xXkanfirXx on 2011-08-19
> **nm_geo said:**
> +1 bkratz that will work too

That is a good link too LOL chili555 and I wrote that baby...

Excellent
I'm sorry if im slow or not doing things right, I'm a noob to Ubuntu Fourms and to Ubuntu :???:
I did the commands you gave me and rebooted and the wireless card still wont come on, also I uninstalled the STA driver in synaptics, but it's still showing it in additional drivers, and that's all it shows. It's deactivated. I then did the commands from bkratz's link and it's still not working.. :(

---

### Post by xXkanfirXx on 2011-08-19
One thing I would like to add and maybe it could help. Is when I put my 11.04 installation CD in and boot off the CD and turn on my wireless switch, the additional driver icon pops up in the top bar and recognizes something... and when i install it, my wireless works but once i go back to booting of my hard drive of course it doesn't work anymore. Is there anyway I can use the Boot disc to fix my problem??

---

### Post by nm_geo on 2011-08-19
> **xXkanfirXx said:**
> One thing I would like to add and maybe it could help. Is when I put my 11.04 installation CD in and boot off the CD and turn on my wireless switch, the additional driver icon pops up in the top bar and recognizes something... and when i install it, my wireless works but once i go back to booting of my hard drive of course it doesn't work anymore. Is there anyway I can use the Boot disc to fix my problem??
I am away from my computer and I bet you have blacklist issues. bkratz might be able to help I will look in later.

---

### Post by bkratz on 2011-08-19
> **nm_geo said:**
> I am away from my computer and I bet you have blacklist issues. bkratz might be able to help I will look in later.



Here is an earlier nm_geo post that describes what to do with the blacklists. The idea is to find where b43 and ssb are blacklisted.

[http://ubuntuforums.org/showpost.php?p=10527475&postcount=5](http://ubuntuforums.org/showpost.php?p=10527475&postcount=5)

---

### Post by bkratz on 2011-08-19
Going to bed now, but if there are questions in what you see copy/paste the output of

ls /etc/modprobe.d

back here and we will help find it for you. (By the way that is an "LS" in lowercase (not a 1) --sometimes it is a bit difficult to determine in these posts.

---

### Post by nm_geo on 2011-08-20
After you boot up next time without ethernet connection just copy and paste the following in the terminal:

```
sudo modprobe b43
```If that turns on you wireless it will be temporary, but never fear we can make it permanent.  

If it doesn't we need to do some looking in dmesg and lsmod again. 

```
dmesg | egrep 'b43|wl|irmware'  

``````
lsmod
``` If you followed the link and my apt-gets you should have got the b43 driver installed. But sometimes it is still blacklisted by the STA (wl) driver.  We can fix that too.

```
egrep -e b43 -e ssb  /etc/modprobe.d/*

```

---

### Post by xXkanfirXx on 2011-08-20
> **nm_geo said:**
> After you boot up next time without ethernet connection just copy and paste the following in the terminal:

```
sudo modprobe b43
```If that turns on you wireless it will be temporary, but never fear we can make it permanent.  

If it doesn't we need to do some looking in dmesg and lsmod again. 

```
dmesg | egrep 'b43|wl|irmware'  

``````
lsmod
``` If you followed the link and my apt-gets you should have got the b43 driver installed. But sometimes it is still blacklisted by the STA (wl) driver.  We can fix that too.

```
egrep -e b43 -e ssb  /etc/modprobe.d/*

```
My wireless light came on! :P Now how do we make it permanent? :confused:

---

### Post by bkratz on 2011-08-20
> **xXkanfirXx said:**
> My wireless light came on! :P Now how do we make it permanent? :confused:




Congratulations, if you add it to the modules loaded at boot time, it should survive a reboot



```
sudo su
echo b43 >> /etc/modules
exit

```


The sudo will require your password which will not be echoed to the screen, just put it in and press enter.

---

### Post by nm_geo on 2011-08-20
> **bkratz said:**
> Congratulations, if you add it to the modules loaded at boot time, it should survive a reboot



```
sudo su
echo b43 >> /etc/modules
exit

```
The sudo will require your password which will not be echoed to the screen, just put it in and press enter.

Thanks for the backup bkratz. I hope **xXkanfirXx**  returns so we can check those blacklist. But if not it appears it is working.

---

### Post by xXkanfirXx on 2011-08-20
> **bkratz said:**
> Congratulations, if you add it to the modules loaded at boot time, it should survive a reboot



```
sudo su
echo b43 >> /etc/modules
exit

```
The sudo will require your password which will not be echoed to the screen, just put it in and press enter.
Am I putting that code in right? This is what I got.. 
anthony@anthony-Latitude-D620:~$ sudo su
[sudo] password for anthony: 
root@anthony-Latitude-D620:/home/anthony# sudo su
root@anthony-Latitude-D620:/home/anthony# echo b43 >> /etc/modules
root@anthony-Latitude-D620:/home/anthony# exit

What do you mean by add it to the modules loaded at boot time??

---

### Post by nm_geo on 2011-08-20
> **xXkanfirXx said:**
> Am I putting that code in right? This is what I got.. 
anthony@anthony-Latitude-D620:~$ sudo su
[sudo] password for anthony: 
root@anthony-Latitude-D620:/home/anthony# sudo su
root@anthony-Latitude-D620:/home/anthony# echo b43 >> /etc/modules
root@anthony-Latitude-D620:/home/anthony# exit

What do you mean by add it to the modules loaded at boot time??

The command bkratz gave you and you used makes sure the b43 is picked up during the booting process.  You inserted b43 into the modules..
That way every time you log on the b43 is loaded.

---

### Post by xXkanfirXx on 2011-08-20
> **nm_geo said:**
> Thanks for the backup bkratz. I hope **xXkanfirXx**  returns so we can check those blacklist. But if not it appears it is working.
This is what I got after entering the black list code..
anthony@anthony-Latitude-D620:~$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist wl
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
anthony@anthony-Latitude-D620:~$ 

In your post you were saying something about adding "#" in front, It doesn't allow me to type anywhere else except for a new command.

---

### Post by nm_geo on 2011-08-20
Please run and post the following for my peace of mind.

```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```

---

### Post by xXkanfirXx on 2011-08-20
> **nm_geo said:**
> Please run and post the following for my peace of mind.

```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```
anthony@anthony-Latitude-D620:~$ egrep -e b43 -e ssb  /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/broadcom-sta-common.conf:# wl module from Broadcom conflicts with ssb
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43legacy
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43
/etc/modprobe.d/broadcom-sta-common.conf:blacklist ssb
anthony@anthony-Latitude-D620:~$

---

### Post by xXkanfirXx on 2011-08-20
Well I rebooted and my wireless came back on and is working fine so I suppose all is well. I thank you both for your patience and all your help! :) I'll let you know if anything goes quirky, hopefully it won't.

---

### Post by nm_geo on 2011-08-20
> /etc/modprobe.d/broadcom-sta-common.conf:blacklist b43
/etc/modprobe.d/broadcom-sta-common.conf:blacklist ssbThose are the ones that are the problem.



There are at least two ways to clean up the blacklist.. I will give you both.. The first is easier and less chance for error.
1)
```
gksudo gedit /etc/modprobe.d/broadcom-sta-common.conf
```add the # in front of blacklist b43 and # in front of blacklist ssb

Save and Exit

2) 

Gets us to the directory
```
cd /etc/modprobe.d
```Verifies we are correct all with blacklist names
```
ls
```This one is very important to be correct we are removing the file
```
sudo rm broadcom-sta-common.conf
```b43 & ssb are no longer blacklisted ...

Run this to check..

```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```

---

### Post by xXkanfirXx on 2011-08-20
> **nm_geo said:**
> Those are the ones that are the problem.



There are at least two ways to clean up the blacklist.. I will give you both.. The first is easier and less chance for error.
1)
```
gksudo gedit /etc/modprobe.d/broadcom-sta-common.conf
```add the # in front of blacklist b43 and # in front of blacklist ssb

Save and Exit

2) 

Gets us to the directory
```
cd /etc/modprobe.d
```Verifies we are correct all with blacklist names
```
ls
```This one is very important to be correct we are removing the file
```
sudo rm broadcom-sta-common.conf
```b43 & ssb are no longer blacklisted ...

Run this to check..

```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```
I did the first one.

---

### Post by nm_geo on 2011-08-20
> I did the first one.

You should be Golden... thanks for revisiting it really helped to explain why your b43 did not auto-start.  Might help others later.

---

### Post by bkratz on 2011-08-21
Just got up, I'm glad nm_geo was able to get you going. Enjoy your wireless!

---

### Post by xXkanfirXx on 2011-08-21
> **bkratz said:**
> Just got up, I'm glad nm_geo was able to get you going. Enjoy your wireless!
Still working great, thank you both!

---

