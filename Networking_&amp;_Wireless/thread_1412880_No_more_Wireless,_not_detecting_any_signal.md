---
title: "No more Wireless, not detecting any signal"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by UnkeptSpatula on 2010-02-21
I went to a hotel over the weekend and they only offered internet with a hardline. So I plugged in the Cat5, used the net over the weekend and left. When I came home my Pangolin was not detecting my wireless signal at the house. My roommate was online so I know the signal is there. I went to school and am still not able to detect any signals. I opened the Network Manager and no signal is shown. I then clicked *Connect to Hidden Wireless Network* The dropdown *Connection* tab had all of my wireless connections I have been using. I tried connecting and none of them would work. 
I can't figure it out. After scanning through forums for 2 hours I ran some terminal commands that may help

bash: Ispici-v: command not found 
(END)  
[1]+  Stopped                 Ispici-v | less 
unkeptspatula@unkeptspatula-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 
 
unkeptspatula@unkeptspatula-laptop:~$  lsmod

sr_mod                 22212  0  
cdrom                  43168  1 sr_mod 
sd_mod                 42392  5  
crc_t10dif              9984  1 sd_mod 
sg                     39732  0  
ahci                   37132  2  
ehci_hcd               43788  0  
libata                178336  1 ahci 
scsi_mod              155468  5 usb_storage,sr_mod,sd_mod,sg,libata 
uhci_hcd               30864  0  
dock                   16656  1 libata 
r8169                  37636  0  
mii                    13440  1 r8169 
usbcore               149616  6 usb_storage,libusual,uvcvideo,ehci_hcd,uhci_hcd 
thermal                23708  0  
processor              42156  4 acpi_cpufreq,thermal 
fan                    12548  0  
fbcon                  47648  0  
tileblit               10880  1 fbcon 
font                   16512  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 
fuse                   60956  3  
unkeptspatula@unkeptspatula-laptop:~$  ifconfig

          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1360 (1.3 KB)  TX bytes:1360 (1.3 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:c3:5c:9e   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-C3-5C-9E-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

unkeptspatula@unkeptspatula-laptop:~$ iwconfig

lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 
 
unkeptspatula@unkeptspatula-laptop:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results 
 
pan0      Interface doesn't support scanning. 

unkeptspatula@unkeptspatula-laptop:~$ lswh -C network

ast=yes wireless=IEEE 802.11abgn 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:90:f5:82:1d:87 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 26:4a:d1:95:42:6e 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 



Any other ideas? I could connect to wireless fine before I used the ethernet cord, but I have been unable to pick up a single signal since. :confused:

---

### Post by UnkeptSpatula on 2010-02-21
I have also tried restarting the computer, turning it off then on and going to the Network Manager and enabling networking and wireless through there.

---

### Post by northd_tech on 2010-02-21
> **UnkeptSpatula said:**
> 
bash: Ispici-v: command not found 
(END)  
[1]+  Stopped                 Ispici-v | less 

** lsmod**
Module   Size    Used by
**r8169**                  37636  0  
mii                    13440  1 **r8169** 
  
**ifconfig**

          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1360 (1.3 KB)  TX bytes:1360 (1.3 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:c3:5c:9e   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-C3-5C-9E-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

  **iwconfig**
 
wlan0     IEEE 802.11abgn  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B    
          Power Management: off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
 
  **sudo iwlist scan **
wlan0     No scan results 
 
**lswh -C network**

ast=yes wireless=IEEE 802.11abgn 
  *-network 
       description: Ethernet interface 
       product: **RTL8111/8168B** PCI Express Gigabit Ethernet controller 
       vendor: **Realtek** Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:90:f5:82:1d:87 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI latency=0 **module=r8169** multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 26:4a:d1:95:42:6e 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

That first comand is supposed to be lspci (lowercase of LSPCI, not Ispci).

It looks like you have a Realtek 8111/8168B ethernet controller (which has those r8169 driver modules loaded).  It is worth searching this forum for "realtek 8168" to find some threads about what goes wrong with those cabled ethernet connections.

I'm still not seeing what kind of wireless interface you've got (and I didn't see ANY modules in the **lsmod** output for what I would consider the "common" ones either).

One thing about the default Network Manager- it tries to keep a connection and will try to switch back and forth between wired when available and wireless at other times (when everything is working "perfectly" :roll: ).  Have you tried unplugging the ethernet cable before you restart ubuntu to "force" a wireless connection?  Sometimes the [Gnome] Network Manager will get "stuck" or confused.

A lack of wireless modules definitely points to a problem though from what I'm seeing.  Let's try to figure out what kind of WiFi hardware that is.

Can you post the results of these terminal commands (it looks like the lshw above got cut off a little):

```
lspci

lsusb

sudo lshw -C network

uname -a
```

---

### Post by UnkeptSpatula on 2010-02-21
Yea I noticed before how it will signals will jump from wireless once a hardline is put in. Yes previous to posting I had restarted the computer while the ethernet cable was _not_ plugged in. 

The commands I had posted above were from my computer while no ethernet was connected (ran command> copy paste to thumb drive). The commands I am going to paste right now are ran off of my computer while a ethernet is connected and I do have access to the web. Didn't know if that mattered at all. 

I also noticed that under the "lswh -C network" I ran it says "*-network DISABLED", I'm not to computer savvy so I don't know if that is related or not.

Here are the commands you requested north:

unkeptspatula@unkeptspatula-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
unkeptspatula@unkeptspatula-laptop:~$ 
unkeptspatula@unkeptspatula-laptop:~$ lsusb
Bus 008 Device 003: ID 5986:0300 Acer, Inc 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
unkeptspatula@unkeptspatula-laptop:~$ 
unkeptspatula@unkeptspatula-laptop:~$ sudo lshw -C network
[sudo] password for unkeptspatula: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:c3:5c:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:82:1d:87
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.16 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:a2:ed:d5:ba:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
unkeptspatula@unkeptspatula-laptop:~$ 
unkeptspatula@unkeptspatula-laptop:~$ 
unkeptspatula@unkeptspatula-laptop:~$ uname -a
Linux unkeptspatula-laptop 2.6.27-16-generic #1 SMP Tue Dec 1 17:56:54 UTC 2009 i686 GNU/Linux
unkeptspatula@unkeptspatula-laptop:~$ 

Thank you so much for your help. If it makes it easier, I can also post any screen shots if needed.

---

### Post by northd_tech on 2010-02-22
> **UnkeptSpatula said:**
>  **lspci**
02:00.0 Network controller: **Intel** Corporation **PRO/Wireless 5300 AGN [Shiloh]** Network Connection
06:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd. **RTL8111/8168B** PCI Express Gigabit Ethernet controller (rev 02)

  **sudo lshw -C network**
[sudo] password for unkeptspatula: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       **logical name: wmaster0**
       version: 00
       serial: 00:16:ea:c3:5c:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: **broadcast=yes** **driver=iwlagn** latency=0 **module=iwlagn** multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:82:1d:87
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 driverversion=2.3LK-NAPI** duplex=full ip=192.168.0.16 latency=0 link=yes **module=r8169** multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:a2:ed:d5:ba:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
 **uname -a**
Linux unkeptspatula-laptop **2.6.27-16-generic** #1 SMP Tue Dec 1 17:56:54 UTC 2009 **i686** GNU/Linux
OK- that's a 32-bit version of the 2.6.27-16-generic kernel (which is pretty old)- do you know if you are running Jaunty Jackalope 9.04 ubuntu or older?  That might actually be a good thing- there have been a lot of problems with the newer Karmic 9.10 version (but it might support new hardware better).

Your wireless is a **Intel** Corporation **PRO/Wireless 5300 AGN [Shiloh]** with the logical name "wmaster0" and uses the driver **iwlagn.**

Can you post the results of this terminal command:
```
lsmod | grep iw
```

I have never worked with that particular wireless though.  There have been a bunch of

 recent threads here though- you might want to read the ones with the most posts/replies- they usually have the most information.

Here are some threads for that Intel 5300AGN "Shiloh" wireless:

[http://ubuntuforums.org/showthread.php?t=1379731](http://ubuntuforums.org/showthread.php?t=1379731)

[This is a good thread with a bug report, and chili555 is a good man IMHO]
[http://ubuntuforums.org/showthread.php?t=1246253](http://ubuntuforums.org/showthread.php?t=1246253)

[Post #3 has a fix, but it is for a 64-bit version of the newer Karmic 9.10]
[http://ubuntuforums.org/showpost.php?p=8813890&postcount=3](http://ubuntuforums.org/showpost.php?p=8813890&postcount=3)

[More chili here, and a possible fix]
[http://ubuntuforums.org/showthread.php?t=1409529](http://ubuntuforums.org/showthread.php?t=1409529)

Good luck.

---

### Post by UnkeptSpatula on 2010-02-22
unkeptspatula@unkeptspatula-laptop:~$ lsmod | grep iw
iwlagn                 99716  0 
iwlcore                94404  1 iwlagn
rfkill                 17048  2 iwlcore
led_class              12164  1 iwlcore
mac80211              216948  2 iwlagn,iwlcore
cfg80211               32520  3 iwlagn,iwlcore,mac80211
unkeptspatula@unkeptspatula-laptop:~$ 


I am not sure what version and my mind is fried from studying finance lectures all day haha. I know my update manager says somethin like "new software distribution available 'Ubuntu 9.04'" or something along those lines, so I am guessing it's older. I will look threw those links and post my progress tomorrow. Thanks again North

---

### Post by northd_tech on 2010-02-22
> **UnkeptSpatula said:**
>  I know my update manager says somethin like "new software distribution available 'Ubuntu 9.04'" or something along those lines, so I am guessing it's older. I will look threw those links and post my progress tomorrow.

I'm back in ubuntu now (Gollum sez: Na$$ty Windoze Vi$$tases ;) ) so I can finally check my notes from a Linux file system.

Try this command for your ubuntu version:

```
cat /etc/lsb-release
```

That last lsmod command is modified specifically for those Intel 5300AGN driver modules (that look OK to me, but I honestly don't have a clue what those specific ones are supposed to look like).  It is common for one module to depend upon several others and that is what it looks like.

You might want to post on one of those other "Intel 5300" threads and link to the results above- someone who is running that same hardware should know more about those Intel beasts than I do.  I've never even seen one before.

---

### Post by UnkeptSpatula on 2010-02-22
unkeptspatula@unkeptspatula-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

I have not had time to go through your suggested links yet, I will be able to look tonight

Thanks

---

