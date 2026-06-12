---
title: "Intel Pro Wireless not working since 2.6.24-19"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by philip_bretton on 2008-12-06
Hi 

I have a laptop with an Intel Pro Wireless 3945ABG wireless adapter. I am running it with the iwl3945 driver.
```
brett@brett-laptop:~$ sudo lshw -C network
[sudo] password for brett: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:18:79:11
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.10 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
``` 

The problem is that if I try to boot up with one of the later kernels (anything after 2.6.24-19) then I cannot get a wireless connection. Restart the machine in 2.6.24-19 and wireless works - I have tried both 2.6.24-21 and 2.6.24-23 and neither of them are able to make a wirelss connection. I am running Ubuntu 8.04.1.

Here is the log generated when I try to connect using the latest kernel:
```
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) started... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'yelnibemoh' is encrypted, but NO valid key exists.  New key needed. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'yelnibemoh'. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'yelnibemoh' received. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  6 10:35:42 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'yelnibemoh' is encrypted, and a key exists.  No new key needed. 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Dec  6 10:35:44 brett-laptop kernel: [   89.913446] NET: Registered protocol family 17
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was '0' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 79656c6e6962656d6f68' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Dec  6 10:35:44 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec  6 10:35:47 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Dec  6 10:36:07 brett-laptop kernel: [  105.660932] iwl3945: Error sending REPLY_TX_PWR_TABLE_CMD: iwl3945_enqueue_hcmd failed: -5
Dec  6 10:37:44 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), failing activation. 
Dec  6 10:37:44 brett-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Dec  6 10:37:45 brett-laptop NetworkManager: <info>  Activation (eth1) failed for access point (yelnibemoh) 
Dec  6 10:37:45 brett-laptop NetworkManager: <info>  Activation (eth1) failed. 
Dec  6 10:37:45 brett-laptop NetworkManager: <info>  Deactivating device eth1. 
```

Any ideas why this is not working?

Thanks

Brett

---

### Post by philip_bretton on 2008-12-17
Well I have tried everything suggested in this and other forums for resolving this issue and nothing seems to work.
<code>
have tried this (amongst others):
sudo rmmod iwl3945
sudo rmprobe iwl3945 disable_hw_scan=1
</code>
But I have found that in the later kernels my wireless device does not even scan for networks correctly
<code>
iwlist -eth1 scan
</code>
returns no results (despite the fact that I am sitting right next to the router and booting up in the older kernel connects immediately. 

I guess this means that if you wnt to use an Intel Wireless device with iwl3945 then use the older kernel.

---

