---
title: "No Wlan0 while device is plugged in and driers are installed?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Mastermind1980 on 2009-11-02
Ok, here is what I did:

1. I downloaded and installed ndisgtk.
2. I got the WPN111 v2.0 Netgear drivers like they told me to in the Ndiswrapper Wiki.
3. I started Windows Wireless Drivers (ndisgtk) I added the file WPN111vx.inf. It said that its unable to see if the hardware is present. I rebooted and started the program again, same story.
4. The strange thing is that when I click away the Error with 'Ok' it sais: Hardware Present?: Yes.
5. Now I did the following commands:

```
mastermind@mastermind-Linux:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07b8:e004 D-Link Corp. Mass Storage Device
**Bus 001 Device 004: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And:

```
mastermind@mastermind-Linux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:83:c7:6b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)

```

And also:

```
mastermind@mastermind-Linux:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wpn111vx : driver installed
    device (1385:5F01) present

```

Another one:

```
mastermind@mastermind-Linux:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

And least but not last:

```
mastermind@mastermind-Linux:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

As I see here there is no Wlan0.... Also the flash on my WPN111 isnt flashing, it also keeps cold, normally it becomes warm if active.

I have no problem with LAN and Im just a few meters away from the router, also I have perfect internet on Windows XP, Vista and 7.

Please help me get internet trough my WPN111 usb internet adaptar!

Best Regards,
Mastermind

---

### Post by Mastermind1980 on 2009-11-02
Update: I installed it trough the Console too, it got wrong on -m and setting it up:

```
mastermind@mastermind-Linux:/etc/modprobe.d$ sudo ndiswrapper -m
[sudo] password for mastermind: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

mastermind@mastermind-Linux:/etc/modprobe.d$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

Anybody a clue?

---

### Post by ArcaVex on 2009-11-02
Is there not two  *.inf  files that need to be installed for most Netgear cards?

I am running a WG111T  and it has to have net*.inf  and ath*.inf   (for atheros chipset inside)  to run.

Are you running 64bit or 32bit Ubuntu?    (No firmware indicates incorrect driver)

---

### Post by Mastermind1980 on 2009-11-02
Only one Inf, Sys en cat file in the DRIVER map.
Im running 64 Bit.

---

### Post by Mastermind1980 on 2009-11-03
Bump

---

### Post by Mastermind1980 on 2009-11-04
*sigh* still no chance to enjoy Linux Ubuntu:

BUMP!

---

### Post by Mastermind1980 on 2009-11-05
bumping time

---

### Post by rencemc on 2009-11-05
I had the same problem when I had 9.04. When I upgraded to 9.10, then I could see the wlan0 - but my Belkin-N USB wireless adapter still won't connect. I had to plug in a Linksys-G USB wireless adapter I had kicking around. That one works. So I now have wlan0 & wlan1 - but the Belkin won't connect.

terry@terry-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"55Surrey"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:3D:B9:F3   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Link Quality=42/100  Signal level=42/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0


wlan0 is my Belkin that can't connect to the internet

---

### Post by Mastermind1980 on 2009-11-06
have you installed the correct drivers? My problem is that Wlan0 wont show up at all.

---

### Post by Tom Handsy on 2009-11-06
plase answer, i have the same problem!
i have evrything of drivers and **** installed but nothing shoiws up!

---

### Post by rencemc on 2009-11-06
I downloaded what I thought was the correct driver from Ralink and did the make & make install and all that and it still won't connect. The wlan0 was not even seen until I upgraded to 9.10.

---

### Post by rencemc on 2009-11-06
My system says that wlan0 (my Belkin that won't connect) is disabled. Here is the listing and the error listed when I try to enable the device.

terry@terry-desktop:~$ sudo lshw -C network
[sudo] password for terry: 
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: eth0
       version: 11
       serial: 00:14:bf:53:02:8f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:16 ioport:a000(size=256) memory:d9005000-d90053ff memory:80000000-8001ffff(prefetchable)
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:4c:81:92:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:0f:66:ee:cd:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320a usb-0000:00:02.1-6 ip=192.168.1.108 link=yes multicast=yes wireless=IEEE 802.11bg
terry@terry-desktop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable

---

### Post by rencemc on 2009-11-06
Mastermind & Tom,

  Are you both running Karmic 9.10 ?

---

### Post by fmfrisch on 2009-11-09
rencemc - I'm in the same boat. I have the Belkin-N USB adapte, had it working for almost a year. And then suddenly it just stopped working. I'm on 9.10. But I've had it working during the beta stages and im not so sure it's a update related issue.

---

### Post by Mastermind1980 on 2009-11-13
Im on 9.10 Indeed, still my problem ATM is just how to get it to make Wlan0 present. Whats the CONF error when running the command?

---

### Post by dagodemon42 on 2009-11-13
I am new to linux use, but I have noticed that wireless is sometimes listed as wlan1, wlan2, eth0, eth1, etc. If using Network Manager, check under wireless tab in edit connections. In WICD, sometimes changing interface number helps. I also have had to modprobe the driver to get a connection.(in my case "sudo modprobe b43". I truly hope this is helpful.

---

### Post by Mastermind1980 on 2009-12-29
Bumppppp still having this problem soo much later, I have tried everything but no results...

---

### Post by pytheas22 on 2009-12-30
Mastermind1980: please post the output of these commands (in this order) and hopefully it will provide a clue as to what's not working:
```

lsmod | grep ndis
sudo modprobe ndiswrapper
uname -rm
lshw -C Network
ndiswrapper -l
dmesg | grep -e ndis -e wlan
```

Note that some of those commands may have no output.

Your problem may be related to the card not being able to load firmware, but in any case the commands above should provide much clearer information.

---

### Post by SeaJayEmm on 2009-12-30
What do you get when you input ndiswrapper -l?

---

### Post by Mastermind1980 on 2009-12-30
I have done the commands you both said, but first I'd really like to thank you for your replies!

Here it comes!

```
mastermind@mastermind-Linux:~$ lsmod | grep ndis
mastermind@mastermind-Linux:~$ sudo modprobe ndiswrapper
[sudo] password for mastermind: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mastermind@mastermind-Linux:~$ uname -rm
2.6.31-14-generic x86_64
mastermind@mastermind-Linux:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:83:c7:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
mastermind@mastermind-Linux:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wpn111vx : driver installed
    device (1385:5F01) present
mastermind@mastermind-Linux:~$ dmesg | grep -e ndis -e wlan
[  225.622339] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  225.968429] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[  225.968438] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[  225.968445] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[  225.968474] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  225.968482] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  225.968496] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  225.968504] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[  225.968513] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  225.968520] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[  225.968528] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  225.968535] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[  225.968550] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  225.968561] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  225.968569] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  225.968577] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  225.968586] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  225.968594] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  225.968623] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  225.968633] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  225.968646] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  225.968654] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  225.968661] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  225.968669] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  225.968676] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  225.968684] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  225.968691] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[  225.968699] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  225.968706] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  225.968714] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  225.968721] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[  225.968729] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[  225.968736] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  225.968744] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[  225.968751] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  225.968759] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  225.968774] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  225.968780] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  225.968783] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wpn111vx'
[  225.969297] ndiswrapper (load_wrap_driver:108): couldn't load driver wpn111vx; check system log for messages from 'loadndisdriver'
[  225.969360] usbcore: registered new interface driver ndiswrapper
mastermind@mastermind-Linux:~$ 
```

---

### Post by pytheas22 on 2009-12-30
Thanks for the information.  I see two problems.  The first is that the ndiswrapper module was not being loaded.  That's simple to solve; just run this command once:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

and ndiswrapper will be added to a list of modules that the system loads automatically at each boot.

The second issue is that, from your 'dmesg' output, it looks like ndiswrapper doesn't like the Windows driver that you loaded into it.  Usually when this happens, trying a different version of the Windows driver (e.g., version 1.0 instead of 2.0, or the Windows 2000 driver instead of the Vista one) can make a difference.

I don't know where you got the current driver from, but [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=652910") contains an attachment for a Windows driver that's promised to work with ndiswrapper and your device.  To uninstall the current Windows driver and install the one from that thread, just run these commands:
```

sudo ndiswrapper -r wpn111vx
wget http://ubuntu-virginia.ubuntuforums.org/attachment.php?attachmentid=54578&d=1198939980
tar -xzvf attachment.php*
sudo ndiswrapper -i win-drivers/netwpn11.inf
```

(If the terminal hangs after the 'wget' command instead of returning you to the command prompt, press control-C to kill it once it has finished downloading the file.  I had to do this for some reason.)

Then reboot and see if things work.  If not, please let me know the output of:
```

dmesg | grep -e ndis -e wlan
sudo iwlist scan
ndiswrapper -l
```

---

### Post by Mastermind1980 on 2009-12-30
instead of all those commandos, can I just use the GUI I installed for ndiswrapper? :D
Its late here and my head is not exactly to it ;)

---

### Post by pytheas22 on 2009-12-30
You can use the GUI if you prefer. You will have to first use it to delete the Windows driver currently installed, then download the attachment containing the new Windows drivers from that thread I linked to in my previous post (the attachment is at the bottom of the first post in that thread), then extract the attachment, and finally use the ndiswrapper GUI to install the new driver.

That said, if I were you, I would just copy and paste the four commands (you can paste into the terminal by right-clicking and selecting paste), because that would be simpler for my tastes.  But either way will produce the same results.

---

### Post by Mastermind1980 on 2009-12-30
I used the GUI since I found it rather easier and since I don't have a LAN cable anywere near I need to go to my Windows to download anything, so I think wget (Wich I think is downloading) wont work anyways! :)

Anyway here are my disappointing results:

```
mastermind@mastermind-Linux:~$ echo ndiswrapper | sudo tee -a /etc/modules
[sudo] password for mastermind: 
ndiswrapper
mastermind@mastermind-Linux:~$



mastermind@mastermind-Linux:~$ dmesg | grep -e ndis -e wlan
[    8.096881] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    8.577878] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    8.577884] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netwpn11'
[    8.578272] ndiswrapper (load_wrap_driver:108): couldn't load driver netwpn11; check system log for messages from 'loadndisdriver'
[    8.578316] usbcore: registered new interface driver ndiswrapper
mastermind@mastermind-Linux:~$ sudo iwlist scan
[sudo] password for mastermind: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

mastermind@mastermind-Linux:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netwpn11 : driver installed
    device (1385:5F01) present
mastermind@mastermind-Linux:~$ 
```

---

### Post by pytheas22 on 2009-12-30
Didn't realize you have no wired connection available.  Thanks for letting me know.

The reason it didn't work this time is that you're running 64-bit Ubuntu but I had you install the 32-bit Windows driver into ndiswrapper (my mistake for not thinking of this).  On 64-bit Ubuntu, you need the 64-bit Windows drivers in order for ndiswrapper to work.

The Windows drivers you installed previously were 64-bit but didn't work for some reason.  If you can find other 64-bit drivers for this card (i.e., other versions of the win64 driver), you can give them a try and they may work better.

Otherwise, your only option may be to install 32-bit Ubuntu and then use the drivers you currently have installed.  That approach should definitely work.

---

### Post by Mastermind1980 on 2009-12-31
That sounds like a plan, ill just go and try every driver I can find :D
I just love 64-Bit machines and they run Much faster on my PC (i7 Overclocked to 3.5Ghz with 16 (!!) GB RAM )

Thanks for helping me, I think I will do these things this evening (Its morning now for me) or tommorow, Thanks for all the help!

---

### Post by Mastermind1980 on 2009-12-31
hmhmh, all the downloads from NETGEAR site are exe's. And since I don't want to **** my windows by installing every single exe for the files, is there an alternativve way of getting the files outta it or can somebody hand me over a few 64 bit versions?

---

### Post by pytheas22 on 2009-12-31
There are a few ways to open up the .exe files without installing them.  [7-zip]("http://www.7-zip.org/") can extract most .exe files and works on Windows and Linux.  The command-line utility cabextract (which you can install through the Ubuntu Software Center) can also usually extract them.  "unzip" also sometimes works in Ubuntu with simple .exe files.

And if all else fails, you can install wine in Ubuntu and just run the installers with it.  They won't make your wireless card work, but usually at some point during the installation the files you need will be extracted to some folder by the installer; once that happens you can can copy them to where you need.  This way you can run all the installers without worrying about mucking up your system, since a simple "rm -r ~/.wine" will clear everything out after you're done and leave with you a fresh wine configuration.

---

### Post by Mastermind1980 on 2009-12-31
Thanks, Ill try that!

---

### Post by Jurgen Oscar on 2010-06-04
> **Mastermind1980 said:**
> Thanks, Ill try that!

hello Mastermind1980,

the last post i read, you said you will try it, at least tomorrow, and
I figured it out it has been more than a year. :)  hehehehe.

Any chance to get a wlan driver works for x86_64 bit ?

Thanks

J.O.

---

### Post by pytheas22 on 2010-06-05
> **Jurgen Oscar said:**
> hello Mastermind1980,

the last post i read, you said you will try it, at least tomorrow, and
I figured it out it has been more than a year. :)  hehehehe.

Any chance to get a wlan driver works for x86_64 bit ?

Thanks

J.O.

You should be able to use ndiswrapper and 64-bit Windows drivers.  Have you tried?

---

