---
title: "NO Internet access ...please help..."
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by zombieub on 2011-07-27
hi ...i am totally new to linux and i love the concept...but the problem i am facing is i am not able to access my internet through ubuntu 11.04...i have dual boot windows 7 + ubuntu 11.04...
all i kknow and could know by googling is to run command in terminal....
Pasting the results ....

 [FONT=&quot]**[SIZE=4]sudo pppoeconf[/SIZE]**

Sorry, I scanned 1 interface, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason for  &#9474; 
          &#9474; the scan failure may also be another running pppoe       &#9474; 
          &#9474; process which controls the modem


[SIZE=4]**ifconfig**[/SIZE]

eth0      Link encap:Ethernet  HWaddr 00:25:64:72:2e:72  
          inet6 addr: fe80::225:64ff:fe72:2e72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720 (720.0 B)  TX bytes:4222 (4.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

[/FONT]
  wat am i doing wrong.....wat am i supposed to do....please help

---

### Post by Wayne_V on 2011-07-27
ubuntu desktop or server?

what type of internet service do you have?

how are you connected to your router/modem?

how do you connect in windows?

---

### Post by zombieub on 2011-07-27
> **Wayne_V said:**
> ubuntu desktop or server?

what type of internet service do you have?

how are you connected to your router/modem?

how do you connect in windows?


i have LAN....cable + router....however m trying to work it up with cable net first coz i guess my driver for wireless connectivity in ubuntu is missing.....


how am i connected......? not very sure of the answer....sorry about that....

how do i connect.....here it is....

Cable > into the laptop slot > open web browser > ISP opens a page by itself, asks for username and password > log in > internet is ready to use.....

wirelss > open web browser > ISP opens a page by itself, asks for username and password > log in > internet is ready to use.....

---

### Post by zombieub on 2011-07-27
okay may not be LAN....i have a cable internet with a router for wifi access at home....

UBUNTU DESKTOP !

---

### Post by Wayne_V on 2011-07-27
you shouldn't need to run pppoeconf in a terminal.  go to System->Preferences->Network Connections and try to configure it there.   I would see if your ISP has any guidelines for configuring Linux - if not, you may need to look at the Windows or Mac guidelines and try to figure out the equivalent steps in Linux.

---

### Post by zombieub on 2011-07-27
Thanks...

but the problem is i do not actually have any settings in windows...it is automatically detected.....and no need of any IP settings ...it is all done automatically....
so how do i do it in ubuntu...

---

### Post by Wayne_V on 2011-07-27
if your windows setting is just straight dhcp on eth0, without any special pppoe config, then the same should work in ubuntu.  do you have eth0 enabled for dhcp in system->preferences->network ?

---

### Post by zombieub on 2011-07-27
i treid these commands....
 [FONT=&quot]sudo ifup eth0[/FONT]
  [FONT=&quot]sudo ifup eth1[/FONT]
   
if that is what you mean....

the first one...says its ON...or similar result..

second says...IGNORED ....

---

### Post by zombieub on 2011-07-27
and also....i have ubuntu 11.04 which does not have system>preferences>network....all i get is search option from which i can at max access network connections menu...

---

### Post by Wayne_V on 2011-07-27
No, I mean to go to System->Prefenences->Network Connections and enable Automatic(DHCP) for IPv4 for wired connection eth0.

---

### Post by zombieub on 2011-07-27
thank you......for replying....

all i get in ubuntu 11.04 is wat the screen shot shows...please help....

---

### Post by Wayne_V on 2011-07-27
[https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html)

according to that 11.04 should be configured by default for DHCP.  try "sudo /etc/init.d/network restart".  then, unplug the cable and plug it back in and watch to see if the network icon changes.

might also post the output of "sudo mii-tool -v" and "sudo ethtool" (if they are installed, hopefully they are on the CD ...)

---

### Post by zombieub on 2011-07-27
[FONT=&quot]pasting the results...
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]sudo/etc/init.d/network restart[/FONT]
  [FONT=&quot]bash: sudo/etc/init.d/network: No such file or directory[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]sudo mii-tool-v[/FONT]
  [FONT=&quot]sudo: mii-tool-v: command not found[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]sudo ethtool[/FONT]
  [FONT=&quot]sudo: ethtool: command not found[/FONT]
  [FONT=&quot] [/FONT]

---

### Post by zombieub on 2011-07-27
tried manual setting....with my ip address.....doesnt work either....:(

---

### Post by lkjoel on 2011-07-27
Copy and paste this into a Terminal window:
```
sudo /etc/init.d/network restart
sudo mii-tool -v
sudo ethtool

```
You forgot a few spaces ;-)

---

### Post by zombieub on 2011-07-28
**[FONT=&quot]sudo /etc/init.d/network restart[/FONT]**
[B][FONT=&quot]
[/FONT][/B]
    [FONT=&quot]sudo: /etc/init.d/network: command not found[/FONT]
  [FONT=&quot]
[/FONT]
[FONT=&quot]sudo mii-tool -v[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]eth0: negotiated 100baseTx-FD flow-control, link ok[/FONT]
  [FONT=&quot]product info: vendor 00:50:43, model 38 rev 0[/FONT]
  [FONT=&quot]basic mode:   autonegotiation enabled[/FONT]
  [FONT=&quot]basic status: autonegotiation complete, link ok[/FONT]
  
[FONT=&quot]capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD[/FONT]
  [FONT=&quot]advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control[/FONT]
  [FONT=&quot]link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control[/FONT]
  [FONT=&quot]
[/FONT]
**[FONT=&quot]sudo ethtool[/FONT]**
[B][FONT=&quot]
[/FONT][/B]
  [FONT=&quot]sudo: ethtool: command not found[/FONT]

---

### Post by Wayne_V on 2011-07-28
that should be 'sudo /etc/init.d/networking restart'

try that, and then send the output of:

sudo ifconfig -a
for f in dmesg messages syslog daemon.log kern.log ; do echo "===== $f"  ; sudo tail -30 /var/log/$f ; done

---

### Post by zombieub on 2011-07-30
**[FONT=&quot]'sudo /etc/init.d/networking restart'[/FONT]**
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces[/FONT]
  [FONT=&quot] * Reconfiguring network interfaces...                                          Plugin rp-pppoe.so loaded.[/FONT]
  [FONT=&quot]                                                                         [ OK ][/FONT]
  **[FONT=&quot]bayar@bayar:~$ sudo ifconfig -a[/FONT]**
  [FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:25:64:72:2e:72  [/FONT]
  [FONT=&quot]          inet6 addr: fe80::225:64ff:fe72:2e72/64 Scope:Link[/FONT]
  [FONT=&quot]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
  [FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=&quot]          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]
  [FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:3866 (3.8 KB)[/FONT]
  [FONT=&quot]          Interrupt:18 [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]lo        Link encap:Local Loopback  [/FONT]
  [FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
  [FONT=&quot]          inet6 addr: ::1/128 Scope:Host[/FONT]
  [FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
  [FONT=&quot]          RX packets:16 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=&quot]          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=&quot]          collisions:0 txqueuelen:0 [/FONT]
  [FONT=&quot]          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]wlan0     Link encap:Ethernet  HWaddr 0c:ee:e6:d1:af:2b  [/FONT]
  [FONT=&quot]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
  [FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]
  [FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]

[FONT=&quot][/FONT]










  
**[FONT=&quot]for f in dmesg messages syslog daemon.log kern.log ; do echo "===== $f" ; sudo tail -30 /var/log/$f ; done[/FONT]**
  
[FONT=&quot][/FONT]
  
[FONT=&quot][   14.521048] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521051] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521053] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521056] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521058] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521060] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521063] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521066] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521068] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521070] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521072] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521075] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521077] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521080] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.521082] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:[/FONT]
  [FONT=&quot][   14.521085] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)[/FONT]
  [FONT=&quot][   14.552497] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT]
  [FONT=&quot][   14.552503] i915 0000:00:02.0: setting latency timer to 64[/FONT]
  [FONT=&quot][   14.567430] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining[/FONT]
  [FONT=&quot][   14.567434] [drm] MTRR allocation failed.  Graphics performance may suffer.[/FONT]
  [FONT=&quot][   14.568761] i915 0000:00:02.0: irq 46 for MSI/MSI-X[/FONT]
  [FONT=&quot][   14.568767] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).[/FONT]
  [FONT=&quot][   14.568769] [drm] Driver supports precise vblank timestamp query.[/FONT]
  [FONT=&quot][   14.603833] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'[/FONT]
  [FONT=&quot][   14.605275] Registered led device: b43-phy0::tx[/FONT]
  [FONT=&quot][   14.605349] Registered led device: b43-phy0::rx[/FONT]
  [FONT=&quot][   14.605420] Registered led device: b43-phy0::radio[/FONT]
  [FONT=&quot][   14.605482] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ][/FONT]
  [FONT=&quot][   14.651716] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem[/FONT]
  [FONT=&quot][   14.652633] fixme: max PWM is zero.[/FONT]
  [FONT=&quot]===== messages[/FONT]
  [FONT=&quot]tail: cannot open `/var/log/messages' for reading: No such file or directory[/FONT]
  [FONT=&quot]===== syslog[/FONT]
  [FONT=&quot]Jul 30 21:47:25 bayar rtkit-daemon[1249]: Successfully made thread 1447 of process 1447 (n/a) owned by '1000' high priority at nice level -11.[/FONT]
  [FONT=&quot]Jul 30 21:47:25 bayar rtkit-daemon[1249]: Supervising 7 threads of 3 processes of 2 users.[/FONT]
  [FONT=&quot]Jul 30 21:47:25 bayar pulseaudio[1447]: pid.c: Daemon already running.[/FONT]
  [FONT=&quot]Jul 30 21:47:26 bayar NetworkManager[721]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))[/FONT]
  [FONT=&quot]Jul 30 21:47:40 bayar NetworkManager[721]: last message repeated 4 times[/FONT]
  [FONT=&quot]Jul 30 21:47:40 bayar pppd[1195]: Timeout waiting for PADO packets[/FONT]
  [FONT=&quot]Jul 30 21:47:40 bayar pppd[1195]: Unable to complete PPPoE Discovery[/FONT]
  [FONT=&quot]Jul 30 21:47:47 bayar ntfs-3g[1653]: Version 2010.8.8 external FUSE 28[/FONT]
  [FONT=&quot]Jul 30 21:47:47 bayar ntfs-3g[1653]: Mounted /dev/sda3 (Read-Write, label "", NTFS 3.1)[/FONT]
  [FONT=&quot]Jul 30 21:47:47 bayar ntfs-3g[1653]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177[/FONT]
  [FONT=&quot]Jul 30 21:47:47 bayar ntfs-3g[1653]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sda3,blkdev,blksize=4096,default_permissions[/FONT]
  [FONT=&quot]Jul 30 21:47:47 bayar ntfs-3g[1653]: Global ownership and permissions enforced, configuration type 1[/FONT]
  [FONT=&quot]Jul 30 21:48:01 bayar NetworkManager[721]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar pppd[1850]: Plugin rp-pppoe.so loaded.[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar pppd[1852]: pppd 2.4.5 started by root, uid 0[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar ntpdate[1876]: Can't find host ntp.ubuntu.com: Name or service not known (-2)[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar ntpdate[1876]: no servers can be used, exiting[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar ntpdate[1914]: Can't find host ntp.ubuntu.com: Name or service not known (-2)[/FONT]
  [FONT=&quot]Jul 30 21:48:18 bayar ntpdate[1914]: no servers can be used, exiting[/FONT]
  [FONT=&quot]Jul 30 21:48:37 bayar NetworkManager[721]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))[/FONT]
  [FONT=&quot]Jul 30 21:48:45 bayar pppd[1195]: Timeout waiting for PADO packets[/FONT]
  [FONT=&quot]Jul 30 21:48:45 bayar pppd[1195]: Unable to complete PPPoE Discovery[/FONT]
  [FONT=&quot]Jul 30 21:48:45 bayar pppd[1195]: Terminating on signal 15[/FONT]
  [FONT=&quot]Jul 30 21:48:45 bayar pppd[1195]: Exit.[/FONT]
  [FONT=&quot]Jul 30 21:48:53 bayar pppd[1852]: Timeout waiting for PADO packets[/FONT]
  [FONT=&quot]Jul 30 21:48:53 bayar pppd[1852]: Unable to complete PPPoE Discovery[/FONT]
  [FONT=&quot]Jul 30 21:49:58 bayar pppd[1852]: Timeout waiting for PADO packets[/FONT]
  [FONT=&quot]Jul 30 21:49:58 bayar pppd[1852]: Unable to complete PPPoE Discovery[/FONT]
  [FONT=&quot]Jul 30 21:51:03 bayar pppd[1852]: Timeout waiting for PADO packets[/FONT]
  [FONT=&quot]Jul 30 21:51:03 bayar pppd[1852]: Unable to complete PPPoE Discovery[/FONT]
  [FONT=&quot]===== daemon.log[/FONT]
  [FONT=&quot]tail: cannot open `/var/log/daemon.log' for reading: No such file or directory[/FONT]
  [FONT=&quot]===== kern.log[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   14.605349] Registered led device: b43-phy0::rx[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   14.605420] Registered led device: b43-phy0::radio[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   14.605482] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ][/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   14.651716] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   14.652633] fixme: max PWM is zero.[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.020720] Console: switching to colour frame buffer device 200x56[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.020758] fb0: inteldrmfb frame buffer device[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.020760] drm: registered panic notifier[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.035788] acpi device:3c: registered as cooling_device2[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037008] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037164] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037190] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037671] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037715] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.037993] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.038025] HDA Intel 0000:00:1b.0: setting latency timer to 64[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.111012] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.111234] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.159132] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.230523] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.327338] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.327343] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found[/FONT]
  [FONT=&quot]Jul 30 21:47:03 bayar kernel: [   15.327346] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/FONT]
  [FONT=&quot]Jul 30 21:47:04 bayar kernel: [   16.552980] sky2 0000:09:00.0: eth0: enabling interface[/FONT]
  [FONT=&quot]Jul 30 21:47:04 bayar kernel: [   16.553224] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  [FONT=&quot]Jul 30 21:47:05 bayar kernel: [   16.614397] ppdev: user-space parallel port driver[/FONT]
  [FONT=&quot]Jul 30 21:47:06 bayar kernel: [   18.182779] sky2 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both[/FONT]
  [FONT=&quot]Jul 30 21:47:06 bayar kernel: [   18.182943] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready[/FONT]
  [FONT=&quot]Jul 30 21:47:10 bayar kernel: [   21.963154] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0[/FONT]
  [FONT=&quot]Jul 30 21:47:17 bayar kernel: [   28.752223] eth0: no IPv6 routers present[/FONT]
  [FONT=&quot]bayar@bayar:~$ [/FONT]
  [FONT=&quot] [/FONT]

---

### Post by westie457 on 2011-07-30
> Jul 30 21:47:03 bayar kernel: [ 15.327338] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Jul 30 21:47:03 bayar kernel: [ 15.327343] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Jul 30 21:47:03 bayar kernel: [ 15.327346] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Hi This looks like it can be the problem. What is the output of ```
lspci -nn
```

And ```
lshw -C network
```

---

### Post by zombieub on 2011-07-30
**lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)





**lshw -C network**

bayar@bayar:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:72:2e:72
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 0c:ee:e6:d1:af:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg

---

### Post by westie457 on 2011-07-30
From the output I see you have the b43lpphy package installed, that is right. However I am not sure if you have the other necessary package, b43-fwcutter.
So to be on the safe side open Synaptic and search for bcm. You should have 9 results in the window.
Now leave the one with lpphy alone. You need to install b43-fwcutter and remove any others with a green box, click apply. When installed a quick reboot should get your wireless and wired connections working. If not we will try something else.

---

### Post by zombieub on 2011-07-31
ok here is wat i did....

i downloaded the installation file in windows.....as in ubuntu to insal b43 - fwcutter it required internet access.....
after downloading the installation file in windows...i installed in unbuntu ...and installation was success....

still i see no internet ......also i noticed in synaptic ....that b43ipphy was not installed.....i did the same as above for ipphy...however installation of IPPHY showed some error...again relating to requirement of interenet for full installation.....

pasting the two links i downloaded both the files from.....


 [http://in.archive.ubuntu.com/ubuntu/...013-3_i386.deb]("http://in.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_013-3_i386.deb") (b43 - fwcuttr)
[http://in.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_4.174.64.19-5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_4.174.64.19-5_all.deb) (IPPHY)

---

### Post by zombieub on 2011-07-31
No internet connectivity after the reboot .....please help...

---

### Post by westie457 on 2011-07-31
> **zombieub said:**
> No internet connectivity after the reboot .....please help...

Run ```
rfkill list all
``` let us know the result

---

### Post by zombieub on 2011-07-31
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by westie457 on 2011-07-31
Still looking to see if it is a driver problem or another issue. 

Can you run ```
lshw -C network
``` And post the output in ```
 tags by clicking New Reply and the # symbol at the top of the message window

And the same with [CODE]ifconfig
```

---

### Post by zombieub on 2011-08-02
#
```

lshw -C network


WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:72:2e:72
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 0c:ee:e6:d1:af:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.















bayar@bayar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:72:2e:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

---

### Post by dineshs on 2011-08-04
First try to make the wired connection OK.For this connect cable and try step-1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2").Then see if the browser opens the login page.
Also can you please boot windows then run and post the result of ```
ipconfig /all
```

---

