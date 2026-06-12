---
title: "wireless distance problem"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by kapetus on 2009-04-16
hello,

I have 2 notebooks at home, thei are twins... one is mine the other is of my wife.
her PC does not have any problems connecting to internet
my PC only connects to internet if it was realy near the wirelles router (1Meter or less)
I have dual boot in both PC's, with XP i can connect at distance and over walls, so its not a wirelles card problem, if both computers have every thing equal I don't understand wy one doesn't work properly.
does any one can help?

PS. the wireless card is: sis190/191

tkx

---

### Post by Funkydonut5000 on 2009-04-16
This doesn't really sound like a ubuntu related issue.  It sounds more like a card manufacture issue.  Contact their support.  Your card might not be functioning properly therefore you might be entitled to a replacement.

---

### Post by kapetus on 2009-04-17
> **Funkydonut5000 said:**
> This doesn't really sound like a ubuntu related issue.  It sounds more like a card manufacture issue.  Contact their support.  Your card might not be functioning properly therefore you might be entitled to a replacement.

it only have problems with ubuntu, so i don't really think that's a mannufactorer problem

---

### Post by Daisuke_Aramaki on 2009-04-17
> **kapetus said:**
> it only have problems with ubuntu, so i don't really think that's a mannufactorer problem

its likely then that your driver is not working properly. so sis190/191 is your wireless card? can you please post the output of the following command in a terminal?

```
lspci
```

---

### Post by Jenkins1 on 2009-04-17
Hi,

I had the exact same problem with a Intel wireless wifi link 4965 agn card, I changed my encryption to WEP and now I can connect any where in the house. Also changing to WPA and not "WPA and WPA2 personal" on the router worked for me.
Hope this helps.

---

### Post by kapetus on 2009-04-25
hi, sorry for my late answer, i'm having some troubles...

the lspci output is:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)


Jenkins1,
i didn't tryed your solution, because the problem isn't only at home, at work i've got the same problem and there i can't use WEP
thanks anyway.

---

### Post by kapetus on 2009-04-25
I'm using the wireless connection to send this reports, but I can't get far from router, more than 2 meters and connection to internet drops, but not with router, i still have IPadress and I can connect to router's home page...

I'm confused, I do't understand whi that hapens

I apreciate any help

---

### Post by ybaruss on 2009-05-01
Hello,

Just to say to I have the same problem with my laptop:
> Wireless internet connexion works Ok everywhere in the flat with Windows Vista.
> Wireless internet connexion works Ok only for 2 meters when with Ubuntu 8.10.

My wireless config is already with WEP (128 bits) and under Ubuntu the wireless connexion manager says everything is all right but it is not possible to access the internet and even not possible to access the router by 192.168.1.1. :confused:

My wireless card is:
~$ lsusb
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter

Thank by advance for any support.

---

### Post by richardjennings on 2009-05-01
first off, type in

```
iwconfig
```

this is what mine looks like (slimmed down):

wlan0     IEEE 802.11bg  ESSID:"2hayling"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:E0:98:51:20:7A   
          Bit Rate=54 Mb/s   Tx-Power=5 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=58/100  Signal level:-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Notice it shows wireless link quality for wlan is 58/100 & Tx-Power = 5


If supported by your wireless card, you can increase the power. Try a small increase, for example (for me)

```
 sudo iwconfig wlan0 txpower 6 
```

---

### Post by kapetus on 2009-05-06
well, I had allmost solve the problem,
in console i gave a command to change the rate from 54mb to 6mb or 1mb,
code:
 # iwconfig wlan0 rate 6M fixed

now i can go a litlle far from router, about 10 meters, but not more

I'll try the option of power up the signal, and i'll comment later

---

### Post by raunhar on 2009-06-30
i too have the same problem.

iwconfig shows:
wlan0     IEEE 802.11bg  ESSID:"Broadcom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:08:5C:D3:25:3F   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=76/100  Signal level:-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If I am two rooms away(10m) (doors closed) signal is there but 8% or so. At that time I am unable to connect to the net.

If I use Win XP there is no problem even if i am 40m away.

What can be the solution?

---

