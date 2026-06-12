---
title: "Intel Wireless in Natty"
date: 2010-12-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-12-09
There was a firmware issue (I believe) with Intel wireless cards starting in kernel 2.6.35 if I remember correctly. The "Fall" distros this year do not work for me due to Wireless failure. My wireless card is not recognized.

Is there any chance of this being fixed soon? Is there a recent launchpad bug report for this? I hope I won't be left in the dust.

---

### Post by seenthelite on 2010-12-10
The problem may be here.  etc/modprobe.d/intel-5300-iwlagn-disable11n.config.

options iwlagn 11n_disable=1

I have done this and it works.

# options iwlagn 11n_disable=1

---

### Post by kaldor on 2011-01-10
*bump*

I do not have Natty on the hardware that I am using right now. But I have seen this fix posted elsewhere for 10.10 and Fedora 14. I hear it causes slow connection issues.

Should this be fixed in 2.6.37?

---

### Post by MacUntu on 2011-01-10
How about telling us which wireless module you use? 6300agn and 3945abg working fine here (but the latter seems to cause problems for some users).

---

### Post by coffeecat on 2011-01-10
Intel 5100agn working fine here with 2.6.37 kernel in Natty.

---

### Post by kaldor on 2011-01-10
*Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)*

No wireless on any distro using 2.6.35 (Fedora 14, Ubuntu 10.10, etc)

---

### Post by mc4man on 2011-01-10
> Intel Corporation ...
Whatever your issue is it's not support for that card, have same on a couple of laptops and has always worked fine inc. 10.10,11.04, stock or custom kernel

> *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 61
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35.7-ck1-wellsee firmware=228.61.2.24 ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f1ffe000-f1ffffff

---

### Post by kaldor on 2011-01-10
I just loaded a Fedora 14 live CD and got this output. Apparently, Wireless IS detected but not running. Maybe post #2 is correct considering this output:

```

[liveuser@localhost ~]$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

[liveuser@localhost ~]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by Starks on 2011-01-10
Myself and others have been trying to figure this one out.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)

---

### Post by kaldor on 2011-01-10
> **Starks said:**
> Myself and others have been trying to figure this one out.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)

My problem is NO connection, not a slow one.

---

### Post by cariboo on 2011-01-10
Have you tried manually associating your wireless device? 

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

I had to use the above commands to get one of my wireless devices to work on both Fedora and openSUSE

---

### Post by kaldor on 2011-01-10
> **cariboo907 said:**
> Have you tried manually associating your wireless device? 

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

I had to use the above commands to get one of my wireless devices to work on both Fedora and openSUSE

Fedora 14 gave me this:

```

[root@localhost liveuser]# ifconfig wlan0 down
[root@localhost liveuser]# dhclient -r wlan0
[root@localhost liveuser]# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
[root@localhost liveuser]# 

```

I'll try it again on Natty soon.

---

### Post by hugmenot on 2011-01-10
Yeah, find the kill switch that disables your wireless and turn it on. Could be a little slider on the case or a combination like  like Fn-F7.

---

### Post by kaldor on 2011-01-10
> **hugmenot said:**
> Yeah, find the kill switch that disables your wireless and turn it on. Could be a little slider on the case or a combination like  like Fn-F7.

That's the first thing I tried. Sometimes my laptop has issues and I need to turn it off and back on, then it works. 

The difference this time is that NO distro with 2.6.35 kernel does anything. It's the first time since starting Linux that I've had no wireless.

---

### Post by hugmenot on 2011-01-11
> **kaldor said:**
> That's the first thing I tried. Sometimes my laptop has issues and I need to turn it off and back on, then it works. 

The difference this time is that NO distro with 2.6.35 kernel does anything. It's the first time since starting Linux that I've had no wireless.

Well, something sets rfkill. It could be software rfkill.

Go and run 

```
sudo dmesg -c
sudo rmmod iwlagn && sudo modprobe iwlagn
dmesg
```

And post that.

If you want even more info in another terminal run
```
tail -f /var/log/daemon.log
```
And post that too.

But rfkill is just disabling your card.

---

### Post by kaldor on 2011-01-11
Again from F14 live CD. Maybe a reboot is needed, because it wouldn't work on the live session ("Wireless is Disabled" and no option to tick the "enable wireless" in network manager).


```

[root@localhost liveuser]# dmesg -c
[  187.730161] iwlagn 0000:07:00.0: PCI INT A disabled
[  187.836497] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:d
[  187.836501] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  187.836761] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  187.836797] iwlagn 0000:07:00.0: setting latency timer to 64
[  187.836858] iwlagn 0000:07:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[  187.879959] iwlagn 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  187.880210] iwlagn 0000:07:00.0: irq 47 for MSI/MSI-X
[  187.883986] iwlagn 0000:07:00.0: loaded firmware version 228.61.2.24
[  187.885276] phy1: Selected rate control algorithm 'iwl-agn-rs'
[  216.913428] HP WMI: Unknown response received
[  217.695567] HP WMI: Unknown response received
[  256.882590] iwlagn 0000:07:00.0: PCI INT A disabled
[  256.917824] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:d
[  256.917828] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  256.917948] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  256.917984] iwlagn 0000:07:00.0: setting latency timer to 64
[  256.918265] iwlagn 0000:07:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[  256.961391] iwlagn 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  256.961507] iwlagn 0000:07:00.0: irq 47 for MSI/MSI-X
[  256.964809] iwlagn 0000:07:00.0: loaded firmware version 228.61.2.24
[  256.966153] phy2: Selected rate control algorithm 'iwl-agn-rs'
[root@localhost liveuser]# rmmod iwlagn && sudo modprobe iwlagn
[root@localhost liveuser]# dmesg
[  302.546110] iwlagn 0000:07:00.0: PCI INT A disabled
[  302.582470] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:d
[  302.582474] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  302.582596] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  302.582638] iwlagn 0000:07:00.0: setting latency timer to 64
[  302.582702] iwlagn 0000:07:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[  302.625789] iwlagn 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  302.625957] iwlagn 0000:07:00.0: irq 47 for MSI/MSI-X
[  302.629893] iwlagn 0000:07:00.0: loaded firmware version 228.61.2.24
[  302.630623] phy3: Selected rate control algorithm 'iwl-agn-rs'
[root@localhost liveuser]# 


```

Maybe a new wireless card is in order? :)

---

### Post by hugmenot on 2011-01-11
No that looks okay. Now do the same with the tail daemon.log line.

With dmesg I had expected to see something related to RF-kill.  Let’s check daemon.log.

And then check 

```
rfkill list
```

Not sure if that is included on the F14 disc.

---

### Post by mc4man on 2011-01-11
If this is a dell and you have a wireless switch (typically a slider), you could try booting to bios and disassociating wifi with the slider, ie. wifi will always be on. 
(would eliminate a (semi)-defective switch

---

### Post by kaldor on 2011-01-12
I just checked Fuduntu which uses Fedora 15 (rawhide's) 2.6.37 kernel and the issue persists. Just to be sure this isn't just my problem, I checked Lucid liveCD and all was fine.

I'll run the stuff shown above soon.

Hopefully I'll be able to use Natty without too much headache!

Cheers.

---

### Post by kaldor on 2011-01-13
I found my 10.10 disc (my internet's too slow to download an 11.04 CD lately... not bothering with 90 kb/s)

This looks interesting.

```
ubuntu@ubuntu:~$ sudo dmesg -c
[  267.149265] iwlagn 0000:07:00.0: PCI INT A disabled
[  267.198316] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  267.198319] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  267.198399] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  267.198413] iwlagn 0000:07:00.0: setting latency timer to 64
[  267.198456] iwlagn 0000:07:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[  267.237299] iwlagn 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  267.237386] iwlagn 0000:07:00.0: irq 47 for MSI/MSI-X
[  267.240511] iwlagn 0000:07:00.0: loaded firmware version 228.61.2.24
[  267.241528] phy1: Selected rate control algorithm 'iwl-agn-rs'
[  274.364469] HP WMI: Unknown response received
[  275.112308] HP WMI: Unknown response received


ubuntu@ubuntu:~$ sudo rmmod iwlagn && sudo modprobe iwlagn


ubuntu@ubuntu:~$ dmesg
[  407.260336] iwlagn 0000:07:00.0: PCI INT A disabled
[  407.306335] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  407.306338] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  407.306421] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  407.306434] iwlagn 0000:07:00.0: setting latency timer to 64
[  407.306662] iwlagn 0000:07:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[  407.345391] iwlagn 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  407.345476] iwlagn 0000:07:00.0: irq 47 for MSI/MSI-X
[  407.348587] iwlagn 0000:07:00.0: loaded firmware version 228.61.2.24
[  407.350961] phy2: Selected rate control algorithm 'iwl-agn-rs'


ubuntu@ubuntu:~$ tail -f /var/log/daemon.log
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> WiFi now disabled by radio killswitch
Jan 14 00:37:30 ubuntu NetworkManager[1538]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/wlan0, iface: wlan0)
Jan 14 00:37:30 ubuntu NetworkManager[1538]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 5)
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): now managed
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): bringing up device.
Jan 14 00:37:30 ubuntu NetworkManager[1538]: <info> (wlan0): deactivating device (reason: 2).
^C
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
ubuntu@ubuntu:~$ 

```

---

### Post by hugmenot on 2011-01-13
I’m not really familiar with rfkill. What is hp-wifi? Is that the little switch on the laptop case? Or is that some ACPI/BIOS like toggle.

Anyhow the tool can turn of the soft rfkill.

Try htis

```
sudo rfkill unblock wifi
```

---

### Post by hugmenot on 2011-01-13
Anyhow google should help now. Search "hp-wifi rfkill".

---

### Post by kaldor on 2011-01-14
Indeed... going to take a look at this again later today. 

Sorry about not using 11.04 for this and bringing F14 and 10.10 into the picture; it was more of a kernel question than a Natty question ;)

Hopefully this will be worked out.

---

### Post by kaldor on 2011-01-14
Didn't work...

```
ubuntu@ubuntu:~$ sudo rfkill unblock wifi
ubuntu@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

But then this user posted: [http://ubuntuforums.org/showpost.php?p=10020947&postcount=5](http://ubuntuforums.org/showpost.php?p=10020947&postcount=5)

```

rfkill list all
sudo rmmod -f hp_wmi
rfkill list all

```

Worked a charm on livecd. Hopefully this will work on a future install too :)

---

### Post by caj420 on 2011-04-18
I've come across this once before.  I have no idea why it occurs, but using the rfkill unblock seems to do job and get the wireless back in operation. thanks guys!

---

