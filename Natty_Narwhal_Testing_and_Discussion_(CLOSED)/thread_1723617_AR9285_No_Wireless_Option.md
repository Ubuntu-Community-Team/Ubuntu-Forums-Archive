---
title: "AR9285 No Wireless Option"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CheresZabor on 2011-04-07
Hello, 
I have just upgraded to Natty and am seeing some issues with the wireless driver. The "enable wireless" option in the network manager is completely grayed out. 

I have tried manually adding ath9k to the modules which did not help, nor did the installation of compat-wireless. 

Any suggestions 

Here is the lspci output; 
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

### Post by ikt on 2011-04-07
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/735431](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/735431)

may be of some help.

---

### Post by CheresZabor on 2011-04-07
Thanks ikt, 
Though it doesn't seem to be similar, they are able to activate wireless networking. In my case there is not even the option to scan wireless networks.

---

### Post by kio_http on 2011-04-07
I have the exact same atheros card and it seems to work fine on Kubuntu 11.04 Beta 1.

Wireless options only grey out if I use the WLAN off hotkey on the laptop, if I tap the hotkey again, the card turns on and the options return.

---

### Post by CheresZabor on 2011-04-07
> **kio_http said:**
> I have the exact same atheros card and it seems to work fine on Kubuntu 11.04 Beta 1.

Wireless options only grey out if I use the WLAN off hotkey on the laptop, if I tap the hotkey again, the card turns on and the options return.

You seem to be correct, (i don't know how I didn't notice that before) 
The only thing is that my hardware switch (its a switch rather then a button combination) is in the "on" position. 

Is there a way to "force" Ubuntu into seeing the card as on?

---

### Post by kio_http on 2011-04-07
> **CheresZabor said:**
> You seem to be correct, (i don't know how I didn't notice that before) 
The only thing is that my hardware switch (its a switch rather then a button combination) is in the "on" position. 

Is there a way to "force" Ubuntu into seeing the card as on?

Not sure, however in some older ubuntu releases my hotkey combination would not work in ubuntu, I had to turn the card on in windows and then reboot into ubuntu.

---

### Post by CheresZabor on 2011-04-07
Seems that the problem is the rfkill is incorrectly recognizing the position of my WiFi switch. 

The output is as follows; 
```
0: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

Any suggestions? 

And yes the switch is in the "wifi on" position

---

### Post by cariboo on 2011-04-07
Do you also have a function key to turn wireless on/off?

---

### Post by CheresZabor on 2011-04-07
> **cariboo907 said:**
> Do you also have a function key to turn wireless on/off?

Nope, there is only a physical switch. The laptop is a Sony Y series (the older one).

---

### Post by jardo on 2011-04-08
i have the same wifi card and no problems on 11.04...except the speed, but i fixed it by reading this post
[http://ubuntuforums.org/showthread.php?p=10642362#post10642362](http://ubuntuforums.org/showthread.php?p=10642362#post10642362)

---

### Post by kio_http on 2011-04-08
> **CheresZabor said:**
> Seems that the problem is the rfkill is incorrectly recognizing the position of my WiFi switch. 

The output is as follows; 
```
0: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

Any suggestions? 

And yes the switch is in the "wifi on" position

Seems like Ubuntu 11.04 sets your ACPI configuration to have a software hotkey, but since their is none there is no way to enable it. However it correctly recognises the position of the hardware on-off switch. Try running rfkill in Maverick is you still have it installed or a live cd.

---

### Post by CheresZabor on 2011-04-08
Hey,
Just tested Maverick, there does not seem to be any issues all devices are set to "no." 

Most ideas hehe??

Is there a way to remove rfkill completely so the card is always in the "on" state?

---

### Post by grahammechanical on 2011-04-08
Have you tried removing the tick mark against Enable networking by clicking it and then clicking it again to put it back. By switching networking off and then on it might (fingers crossed) activate the Enable wireless side of things. Otherwise, try in a terminal  ifconifg wlan0 up    or in your case ifconfig phy0 up. I am guessing the phy0 is your wireless device.

Regards.

---

### Post by CheresZabor on 2011-04-09
> **grahammechanical said:**
> Have you tried removing the tick mark against Enable networking by clicking it and then clicking it again to put it back. By switching networking off and then on it might (fingers crossed) activate the Enable wireless side of things. Otherwise, try in a terminal  ifconifg wlan0 up    or in your case ifconfig phy0 up. I am guessing the phy0 is your wireless device.

Regards.


Hello,
Just tried you suggestion, it did not work. 

There seems to be a problem with phy0 "hard block" always staying on. I am now wondering if there is a way to completely remove the rfkill functionality and set the wireless card to "Always On" mode. Is there a way to do that?

Thanks

---

### Post by blandwa on 2011-04-10
I have the same problem (also with an AR9285, also in a Sony Vaio Y).  I've tried two things that didn't help:

1. Running "rfkill unblock all".  The message in the menu changes from "wireless is disabled by hardware switch" to "wireless is disabled".

2. The instructions given here: [http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503).  (I used compat-wireless-2.6.38.2-2.tar.bz2)

---

### Post by blandwa on 2011-04-10
My wireless (AR9285) works using Wicd network manager instead of the default network manager (when combined with "rfkill unblock all").

---

### Post by jardo on 2011-04-10
maybe this can help you...
that wifi card works fine for me and i don't use neither wicd...but i don't have any button to enable...except fn+F5 , anyway it's enabled by default when booting up the laptop

---

### Post by CheresZabor on 2011-04-10
> **jardo said:**
> maybe this can help you...
that wifi card works fine for me and i don't use neither wicd...but i don't have any button to enable...except fn+F5 , anyway it's enabled by default when booting up the laptop


That worked can confirm connectivity, so this means that there is a bug in network-manager... any idea how to file it to launchpad?

---

### Post by blandwa on 2011-04-10
I solved this problem by adding:

blacklist acer-wmi

to /etc/modprobe.d/blacklist.conf

---

### Post by CheresZabor on 2011-04-10
> **blandwa said:**
> I solved this problem by adding:

blacklist acer-wmi

to /etc/modprobe.d/blacklist.conf

Could you tell what are the specs of your hardware? 


Thanks

---

### Post by blandwa on 2011-04-11
> **CheresZabor said:**
> Could you tell what are the specs of your hardware? 


Thanks

> **CheresZabor said:**
> Could you tell what are the specs of your hardware? 


Thanks

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e017
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

Sony Vaio Y (it says "VPCY2" below the screen).  Do you want to know anything else?

---

### Post by jardo on 2011-04-11
> **CheresZabor said:**
> That worked can confirm connectivity, so this means that there is a bug in network-manager... any idea how to file it to launchpad?

network-manager works fine for me..why do u think it's a bug ?

by the way, did anyone notice that if u use a too complex wpa2 AEs protection it doesn't allow u to estabilish the connection?  i have to use an 8 characters password to get a fine connection. is it a known issue of network-manager?

---

### Post by tnat on 2011-04-27
> **blandwa said:**
> I solved this problem by adding:

blacklist acer-wmi

to /etc/modprobe.d/blacklist.conf

This worked for my acer timeline-x!!!
Thanks!!

---

