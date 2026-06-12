---
title: "Nothing happened after installed the latest madwifi wireless driver"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by ChipWolf on 2010-01-09
In order to test aircrack, i try to install madwifi driver
after i make install ,i add ath9k into blacklist then reboot, but nothing hanpped. why?
driver:
madwifi-0.9.4-r4100-20091230
lspci
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
uname -r
2.6.31-17-generic
lsmod
ath_pci                92284  0 
wlan                  198800  1 ath_pci
ath_hal               192272  1 ath_pci
...
dmesg
[   14.133963] wlan: 0.9.4.1
[   14.157261] ath_pci: 0.9.4.1
[   25.508021] eth0: no IPv6 routers present
[   79.001056] Clocksource tsc unstable (delta = -220174698 ns)
[  742.348180] cfg80211: Calling CRDA to update world regulatory domain
[  742.360046] cfg80211: World regulatory domain updated:
[  824.308381] ath_pci: driver unloaded
[  824.332046] wlan: driver unloaded
[  824.348054] ath_hal: driver unloaded
[  853.369440] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  853.401038] wlan: 0.9.4.1
[  853.407719] ath_pci: 0.9.4.1
(i used modprobe command to reload the driver)

lspci -v
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 1a32:0303
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d0400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel modules: ath9k

does anybody know why the driver do nothing?

---

### Post by drpjkurian on 2010-01-09
> **ChipWolf said:**
> In order to test aircrack, i try to install madwifi driver
after i make install ,i add ath9k into blacklist then reboot, but nothing hanpped. why?
driver:
madwifi-0.9.4-r4100-20091230
lspci
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
uname -r
2.6.31-17-generic
lsmod
ath_pci                92284  0 
wlan                  198800  1 ath_pci
ath_hal               192272  1 ath_pci
...
dmesg
[   14.133963] wlan: 0.9.4.1
[   14.157261] ath_pci: 0.9.4.1
[   25.508021] eth0: no IPv6 routers present
[   79.001056] Clocksource tsc unstable (delta = -220174698 ns)
[  742.348180] cfg80211: Calling CRDA to update world regulatory domain
[  742.360046] cfg80211: World regulatory domain updated:
[  824.308381] ath_pci: [COLOR="red"]**driver unloaded**[/COLOR]
[  824.332046] wlan: driver unloaded
[  824.348054] ath_hal: [COLOR="Red"]**driver unloaded**[/COLOR]
[  853.369440] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  853.401038] wlan: 0.9.4.1
[  853.407719] ath_pci: 0.9.4.1
(i used modprobe command to reload the driver)

lspci -v
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 1a32:0303
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d0400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel modules: ath9k

does anybody know why the driver do nothing?


Hi 
Are you sure that driver is loaded correctly?
It shows as unloaded (Red Letters)
Please visit the #62 of my thread
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Dr Kurian

---

