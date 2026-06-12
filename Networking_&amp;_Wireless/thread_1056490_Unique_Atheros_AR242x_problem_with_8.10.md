---
title: "Unique Atheros AR242x problem with 8.10"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by SaintMantooth on 2009-01-31
I've looked around and I haven't seen anyone else that has had this same problem. When I initially got my laptop, I went through the same mess that everyone else went through to get this chipset working. Well, it worked fine for about 4 months or so. Well, not too long ago, I did a kernel update, and naturally, it destroyed everything, so I went throught the struggle of reinstalling the drivers(This time I ended up having to use the compat-wireless drivers) I got it working. But less week, it just quit working. It quit scanning, wouldn't connect. The computer recognizes my card, then it won't recognize my card, etc. I got it working again, don't know how, but I did.

Well now again today, It was working fine. Then it quits loading anything on the net, so I unplug the router, plug it back in, and try to reconnect... nothing. It can see the ap, but it won't connect. I reboot and all of a sudden, it's not finding any ap's.  That's where I'm at now. I've tried everything from uninstalling to reinstalling the drivers and nothing. Here's some info for y'all.

lspci -v
> 07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k


lshw -C Network
>   *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e1:7d:cc:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg


iwconfig
> wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and ifconfig doesn't list wlan0

The weird thing that I haven't seen happen with anyone else is how it says *-network DISABLED when I do lshw.

Also, if when I try to install madwifi, I get an error when I do "sudo make", so that's why I went to compat-wireless, which worked for a while, and then this happened.

Anyone out there have any ideas?

---

### Post by SaintMantooth on 2009-02-01
I take it no one else knows why it says *-network DISABLED ?

---

### Post by kevdog on 2009-02-01
Ok, so using ath5k driver which is OK.

What happens if you 
sudo modprobe -r ath5k
sudo modprobe ath5k

Does dmesg | grep ath
show anything after you run the process above?

---

