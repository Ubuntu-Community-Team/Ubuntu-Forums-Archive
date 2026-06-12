---
title: "RT5390 wireless card"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by Panos_Papajohn on 2012-02-25
Hello everyone. I just desided to start with Ubuntu. I have a presario cq57 with a Ralink RT5390 wireless card and i cant get it to work. At first using the iwconfig I couldnt see any wireless adapters. Then I followed some other steps that i saw in some threads [http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3) and I managed to see the wireless card. Everytime i try the ```
ifconfig wlan0 up
SIOCSIFFLAGS : Operation not permitted 
``` also when i do ```
service networking restart 
restart : Unknown instance: 
```  Btw my /proc/modules folder is empty. Is this relevant. I just migrate from windows so excuse my ignorance. Thanks for the help

---

### Post by chili555 on 2012-02-25
Please do:```
lsmod | grep rt5
```Is the module loaded? If not, then do:```
sudo modprobe rt5390sta
```Is a wireless interface created?```
iwconfig
```Does it scan for networks?```
sudo iwlist wlan0 scan
```Can you click the Network manager icon and see your network? What does this tell us?```
rfkill list all
dmesg | grep rt5
```Thanks.

---

### Post by Panos_Papajohn on 2012-02-25
Ok chili555 let me rephrase that. Im running Backtrack 5 not Ubuntu its just that Backtrack is Ubuntu based thats why I asked the question here.
```
lsmod | grep rt5 
rt5390sta            1345474  0 
``````
modprobe rt5390sta
``` returns nothing
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
iwlist wlan0 scan
wlan0     No scan results

``````
 dmesg | grep rt5
[   11.436623] rt5390 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   11.436776] rt5390 0000:07:00.0: setting latency timer to 64

```Thank you

---

### Post by chili555 on 2012-02-25
What kernel version are you running?```
uname -r
```Which version of the driver did you compile? Did you make the changes mentioned in the README?> 3> In os/linux/config.mk 
		** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'If not, you'll need to make the changes and rebuild the driver:```
cd Downloads/RT5390 <--or wherever you extracted the driver
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe -r rt5390sta
modprobe rt5390sta
exit
```

---

### Post by Panos_Papajohn on 2012-02-26
```
 uname -r
2.6.38

```

I did make the changes to the as the read me file said.
I have installed the v2.5.0.3 driver. I executed the commands you told me. Do you want any screen-shots ? I still have no wireless.
What should i do next?

---

### Post by chili555 on 2012-02-26
Please show us:```
lspci -nn | grep 0280
dmesg | grep -i rt
iwconfig
```Thanks.

---

### Post by Panos_Papajohn on 2012-02-26
```
lspci -nn | grep 0280
07:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
```
```
dmesg | grep -i rt
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015801] mce: CPU supports 6 MCE banks
[    0.335218] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.480263] ACPI: (supports S0 S3 S4 S5)
[    0.536406] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.537863] pci 0000:00:01.0: supports D1 D2
[    0.544022] pci 0000:00:12.2: supports D1 D2
[    0.544034] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.544331] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.544759] pci 0000:00:15.0: supports D1 D2
[    0.544891] pci 0000:00:15.1: supports D1 D2
[    0.545041] pci 0000:00:15.3: supports D1 D2
[    0.549717] pci 0000:00:16.2: supports D1 D2
[    0.549729] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.550856] pci 0000:02:00.0: supports D1 D2
[    0.550862] pci 0000:02:00.0: PME# supported from D1 D2 D3hot
[    0.551221] pci 0000:06:00.0: supports D1 D2
[    0.551226] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.551718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.552029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    0.552126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    0.552225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB3._PRT]
[    0.552406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.551592] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.111127] Linux agpgart interface v0.103
[    2.280825] ehci_hcd 0000:00:12.2: debug port 1
[    2.330292] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.360224] hub 1-0:1.0: 5 ports detected
[    2.490563] ehci_hcd 0000:00:16.2: debug port 1
[    2.540313] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.569669] hub 2-0:1.0: 4 ports detected
[    2.778058] hub 3-0:1.0: 5 ports detected
[    2.954693] hub 4-0:1.0: 2 ports detected
[    3.147145] hub 5-0:1.0: 4 ports detected
[    3.194917] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.207856] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.233820] rtc_cmos 00:05: RTC can wake from S4
[    3.290475] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.303688] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    3.541745] rtc_cmos 00:05: setting system clock to 2012-02-26 13:15:22 UTC (1330262122)
[    3.726614] udev: starting version 151
[    4.009970] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    4.024065] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    4.035661] r8169 0000:06:00.0: eth0: RTL8101e at 0xffffc900050e0000, e4:11:5b:fc:64:4e, XID 00a00000 IRQ 40
[    4.149051] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.208906] [drm] No driver support for vblank timestamp query.
[    5.196439] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.964485] udev: starting version 151
[   11.435868] input: HP WMI hotkeys as /devices/virtual/input/input6
[   11.450944] rt5390 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   11.451103] rt5390 0000:07:00.0: setting latency timer to 64
[   11.451669] <-- RTMPAllocTxRxRingMemory, Status=0
[   11.451809] <-- RTMPAllocAdapterBlock, Status=0
[   13.765753] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[   13.781979] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[   21.209625] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[  752.250328] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[  761.791048] rt5390 0000:07:00.0: setting latency timer to 64
[  761.791821] <-- RTMPAllocTxRxRingMemory, Status=0
[  761.792045] <-- RTMPAllocAdapterBlock, Status=0
[  761.965526] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[  761.981040] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[  776.060989] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[  786.198466] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]

```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by chili555 on 2012-02-26
> ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]That's not a good thing!

I saw this: [http://forum.soft32.com/linux/Bug-588863-linux-image-686-rt3090sta-module-requires-Wireles-ftopict517808.html](http://forum.soft32.com/linux/Bug-588863-linux-image-686-rt3090sta-module-requires-Wireles-ftopict517808.html)> The rt3090sta module loads but does not function if the file
/etc/Wireless/RT2860STA/RT2860STA.dat is not present, thus breaking wifi
for devices using this module. This file corresponds to the wrong kernel
module name and is not distributed in any debian package. Note that the driver
functions correctly if the file is present but empty.

The file is reported as being optional for RT2860 but appears manditory for
rt3090.

Comparing rt2860/rt_profile.c and rt3090/rt_profile.c shows some
differences in the implementation of ***RTMPReadParametersHook*** which is the
function *which reads the file*.Let's make sure we have the correct .dat file in the right place. Please do:```
cd Downloads/RT5390 <--or wherever you extracted the driver
sudo su
mkdir /etc/Wireless/RT2860STA
cp RT2860STA.dat /etc/Wireless/RT2860STA/
exit
```Reboot and let's have another look at:```
dmesg | grep RT
```

---

### Post by Panos_Papajohn on 2012-02-26
I have two folders int the /etc/Wireless/ directory, RT2860STA and RT5390STA. The first one contains the RT2860STA.dat and the other one is empty. Is this relevant? Is there a way to go back to square one and uninstall everything and redo the whole process ? Whould this be easier? thnks

---

### Post by chili555 on 2012-02-26
> have two folders int the /etc/Wireless/ directory, RT2860STA and RT5390STA. The first one contains the RT2860STA.dat and the other one is empty.Let's try this:```
sudo cp /etc/Wireless/RT2860STA/RT2860STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
```Reboot and let's have another look at:
```
dmesg | grep RT
```Thanks.

---

### Post by Panos_Papajohn on 2012-02-26
OHHHHH YEAH. I can see my network now. Im writing this post from this connection now. Thank you very much for your help.
So to sum up I would like to describe this whole procedure in order to understand the problem completely. 
1) I downloaded the drivers for my wireless card
2) I patched  the drivers in order to work with my WiFi card model
3) made changes to the config file to much my device
4) I renamed the .dat file to much the name of my WiFi card
5) create a new folder in the /etc/Wireless/ directory and copy the .dat file in there

Is that correct? Can you correct any steps or add any that I forgot to mention? Thanks again

---

### Post by chili555 on 2012-02-26
Awesome! Glad it's working. The .dat file was covered in the original post you used: > patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
[COLOR="Red"]cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA[/COLOR]
make clean
make
make install
modprobe rt5390sta
exitPerhaps you missed that step or made a typo.> 1) I downloaded the drivers for my wireless card
2) I patched the drivers in order to work with my WiFi card model
3) made changes to the config file to much my device
4) I renamed the .dat file to much the name of my WiFi card
5) create a new folder in the /etc/Wireless/ directory and copy the .dat file in thereThat's it!

I'm not sure the patches are needed in the later driver version and later kernels.

When you get a later kernel version (also known as linux-image) by an update, you'll need to rebuild the driver as above.

Would you please use Thread Tools at the top and Mark Solved?

---

