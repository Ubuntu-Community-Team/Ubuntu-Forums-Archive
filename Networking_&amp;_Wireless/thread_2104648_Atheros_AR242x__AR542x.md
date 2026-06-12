---
title: "Atheros AR242x / AR542x"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by mörgæs on 2013-01-13
Trying to get a Toshiba Satellite L40 work with 64 bit Xubuntu 12.10, kernel 3.5.0-21.

Wired internet connection runs well, and all updates have been applied. The problem is the wirefree connection through the Atheros card.

**lspci -vnn** gives 

```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7128]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at ff2f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```and **rfkill list all** gives
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```Searching seems to indicate that the Askey cards have been known to cause problems in older releases. Is there a solution for 12.10?

---

### Post by chili555 on 2013-01-15
The driver ath5k generally works pretty well. What is your specific issue? Does it see networks and try to connect? Detach the ethernet, please and let's run some diagnostics:```
nm-tool
dmesg | grep ath
```Thanks.

---

### Post by mörgæs on 2013-01-15
Thanks for noticing.

The problem is that I don't see any networks. Now using Xubuntu 12.04 the output is:

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:FB:7B:2D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1B:9E:3F:15:30

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```and

```
[   17.545468] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.545484] ath5k 0000:02:00.0: setting latency timer to 64
[   17.545543] ath5k 0000:02:00.0: registered as 'phy0'
[   18.075304] ath: EEPROM regdomain: 0x65
[   18.075308] ath: EEPROM indicates we should expect a direct regpair map
[   18.075313] ath: Country alpha2 being used: 00
[   18.075315] ath: Regpair used: 0x65
[   18.207771] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```Are there any more commands that I should run?

---

### Post by chili555 on 2013-01-15
Ahhhh! My favorite kind of problem: everything looks just perfect except it doesn't work.

Let's see:```
dmesg | grep -i -e 02:00 -e error -e 80211
```I'm struggling to find anything to fix!!

---

### Post by mörgæs on 2013-01-15
Well, not really my favorite... :-)

Here we go:

```
[    0.097388] pci 0000:02:00.0: [168c:001c] type 0 class 0x000200
[    0.097455] pci 0000:02:00.0: reg 10: [mem 0xff2f0000-0xff2fffff 64bit]
[    0.097795] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[   16.299715] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.481202] cfg80211: Calling CRDA to update world regulatory domain
[   16.822952] cfg80211: World regulatory domain updated:
[   16.822957] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.822961] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.822965] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.822969] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.822972] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.822976] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.263007] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.263023] ath5k 0000:02:00.0: setting latency timer to 64
[   17.263082] ath5k 0000:02:00.0: registered as 'phy0'
[   17.811088] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.811092] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811095] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.811099] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811102] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.811106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811109] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.811113] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811116] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.811120] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811123] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.811127] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811130] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.811134] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811137] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.811141] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811144] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.811148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811151] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.811155] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811158] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.811162] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811165] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.811169] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811172] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.811176] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   17.811179] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   17.811310] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   18.066573] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'


```I have not added xubuntu-restricted-extras.
Yesterday I tried various configurations with *nohwcrypt*, but they are removed again.

---

### Post by chili555 on 2013-01-15
> pci [COLOR="Red"]0000:02:00.0[/COLOR]: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'02:00.0 is the PCI bus the wireless card is on:> 02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter I don't know if power management has any effect here, but it's about our only suspect. What does this tell us about power management?```
iwconfig
```Does this change anything?```
sudo iwconfig wlan0 power off
sudo iwlist wlan0 scan
```

---

### Post by mörgæs on 2013-01-15
iwconfig:

```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

sudo iwconfig wlan0 power off:
```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```
sudo iwlist wlan0 scan:
```
wlan0     No scan results

```

---

### Post by chili555 on 2013-01-15
Frankly, I still see nothing wrong! Are you sure there are wireless networks nearby to scan?

You might try the suggested kernel boot parameter to see if it helps:> disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'If you are not already experienced, this is how to enable a boot parameter: [https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot)

I wouldn't take out any wordings; just add pcie_aspm=force after quiet splash. That will be a temporary fix and will not be effective upon reboot. If it helps, we can change a file and make it persistent.

---

### Post by mörgæs on 2013-01-17
Thanks for the suggestion, but boot options didn't help. I am sure that there should be a hotspot available, as several other computers can pick it up.

As mentioned before I have found various (older) reports on problems with Askey cards. Do you know if they are still relevant?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)

---

### Post by chili555 on 2013-01-17
I have not been aware that it's particularly a problem. Frankly, I'm skeptical that it's an Askey problem; I'd think, as Shakespeare inferred, an 168c:001c is an 168c:001c by any other name.

Usually, that parameter is useful when a card is slow or sees networks but never quite connects or when it drops. Your case is altogether different; although rfkill reports no block, the card doesn't see networks and makes no hint that it tries to connect.

Did you try the parameter? The general temporary method is:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=Y
```Note the parameter is boolean, not an integer as used elsewhere.> $ modinfo ath5k
filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
<snip>
parm:           [COLOR="Red"]nohwcrypt[/COLOR]:Disable hardware encryption. ([COLOR="Red"]bool[/COLOR])
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)I have heard it suggested that, in this context, 1 and Y are equivalent, however, I prefer to do it the right way.

You might also try all the other parameters in turn:```
sudo modprobe -r ath5k
sudo modprobe ath5k all_channels=Y
```...and so forth.

You might also try the Ubuntu tweaked compat-wireless package:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Reboot afterwards and tell us if there is any improvement.

---

### Post by mörgæs on 2013-01-17
This is embarrassing, and I am sorry for wasting your time. The wifi switch on the front was turned off. Now it all works well.

It surprises me that **rfkill list all** did not report anything blocked.

Thanks for help anyway.

---

### Post by chili555 on 2013-01-17
> It surprises me that rfkill list all did not report anything blocked.Indeed.

No problem. I'll take a Solved any way I can get it. Glad it's working.

---

### Post by Diabolis on 2013-07-11
I'm on the same boat. However, I'm still not sure if its just the front switch that its set to off; it has a spring that makes it go back to its starting position...

Acer Aspire one ZG5
```
uname -r
3.5.0-36-generic
cat /etc/issue
Ubuntu 12.04.2 LTS
```

Same error, already tried:
  -disable encryption
  -disable network-manager (actually uninstalled it)

---

### Post by chili555 on 2013-07-11
> **Diabolis said:**
> I'm on the same boat. However, I'm still not sure if its just the front switch that its set to off; it has a spring that makes it go back to its starting position...

Acer Aspire one ZG5
```
uname -r
3.5.0-36-generic
cat /etc/issue
Ubuntu 12.04.2 LTS
```

Same error, already tried:
  -disable encryption
  -disable network-manager (actually uninstalled it)How about a little more information:```
rfkill list all
dmesg | grep ath

```

---

