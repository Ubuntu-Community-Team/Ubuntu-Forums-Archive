---
title: "Wireless Unstable in 10.04 - AR5001 Wireless Network Adapter"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by barlaventoexpert on 2010-08-30
I am severe wireless problems with Ubuntu 10.04 on my laptop.(Spec below)

I have just performed the first clean install since new. Installed a new Hard Drive as well. The machine and wifi was fine under Ubuntu 9.04.

It is booting  much faster now but the wifi keeps dropping off. 

Any assistance in resolving this would be appreciated as I use this machine for work. 

Spec:

Machine - Acer Aspire 4310

Wireless card - *-network      
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:69:1b:da:8f
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d8000000-d800ffff

and

iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BUFFALO-g-001601A1B5F0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
pan0      no wireless extensions.

---

### Post by Donalt2010 on 2010-08-30
Does your laptop have an actual power button for the wifi card to turn it on and off? Install madwifi from the ubuntu software centre and make sure to do any updates from the system/administration menu then reboot and try to connect to your network.
I had the exact same problem on my friends laptop with the same wifi card and that solution has worked:)
Hope it helps

Regards
Donalt

---

### Post by zob on 2010-09-25
I have the same problem. I only happens when wireless strength drops a bit below 100%. As long as it's 100% it keeps the connection here.
There was a bug-report on this but unfortunately it expired. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601457)

I've been googling for hours. I don't think there is a solution to this problem other than downgrading to 9.10 (I think it was when it last worked - but I'm not sure). From other comments I conclude that ndiswrapper doesn't work either.

To check what Donalt2010 asks for regarding if wifi has been turned off either by soft-button combination or by some kind of switch you can use the rfkill command. Goes like this ```
rfkill list
```
But that's of course not the problem, as it DOES connect. It's just very unstable.

EDIT: Should have mentioned. I have the same wifi-card of course. Atheros ar5001. I my case in an eeepc 702.
Also have a look on this page: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
I don't really know. I've tried manually removing ath_pci module. But it's not there in the first place so I don't see the point in blacklisting it. It's based on an old solution from when the ath5k didn't load at all. That is not the case however as you can see if you check out the output of lsmod or even lsmod | grep ath if you want it shorter.

---

