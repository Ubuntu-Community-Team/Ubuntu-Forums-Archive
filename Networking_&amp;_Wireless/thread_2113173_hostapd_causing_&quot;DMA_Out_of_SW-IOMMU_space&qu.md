---
title: "hostapd causing &quot;DMA: Out of SW-IOMMU space&quot;?"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2013-02-06
I started to get these errors in dmesg which grinds my system to a halt:


```
    [ 3429.303756] DMA: Out of SW-IOMMU space for 70 bytes at device 0000:02:00.0
    [ 3429.358577] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.360040] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.405897] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.509070] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.561499] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.561938] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
    [ 3429.610809] DMA: Out of SW-IOMMU space for 70 bytes at device 0000:02:00.0
    [ 3429.611818] DMA: Out of SW-IOMMU space for 3860 bytes at device 0000:00:1a.0
```

I had just started using hostapd to create a virtual Infrastructure mode, and looked up the device ID:


  ```
  # lshw|grep 0000:02:00.0 -A 5 -B 5
               *-network      
                    description: Wireless interface
                    product: RTL8188CE 802.11b/g/n WiFi Adapter
                    vendor: Realtek Semiconductor Co., Ltd.
                    physical id: 0
                    bus info: pci@0000:02:00.0
                    logical name: mon.wlan3
                    version: 01
                    serial: 9c:b7:0d:a5:45:67
                    width: 64 bits
                    clock: 33MHz
```

Sure enough wlan3 is my internal wifi, and mon.wlan3 is the dev created by hostapd. 

This is the hostapd.conf I was using at the time, it happened twice and each time I had to reboot to get the system back running right:

  ```
  interface=wlan3
    driver=nl80211
    ssid=matt
    hw_mode=g
    channel=1
    macaddr_acl=0
    auth_algs=1
    ignore_broadcast_ssid=0
    
    #wpa=3
    #wpa_passphrase="888444111333"
    #wpa_key_mgmt=WPA-PSK
    #wpa_pairwise=TKIP
    #rsn_pairwise=CCMP
    
    #beacon_int=100
    #dtim_period=2
    #max_num_sta=32
    #rts_threshold=2347
    #fragm_threshold=2346
    
    #wep_default_key=1
    #wep_key1="ZzZzZ"
    #wep_key_len_broadcast="5"
    #wep_key_len_unicast="5"
    #wep_rekey_period=300
    
    logger_stdout=-1
    logger_stdout_level=0

```
Any ideas?  And here is the other device id:



  ```
  # lshw|grep 0000:00:1a.0 -B 5 -A 5
            *-usb:0           
                 description: USB controller
                 product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
                 vendor: Intel Corporation
                 physical id: 1a
                 bus info: pci@0000:00:1a.0
                 version: 04
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm debug ehci bus_master cap_list
                 configuration: driver=ehci_hcd latency=0



```

---

### Post by mvmacd on 2013-02-26
bump.. anybody know?

---

