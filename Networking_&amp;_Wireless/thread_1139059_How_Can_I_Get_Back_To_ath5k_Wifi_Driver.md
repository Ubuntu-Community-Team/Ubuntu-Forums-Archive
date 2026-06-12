---
title: "How Can I Get Back To ath5k Wifi Driver?"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by rrojas on 2009-04-26
I recently used the Hardware Drivers tool to attempt to use the Madwifi drivers over the ath5k for my Atheros network adapter. Unfortunately now I can't find my wlan0 interface using either 'ifconfig' or 'iwconfig.'

When I go back to the Hardware Drivers, it doesn't show that the adapter is using the "Alternate Atheros 'madwifi' driver." 

Using the network manager applet at the top right no longer shows anything regarding wireless.

How can I revert whatever I did and resume using the ath5k driver with my adapter again?

Thanks.

Edit: In fact, I can no longer find any evidence of my wireless adapter in Network Manager or anywhere else. Hmmm.

---

### Post by t0mppa on 2009-04-26
The alternative driver in Hardware Drivers IS ath5k, at least on Intrepid and Jaunty.

If you can't find your wireless interface at all, maybe you just disabled by using a keyboard combination or a wireless button. It should show up on the following terminal commands, even if the drivers aren't working: 'lspci', 'iwconfig' and 'lshw -C network'.

---

### Post by rrojas on 2009-04-26
A little more information:

The wlan0 interface was working before. Then on several restarts of my laptop it wouldn't connect to my access point (probably WPA2 related, but that's another story). So I thought I'd use Hardware Drivers to switch the driver to the madwifi one.

After that, Network Manager was unable to see my wireless adapter (no options to enable/disable wireless in the applet). 

I found out that the original ath5k driver was blacklisted in /etc/modprobe.d so I removed the blacklist file and modified the madwifi.conf which also had a "blacklist ath5k" line.

On restarts, then, Network Manager no longer even tries to connect to my wireless network. 

lspci -v:

```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a32:0105
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at ca400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k
```

lshw -C Network:

```
*-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:2e:39:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

iwconfig:

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist wlan0 scan:

```
wlan0     No scan results
```

lsmod | grep ath:

```
ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
ath5k                 107008  0 
mac80211              217208  1 ath5k
cfg80211               38032  2 ath5k,mac80211
led_class              12036  2 ath5k,acer_wmi
```

/etc/modprobe.d/madwifi.conf:

```
## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
#blacklist ath5k

## madwifi (non-free)
blacklist ath_hal
blacklist ath_pci
blacklist ath_rate_amrr
blacklist ath_rate_onoe
blacklist ath_rate_sample
blacklist wlan
blacklist wlan_acl
blacklist wlan_ccmp
blacklist wlan_scan_ap
blacklist wlan_scan_sta
blacklist wlan_tkip
blacklist wlan_wep
blacklist wlan_xauth

```

I've also pressed the wifi button on the laptop and restarted the machine to no success.

---

### Post by t0mppa on 2009-04-26
Ok, that clarifies things. The interface is associated with the ath5k driver, but both it and the madwifi are loaded in kernel and then the madwifi driver is blacklisted and on top of this the interface is disabled.

I think the first order of business should be to clean up the madwifi driver from the kernel, so there's no need to blacklist anything and it won't cause conflicts with the ath5k. This may not fix the wireless issue as Network Manager won't see anything long as the interface stays disabled, but it'll lessen the number of variables at play and thus make further moves that much easier.

On the snapshots at their [home page]("http://snapshots.madwifi-project.org"), the madwifi driver comes with a scripts directory that includes scripts for cleaning up any madwifi modules from the kernel (1). Since you used what was already on the hdd, they might be found from your disc as well, but I have no idea where they'd be installed. So, you could do a search for them or just download the newest (0.10.5.6-current) snapshot, extract the contents, and find them that way.

(1) ```
~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ ls
find-madwifi-modules.sh  hal_unmangle.sed         make-release.bash
get_arch.mk              if_ath_hal_generator.pl  update_hal_unmangle
hal_unmangle_log         madwifi-indent
hal_unmangle.objcopy     madwifi-unload
``` It's the find-madwifi-modules.sh and madwifi-unload that clean up any traces of madwifi from the kernel.

---

### Post by rrojas on 2009-04-26
Okay, I found madwifi-unload under /usr/local/bin.

I ran it as root and it gave the following output:

```

Unloading "ath_pci"
Unloading "wlan"
Unloading "ath_hal"
```

Is there anything else I should do for removing madwifi?

Edit: On a restart, I'm finding that the above three modules are still being loaded.

Update: So I tried to shut the machine down completely instead of commanding a restart. For some odd reason my wireless adapter can now see wireless networks in the area. All the diagnostic information I posted above is exactly the same. I am at a complete loss.

---

### Post by t0mppa on 2009-04-27
So, let me get this straight: lshw says the interface is still disabled, but iwlist scan shows networks found? That's truly strange indeed. Will have to do some more digging for this one.

---

### Post by rrojas on 2009-04-27
> **t0mppa said:**
> So, let me get this straight: lshw says the interface is still disabled, but iwlist scan shows networks found? That's truly strange indeed. Will have to do some more digging for this one.

I apologize. It was late when I wrote the last message. 

Indeed, not, lshw does not show the interface disabled. 

The driver information from lsmod | grep ath, however, show the same drivers loaded (both ath5k and the madwifi ones).

---

### Post by t0mppa on 2009-04-27
Ok, that's good news then. So, all you're missing now is the ability to connect to a network? Does this only apply for your own routers network or for any network around?

I did some rechecking of my own setup, inspired by this and I do have the same two sets of drivers loaded, and Jaunty upgrade blacklisted my ath_hal, ath_pci, etc. This still keeps my ath5k working though. So, a working configuration should be possible to achieve without having to clean up the madwifi drivers. As digging up how they get reloaded during reboots could be a bit time consuming without any good ideas.

---

### Post by rrojas on 2009-04-27
Yes, I believe my only issues now are the intermittent ability to connect to my home WPA2 authenticated router. When I kill security to my router, the wireless connects without a problem. But with WPA2 enabled, it's hit or miss whether the wireless will connect.

That's fine, though. I imagine there are other threads that deal with that particular issue.

Thanks for all your help!

---

### Post by t0mppa on 2009-04-27
Glad I could be of some help and good luck with the hunt for WPA2 enabled solution, I've never run into trouble with that one.

---

### Post by sb92075 on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x)

Might help, then again might not

---

