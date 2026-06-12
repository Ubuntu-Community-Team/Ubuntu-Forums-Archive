---
title: "Wireless works with XP but not Ubuntu!"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by zozza on 2009-11-21
I am having problems connecting to Wireless.  I can connect to the wireless network with XP but when I try with Ubuntu I get this error.

Here is an example with a public hotspot. 

Authentication with 00:26:50:9b:64:a4 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:26:50:9b:64:a4 (SSID='BTOpenzone' freq=2442 MHz)
Associated with 00:26:50:9b:64:a4
CTRL-EVENT-CONNECTED - Connection to 00:26:50:9b:64:a4 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

If another log would provide better information please let me know.  

On my home wireless network I often have problems as well.  Usually I have to reboot a couple of times for wireless to connect.  With XP I never have any problems and the home network connects automatically.

Here is, I believe, the relevent line from lspci -v. 

Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 1a3b:1067
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k


Any ideas?  Thanks.

---

