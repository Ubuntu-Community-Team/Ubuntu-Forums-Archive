---
title: "Intrepid x64 with Intel Wireless 5300 AGN wlan Cannot Obtain IP unless next to router"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by rickl on 2009-03-14
Hello. I recently bought a Sager 2096 laptop, which contains Intel Wireless 5300 AGN wlan  hardware. I have kubuntu 8.10 x64 installed on my system.

The problem I am having is that when I try to connect to the Internet via wlan, I cannot connect unless I am right next to the router. I know that the router works, as I can connect to it with other wireless devices from a distance. In addition, I  know that this wireless card works, because I have tested it running my second operating system on my machine, Windows 7 build 7048 x64, and using the drivers that came from the Intel driver site. Currently, when I try to connect to my unsecured public home network, my wireless manager cannot get past "Obtaining IP Address".

Here are some more infos:

```
rick@rick-laptop:~$ uname -a
Linux rick-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

```
rick@rick-laptop:~$ modinfo iwlagn                                                      
filename:       /lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965                                                                      
license:        GPL                                                                          
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>               
version:        1.3.27ks                                                                     
description:    Intel(R) Wireless WiFi Link AGN driver for Linux                             
firmware:       iwlwifi-4965-2.ucode                                                         
firmware:       iwlwifi-5150-2.ucode                                                         
firmware:       iwlwifi-5000-1.ucode                                                         
firmware:       iwlwifi-6050-2.ucode                                                         
firmware:       iwlwifi-6000-2.ucode                                                         
srcversion:     F7FC31C63173A2C36059C3E                                                      
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000085sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000082sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00000082sv*sd00001122bc*sc*i*                                  
alias:          pci:v00008086d00000085sv*sd00001112bc*sc*i*                                  
alias:          pci:v00008086d00000082sv*sd00001102bc*sc*i*                                  
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*                                         
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*                                         
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*                                  
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*                                  
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*                                  
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*                                  
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*                                  
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*                                  
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*                                  
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*                                  
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*                                  
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*                                         
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*                                         
depends:        iwlcore,cfg80211,mac80211                                                    
vermagic:       2.6.27-11-generic SMP mod_unload modversions                                 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)       
parm:           swcrypto50:using software crypto engine (default 0 [hardware])               
 (bool)                                                                                      
parm:           debug50:50XX debug output mask (uint)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)
```

The solutions I have attempted include switching to wicd instead of knetworkmanager (same results), updating and reinstalling drivers (same results), and changing settings such as the channel on my home wifi router (same results).

It is important for me to solve this within the next 5 days, as I am leaving the country and want to be able to connect to what little internet I may have at my destination, some of which could be wifi.

JUST TO RECAP:
I can connect to my wireless network when I am (literally) on top of my wireless router. I cannot connect at distances more than 3 meters. However, I still can read the signal of the network from a distance. My problem is that I cannot obtain an IP address, or at least that is where the problem occurs.


Thank you very much

-Rick

---

### Post by rickl on 2009-03-15
bump (I have 3 days left to fix this)

---

### Post by andlinux on 2009-05-11
Wow, I have the same problem. I bought a new modem/router because my old one (e-tech) got broken, the new one is from levelone, wbr-3600.

Well, I installed this new router and configured it with my desktop computer (windowsxp). Then I started my laptop that has ubuntu 9.04 and I tried to connect to my new router, but it didn't work. 

So some time later I took a modem/router (philips) from work to test it here at home. And I could connect to that router without a problem. At some point I was in my basement where the routers are standing and my laptop was connected with a utp cable to my new levelone wbr-3600 router. I unplugged the cable and selected the ssid from that router and after some time it connected.

Then I went to the kitchen and I still had a very good signal and I could do anything, I never lost signal but if I selected the other router (philips from work) and wanted to go back to my new router (levelone) then it didn't work. BUT if I was standing next to my new router in the basement then it connected.

I have an Intel Wireless 4965 AGN card in my laptop and I also have this problem. It's strange that a windows computer can connect without a problem... I'm still searching for a solution but haven't found one.

---

### Post by angelcaf on 2010-01-28
Same problem here with an Intel iwl4965 AGN chipset on a Dell XPS m1330 and Kubuntu karmic!!
Anyone has found a solution? please...

---

### Post by andlinux on 2010-01-28
> **angelcaf said:**
> Same problem here with an Intel iwl4965 AGN chipset on a Dell XPS m1330 and Kubuntu karmic!!
Anyone has found a solution? please...

I bought another card, an atheros card and I thought it was a ar5008 (I'm not at my linux comp at the moment). And the problem was solved.

---

