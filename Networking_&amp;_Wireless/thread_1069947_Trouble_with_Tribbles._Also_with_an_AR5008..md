---
title: "Trouble with Tribbles. Also with an AR5008."
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by Aped on 2009-02-14
AR5008! Not even working a little bit! I tried to download ath9k! On install, it said FATAL: ath5k missing; well, sweet, I don't even know where to get ath5k if it wasn't in the package I DL'd ([http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)) since it's the only thing in that durn download section. 

I'll post the output of a 'lshw -c network' here, since it seemed to help other posters with specificity. 

```
andrew@andrew-desktop:~$ sudo lshw -c network
[sudo] password for andrew: 
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:60:6d:25:b0
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=168
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:a0:5c:f0:6e:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
andrew@andrew-desktop:~$ 

```

If it helps, DISABLED is (possibly) an onboard Realtek 8187 11G device which I turned off from BIOS to keep this from getting complicated; it had a different host of issues, but if you think it would be easier to work with that, I am flexible. 

Oh, one more thing. 'lspci' renders the following little gem: 
```
05:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
        Subsystem: D-Link System Inc Device 3a6d
        Flags: 66MHz, medium devsel, IRQ 18
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        **_Kernel modules: ath9k_**

```

Pretty sure the bolded bit wasn't there before I added compat-wireless, even though I wasn't more than 70% sure of what I was doing at any point...

Thanks in advance for any and all help.

---

### Post by tges on 2009-03-25
I have my AR5008 running straight out of a install of Intrepid. Only problem is the speed stuck on 1Mb/s. I also tried the madwifi driver but can't seem to enable it. This is my first linux install so I'm not sure if the output below will help.

```

$ iwconfig wlan0

wlan0     IEEE 802.11bgn  ESSID:"Belkin_N_Wireless_EBBD7F"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:EB:BD:7F   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=50/100  Signal level:-63 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:11:6b:1b:07:40  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe1b:740/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1118338 (1.1 MB)  TX bytes:159839 (159.8 KB)

$ sudo lspci -k

05:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath_pci, ath9k

$ lsmod | grep ath
ath_pci               223552  0 
wlan                  262176  1 ath_pci
ath_hal               339216  1 ath_pci
ath9k                 296248  0 
mac80211              253440  1 ath9k


$ lspci -k

 *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:11:6b:1b:07:40
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless configuration: broadcast=yes driver=ath9k ip=192.168.2.2 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```

---

