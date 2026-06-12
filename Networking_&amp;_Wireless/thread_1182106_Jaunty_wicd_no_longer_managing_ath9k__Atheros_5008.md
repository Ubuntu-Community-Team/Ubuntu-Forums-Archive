---
title: "Jaunty: wicd no longer managing ath9k / Atheros 5008 properly?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by ewy on 2009-06-08
Hello, I have been struggling with poor wireless performance, dropped connections, and inconsistent connections ever since I installed a fresh copy of Ubuntu Jaunty 9.04. Originally I was using NetworkManager, but there seemed to be major problems in reconnecting to wireless networks after resuming from suspend. I googled around and finally saw that some people tackled a similar problem by installing wicd and the linux-backports-modules package.

wicd seemed to help at first: it showed a much better signal strength for my home network, and could connect to other wireless networks after resume. But I was still seeing inconsistencies and was sometimes unable to connect to my WPA2 home network despite seeing signal strengths in the tray applet of 30-60%. Now, something major seems to have happened, and I'm no longer seeing any wireless networks in the wicd tray applet. Ethernet is now my only option. I have tried uninstalling wicd and reinstalling it, but that does not seem to fix the problem.

wicd is using wext as WPA supplicant driver.

It appears that ndiswrapper is being loaded from the following line in messages.log:
```

Jun  7 11:08:42 e-u400 kernel: [   12.582558] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
```

(I may have tried it when I first installed Jaunty, as I was having connection problems and thought it was the driver.)

That said, it doesn't look like it is being used, as the output from
```
lspci -kvv
```
is:

```
08:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7125                                             
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 17                                                                    
        Region 0: Memory at c2100000 (64-bit, non-prefetchable) [size=64K]                                   
        Capabilities: <access denied>                                                                        
        Kernel driver in use: ath9k                                                                          
        Kernel modules: ath9k
```     

AND when I run
```
ndiswrapper -l
```

The output is
```
The program 'ndiswrapper' is currently not installed.
```

More info:

```
lshw -C

  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:d9:40:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

```
This is interesting to me because the only line in messages.log that references the wireless adapter is:

```
Jun  7 11:08:42 e-u400 kernel: [   12.183715] phy0: Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81: mem=0xf8080000, irq=17
```

Which may just be what the system is trying to control the card with, I dunno.

ifconfig output:

```
wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:d9:40:bc
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig output:

```
wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwlist scan output:

```
wlan0     No scan results
```

uname -a output:

```
Linux e-u400 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```
The computer is a Toshiba Satellite u400, purchased in Canada.

It is frustrating to be constantly wrestling with my wireless. I feel like I waste hours every week just trying to reboot, play around, etc. to find a connection... what other steps can I take to troubleshoot this? Should I uninstall ndiswrapper? Should I try a different WPA supplicant driver? Should I blacklist some driver or another? I find the information on the web concerning similar problems still quite confusing and patchy; I'm never sure if it's the same problem I have.

---

