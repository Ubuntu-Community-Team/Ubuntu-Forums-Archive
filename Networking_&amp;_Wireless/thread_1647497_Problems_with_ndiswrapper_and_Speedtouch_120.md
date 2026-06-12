---
title: "Problems with ndiswrapper and Speedtouch 120"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by stampatore on 2010-12-17
I have a Speedtouch 120 which works fine with my Windows XP setup. 

After installing ndiswrapper on my Linux setup I tried loading both the Windows XP and the Windows 98 drivers. In both cases I get the same problem. 

$ lsusb
Bus 001 Device 003: ID 0d4e:1000 Agere Systems Netherland BV Wireless Card Model 0801

$ ndiswrapper -l
wlags51 : driver installed
        device (0D4E:1000) present

All looking good so far. But I can't see any wireless connections: 

$ lshw -C Network
*-network
   description: Ethernet interface
   physical id: 1
   logical name: eth0
   serial: 00:00:e8:ea:a1:1a
   capabilities: ethernet physical
   configuration: broadcast=yes multicast=yes

No mention of wireless at all.

Then I try
$ modprobe ndiswrapper

and the system just hangs

demsg
gives me
ndiswrapper: driver wlags51 (Agere Systems,04/30/2002, 7.62.0.316) loaded
ndiswrapper (IofCallDriver:344): invalid irp: d7014540, 0
ndiswrapper (IofCallDriver:344): invalid irp: d7014900, 0
BUG: unable to handle kernel paging request at 55656489

Can anyone point me in the right direction to investigate and resolve this issue?

---

### Post by chili555 on 2010-12-17
Please see: [http://forums.opensuse.org/english/get-help-here/wireless/403415-need-help-ndiswrapper.html](http://forums.opensuse.org/english/get-help-here/wireless/403415-need-help-ndiswrapper.html)

Please notice his device is the same:> ID 0d4e:1000 Agere Systems Netherland BV Wireless Card Model 0801And his solution is:> In the meantime I have solved the problem, and I'm not using any windows drivers at all.

To close this thread, I'll give some directions to other Linux users that are searching for such driver.

The driver that worked for me is called orinoco_usb.The module orinoco_usb is already a part of recent kernels. Did you try it? Is it loading and interfering with ndiswrapper?```
lsmod | grep orinoco
```

---

### Post by chili555 on 2010-12-17
Upon further research, I believe the orinoco_usb driver requires firmware orinoco_ezusb_fw which is not installed by default. I am working out where to download it and install it.

---

### Post by stampatore on 2010-12-18
Thanks for pointing me in this direction. It's been helpful but unfortunately not successful. 

"make" is failing for orinoco_usb even after patching with orinoco_usb-2.6.27.patch

One of the errors is:

/home/nick/orinoco_usb/usb/orinoco_usb.c: In function ‘ezusb_probe’:
/home/nick/orinoco_usb/usb/orinoco_usb.c:1465: error: ‘struct net_device’ has no member named ‘hard_start_xmit’

From what I can gather from the net, version 2.6.31 removed support for the old net_device api and this may be causing the problem? (I'm running 2.6.32).

Seems to be dead-end time.

---

### Post by chili555 on 2010-12-18
Please recall I said:> The module orinoco_usb is already a part of recent kernels.There is no reason to download and build a stale module.> (I'm running 2.6.32).Do you have the module?```
modinfo orinoco_usb
```

Is the firmware file I referred to included in the package?

---

### Post by stampatore on 2010-12-19
Thanks for your continued help.

I can't find orinoco_usb on my system. I tried 
$ modinfo orinoco_usb
ERROR: modinfo: could not find module orinoco_usb

However, I did find orinoco_cs
$ modinfo orinoco_cs
filename:       /lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
license:        Dual MPL/GPL
description:    Driver for PCMCIA Lucent Orinoco, Prism II based and similar wireless cards
author:         David Gibson <hermes@gibson.dropbear.id.au>
srcversion:     09C1D35793FA77748DE09B3
alias:          pcmcia:m*c*f*fn*pfn*pa273FE3DBpb32A1EAEEpc*pd*
alias:          pcmcia:m*c*f*fn*pfn*paA5F472C2pb590EB502pcC9049A39pd*
--- etc
--- etc
depends:        pcmcia,orinoco,pcmcia_core
vermagic:       2.6.32-26-generic SMP mod_unload modversions 586 
parm:           ignore_cis_vcc:Allow voltage mismatch between card and socket (int)

This seems to be the pcmcia version which is included in the linux kernel. My Speedtouch 120, however, is the usb version and my understanding is that I have to use orinoco_usb which doesn't seem to be included in the kernel - or I can't find it. 

The version of orinoco_usb that I have (the one I've not been able to install) was downloaded from 
orinoco.svn.sourceforge.net

It does include a firmware folder which contains
get_ezusb_fw
which seems to be designed to download the firmware

I am very new to this but it does seem a bit previous to do anything with the firmware before I have a working orinico_usb module?

---

### Post by chili555 on 2010-12-19
It is a bit previous, however, if you had the module on your system, the firmware would have been the only thing standing in the way.

You are correct. orinoco_cs is for the PCMCIA device.

It seems you are stuck in the middle. the downloadable tarball is too old for your system, yet your system is not new enough to have orinoco_usb in it. It seems we have two choices: first, upgrade your system to 10.10 where orinoco_usb is present or try to fine-tune your ndiswrapper install.

You could try the live CD to see if the orinoco_usb module works. I have worked out the firmware issue, using clues here: [http://wireless.kernel.org/en/users/Drivers/orinoco](http://wireless.kernel.org/en/users/Drivers/orinoco)> wget [http://www.lsi.com/DistributionSystem/AssetDocument/support/downloads/legacy/windows_drivers_sr02-2.3.zip](http://www.lsi.com/DistributionSystem/AssetDocument/support/downloads/legacy/windows_drivers_sr02-2.3.zip)

unzip windows_drivers_sr02-2.3.zip WLAGS51.SYS

dd if=WLAGS51.SYS of=orinoco_ezusb_fw skip=10312 count=436 bs=16

Perhaps the various .sys files did not get installed in ndiswrapper. Find out with:```
ls /etc/ndiswrapper
```It appears, from the above, that WLAGS51.SYS is required.

---

### Post by stampatore on 2010-12-19
I'm trying the ubuntu 10.10 option. No doubt I'll be back for help with more issues to resolve!

---

### Post by stampatore on 2010-12-20
OK, lots of progress but still not quite there yet.

I installed 10.10 maverick and that does have orinoco_usb in the kernel. I tried to load the firmware patch but it didn't seem to end up in the right place:

```
$ dmesg | grep orinoco
[   35.247410] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   35.874913] orinoco_usb 0.15 (Manuel Estrada Sainz)
[   36.595823] orinoco_usb: No firmware to download
[   36.595917] orinoco_usb: probe of 1-2.1:1.0 failed with error -14
[   36.596015] usbcore: registered new interface driver orinoco_usb
```It looked as though I had got the firmware in the wrong location so I then simply copied oricono_ezusb_fw into /lib/firmware and rebooted.

More progress! interface eth1 now appeared

I set up eth1 as a wireless connection using the Network Manager gui via System | Network Tools (set up SSID and WEP key) and then tried connecting but it seemed to hang, dmesg shows lots of messages saying

```
[ 1446.807110] eth1: Lucent/Agere firmware doesn't support manual roaming
```Thought this might be a problem with the gui network manager so I tried to configure eth1 using the command line following instructions on [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

```
$ sudo ifconfig eth1 down
$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 1144
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:02:2d:88:0c:f2
Sending on   LPF/eth1/00:02:2d:88:0c:f2
Sending on   Socket/fallback
$ sudo ifconfig eth1 up
$ sudo iwconfig eth1 essid "<SSID>"
$ sudo iwconfig eth1 key <WEP KEY>
$ sudo iwconfig eth1 mode Managed
$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:02:2d:88:0c:f2
Sending on   LPF/eth1/00:02:2d:88:0c:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```So something still not quite right. Googled a bit more and found some suggestions that Network Manager could be causing the problem and recommending wicd instead. Loaded wicd and removed network-manager. Configured wicd to tell it that my wireless connection is eth1. Refreshed network list and suddenly, for the first time, got a list of all my local wifi networks. Small hurrah.

Selected my wifi network and configured it with WEP key then tried to connect. Got message "Connection Failed: Bad password". Changed WEP type from WEP (Hex [0-9/A-F]) to WEP Shared/Restricted and tried again. System froze.

I've double checked the WEP key and it's correct. I see other people have had similar problems but I can't find a solution. So nearly there.

To make matters worse I've now managed to lose my wired connection as well (possibly because I accidentally deleted my wired profile in wicd) - get the message that it's unable to find an ip address. Further googling suggests this might be a wicd problem and recommends going back to network-manager! Maybe I should just go back to xp. 


Current status of system given by various commands: 

```
$ lshw -C network
  *-network:0             
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:00:e8:ea:a1:1a
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:88:0c:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=2.6.35-23-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
``````
$ lsmod | grep orinoco
orinoco_usb            16857  0 
orinoco                64558  1 orinoco_usb
cfg80211              144470  1 orinoco
``````
$ lsusb
Bus 001 Device 003: ID 0d4e:1000 Agere Systems Netherland BV Wireless Card Model 0801
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e8:ea:a1:1a  
          inet6 addr: fe80::200:e8ff:feea:a11a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:157 dropped:0 overruns:0 carrier:310
          collisions:2635 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33980 (33.9 KB)
          Interrupt:11 Base address:0x220 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:88:0c:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:00:e8:ea:a1:1a  
          inet addr:169.254.8.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)
``````
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"O2wireless186162"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2010-12-20
You are making great progress. Let's see if the system has any interesting clues. Please run and post:```
dmesg | grep -e orinoco -e eth
```

---

### Post by stampatore on 2010-12-20
Here it is. The first part is immediately following reboot. From about [117.] or [119.] it's after I tried to reconnect to my router using wicd. 

```
$ dmesg | grep -e orinoco -e eth
[   35.168973] NE*000 ethercard probe at 0x220:00:00:e8:ea:a1:1a
[   35.227353] eth0: NE2000 found at 0x220, using IRQ 11.
[   36.737247] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   36.908271] orinoco_usb 0.15 (Manuel Estrada Sainz)
[   38.179881] usbcore: registered new interface driver orinoco_usb
[   41.806808] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   41.923776] eth1: New link status: Connected (0001)
[   41.924047] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   46.816704] NETDEV WATCHDOG: eth0 (): transmit queue 0 timed out
[   46.816713] Modules linked in: r128 drm binfmt_misc parport_pc ppdev michael_mic snd_ens1371 gameport snd_ac97_codec ac97_bus snd_pcm snd_seq_midi orinoco_usb snd_rawmidi orinoco snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 intel_agp ne snd psmouse 8390p soundcore serio_raw lp shpchp snd_page_alloc i2c_piix4 agpgart parport firewire_ohci aic7xxx firewire_core scsi_transport_spi crc_itu_t
[   46.817334] eth0: Tx timed out, cable problem? TSR=0x16, ISR=0x0, t=58.
[   50.135269] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   50.250389] eth1: New link status: Connected (0001)
[   50.250659] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   60.481424] eth1: no IPv6 routers present
[   62.361530] eth0: no IPv6 routers present
[  111.820410] eth0: Tx timed out, cable problem? TSR=0x16, ISR=0x0, t=65.
[  116.697993] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  116.885332] eth1: New link status: Connected (0001)
[  116.885616] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  117.103021] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  117.512233] eth1: New link status: Connected (0001)
[  117.512512] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  119.020819] eth0: Tx timed out, cable problem? TSR=0x16, ISR=0x0, t=53.
[  119.655435] eth1: Lucent/Agere firmware doesn't support manual roaming
[  120.101872] eth1: Lucent/Agere firmware doesn't support manual roaming
[  125.849648] eth1: Lucent/Agere firmware doesn't support manual roaming
[  127.717321] eth0: no IPv6 routers present
[  128.325360] eth1: no IPv6 routers present
[  131.637417] eth1: Lucent/Agere firmware doesn't support manual roaming
[  137.370107] eth1: Lucent/Agere firmware doesn't support manual roaming
[  143.774525] eth1: Lucent/Agere firmware doesn't support manual roaming
[  149.627619] eth1: Lucent/Agere firmware doesn't support manual roaming
[  155.298637] eth1: Lucent/Agere firmware doesn't support manual roaming
[  158.274951] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  169.023708] eth0: no IPv6 routers present
[  240.537476] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  240.696763] eth1: New link status: Connected (0001)
[  240.697031] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  251.420503] eth1: no IPv6 routers present
[  283.464487] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  283.650632] eth1: New link status: Connected (0001)
[  283.650906] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  284.016250] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  284.272532] eth1: New link status: Connected (0001)
[  284.272804] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  286.554371] eth1: Lucent/Agere firmware doesn't support manual roaming
[  287.128821] eth1: Lucent/Agere firmware doesn't support manual roaming
[  293.016697] eth1: Lucent/Agere firmware doesn't support manual roaming
[  294.318999] eth1: no IPv6 routers present
[  294.807028] eth0: no IPv6 routers present
[  299.011012] eth1: Lucent/Agere firmware doesn't support manual roaming
[  304.854461] eth1: Lucent/Agere firmware doesn't support manual roaming
[  310.678495] eth1: Lucent/Agere firmware doesn't support manual roaming
[  316.580699] eth1: Lucent/Agere firmware doesn't support manual roaming
[  322.391796] eth1: Lucent/Agere firmware doesn't support manual roaming
[  322.478639] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  333.081254] eth0: no IPv6 routers present

```

---

### Post by chili555 on 2010-12-20
First of all, if it is at all an option, I'd suggest WPA2 over WEP. If your router or other equipment doesn't support WPA2, then you are stuck.

Here is an interesting piece: [http://wireless.kernel.org/en/users/Drivers/orinoco](http://wireless.kernel.org/en/users/Drivers/orinoco)> Known issues

Roaming and WPA_supplicant

Lucent/Agere firmware doesn't support manual roaming

On the Agere cards, roaming is controlled by the firmware instead of userspace. You will get the above message if userspace attempts to associate with a specific AP rather than by SSID.

If you are using wpa_supplicant use ap_scan=2 mode.

NetworkManager uses wpa_supplicant, so the above also applies. Wicd uses wpa_supplicant, also.

You might edit /etc/wicd/encryption/templates/wep-hex like this:```
name = WEP (Hex [0-9/A-F])
author = Adam Blackburn
version = 1
require key *Key
-----
ctrl_interface=/var/run/wpa_supplicant
[COLOR="Red"]ap_scan=2[/COLOR]
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       key_mgmt=NONE
       wep_key0=$_KEY
       wep_tx_keyidx=0
       priority=5
}

```Try to connect and let us see a dmesg again.

---

### Post by stampatore on 2010-12-20
Thanks for the continued help and advice. I'm willing to have a go at anything, but I'm not sure about your suggestion

> I'd suggest WPA2 over WEP

since the page you quote says

> **[SIZE=2]not supported[/SIZE]**

 
[LIST]
[*]WPA2
[*]WPA-PSK (CCMP)
[/LIST]


so wouldn't I be going in the wrong direction to try to use WPA2?

---

### Post by chili555 on 2010-12-20
Oops! Sorry 'bout that. Please try WPA.

---

### Post by stampatore on 2010-12-20
I've switched my router over to using WPA (preshared key) and have reconnected with no problem using my netbook running windows xp. 

I changed 3 encryption template files (wep-hex, wpa, wpa-psk) to add the line 
ap_scan=2 

Then rebooted and tried to connect again. Still failing with bad password. dmesg output follows - interesting there is still the doesn't support manual roaming message.

```
$ dmesg | grep -e orinoco -e eth1
[   36.404351] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   36.595660] orinoco_usb 0.15 (Manuel Estrada Sainz)
[   37.812718] usbcore: registered new interface driver orinoco_usb
[   42.326318] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.408685] eth1: New link status: Connected (0001)
[   42.408953] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   49.983744] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   50.045383] eth1: New link status: Connected (0001)
[   50.045657] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   60.423656] eth1: no IPv6 routers present
[  119.272646] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  119.456388] eth1: New link status: Connected (0001)
[  119.456741] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  121.803004] Modules linked in: r128 drm binfmt_misc parport_pc ppdev snd_ens1371 michael_mic gameport snd_ac97_codec ac97_bus snd_pcm snd_seq_midi orinoco_usb snd_rawmidi orinoco snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 intel_agp ne snd psmouse 8390p soundcore shpchp serio_raw i2c_piix4 lp agpgart snd_page_alloc parport firewire_ohci aic7xxx firewire_core scsi_transport_spi crc_itu_t
[  129.714237] eth1: no IPv6 routers present
[  163.978267] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  164.297838] eth1: New link status: Connected (0001)
[  164.298107] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  164.523070] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  164.911644] eth1: New link status: Connected (0001)
[  164.911916] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  167.501430] eth1: Lucent/Agere firmware doesn't support manual roaming
[  175.182731] eth1: no IPv6 routers present
[  204.010026] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by stampatore on 2010-12-20
Oops, just seen that WPA-PSK (CCMP) isn't supported either, so maybe I need to use some other version of WPA? Unfamiliar territory for me.

---

### Post by stampatore on 2010-12-20
Just as a temporary test I've removed encryption from my router altogether and have been able to connect ok - and am using this wireless connection to post this. This is good, though obviously not a long term secure solution. 

I'll continue to experiment with various settings to see whether I can crack it. In the meantime, if you have any further ideas, do please post them for me. I'm very grateful for all your help so far.

---

### Post by stampatore on 2010-12-22
To leave things reasonably neat, here's my final status summary.

**Issue**: 
getting ubuntu to work with Agere USB wireless card model 0801 (badged as Speedtouch 120). 

**Config**: 
PC - old Fujitsu Siemens Pentium III running ubuntu 10.10 maverick
Network manager - wicd
Wireless router - Thomson TG585v7 (badged as O2 wireless II) - security configuration:
```
Broadcast Network Name:    Yes
Allow New Devices:    New stations are allowed (automatically)
Security Mode:        WPA-PSK
WPA-PSK Preshared Key:    <KEY>
WPA-PSK Encryption:    TKIP
WPA-PSK Version:    WPA

```**Summary**:

[LIST=1]
[*]I can get it to work fine if I totally disable encryption on the wireless router but this is clearly not an acceptable solution
[*]I can get it to connect briefly using WPA encryption and manual startup but only long enough to load one page in Firefox before it drops
[*]It's taken me over 20 hours to get this far and there's clearly still a long way to go with no clear path
[*]I've decided to bin the usb device and instead am using a TP-Link WA500G wireless access point as a bridge between two lans, so my ubuntu pc uses its wired ethernet connection. Working perfectly.
[*]I've learned a lot (not least of which is don't do that again!)
[/LIST]

Many thanks to chili555 for essential assistance.

================================================================

And some final details for anyone who's interested: 

**Connecting using WPA**

Several people on the net say that remnants of network-manager can cause interference with wicd. The solution to this was: 

```
$ sudo apt-get purge network-manager
```This removed everything apart from a couple of folders with some files left in them so I removed these manually and then rebooted the system. 

Still had a problem (bad password) trying to connect using the wicd gui. 

Further googling suggested a workaround:

I set up copy of the encryption template wpa-psk (wpa-psk-minimal-NB) with minimal info including the actual SSID and WPA key as follows:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
       ssid="O2wirelessxxxxxx"
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<hex key>"
}
```I then ran

```
$ sudo wpa_supplicant -i eth1 -D wext -c /etc/wicd/encryption/templates/wpa-psk-minimal-NB -B
```And brief success! It connected successfully and authenticated ok and I was able to load the bbc.co.uk home page but then lost connection within a few seconds (not long enough to load a second page)

Further googling showed quite a few people with similar problems of connections dropping out after a short time. The few suggested solutions were all different from each other and included upgrading and/or downgrading o/s and/or network software and/or many other system tweaks. Faced with another possible 20 hours of trial and error I put my hands up and surrendered. Life's too short.

---

