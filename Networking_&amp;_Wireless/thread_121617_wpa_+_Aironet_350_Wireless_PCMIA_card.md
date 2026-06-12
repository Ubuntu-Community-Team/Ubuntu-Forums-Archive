---
title: "wpa + Aironet 350 Wireless PCMIA card"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-01-25
I’m trying to setup a Cisco Aironet 350 wireless PCMIA card to use WPA. The card itself is working without problems when no security is used. Tried to setup WPA supplicant but with no luck.
   
  After doing a little research on the [net]("http://hostap.epitest.fi/wpa_supplicant/") and on this [forum]("http://www.ubuntuforums.org/showthread.php?t=52835&highlight=airo%2A+wpa"), I found that WPA Supplicant does not support Airo chips. :(

   
  Doing a little more research I found this [link]("http://castet.matthieu.free.fr/airo/") which is an Airo driver patch to make it work with WPA, I’m new to linux but not to computers, how would I apply this patch? I assume that I need to recompile my kernel, right? If my guess is correct, is there a good HowTo somewhere to walk me through the process.
   
  Thanks.

---

### Post by FLeiXiuS on 2006-01-25
Not at all!  For this particular model of card, it's best if you use NDISWRAPPER to install the windows drivers on linux.  It'll provide you with a much more stable system then to use unstable kernel patches.  

A bit of info about your card.
Card: Aironet 350 PCI 
Chipset: Aironet MAC + PrismII 
PCI ID: 14b9:0350 
Driver: [http://tools.cisco.com/support/downloads/pub/MDFTree.x?butype=wireless](http://tools.cisco.com/support/downloads/pub/MDFTree.x?butype=wireless)
Other: In order to use with version 1.4, you need to remove pcx500mp.sys from /etc/ndiswrapper/netx500/. For WPA support don't forget to update your firmware. Sould work with other aironet cards. 

GUI ndiswrapper howto:
[http://ubuntuforums.org/showthread.php?t=85378](http://ubuntuforums.org/showthread.php?t=85378)

---

### Post by ssalman on 2006-01-25
I'm speachless :D, Thank you [[COLOR=#d40000]**FLeiXiuS**[/COLOR]]("http://www.ubuntuforums.org/member.php?u=26"), you just made my day.

---

### Post by FLeiXiuS on 2006-01-25
Not a problem, hopefully you get things worked out!  :-)

---

### Post by ssalman on 2006-01-26
Okay,
    I'm still trying to get this to work, I downloaded the XP drivers from Cisco, and installed ndiswrapper and util, added the driver but it said the hardware is not present.

    I go lookup a couble of howtos ([1]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") & [2]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29")) on the wiki and follow it, and the very first steps are a no go for me... it asks to identify the chip using lspci, here is the output:

lspci

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:08.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:0a.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
``` 

so I can't find my card, but when I do ifconfig it is there!

 ifconfig eth2
```
eth2      Link encap:Ethernet  HWaddr 00:08:E3:5F:47:20
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:123 dropped:0 overruns:0 frame:123
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

``` 

what am I missing here.

Thanks.

---

### Post by FLeiXiuS on 2006-01-26
What does iwconfig say?

$ sudo iwconfig

---

### Post by ssalman on 2006-01-26
[quote=FLeiXiuS]What does iwconfig say?

$ sudo iwconfig[/quote]

Thanks for your help FLeiXiuS!!!

```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-109 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2513   Missed beacon:0

eth1      IEEE 802.11-DS  ESSID:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-109 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2513   Missed beacon:0


```

---

