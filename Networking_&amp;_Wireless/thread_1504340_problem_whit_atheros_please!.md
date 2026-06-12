---
title: "problem whit atheros please!"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by superope on 2010-06-07
please i really need help !

the situation is this:
i have  a laptop packard belle  whit a wireless card  ralink rt61 / rt2500 anyway this card work only in ubuntu 9.04 so i bought  a Atheros card  called[HTML] Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/HTML]but still doesn't work   please help me ! here i let you some of  the commands

```
priss@priss-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

``````

priss@priss-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:24:29:60:68  
          Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21b:24ff:fe29:6068/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:94709 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:62406 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:134945893 (134.9 MB)  TX bytes:5010492 (5.0 MB)
          Interrupción:21 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:20 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:16:cf:50:87:28  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
``````

priss@priss-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
priss@priss-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results


```

---

### Post by marcoftheknight on 2010-06-07
Code please print: lshw -C network

This code will tell you the chipset if you have a driver loded the way its connect the logical id its logical name the vendor and It will help you know  what mother board vendor it's integrated on or it's PCI ID

DUde post this that will give a really good idea

Thanks

---

### Post by superope on 2010-06-07
done!
```
priss@priss-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:29:60:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:a000(size=256) memory:c0100000-c01000ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:50:87:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0110000-c011ffff

```

what it means that?

---

### Post by superope on 2010-06-08
cmon need some help here!!!:lolflag:

---

### Post by superope on 2010-06-08
ok something new here...

```
priss@priss-laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
    Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
    Kernel modules: shpchp
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
09:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
    Kernel modules: ath_pci, ath5k
```

so you can see there is not kernel driver in use on  atheros communication my question is how can  enable ath_pci?

---

### Post by b k on 2010-06-08
> **superope said:**
> 
09:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
Kernel modules: ath_pci, ath5k[/CODE]
 

 
Hi there, I don't own the NIC that you have but maybe you have conflicting drivers loaded.
 
See if this helps:
 
Go to a Terminal window and do this:
 
Code:
[COLOR=blue]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]
 
 
and add this line at the end of the opened file
 
 
[COLOR=red]blacklist ath_pci[/COLOR]

[COLOR=black]**save** and close[/COLOR]
 
reboot
 
If it does not work, you can always execute the code again to remove the line added above.
 
Hope the info can help. Good luck.
 
PS : this link is probably helpful to you [http://wiki.debian.org/ath5k](http://wiki.debian.org/ath5k)
       and probably this link [http://wiki.debian.org/WiFi/ath_pci](http://wiki.debian.org/WiFi/ath_pci)

---

### Post by marcoftheknight on 2010-06-09
**This looks liek what your looking for :**

Source [http://wireless.kernel.org/en/users/Drivers/ath5k#supported_chips](http://wireless.kernel.org/en/users/Drivers/ath5k#supported_chips)

**Enabling ath5k**

 To enable ath5k in the kernel configuration, you must first enable mac80211: 

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)Please note that there is another 802.11 networking stack: 

    <M> Generic IEEE 802.11 Networking StackYou do not need this. This option enables the old SoftMAC stack we hope to kill one of these days. You can still safely enable this though. 
You can then enable ath5k in the kernel configuration under 

Device Drivers  --->
  
[*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 5xxx wireless cards support 
**supported chips**

 
AR5210   - 802.11a   (Crete/fez)
AR5211   - 802.11ab  (Oahu) (draft g -OFDM only- supported by hw but not by ath5k)
AR5212   - 802.11abg (Venice)
AR5213   - 802.11abg (Hainan)
AR2413/4 - 802.11bg  (Griffin)
AR5413/4 - 802.11abg (Eagle)
AR5423/4 - 802.11abg (Condor) (PCI-E)
AR2425   - 802.11bg  (Swan) (PCI-E)
AR2417   - 802.11bg  (Nala) (PCI-E)To try the driver you can do this: 

modprobe ath5k
sudo ip link set wlan%d up
sudo iwconfig wlan%d essid any
# Make sure you get auth'd and then assoc'd
# Then either set an IP manually or get it via DHCP
ping gwYou'll probably see an immediate rate drop to 1M, this is because of how we currently handle rate control. You should be able to keep at least at 11M for 802.11b/g but for now set this manually: 

iwconfig wlan%d rate 11MCurrently supported PCI ID list with respective status report on basic-testing as defined above. 

Vendor:device   Type    Name    Basic-testing
168c:0207       AR5210  AR5210  No tx - working on it
168c:0007       <<      <<      No tx - working on it

168c:0011       AR5211  AR5211  Should work
168c:0012       <<      <<      OK

168c:0013       AR5212  AR5212  OK
a727:0013       <<      <<      Should Work
10b7:0013       <<      <<      <<
168c:0014       <<      <<      <<
168c:0015       <<      <<      <<
168c:0016       <<      <<      <<
168c:0017       <<      <<      <<
168c:0018       <<      <<      <<
168c:0019       <<      <<      <<
168c:001a       <<      AR2413  OK
168c:001b       <<      AR5413  OK
168c:001c       <<      AR5424  OK (*)
168c:001d       <<      AR2417  OK 
**Notes on supported devices**

 "OK" means that card operates almost as good as with binary drivers (performance is around 25Mbits max depending on environment -that's because we still don't support ANI or tx power calibration) 
"Should work" means that card hasn't been tested (we haven't received any reports) but since chipset is the same with a tested, working card, it should work as well. 
(*) 001c is used also for RF2425 parts. 

[LIST]
[*][MadWifi]("http://madwifi-project.org/") and ndis drivers perform better on noisy environments than ath5k because we don't support Adaptive Noise Immunity (ANI) yet. 
[/LIST]
 
**Available devices**

 See the [ath5k device list]("http://wireless.kernel.org/en/users/Drivers/ath5k/devices"). A longer but less reliable list can be found at [http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility) 
 
**features**

 Supports 802.11abg, depending on the chipset. This driver requires no firmware or binary-only HAL !

---

### Post by superope on 2010-06-09
thanks a lot  for everyone     i will givr this thread like solved   was very helpfuly:popcorn:

---

### Post by b k on 2010-06-09
> **superope said:**
> thanks a lot  for everyone     i will givr this thread like solved   was very helpfuly:popcorn:

Hi there, for the benefit of future readers facing the same problem could you please briefly post what you actually did to have the problem solved (I am presuming that your problem is solved).

Thanks

---

