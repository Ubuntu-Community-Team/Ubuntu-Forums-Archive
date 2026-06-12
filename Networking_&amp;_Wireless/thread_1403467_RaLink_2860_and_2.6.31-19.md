---
title: "RaLink 2860 and 2.6.31-19"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by steliyan on 2010-02-10
So, I've installed latest drivers (v2.3.0.0) from [**_RaLink's_**](http://www.ralinktech.com/support.php?s=2) site. 
I can't find any wireless networks. GNOME's network manager show that wireless is disconnect, WiCD fails to detect any networks too.

So here are some outputs:
```
lsmod | grep rt2860
rt2860sta             764960  1


modinfo rt2860sta
filename:       /lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.3.0.0
license:        GPL
srcversion:     73F7AA771D91BB10E13F38D
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31-19-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)


iwconfig ra0
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Greetings, steliyan! ;)

---

