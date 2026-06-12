---
title: "Intel Wireless WiFi Link 4965AGN"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by edscott on 2009-10-26
I'm at the end of the rope. I've searched the forums and tried everything, and still no go. The problem is with the *Intel Wireless WiFi Link 4965AGN*. Wireless network just won't work.

Here's what happens on  *Ubuntu 9.04 - Jaunty Jackalope*

wifi does not turn on, so I installed *linux-modules-backports* since that did the trick on a different box. Result: nothing. Seems that there is a problem with "RF Kill switch", but, this laptop does not have a hardware RF switch, nor is there a BIOS option to turn radio on and off. 

result of "**dmesg |grep iw**":[INDENT][   11.683885] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.683889] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.683971] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.683980] iwlagn 0000:04:00.0: setting latency timer to 64
[   11.684028] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.722652] iwlagn 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.722726] iwlagn 0000:04:00.0: irq 2299 for MSI/MSI-X
[   11.723361] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   27.581383] iwlagn 0000:04:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode
[   27.678816] iwlagn 0000:04:00.0: loaded firmware version 228.57.2.23
[   27.678984] iwlagn 0000:04:00.0: Radio disabled by HW RF Kill switch
[/INDENT]Since I found some related stuff to HW RF switch on kernel development, I went ahead and installed **linux-2.6.31.4** using make oldconfig with the distributed .config file distributed with ubuntu. 

Result: it did not work, although the  "RF Kill switch" was replaced by a message about not being able to load firmware. So I installed firmware iwlwifi-4965-ucode-228.61.2.24 and the message dissappeared from dmesg, but the radio was still off.

Since then, a new kernel release came for ubuntu (*2.6.28-16-generic)* so I went ahead and installed. The "RF Kill switch" message is still there, but  the radio _does turn on_, as seen from **iwconfig**:[INDENT]wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]But the radio activity led is still off and the result of** iwlist scan** is not encouraging:[INDENT]lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     No scan results
pan0      Interface doesn't support scanning.
[/INDENT]I think I'm getting close. Any ideas?

BTW, wifi and bluetooth worked fine under XP, but XP is no longer available on this box for any further testing.

---

### Post by t0mppa on 2009-10-27
I have no idea how to troubleshoot Intel drivers/firmware one way or the other, but in my experience the report about HW RF kill switch is usually true, rather than a driver/firmware mix up. Are you sure your laptop doesn't have one that's enabled by some key combination (usually Fn + F5), if there's no specific button for it?

---

