---
title: "How do i remove wireless drivers?"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by jjjjeremy on 2010-11-15
I would like to install a windows driver with ndisgtk, and I have the .inf. [Here]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") it says that I first need to make sure that I don't have any wireless drivers already installed. How do I do that? I've spend about an hour looking here, and elsewhere, but I can't find anything.

Thanks,

- jjjjeremy

---

### Post by chili555 on 2010-11-15
You remove them by blacklisting them; first you have to know what they are. If you have a native driver loaded, why isn't it working? Maybe we can fix it.

Please tell us what card you have. If built-in, post:```
lspci -nn
```If it's USB, post:```
lsusb
```

---

### Post by uncaspi on 2010-11-15
Remove module and then blacklist them from beeing loaded.
Try sudo rmmod or perhaps it is sudo delmod
Blacklist located in /etc/modprobe.d/blacklist.conf

---

### Post by jjjjeremy on 2010-11-15
Thanks for replying quickly.

I'm having problems with my university's network. After connecting to the wireless, I get internet for a bit (5 seconds to 15 minutes), but after that my browser will hang a "Sending request . . . "

I wanted to try the Windows driver, because I'm not having any problems in Win7 on my other partition.

lspci -nn gives me:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```

Thanks for the help.

---

### Post by uncaspi on 2010-11-15
Take a look at this thread
[http://ubuntuforums.org/showthread.php?t=1286503&highlight=ar9285](http://ubuntuforums.org/showthread.php?t=1286503&highlight=ar9285)

---

### Post by chili555 on 2010-11-15
> AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)This card uses the driver ath9k. So do:```
sudo su
rmmod -f ath9k
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

---

### Post by jjjjeremy on 2010-11-15
Unfortunately for me, I got nothing.

After running "rmmod -f ath9k" I got No such file or directory.

Assuming that I had removed it in other attempts, I did ndisgtk and tried to install the .inf wireless driver, restarted, but wireless is now missing from the network manager taskbar icon (as well as a wireless enable toggle). I then removed the .inf driver with ndisgtk, and rebooted, again with no wireless.

Then, I tried the suggested thread. Terminal didn't give me any errors, but after a reboot I still don't have wireless.

Any more ideas?

---

### Post by chili555 on 2010-11-15
Please run:```
sudo lshw -C network
```What driver is associated with your card? Also try:```
lsmod | grep ath
ndiswrapper -l
```

---

### Post by jjjjeremy on 2010-11-15
lshw gives

```
   *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:16:e6:d8:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=129.81.194.44 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:3000(size=256) memory:90410000-90410fff(prefetchable) memory:90400000-9040ffff(prefetchable) memory:90420000-9043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:92600000-9260ffff
jeremy@jeremy-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:16:e6:d8:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=129.81.194.44 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:3000(size=256) memory:90410000-90410fff(prefetchable) memory:90400000-9040ffff(prefetchable) memory:90420000-9043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:92600000-9260ffff

```

"lshmod | grep ath" and "ndiswrapper -l" didn't do anything.

---

### Post by chili555 on 2010-11-15
> "ndiswrapper -l" didn't do anything.Then your ndiswrapper install didn't go well. Please retrace your steps. The command:```
ndiswrapper -l
```Is supposed to tell you the currently installed driver; you evidently have none.

No native driver is associated with your Atheros wireless card; that part is fine.

---

### Post by jamesjony2 on 2010-11-15
Linksys Wireless USB dongle a specific set of drivers that explain how to tell the computer signals.Assuming other efforts that I had removed the wireless, I was ndisgtk inf. Allows the driver tried to install wireless uses, restarted, but the wireless network manager taskbar icon is missing from now.

---

### Post by jjjjeremy on 2010-11-15
Now that I see that I don't have a driver installed, I entered ```
 sudo ndiswrapper -i windowsdriver.inf 
```

now ndiswrapper -l reads ```
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathrx : driver installed
	device (168C:002B) present (alternate driver: ath9k)

```

but I still don't have wireless in the network manager tray icon, or an enable toggle.

---

### Post by chili555 on 2010-11-16
Let's have a look at:```
dmesg | grep -e ndis -e ath
lsmod | grep -e ndis -e ath
```You can fix your other issue by doing:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by jjjjeremy on 2010-11-16
```
 dmesg | grep -e ndis -e ath 
``` gives 

```
[    0.410276] device-mapper: multipath: version 1.1.0 loaded
[    0.410280] device-mapper: multipath round-robin: version 1.0.0 loaded
[   10.606983] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.315576] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   12.315628] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   12.315672] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   12.315719] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'_local_unwind'
[   12.315764] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   12.315813] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   12.315854] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   12.315898] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   12.315939] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   12.315987] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   12.316026] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   12.316071] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   12.316123] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.316174] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   12.316222] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   12.316262] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   12.316306] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   12.316353] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   12.316393] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.316435] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   12.316477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   12.316528] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   12.316575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   12.316611] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   12.316652] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   12.316693] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   12.316731] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   12.316783] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   12.316819] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   12.316865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   12.316911] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   12.316957] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   12.317001] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   12.317040] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   12.317085] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.317130] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   12.317170] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   12.317213] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   12.317261] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   12.317303] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   12.317345] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   12.317381] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   12.317425] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   12.317475] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   12.317519] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   12.317561] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.318311] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   12.319070] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathrx'
[   12.321695] ndiswrapper (load_wrap_driver:108): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   12.323239] usbcore: registered new interface driver ndiswrapper
```


```
 lsmod | grep -e ndis -e ath 
``` gives

```
 ndiswrapper           244800  0
```

---

### Post by chili555 on 2010-11-16
It appears you may have either a Vista driver when it wants XP or else you have a 64-bit system with a 32-bit driver. Here is what man ndiswrapper-1.9 says, in part:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Windows [COLOR="RoyalBlue"]XP[/COLOR] drivers and kernel module to load the Windows [COLOR="RoyalBlue"]XP[/COLOR] drivers. Both are called ndiswrapper.

---

### Post by jjjjeremy on 2010-12-03
Ok, so I've searched around and haven't found an XP driver for my wireless card. How do I go back to the driver that ubuntu shipped with? Right now, it doesn't seem as if ubuntu is recognizing that I have a wireless card.

sudo ifconfig -a gives:

```
 jeremy@jeremy-laptop:~$ sudo ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1f:16:e6:d8:cc  
          inet addr:129.81.194.44  Bcast:129.81.194.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fee6:d8cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1837250 (1.8 MB)  TX bytes:274567 (274.5 KB)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14984 (14.9 KB)  TX bytes:14984 (14.9 KB)

```

---

### Post by chili555 on 2010-12-03
> How do I go back to the driver that ubuntu shipped with?Please do:```
sudo ndiswrapper -e netathrx
sudo rmmod -f ndiswrapper
sudo modprobe ath9k
iwconfig
```Is a wireless interface created? If so, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If the module ath9k is listed, please remove it and save and close gedit.

If you have no wireless interface, please post:```
dmesg | grep -i ath
```

---

### Post by jjjjeremy on 2010-12-03
Thanks for the help! Wireless is back and running fine!

ath9k wasn't blacklisted, but I remember it being there before. I must have taken it out earlier.


Wireless interface? What's that?

```
 dmesg | grep -i ath 
``` gives

```
 [    0.419057] device-mapper: multipath: version 1.1.0 loaded
[    0.419059] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 8626.600276] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8626.600293] ath9k 0000:02:00.0: setting latency timer to 64
[ 8626.651608] ath: EEPROM regdomain: 0x69
[ 8626.651610] ath: EEPROM indicates we should expect a direct regpair map
[ 8626.651613] ath: Country alpha2 being used: 00
[ 8626.651614] ath: Regpair used: 0x69
[ 8626.682045] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 8626.682624] Registered led device: ath9k-phy0::radio
[ 8626.682637] Registered led device: ath9k-phy0::assoc
[ 8626.682650] Registered led device: ath9k-phy0::tx
[ 8626.682663] Registered led device: ath9k-phy0::rx
[ 8626.682672] phy0: Atheros AR9285 Rev:2 mem=0xffffc90016520000, irq=17 
```

---

### Post by chili555 on 2010-12-03
> Wireless interface? What's that?It's the identifier that the system uses to connect the phsical hardware and the driver and then hand control to Network Manager. Here is mine:```
chili@LAPTOP60:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

[COLOR="Red"]wlan0 [/COLOR]    IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:56:AA:D7:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```If your wireless is running fine, you have no worries. Glad it's working.

---

