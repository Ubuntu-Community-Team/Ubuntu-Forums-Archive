---
title: "RTL8188CUS dosn't work - driver installed"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by Bob.Sponge on 2011-04-26
Hello,  

The USB adapter is connected to a PC with Win7 x64. 
Backtrack 4 R2 runs on VMWARE. 
I can't see the device in Wicd network manager nor I get any devices in airmon-gn.   

root@bt:~# lsusb Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

VMWARE is aware of the device.  

The device shows ONLY with ifconfig -a:
 ------- 
wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:e4:a8:e7           BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) -------  root@bt:~# iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     unassociated  Nickname:&quot;&quot;           Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0           Retry           Encryption key           Power Management           Link Quality=0/100  Signal level=0 dBm           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  

Driver was build successfully( from Realtek): 
root@bt:~# lsmod | grep 8192cu 
8192cu                305198  0  

root@bt:~# lshw -C network 
----------   
*-network DISABLED        
description: Wireless interface        
physical id: 1        
logical name: wlan0        
serial: 00:1f:1f:e4:a8:e7        
capabilities: ethernet physical wireless        
configuration: broadcast=yes multicast=yes wireless=unassociated  

The device fails to start: 
root@bt:~# ifconfig wlan0 up 
SIOCSIFFLAGS: Operation not permitted   

Linux noob, please advise, 
Bob  

P.S Don't judge me for running root, I'm Windows user...

---

### Post by Bob.Sponge on 2011-04-27
dump

---

### Post by josephmills on 2011-04-27
go to the backtrack icon(bottom left) then go to internet-->wicd mnager wait for it to start up if it does do you see your eth0?
also try ```
start network
``` 
or ```
/etc/init.d/networking start
```
also try [http://www.backtrack-linux.org/forums/backtrack-howtos/209-how-start-networking-backtrack.html](http://www.backtrack-linux.org/forums/backtrack-howtos/209-how-start-networking-backtrack.html)

---

### Post by Bob.Sponge on 2011-04-27
Hi,  

Wicd Network Manager only lists the wired connection (eth0). 
I am using it for internet and it works fine. 
 About the wireless it says: "No wireless networks found". 
  root@bt:~# /etc/init.d/networking start 
------------------------------------- 
SIOCSIFFLAGS: Operation not permitted 
SIOCSIFFLAGS: Operation not permitted 
Listening on LPF/wlan0/00:1f:1f:e4:a8:e7 
Sending on   LPF/wlan0/00:1f:1f:e4:a8:e7 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
if-up.d/mountnfs[wlan0]: waiting for interface eth1 before doing NFS mounts 
if-up.d/mountnfs[wlan0]: waiting for interface eth2 before doing NFS mounts 
if-up.d/mountnfs[wlan0]: waiting for interface ath0 before doing NFS mounts 

I think the problem lies here: 
root@bt:~# ifconfig wlan0 up 
SIOCSIFFLAGS: Operation not permitted  

Any ideas?  
Bob

---

### Post by josephmills on 2011-04-27
disconnect your eth0 and do a 
```

macchanger -r wlan0

```
if you get it great if not then. 
did you down load a bt4r2 vmware image? before install or is it a reg bt4r2 image? lets see a 
```

lspci -nn

```
please take out all ip and mac address (you have root priv)
```

lshw -C network

```

---

### Post by Bob.Sponge on 2011-04-27
josephmills,

Randomizing wlan0 MAC address did not help.

I installed BackTrack 4 R2 from and ISO image onto vmware.
Here is the lspci -nn printout:

root@bt:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 01)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 08)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:07.7 System peripheral [0880]: VMware Virtual Machine Communication Interface [15ad:0740] (rev 10)
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]
00:10.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev 01)
00:11.0 PCI bridge [0604]: VMware PCI bridge [15ad:0790] (rev 02)
00:15.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
02:00.0 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112]
02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
02:03.0 USB Controller [0c03]: VMware USB2 EHCI Controller [15ad:0770]

Here is lshw printout:

root@bt:~# lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:43:b1:aa
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.4.0 duplex=full firmware=N/A latency=64 link=yes maxlatency=255 mingnt=6 module=vmxnet multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: d6:10:ba:ad:ca:db
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=unassociated


Thanks,
Bob.

---

### Post by josephmills on 2011-04-27
> **Bob.Sponge said:**
> josephmills,

Randomizing wlan0 MAC address did not help.

I installed BackTrack 4 R2 from and ISO image onto vmware.
Here is the lspci -nn printout:

 please look at this [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)
which one did you use?

---

### Post by Bob.Sponge on 2011-04-28
> **josephmills said:**
> please look at this [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)
which one did you use?

**BackTrack 4 R2 Release ISO**

 [COLOR=#ff0000]Last Update: 22.11.2010[/COLOR]
 **Name:**: bt4-r2.iso  **Size**: 2000 MB  
 [**MD5**]("https://www.offensive-security.com/md5/bt4-r2.txt"): 9a94caa0e980a7331e9abc1d4c42c9a9  

Afterwards I installed vmware tools.

Bob.

---

### Post by AMSlider on 2011-05-20
They've got a new driver on the Realtek site for our chipset.  It may be worth a whirl... 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS")

Cheers

---

### Post by chrisauk0 on 2011-11-10
For recent kernels the rtl8192 that is in the kernel works. You just need the firmware file /lib/firmware/rtlwifi/rtl8192cufw.bin. The firmware should be in the firmware.
[http://packages.ubuntu.com/oneiric/all/linux-firmware/filelist](http://packages.ubuntu.com/oneiric/all/linux-firmware/filelist)

---

### Post by =CrAzYG33K= on 2012-03-05
> **AMSlider said:**
> They've got a new driver on the Realtek site for our chipset.  It may be worth a whirl... 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS")

Cheers

Mine was showing up as RTL8192cus (from lsusb). I was using a Sabrent USB-A11N wireless USB adapter (nano USB receiver).

I got the drivers for RTL8192CU from the Realtek drivers link posted by AMSlider. I just used the given install.sh script -> which makes/compiles and tries to insmod the .ko file. However, on using dmesg : ```
dmesg | grep rtl8192
```) I got the following error: ```
"Error: driver 'xxxxx' is already registered, aborting"
```

I found this thread on googling up the "Error: driver 'xxxxx' is already registered, aborting" message : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441303](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441303)

Someone suggested blacklisting the module in /etc/modprobe.d/blacklist.conf.

On googling how to blacklist a module, I hit up this link : [http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html](http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html)

I just blacklisted my relevant module by adding the line 
```
blacklist <module_name>
```
in ```
/etc/modprobe.d/blacklist.conf
```

Then, did a reboot.

Sure enough, ```
lsmod | grep rtl8192
``` did not come up with any any results.
The, I uncommented the blacklist line and happily ran
```
sudo ./install.sh
```

and the driver was properly installed! :P

---

