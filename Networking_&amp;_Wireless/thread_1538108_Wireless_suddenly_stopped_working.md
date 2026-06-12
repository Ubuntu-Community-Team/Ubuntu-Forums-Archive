---
title: "Wireless suddenly stopped working"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by Odexios on 2010-07-24
Hi everyone!

I'm using Ubuntu 10.04. I was happily connected to internet and surfing some forum, when wireless connection suddenly stopped working.

Now I can't find any access point, and I'm pretty sure I didn't do anything to justify this behaviour.

It already happened a month ago, but I had to format my drive, so I didn't really bother to try to solve the problem.

Anyway. I'm posting here the results of the commands I think I can help with a diagnosis; if something else is needed, please let me know.

I'm using a different computer to post this thread, so I'm manually writing the output.

```
sudo iwconfig wlan0

wlan 0     IEEE 802.11bg   ESSID: off/any
           Mode:Managed   Access Point: Not-Associated Tx-Power=20 dBm
           Retry long limit:7  RTS thr:off  Fragment thr:off
           Encryption key:off
           Power Management:off


sudo iwlist wlan0 scan

wlan0     No scan results
```

---

### Post by Odexios on 2010-07-24
Ok, I didn't notice the topped thread.

Here are the additional commands:

```
lspci

06:00.0 Ethernet Controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

sudo lshw -C network

 *-network
  description: Wireless interface
  product: Ar5001 Wireless Network Adapter
  vendor: Atheros Communications Inc.
  physical id: 0
  bus info: pci@0000:06:00.0
  logical name: wlan0
  version: 01
  serial: 00:22:43:47:2b:0d
  width: 64 bits
  clock: 3MHz
  capabilities: pm msi pciexpress msix bus_baster cap_list ethernet physical wireless
  configuration: broadcast =yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
  resources: irqP19 memory:fe9f0000-fe0fffff
```

Hope it can help!

---

### Post by Odexios on 2010-07-24
Ok, I found the problem; it was the noise floor calibration timeout error linked with Atheros cards (same as [here]("http://ubuntuforums.org/showthread.php?t=1324625").

However, I wasn't able to find one single thread with a working solution. The only way I currently have found to make everything work again is to start the system with a previous kernel (.31, I think).

If anyone has a better idea, I'm all open to suggestions

---

