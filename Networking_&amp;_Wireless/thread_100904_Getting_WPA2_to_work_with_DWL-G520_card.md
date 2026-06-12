---
title: "Getting WPA2 to work with DWL-G520 card"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by TrinitronX on 2005-12-08
I have a D-Link DWL-G520 (Revision B) card linked up to a DI-624 router running some new beta firmware that supports WPA2.  I have found some windows drivers for my card's atheros chipset (Atheros AR5212) that supports WPA2, and I can use these in windows successfully.
I am currently using a WEP key configuration to connect to my network, but now that my router supports WPA2, I would like to get this working in ubuntu as well.
Ok, I've sucessfully installed the same drivers I use for my card in windows (I have a dual boot machine) using ndiswrapper.
Using 'ndiswrapper -l' gives me: 
```
Installed ndis drivers:
net5211 driver present, hardware present
```
I looked at the output of 'lshw' and found my wireless card listed:
```
irq:18
           *-network:0
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 3
                bus info: pci@02:03.0
                logical name: ath0
                version: 01
                serial: 00:11:95:bb:10:2e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.0.101 multicast=yes wireless=IEEE 802.11g
```

Also, if I run 'ifconfig ath0', I get:
```
ath0      Link encap:Ethernet  HWaddr 00:11:95:BB:10:2E
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:febb:102e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102977 errors:14950 dropped:0 overruns:0 frame:14950
          TX packets:63132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:133507072 (127.3 MiB)  TX bytes:5159418 (4.9 MiB)
          Interrupt:19 Memory:f8ea0000-f8eb0000
```

I've gotten the wpa_supplicant package, and have been trying to make it work correctly so that I can configure it to work with WPA2.
Here is what my wpa_supplicant.conf looks like (in /etc/wpa_supplicant.conf):
```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
	scan_ssid=1

	ssid="** My SSID here **"

	proto=WPA2

	key_mgmt=WPA-PSK

	pairwise=CCMP

	group=CCMP

	psk="** My PSK here **"
}

```

I've gotten ndiswrapper installed as a module, and when I use 'modprobe -l | grep ndiswrapper', it gives me:
```
/lib/modules/2.6.12-9-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
```

So hopefully this information will help in figuring out what's wrong.  Whenever I change my router's security settings back to WPA2, I can't get a connection to the network, so I have to go back into windows and connect so I can reset the router back to WEP authorization.  I'm wondering if I should try using madwifi instead of ndiswrapper?
Any help would be appreciated.

---

### Post by TrinitronX on 2005-12-09
Ok... so I found out one problem.  Apparently since the madwifi drivers had already installed themselves with the default installation of ubuntu, the ndiswrapper ones weren't even being used at all.  I compiled a custom kernel last night, so I could take advantage of my CPU's hyperthreading and other optimizations, and I noticed that when I start up using the new kernel, my wireless card does not show as 'ath0' anymore.
I went in and got the source code for ndiswrapper and wpa_supplicant, so I could do things myself to make sure the installation was good.
I compiled ndiswrapper flawlessly, as well as wpa_supplicant, and now my wireless card is showing up as 'wlan0'.  So now I know that the ndiswrapper drivers are actually being used this time :P.
I went through the basic installation of those drivers for my card, and they installed fine, but they aren't even working with WEP like the madwifi ones did.  I haven't used wpa_supplicant yet, I'm just trying to test out if the ndiswrapper ones work at the moment.  I seem to be getting some warning messages about the driver now, so hopefully these can help to diagnose the problem.
So far I've tried 2 different windows drivers with ndiswrapper, the first ones are the same exact ones my windows installation is using, and the second ones are some I found through looking up my card's chipset in the ndiswrapper wiki.

Anyways, here's some error messages I've been noticing (whether they be in my system log, or when I execute 'iwconfig wlan0'):
```
trinitronx@Arcturus:/etc/ndiswrapper/net5211$ iwconfig wlan0
[b]Warning: Driver for device wlan0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...[/b]

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:108 Mb/s
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


trinitronx@Arcturus:~/Desktop$ dmesg | grep ndiswrapper
[4294695.225000] ndiswrapper version 1.6 loaded (preempt=no,smp=yes)
[4294695.280000] ndiswrapper: driver net5211 (,08/30/2005,4.2.0.82) loaded
[4294695.762000] ndiswrapper: using irq 18
**[4294695.864000] ndiswrapper (ExAllocatePoolWithTag:1062): Windows driver allocating too big a block at DISPATCH_LEVEL: 203412**
[4294696.764000] wlan0: ndiswrapper ethernet device 00:11:95:bb:10:2e using driver net5211, 168C:0013.5.conf
```

I've hilighted the messages of concern.  Anyone know what's going on here?  I'm wondering if it's complaining that the wireless tools package is not current... which is weird, because I'm sure I got the package from the synaptic package manager.

---

### Post by PsTJsT on 2006-02-06
Please note that one shouldn't need to use ndiswrapper/Windows drivers with a D-Link DWL-G520 adapter under Breezy (assuming the adapter has an Atheros chipset).  The madwifi drivers included in Breezy work great.  Generally all that is necessary to enable WPA or WPA2 for a DWL-G520 is to install/configure wpasupplicant per the excellent How-To/thread at [http://www.ubuntuforums.org/showthread.php?t=90450](http://www.ubuntuforums.org/showthread.php?t=90450).

---

### Post by TrinitronX on 2006-02-12
Oops.. this post is a bit old... I've already figured that out... and am now happily using WPA2 with wpa_supplicant and the madwifi drivers.

Thanks though :D

---

### Post by dakira on 2006-02-16
Hi,

AFAIK madwifi and wpasupplicant DO NOT work perfectly in Breezy. At least not, if you want to use DHCP. If you want to use DHCP you need to patch the wpasupplicant to work with some strange modifications done to the madwifi build that comes with Breezy.

dakira

---

