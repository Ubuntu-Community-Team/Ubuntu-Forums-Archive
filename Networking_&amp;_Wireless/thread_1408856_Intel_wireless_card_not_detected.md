---
title: "Intel wireless card not detected"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by llueveYescampa on 2010-02-16
My Hp laptop is not accessing its wireless card.

Here is the relevant part of output of the 'sudo lshw -c network command:

  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:0a:f8:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:da100000-da101fff


Thank you all in advance for the help provided.

---

### Post by chili555 on 2010-02-17
I wonder what the kernel says about it? Please post:```
dmesg | grep iwl
rfkill list
```Also, is your ethernet connected? Network Manager will not activate your wireless if wired ethernet is available.

---

### Post by llueveYescampa on 2010-02-17
Thanks for your replay.


laptop:~$ dmesg | grep iwl

[    9.542650] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.542653] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.544810] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.544871] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.545050] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[    9.605099] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.605314] iwlagn 0000:02:00.0: irq 36 for MSI/MSI-X
[    9.725115] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.159947] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   14.205238] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   14.205368] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   14.207815] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   14.207949] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   14.210566] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   14.210647] iwlagn 0000:02:00.0: Could not read microcode: -2
[   14.899994] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   14.902640] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   14.902757] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   14.904925] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   14.905048] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   14.907258] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   14.907376] iwlagn 0000:02:00.0: Could not read microcode: -2


laptop:~$ rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I just learn that the card is a "Intel Centrino Advanced-N 6200 AGN"
Intel, in its web page, said that this card work with ubuntu.


Any help will be appreciated.

---

### Post by Cabs21 on 2010-02-17
are your drivers up to date.  Did you hard wire connect to internet and update your drivers?  In network manager do you have wireless ENABLED?  Is your router functioning properly?  Is the little light/switch/button that turns your wireless card on and off from the exterior body turned to the ON position?  What version of Ubuntu are you using?  How new to Ubuntu are you?

---

### Post by llueveYescampa on 2010-02-17
> **Cabs21 said:**
> are your drivers up to date.  Did you hard wire connect to internet and update your drivers?  In network manager do you have wireless ENABLED?  Is your router functioning properly?  Is the little light/switch/button that turns your wireless card on and off from the exterior body turned to the ON position?  What version of Ubuntu are you using?  How new to Ubuntu are you?
  

I do not know if my drivers are updated.
I can hard wire to the internet. No problems there.
No. I have not updated the drivers.
Yes, The wireless is ENABLED.
Yes my router is fine. others computers are working wireless without problem.
Yes, the light indicating the wireless activity in on.
I am using ubuntu 9.10
I have used linux/ubuntu for several years.

Thanks for you replay.

P.D: I just learn that  the card is a "Intel Centrino Advanced-N 6200 AGN"
Intel, in its web page, said that this card work with ubuntu.


Any help will be appreciated.

---

### Post by chili555 on 2010-02-17
> Could not read microcode: -2It can't find the firmware it needs. I have no idea why the firmware you have is not the firmware it wants. You might just, with the ethernet attached and active, do:```
sudo apt-get install linux-backports-modules-karmic-generic
```It has an updated driver and firmware. Then I would do:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn
```Your wireless should spring to life. If not, please reboot.

---

### Post by Cabs21 on 2010-02-17
First thing I would do is connect to the net and update my drivers. Reboot.  Test wireless connectivity.  Sounds like you have compatible hardware but you need drivers to help Ubuntu use the Wireless card.

---

### Post by llueveYescampa on 2010-02-17
Thank you all. it is working.

This command failed:

sudo apt-get install linux-backports-modules-karmic-generic
Then I went to the Synaptic Package Manager and chose Networking (multiverse) and use 'Mark all Upgrades'. It start a process in which 220 packages were installed/updated.

after it finish, and before a required reboot, I tried the above command again. It worked this time.

After rebooting, the wireless card was working. I do not know which of the two processes was the one that make the trick. I just wanted to know that the card was able to work.

Latter on I will install ubuntu 9.10 form the distribution disk and find out which one is the right procedure, but for now I need to fix (improve) my Video.

thanks you all very much.

---

### Post by mgsmith7475 on 2010-03-22
I ran into the same problem as described above. This completely fixed the problem once and for all! Extract and vi on the README text to compile the drivers for your >=2.6.26 kernel

It's very easy! Enjoy!

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by Vinnare on 2010-04-06
Hello Guys,

I'm new to linux. This is the message I got when I typed *dmesg | grep iwl*. I am not able to use bluetooth and I came across this thread when searching for how to do it. My card is *[FONT=Arial][SIZE=2]Intel® Centrino® Advanced-N 6200[/SIZE][/FONT]* and at Intel's site [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3200&DwnldID=17045&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3200&DwnldID=17045&lang=eng) I'm not able to locate the driver download link. I tried [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) too but didn't understand a thing written there. Could you help me with the same?


-------------------------------------------------------------------------------------------------
 dmesg | grep iwl
[   18.590988] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   18.590991] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   18.591102] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.591139] iwlagn 0000:02:00.0: setting latency timer to 64
[   18.591209] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[   18.618422] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   18.618501] iwlagn 0000:02:00.0: irq 36 for MSI/MSI-X
[   18.624061] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2329.915406] iwlagn 0000:02:00.0: PCI INT A disabled
[ 2356.605747] iwlagn: disagrees about version of symbol iwl_rxon_add_station
[ 2356.605752] iwlagn: Unknown symbol iwl_rxon_add_station
[ 2356.605891] iwlagn: disagrees about version of symbol iwl_set_mode
[ 2356.605894] iwlagn: Unknown symbol iwl_set_mode
[ 2356.606091] iwlagn: disagrees about version of symbol iwl_scan_cancel_timeout
[ 2356.606096] iwlagn: Unknown symbol iwl_scan_cancel_timeout
[ 2356.606304] iwlagn: disagrees about version of symbol iwl_mac_add_interface
[ 2356.606309] iwlagn: Unknown symbol iwl_mac_add_interface
[ 2356.606735] iwlagn: disagrees about version of symbol iwl_connection_init_rx_config
[ 2356.606740] iwlagn: Unknown symbol iwl_connection_init_rx_config
[ 2356.607164] iwlagn: disagrees about version of symbol iwl_send_statistics_request
[ 2356.607168] iwlagn: Unknown symbol iwl_send_statistics_request
[ 2356.607422] iwlagn: Unknown symbol iwl_ht_enabled
[ 2356.607708] iwlagn: disagrees about version of symbol iwl_set_default_wep_key
[ 2356.607712] iwlagn: Unknown symbol iwl_set_default_wep_key
[ 2356.607928] iwlagn: disagrees about version of symbol iwl_scan_cancel
[ 2356.607932] iwlagn: Unknown symbol iwl_scan_cancel
[ 2356.608531] iwlagn: disagrees about version of symbol iwl_chain_noise_calibration
[ 2356.608536] iwlagn: Unknown symbol iwl_chain_noise_calibration
[ 2356.608885] iwlagn: Unknown symbol iwl_setup_spectrum_handlers
[ 2356.609096] iwlagn: disagrees about version of symbol ieee80211_free_hw
[ 2356.609100] iwlagn: Unknown symbol ieee80211_free_hw
[ 2356.609514] iwlagn: disagrees about version of symbol iwl_remove_dynamic_key
[ 2356.609519] iwlagn: Unknown symbol iwl_remove_dynamic_key
[ 2356.609818] iwlagn: disagrees about version of symbol iwl_get_ra_sta_id
[ 2356.609822] iwlagn: Unknown symbol iwl_get_ra_sta_id
[ 2356.610119] iwlagn: disagrees about version of symbol iwl_rx_reply_compressed_ba
[ 2356.610123] iwlagn: Unknown symbol iwl_rx_reply_compressed_ba
[ 2356.610336] iwlagn: disagrees about version of symbol iwl_txq_update_write_ptr
[ 2356.610341] iwlagn: Unknown symbol iwl_txq_update_write_ptr
[ 2356.610550] iwlagn: disagrees about version of symbol iwl_eeprom_free
[ 2356.610554] iwlagn: Unknown symbol iwl_eeprom_free
[ 2356.610960] iwlagn: Unknown symbol iwlcore_eeprom_enhanced_txpower
[ 2356.611173] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[ 2356.611178] iwlagn: Unknown symbol ieee80211_start_tx_ba_session
[ 2356.611600] iwlagn: disagrees about version of symbol iwl_sta_tx_modify_enable_tid
[ 2356.611605] iwlagn: Unknown symbol iwl_sta_tx_modify_enable_tid
[ 2356.611815] iwlagn: disagrees about version of symbol iwl_power_update_mode
[ 2356.611820] iwlagn: Unknown symbol iwl_power_update_mode
[ 2356.612028] iwlagn: disagrees about version of symbol iwlcore_eeprom_release_semaphore
[ 2356.612033] iwlagn: Unknown symbol iwlcore_eeprom_release_semaphore
[ 2356.612274] iwlagn: disagrees about version of symbol iwl_hw_txq_ctx_free
[ 2356.612278] iwlagn: Unknown symbol iwl_hw_txq_ctx_free
[ 2356.612690] iwlagn: disagrees about version of symbol iwl_eeprom_init
[ 2356.612695] iwlagn: Unknown symbol iwl_eeprom_init
[ 2356.612978] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[ 2356.612983] iwlagn: Unknown symbol ieee80211_restart_hw
[ 2356.613195] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[ 2356.613200] iwlagn: Unknown symbol ieee80211_rate_control_unregister
[ 2356.613419] iwlagn: disagrees about version of symbol iwl_set_rxon_ht
[ 2356.613423] iwlagn: Unknown symbol iwl_set_rxon_ht
[ 2356.613658] iwlagn: Unknown symbol iwl_setup_rxon_timing
[ 2356.613871] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[ 2356.613875] iwlagn: Unknown symbol ieee80211_wake_queue
[ 2356.614194] iwlagn: Unknown symbol iwl_debug_level
[ 2356.614427] iwlagn: Unknown symbol iwl_tt_initialize
[ 2356.614725] iwlagn: disagrees about version of symbol iwl_txq_ctx_stop
[ 2356.614729] iwlagn: Unknown symbol iwl_txq_ctx_stop
[ 2356.614937] iwlagn: disagrees about version of symbol iwlcore_eeprom_acquire_semaphore
[ 2356.614942] iwlagn: Unknown symbol iwlcore_eeprom_acquire_semaphore
[ 2356.615150] iwlagn: disagrees about version of symbol iwl_init_drv
[ 2356.615154] iwlagn: Unknown symbol iwl_init_drv
[ 2356.615391] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[ 2356.615395] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state
[ 2356.615748] iwlagn: disagrees about version of symbol iwl_tx_cmd_complete
[ 2356.615752] iwlagn: Unknown symbol iwl_tx_cmd_complete
[ 2356.615958] iwlagn: disagrees about version of symbol iwl_reset_ict
[ 2356.615962] iwlagn: Unknown symbol iwl_reset_ict
[ 2356.616172] iwlagn: disagrees about version of symbol iwl_rx_reply_rx_phy
[ 2356.616177] iwlagn: Unknown symbol iwl_rx_reply_rx_phy
[ 2356.616391] iwlagn: disagrees about version of symbol iwl_setup_rx_scan_handlers
[ 2356.616396] iwlagn: Unknown symbol iwl_setup_rx_scan_handlers
[ 2356.616605] iwlagn: disagrees about version of symbol iwl_send_cmd_pdu
[ 2356.616609] iwlagn: Unknown symbol iwl_send_cmd_pdu
[ 2356.616817] iwlagn: disagrees about version of symbol iwl_set_rxon_hwcrypto
[ 2356.616822] iwlagn: Unknown symbol iwl_set_rxon_hwcrypto
[ 2356.617071] iwlagn: disagrees about version of symbol iwl_init_sensitivity
[ 2356.617075] iwlagn: Unknown symbol iwl_init_sensitivity
[ 2356.617285] iwlagn: disagrees about version of symbol iwl_rx_reply_rx
[ 2356.617290] iwlagn: Unknown symbol iwl_rx_reply_rx
[ 2356.617492] iwlagn: disagrees about version of symbol iwl_mac_get_tx_stats
[ 2356.617496] iwlagn: Unknown symbol iwl_mac_get_tx_stats
[ 2356.617708] iwlagn: disagrees about version of symbol iwl_reset_run_time_calib
[ 2356.617712] iwlagn: Unknown symbol iwl_reset_run_time_calib
[ 2356.617924] iwlagn: disagrees about version of symbol iwl_send_static_wepkey_cmd
[ 2356.617928] iwlagn: Unknown symbol iwl_send_static_wepkey_cmd
[ 2356.618140] iwlagn: disagrees about version of symbol iwl_irq_handle_error
[ 2356.618145] iwlagn: Unknown symbol iwl_irq_handle_error
[ 2356.618479] iwlagn: disagrees about version of symbol iwl_bss_info_changed
[ 2356.618483] iwlagn: Unknown symbol iwl_bss_info_changed
[ 2356.618935] iwlagn: disagrees about version of symbol iwl_clear_stations_table
[ 2356.618940] iwlagn: Unknown symbol iwl_clear_stations_table
[ 2356.619144] iwlagn: disagrees about version of symbol iwl_uninit_drv
[ 2356.619148] iwlagn: Unknown symbol iwl_uninit_drv
[ 2356.619357] iwlagn: disagrees about version of symbol iwl_rx_missed_beacon_notif
[ 2356.619362] iwlagn: Unknown symbol iwl_rx_missed_beacon_notif
[ 2356.619704] iwlagn: disagrees about version of symbol iwl_activate_qos
[ 2356.619708] iwlagn: Unknown symbol iwl_activate_qos
[ 2356.619958] iwlagn: disagrees about version of symbol iwl_eeprom_get_mac
[ 2356.619962] iwlagn: Unknown symbol iwl_eeprom_get_mac
[ 2356.620172] iwlagn: disagrees about version of symbol iwl_send_lq_cmd
[ 2356.620177] iwlagn: Unknown symbol iwl_send_lq_cmd
[ 2356.620380] iwlagn: disagrees about version of symbol iwl_rx_pm_sleep_notif
[ 2356.620385] iwlagn: Unknown symbol iwl_rx_pm_sleep_notif
[ 2356.620588] iwlagn: disagrees about version of symbol iwl_rf_kill_ct_config
[ 2356.620592] iwlagn: Unknown symbol iwl_rf_kill_ct_config
[ 2356.620985] iwlagn: disagrees about version of symbol iwl_sta_rx_agg_start
[ 2356.620989] iwlagn: Unknown symbol iwl_sta_rx_agg_start
[ 2356.621204] iwlagn: disagrees about version of symbol iwl_eeprom_query16
[ 2356.621209] iwlagn: Unknown symbol iwl_eeprom_query16
[ 2356.621442] iwlagn: Unknown symbol iwl_tt_exit_ct_kill
[ 2356.622002] iwlagn: disagrees about version of symbol iwl_full_rxon_required
[ 2356.622006] iwlagn: Unknown symbol iwl_full_rxon_required
[ 2356.622212] iwlagn: disagrees about version of symbol iwlcore_eeprom_query_addr
[ 2356.622216] iwlagn: Unknown symbol iwlcore_eeprom_query_addr
[ 2356.622420] iwlagn: disagrees about version of symbol iwl_free_isr_ict
[ 2356.622424] iwlagn: Unknown symbol iwl_free_isr_ict
[ 2356.622657] iwlagn: Unknown symbol iwl_is_ht40_tx_allowed
[ 2356.622869] iwlagn: disagrees about version of symbol iwl_sensitivity_calibration
[ 2356.622873] iwlagn: Unknown symbol iwl_sensitivity_calibration
[ 2356.623099] iwlagn: disagrees about version of symbol ieee80211_wake_queues
[ 2356.623104] iwlagn: Unknown symbol ieee80211_wake_queues
[ 2356.623315] iwlagn: disagrees about version of symbol iwl_send_calib_results
[ 2356.623320] iwlagn: Unknown symbol iwl_send_calib_results
[ 2356.623528] iwlagn: disagrees about version of symbol iwl_rx_queue_free
[ 2356.623532] iwlagn: Unknown symbol iwl_rx_queue_free
[ 2356.623742] iwlagn: disagrees about version of symbol ieee80211_rate_control_register
[ 2356.623746] iwlagn: Unknown symbol ieee80211_rate_control_register
[ 2356.624173] iwlagn: disagrees about version of symbol iwl_mac_hw_scan
[ 2356.624177] iwlagn: Unknown symbol iwl_mac_hw_scan
[ 2356.624461] iwlagn: disagrees about version of symbol iwl_verify_ucode
[ 2356.624466] iwlagn: Unknown symbol iwl_verify_ucode
[ 2356.624674] iwlagn: disagrees about version of symbol iwl_add_station
[ 2356.624678] iwlagn: Unknown symbol iwl_add_station
[ 2356.624976] iwlagn: Unknown symbol iwl_tt_handler
[ 2356.625177] iwlagn: disagrees about version of symbol iwl_mac_config
[ 2356.625182] iwlagn: Unknown symbol iwl_mac_config
[ 2356.625384] iwlagn: disagrees about version of symbol iwl_set_tx_power
[ 2356.625388] iwlagn: Unknown symbol iwl_set_tx_power
[ 2356.625667] iwlagn: disagrees about version of symbol iwl_rx_statistics
[ 2356.625671] iwlagn: Unknown symbol iwl_rx_statistics
[ 2356.625874] iwlagn: disagrees about version of symbol iwl_setup_mac
[ 2356.625878] iwlagn: Unknown symbol iwl_setup_mac
[ 2356.626091] iwlagn: disagrees about version of symbol iwl_update_tkip_key
[ 2356.626095] iwlagn: Unknown symbol iwl_update_tkip_key
[ 2356.626314] iwlagn: disagrees about version of symbol iwl_send_cmd
[ 2356.626318] iwlagn: Unknown symbol iwl_send_cmd
[ 2356.626525] iwlagn: disagrees about version of symbol iwl_tx_skb
[ 2356.626529] iwlagn: Unknown symbol iwl_tx_skb
[ 2356.626731] iwlagn: disagrees about version of symbol iwl_alloc_isr_ict
[ 2356.626735] iwlagn: Unknown symbol iwl_alloc_isr_ict
[ 2356.627232] iwlagn: disagrees about version of symbol iwl_tx_agg_start
[ 2356.627237] iwlagn: Unknown symbol iwl_tx_agg_start
[ 2356.627451] iwlagn: disagrees about version of symbol ieee80211_stop_queues
[ 2356.627456] iwlagn: Unknown symbol ieee80211_stop_queues
[ 2356.627665] iwlagn: disagrees about version of symbol iwl_tx_queue_reclaim
[ 2356.627670] iwlagn: Unknown symbol iwl_tx_queue_reclaim
[ 2356.627872] iwlagn: disagrees about version of symbol iwl_mac_beacon_update
[ 2356.627877] iwlagn: Unknown symbol iwl_mac_beacon_update
[ 2356.628091] iwlagn: disagrees about version of symbol iwl_eeprom_check_version
[ 2356.628095] iwlagn: Unknown symbol iwl_eeprom_check_version
[ 2356.628301] iwlagn: disagrees about version of symbol iwl_get_channel_info
[ 2356.628305] iwlagn: Unknown symbol iwl_get_channel_info
[ 2356.628983] iwlagn: disagrees about version of symbol iwl_set_hw_params
[ 2356.628988] iwlagn: Unknown symbol iwl_set_hw_params
[ 2356.629265] iwlagn: disagrees about version of symbol iwl_rx_replenish
[ 2356.629269] iwlagn: Unknown symbol iwl_rx_replenish
[ 2356.629471] iwlagn: disagrees about version of symbol iwl_setup_scan_deferred_work
[ 2356.629476] iwlagn: Unknown symbol iwl_setup_scan_deferred_work
[ 2356.629610] iwlagn: disagrees about version of symbol iwl_check_rxon_cmd
[ 2356.629612] iwlagn: Unknown symbol iwl_check_rxon_cmd
[ 2356.629704] iwlagn: disagrees about version of symbol iwl_mac_reset_tsf
[ 2356.629706] iwlagn: Unknown symbol iwl_mac_reset_tsf
[ 2356.629797] iwlagn: disagrees about version of symbol iwl_rate_get_lowest_plcp
[ 2356.629800] iwlagn: Unknown symbol iwl_rate_get_lowest_plcp
[ 2356.629897] iwlagn: disagrees about version of symbol iwl_hw_nic_init
[ 2356.629899] iwlagn: Unknown symbol iwl_hw_nic_init
[ 2356.630055] iwlagn: Unknown symbol rate_control_send_low
[ 2356.630175] iwlagn: disagrees about version of symbol iwl_hw_detect
[ 2356.630178] iwlagn: Unknown symbol iwl_hw_detect
[ 2356.630270] iwlagn: disagrees about version of symbol iwl_alloc_all
[ 2356.630272] iwlagn: Unknown symbol iwl_alloc_all
[ 2356.630363] iwlagn: disagrees about version of symbol iwl_disable_ict
[ 2356.630365] iwlagn: Unknown symbol iwl_disable_ict
[ 2356.630460] iwlagn: disagrees about version of symbol ieee80211_unregister_hw
[ 2356.630463] iwlagn: Unknown symbol ieee80211_unregister_hw
[ 2356.630569] iwlagn: Unknown symbol iwl_tt_enter_ct_kill
[ 2356.630718] iwlagn: disagrees about version of symbol iwl_power_initialize
[ 2356.630721] iwlagn: Unknown symbol iwl_power_initialize
[ 2356.630815] iwlagn: disagrees about version of symbol iwl_sta_rx_agg_stop
[ 2356.630817] iwlagn: Unknown symbol iwl_sta_rx_agg_stop
[ 2356.631068] iwlagn: disagrees about version of symbol iwl_hwrate_to_tx_control
[ 2356.631071] iwlagn: Unknown symbol iwl_hwrate_to_tx_control
[ 2356.631251] iwlagn: disagrees about version of symbol iwl_leds_register
[ 2356.631253] iwlagn: Unknown symbol iwl_leds_register
[ 2356.631342] iwlagn: disagrees about version of symbol iwl_rx_reply_error
[ 2356.631344] iwlagn: Unknown symbol iwl_rx_reply_error
[ 2356.631436] iwlagn: disagrees about version of symbol iwl_remove_default_wep_key
[ 2356.631438] iwlagn: Unknown symbol iwl_remove_default_wep_key
[ 2356.631561] iwlagn: disagrees about version of symbol iwl_send_cmd_pdu_async
[ 2356.631563] iwlagn: Unknown symbol iwl_send_cmd_pdu_async
[ 2356.631651] iwlagn: disagrees about version of symbol iwl_rx_queue_restock
[ 2356.631654] iwlagn: Unknown symbol iwl_rx_queue_restock
[ 2356.631771] iwlagn: Unknown symbol iwl_tx_ant_restriction
[ 2356.631862] iwlagn: disagrees about version of symbol iwl_eeprom_query_addr
[ 2356.631864] iwlagn: Unknown symbol iwl_eeprom_query_addr
[ 2356.631957] iwlagn: disagrees about version of symbol iwl_leds_unregister
[ 2356.631959] iwlagn: Unknown symbol iwl_leds_unregister
[ 2356.632052] iwlagn: disagrees about version of symbol ieee80211_beacon_get
[ 2356.632054] iwlagn: Unknown symbol ieee80211_beacon_get
[ 2356.632143] iwlagn: disagrees about version of symbol iwl_mac_conf_tx
[ 2356.632145] iwlagn: Unknown symbol iwl_mac_conf_tx
[ 2356.632233] iwlagn: disagrees about version of symbol iwl_rx_csa
[ 2356.632235] iwlagn: Unknown symbol iwl_rx_csa
[ 2356.632332] iwlagn: disagrees about version of symbol iwl_rx_replenish_now
[ 2356.632334] iwlagn: Unknown symbol iwl_rx_replenish_now
[ 2356.632426] iwlagn: disagrees about version of symbol iwl_find_station
[ 2356.632428] iwlagn: Unknown symbol iwl_find_station
[ 2356.632520] iwlagn: disagrees about version of symbol iwl_set_dynamic_key
[ 2356.632523] iwlagn: Unknown symbol iwl_set_dynamic_key
[ 2356.632612] iwlagn: disagrees about version of symbol iwl_send_bt_config
[ 2356.632614] iwlagn: Unknown symbol iwl_send_bt_config
[ 2356.632703] iwlagn: disagrees about version of symbol iwl_mac_remove_interface
[ 2356.632705] iwlagn: Unknown symbol iwl_mac_remove_interface
[ 2356.632796] iwlagn: disagrees about version of symbol iwl_txq_check_empty
[ 2356.632798] iwlagn: Unknown symbol iwl_txq_check_empty
[ 2356.632917] iwlagn: disagrees about version of symbol iwl_rx_queue_update_write_ptr
[ 2356.632919] iwlagn: Unknown symbol iwl_rx_queue_update_write_ptr
[ 2356.633017] iwlagn: disagrees about version of symbol iwl_tx_agg_stop
[ 2356.633019] iwlagn: Unknown symbol iwl_tx_agg_stop
[ 2356.633264] iwlagn: disagrees about version of symbol iwl_set_rxon_chain
[ 2356.633266] iwlagn: Unknown symbol iwl_set_rxon_chain
[ 2356.633355] iwlagn: disagrees about version of symbol iwl_configure_filter
[ 2356.633357] iwlagn: Unknown symbol iwl_configure_filter
[ 2356.633462] iwlagn: disagrees about version of symbol iwlcore_eeprom_verify_signature
[ 2356.633465] iwlagn: Unknown symbol iwlcore_eeprom_verify_signature
[ 2356.633578] iwlagn: disagrees about version of symbol iwl_rx_pm_debug_statistics_notif
[ 2356.633580] iwlagn: Unknown symbol iwl_rx_pm_debug_statistics_notif
[ 2356.633686] iwlagn: Unknown symbol iwl_tt_exit
[ 2356.633776] iwlagn: disagrees about version of symbol iwl_rxq_stop
[ 2356.633779] iwlagn: Unknown symbol iwl_rxq_stop
[ 2366.845329] iwlagn: disagrees about version of symbol iwl_rxon_add_station
[ 2366.845335] iwlagn: Unknown symbol iwl_rxon_add_station
[ 2366.845473] iwlagn: disagrees about version of symbol iwl_set_mode
[ 2366.845476] iwlagn: Unknown symbol iwl_set_mode
[ 2366.845614] iwlagn: disagrees about version of symbol iwl_scan_cancel_timeout
[ 2366.845618] iwlagn: Unknown symbol iwl_scan_cancel_timeout
[ 2366.845750] iwlagn: disagrees about version of symbol iwl_mac_add_interface
[ 2366.845753] iwlagn: Unknown symbol iwl_mac_add_interface
[ 2366.846021] iwlagn: disagrees about version of symbol iwl_connection_init_rx_config
[ 2366.846024] iwlagn: Unknown symbol iwl_connection_init_rx_config
[ 2366.846294] iwlagn: disagrees about version of symbol iwl_send_statistics_request
[ 2366.846298] iwlagn: Unknown symbol iwl_send_statistics_request
[ 2366.846459] iwlagn: Unknown symbol iwl_ht_enabled
[ 2366.846680] iwlagn: disagrees about version of symbol iwl_set_default_wep_key
[ 2366.846685] iwlagn: Unknown symbol iwl_set_default_wep_key
[ 2366.846835] iwlagn: disagrees about version of symbol iwl_scan_cancel
[ 2366.846839] iwlagn: Unknown symbol iwl_scan_cancel
[ 2366.847221] iwlagn: disagrees about version of symbol iwl_chain_noise_calibration
[ 2366.847224] iwlagn: Unknown symbol iwl_chain_noise_calibration
[ 2366.847447] iwlagn: Unknown symbol iwl_setup_spectrum_handlers
[ 2366.847581] iwlagn: disagrees about version of symbol ieee80211_free_hw
[ 2366.847584] iwlagn: Unknown symbol ieee80211_free_hw
[ 2366.847848] iwlagn: disagrees about version of symbol iwl_remove_dynamic_key
[ 2366.847851] iwlagn: Unknown symbol iwl_remove_dynamic_key
[ 2366.848040] iwlagn: disagrees about version of symbol iwl_get_ra_sta_id
[ 2366.848043] iwlagn: Unknown symbol iwl_get_ra_sta_id
[ 2366.848227] iwlagn: disagrees about version of symbol iwl_rx_reply_compressed_ba
[ 2366.848231] iwlagn: Unknown symbol iwl_rx_reply_compressed_ba
[ 2366.848386] iwlagn: disagrees about version of symbol iwl_txq_update_write_ptr
[ 2366.848390] iwlagn: Unknown symbol iwl_txq_update_write_ptr
[ 2366.848564] iwlagn: disagrees about version of symbol iwl_eeprom_free
[ 2366.848568] iwlagn: Unknown symbol iwl_eeprom_free
[ 2366.848840] iwlagn: Unknown symbol iwlcore_eeprom_enhanced_txpower
[ 2366.848979] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[ 2366.848986] iwlagn: Unknown symbol ieee80211_start_tx_ba_session
[ 2366.849256] iwlagn: disagrees about version of symbol iwl_sta_tx_modify_enable_tid
[ 2366.849263] iwlagn: Unknown symbol iwl_sta_tx_modify_enable_tid
[ 2366.849398] iwlagn: disagrees about version of symbol iwl_power_update_mode
[ 2366.849404] iwlagn: Unknown symbol iwl_power_update_mode
[ 2366.849538] iwlagn: disagrees about version of symbol iwlcore_eeprom_release_semaphore
[ 2366.849545] iwlagn: Unknown symbol iwlcore_eeprom_release_semaphore
[ 2366.849699] iwlagn: disagrees about version of symbol iwl_hw_txq_ctx_free
[ 2366.849706] iwlagn: Unknown symbol iwl_hw_txq_ctx_free
[ 2366.849973] iwlagn: disagrees about version of symbol iwl_eeprom_init
[ 2366.849979] iwlagn: Unknown symbol iwl_eeprom_init
[ 2366.850161] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[ 2366.850166] iwlagn: Unknown symbol ieee80211_restart_hw
[ 2366.850302] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[ 2366.850308] iwlagn: Unknown symbol ieee80211_rate_control_unregister
[ 2366.850450] iwlagn: disagrees about version of symbol iwl_set_rxon_ht
[ 2366.850457] iwlagn: Unknown symbol iwl_set_rxon_ht
[ 2366.850607] iwlagn: Unknown symbol iwl_setup_rxon_timing
[ 2366.850745] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[ 2366.850751] iwlagn: Unknown symbol ieee80211_wake_queue
[ 2366.850949] iwlagn: Unknown symbol iwl_debug_level
[ 2366.851099] iwlagn: Unknown symbol iwl_tt_initialize
[ 2366.851290] iwlagn: disagrees about version of symbol iwl_txq_ctx_stop
[ 2366.851296] iwlagn: Unknown symbol iwl_txq_ctx_stop
[ 2366.851480] iwlagn: disagrees about version of symbol iwlcore_eeprom_acquire_semaphore
[ 2366.851489] iwlagn: Unknown symbol iwlcore_eeprom_acquire_semaphore
[ 2366.851662] iwlagn: disagrees about version of symbol iwl_init_drv
[ 2366.851669] iwlagn: Unknown symbol iwl_init_drv
[ 2366.851819] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[ 2366.851825] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state
[ 2366.852051] iwlagn: disagrees about version of symbol iwl_tx_cmd_complete
[ 2366.852057] iwlagn: Unknown symbol iwl_tx_cmd_complete
[ 2366.852190] iwlagn: disagrees about version of symbol iwl_reset_ict
[ 2366.852196] iwlagn: Unknown symbol iwl_reset_ict
[ 2366.852337] iwlagn: disagrees about version of symbol iwl_rx_reply_rx_phy
[ 2366.852343] iwlagn: Unknown symbol iwl_rx_reply_rx_phy
[ 2366.852481] iwlagn: disagrees about version of symbol iwl_setup_rx_scan_handlers
[ 2366.852486] iwlagn: Unknown symbol iwl_setup_rx_scan_handlers
[ 2366.852622] iwlagn: disagrees about version of symbol iwl_send_cmd_pdu
[ 2366.852627] iwlagn: Unknown symbol iwl_send_cmd_pdu
[ 2366.852812] iwlagn: disagrees about version of symbol iwl_set_rxon_hwcrypto
[ 2366.852820] iwlagn: Unknown symbol iwl_set_rxon_hwcrypto
[ 2366.853053] iwlagn: disagrees about version of symbol iwl_init_sensitivity
[ 2366.853059] iwlagn: Unknown symbol iwl_init_sensitivity
[ 2366.853243] iwlagn: disagrees about version of symbol iwl_rx_reply_rx
[ 2366.853251] iwlagn: Unknown symbol iwl_rx_reply_rx
[ 2366.853446] iwlagn: disagrees about version of symbol iwl_mac_get_tx_stats
[ 2366.853454] iwlagn: Unknown symbol iwl_mac_get_tx_stats
[ 2366.853679] iwlagn: disagrees about version of symbol iwl_reset_run_time_calib
[ 2366.853689] iwlagn: Unknown symbol iwl_reset_run_time_calib
[ 2366.853905] iwlagn: disagrees about version of symbol iwl_send_static_wepkey_cmd
[ 2366.853914] iwlagn: Unknown symbol iwl_send_static_wepkey_cmd
[ 2366.854177] iwlagn: disagrees about version of symbol iwl_irq_handle_error
[ 2366.854186] iwlagn: Unknown symbol iwl_irq_handle_error
[ 2366.854560] iwlagn: disagrees about version of symbol iwl_bss_info_changed
[ 2366.854569] iwlagn: Unknown symbol iwl_bss_info_changed
[ 2366.855046] iwlagn: disagrees about version of symbol iwl_clear_stations_table
[ 2366.855056] iwlagn: Unknown symbol iwl_clear_stations_table
[ 2366.855259] iwlagn: disagrees about version of symbol iwl_uninit_drv
[ 2366.855264] iwlagn: Unknown symbol iwl_uninit_drv
[ 2366.855451] iwlagn: disagrees about version of symbol iwl_rx_missed_beacon_notif
[ 2366.855457] iwlagn: Unknown symbol iwl_rx_missed_beacon_notif
[ 2366.855718] iwlagn: disagrees about version of symbol iwl_activate_qos
[ 2366.855722] iwlagn: Unknown symbol iwl_activate_qos
[ 2366.855880] iwlagn: disagrees about version of symbol iwl_eeprom_get_mac
[ 2366.855883] iwlagn: Unknown symbol iwl_eeprom_get_mac
[ 2366.856017] iwlagn: disagrees about version of symbol iwl_send_lq_cmd
[ 2366.856023] iwlagn: Unknown symbol iwl_send_lq_cmd
[ 2366.856152] iwlagn: disagrees about version of symbol iwl_rx_pm_sleep_notif
[ 2366.856158] iwlagn: Unknown symbol iwl_rx_pm_sleep_notif
[ 2366.856287] iwlagn: disagrees about version of symbol iwl_rf_kill_ct_config
[ 2366.856295] iwlagn: Unknown symbol iwl_rf_kill_ct_config
[ 2366.856548] iwlagn: disagrees about version of symbol iwl_sta_rx_agg_start
[ 2366.856554] iwlagn: Unknown symbol iwl_sta_rx_agg_start
[ 2366.856763] iwlagn: disagrees about version of symbol iwl_eeprom_query16
[ 2366.856771] iwlagn: Unknown symbol iwl_eeprom_query16
[ 2366.857040] iwlagn: Unknown symbol iwl_tt_exit_ct_kill
[ 2366.857392] iwlagn: disagrees about version of symbol iwl_full_rxon_required
[ 2366.857396] iwlagn: Unknown symbol iwl_full_rxon_required
[ 2366.857507] iwlagn: disagrees about version of symbol iwlcore_eeprom_query_addr
[ 2366.857511] iwlagn: Unknown symbol iwlcore_eeprom_query_addr
[ 2366.857617] iwlagn: disagrees about version of symbol iwl_free_isr_ict
[ 2366.857620] iwlagn: Unknown symbol iwl_free_isr_ict
[ 2366.857738] iwlagn: Unknown symbol iwl_is_ht40_tx_allowed
[ 2366.857842] iwlagn: disagrees about version of symbol iwl_sensitivity_calibration
[ 2366.857847] iwlagn: Unknown symbol iwl_sensitivity_calibration
[ 2366.857967] iwlagn: disagrees about version of symbol ieee80211_wake_queues
[ 2366.857971] iwlagn: Unknown symbol ieee80211_wake_queues
[ 2366.858078] iwlagn: disagrees about version of symbol iwl_send_calib_results
[ 2366.858082] iwlagn: Unknown symbol iwl_send_calib_results
[ 2366.858190] iwlagn: disagrees about version of symbol iwl_rx_queue_free
[ 2366.858194] iwlagn: Unknown symbol iwl_rx_queue_free
[ 2366.858302] iwlagn: disagrees about version of symbol ieee80211_rate_control_register
[ 2366.858306] iwlagn: Unknown symbol ieee80211_rate_control_register
[ 2366.858526] iwlagn: disagrees about version of symbol iwl_mac_hw_scan
[ 2366.858529] iwlagn: Unknown symbol iwl_mac_hw_scan
[ 2366.858611] iwlagn: disagrees about version of symbol iwl_verify_ucode
[ 2366.858613] iwlagn: Unknown symbol iwl_verify_ucode
[ 2366.858673] iwlagn: disagrees about version of symbol iwl_add_station
[ 2366.858675] iwlagn: Unknown symbol iwl_add_station
[ 2366.858761] iwlagn: Unknown symbol iwl_tt_handler
[ 2366.858819] iwlagn: disagrees about version of symbol iwl_mac_config
[ 2366.858822] iwlagn: Unknown symbol iwl_mac_config
[ 2366.858880] iwlagn: disagrees about version of symbol iwl_set_tx_power
[ 2366.858883] iwlagn: Unknown symbol iwl_set_tx_power
[ 2366.858963] iwlagn: disagrees about version of symbol iwl_rx_statistics
[ 2366.858965] iwlagn: Unknown symbol iwl_rx_statistics
[ 2366.859024] iwlagn: disagrees about version of symbol iwl_setup_mac
[ 2366.859026] iwlagn: Unknown symbol iwl_setup_mac
[ 2366.859085] iwlagn: disagrees about version of symbol iwl_update_tkip_key
[ 2366.859088] iwlagn: Unknown symbol iwl_update_tkip_key
[ 2366.859151] iwlagn: disagrees about version of symbol iwl_send_cmd
[ 2366.859153] iwlagn: Unknown symbol iwl_send_cmd
[ 2366.859212] iwlagn: disagrees about version of symbol iwl_tx_skb
[ 2366.859214] iwlagn: Unknown symbol iwl_tx_skb
[ 2366.859272] iwlagn: disagrees about version of symbol iwl_alloc_isr_ict
[ 2366.859274] iwlagn: Unknown symbol iwl_alloc_isr_ict
[ 2366.859415] iwlagn: disagrees about version of symbol iwl_tx_agg_start
[ 2366.859417] iwlagn: Unknown symbol iwl_tx_agg_start
[ 2366.859477] iwlagn: disagrees about version of symbol ieee80211_stop_queues
[ 2366.859479] iwlagn: Unknown symbol ieee80211_stop_queues
[ 2366.859539] iwlagn: disagrees about version of symbol iwl_tx_queue_reclaim
[ 2366.859541] iwlagn: Unknown symbol iwl_tx_queue_reclaim
[ 2366.859599] iwlagn: disagrees about version of symbol iwl_mac_beacon_update
[ 2366.859602] iwlagn: Unknown symbol iwl_mac_beacon_update
[ 2366.859663] iwlagn: disagrees about version of symbol iwl_eeprom_check_version
[ 2366.859666] iwlagn: Unknown symbol iwl_eeprom_check_version
[ 2366.859724] iwlagn: disagrees about version of symbol iwl_get_channel_info
[ 2366.859727] iwlagn: Unknown symbol iwl_get_channel_info
[ 2366.859920] iwlagn: disagrees about version of symbol iwl_set_hw_params
[ 2366.859922] iwlagn: Unknown symbol iwl_set_hw_params
[ 2366.860001] iwlagn: disagrees about version of symbol iwl_rx_replenish
[ 2366.860004] iwlagn: Unknown symbol iwl_rx_replenish
[ 2366.860064] iwlagn: disagrees about version of symbol iwl_setup_scan_deferred_work
[ 2366.860066] iwlagn: Unknown symbol iwl_setup_scan_deferred_work
[ 2366.860133] iwlagn: disagrees about version of symbol iwl_check_rxon_cmd
[ 2366.860135] iwlagn: Unknown symbol iwl_check_rxon_cmd
[ 2366.860193] iwlagn: disagrees about version of symbol iwl_mac_reset_tsf
[ 2366.860195] iwlagn: Unknown symbol iwl_mac_reset_tsf
[ 2366.860253] iwlagn: disagrees about version of symbol iwl_rate_get_lowest_plcp
[ 2366.860256] iwlagn: Unknown symbol iwl_rate_get_lowest_plcp
[ 2366.860323] iwlagn: disagrees about version of symbol iwl_hw_nic_init
[ 2366.860326] iwlagn: Unknown symbol iwl_hw_nic_init
[ 2366.860413] iwlagn: Unknown symbol rate_control_send_low
[ 2366.860489] iwlagn: disagrees about version of symbol iwl_hw_detect
[ 2366.860491] iwlagn: Unknown symbol iwl_hw_detect
[ 2366.860549] iwlagn: disagrees about version of symbol iwl_alloc_all
[ 2366.860551] iwlagn: Unknown symbol iwl_alloc_all
[ 2366.860609] iwlagn: disagrees about version of symbol iwl_disable_ict
[ 2366.860611] iwlagn: Unknown symbol iwl_disable_ict
[ 2366.860671] iwlagn: disagrees about version of symbol ieee80211_unregister_hw
[ 2366.860673] iwlagn: Unknown symbol ieee80211_unregister_hw
[ 2366.860741] iwlagn: Unknown symbol iwl_tt_enter_ct_kill
[ 2366.860840] iwlagn: disagrees about version of symbol iwl_power_initialize
[ 2366.860842] iwlagn: Unknown symbol iwl_power_initialize
[ 2366.860901] iwlagn: disagrees about version of symbol iwl_sta_rx_agg_stop
[ 2366.860904] iwlagn: Unknown symbol iwl_sta_rx_agg_stop
[ 2366.861062] iwlagn: disagrees about version of symbol iwl_hwrate_to_tx_control
[ 2366.861065] iwlagn: Unknown symbol iwl_hwrate_to_tx_control
[ 2366.861180] iwlagn: disagrees about version of symbol iwl_leds_register
[ 2366.861182] iwlagn: Unknown symbol iwl_leds_register
[ 2366.861240] iwlagn: disagrees about version of symbol iwl_rx_reply_error
[ 2366.861242] iwlagn: Unknown symbol iwl_rx_reply_error
[ 2366.861301] iwlagn: disagrees about version of symbol iwl_remove_default_wep_key
[ 2366.861304] iwlagn: Unknown symbol iwl_remove_default_wep_key
[ 2366.861383] iwlagn: disagrees about version of symbol iwl_send_cmd_pdu_async
[ 2366.861385] iwlagn: Unknown symbol iwl_send_cmd_pdu_async
[ 2366.861444] iwlagn: disagrees about version of symbol iwl_rx_queue_restock
[ 2366.861446] iwlagn: Unknown symbol iwl_rx_queue_restock
[ 2366.861514] iwlagn: Unknown symbol iwl_tx_ant_restriction
[ 2366.861572] iwlagn: disagrees about version of symbol iwl_eeprom_query_addr
[ 2366.861574] iwlagn: Unknown symbol iwl_eeprom_query_addr
[ 2366.861634] iwlagn: disagrees about version of symbol iwl_leds_unregister
[ 2366.861636] iwlagn: Unknown symbol iwl_leds_unregister
[ 2366.861695] iwlagn: disagrees about version of symbol ieee80211_beacon_get
[ 2366.861697] iwlagn: Unknown symbol ieee80211_beacon_get
[ 2366.861754] iwlagn: disagrees about version of symbol iwl_mac_conf_tx
[ 2366.861757] iwlagn: Unknown symbol iwl_mac_conf_tx
[ 2366.861814] iwlagn: disagrees about version of symbol iwl_rx_csa
[ 2366.861816] iwlagn: Unknown symbol iwl_rx_csa
[ 2366.861879] iwlagn: disagrees about version of symbol iwl_rx_replenish_now
[ 2366.861881] iwlagn: Unknown symbol iwl_rx_replenish_now
[ 2366.861940] iwlagn: disagrees about version of symbol iwl_find_station
[ 2366.861943] iwlagn: Unknown symbol iwl_find_station
[ 2366.862002] iwlagn: disagrees about version of symbol iwl_set_dynamic_key
[ 2366.862004] iwlagn: Unknown symbol iwl_set_dynamic_key
[ 2366.862062] iwlagn: disagrees about version of symbol iwl_send_bt_config
[ 2366.862064] iwlagn: Unknown symbol iwl_send_bt_config
[ 2366.862121] iwlagn: disagrees about version of symbol iwl_mac_remove_interface
[ 2366.862123] iwlagn: Unknown symbol iwl_mac_remove_interface
[ 2366.862182] iwlagn: disagrees about version of symbol iwl_txq_check_empty
[ 2366.862184] iwlagn: Unknown symbol iwl_txq_check_empty
[ 2366.862260] iwlagn: disagrees about version of symbol iwl_rx_queue_update_write_ptr
[ 2366.862263] iwlagn: Unknown symbol iwl_rx_queue_update_write_ptr
[ 2366.862326] iwlagn: disagrees about version of symbol iwl_tx_agg_stop
[ 2366.862328] iwlagn: Unknown symbol iwl_tx_agg_stop
[ 2366.862484] iwlagn: disagrees about version of symbol iwl_set_rxon_chain
[ 2366.862487] iwlagn: Unknown symbol iwl_set_rxon_chain
[ 2366.862544] iwlagn: disagrees about version of symbol iwl_configure_filter
[ 2366.862546] iwlagn: Unknown symbol iwl_configure_filter
[ 2366.862614] iwlagn: disagrees about version of symbol iwlcore_eeprom_verify_signature
[ 2366.862617] iwlagn: Unknown symbol iwlcore_eeprom_verify_signature
[ 2366.862690] iwlagn: disagrees about version of symbol iwl_rx_pm_debug_statistics_notif
[ 2366.862692] iwlagn: Unknown symbol iwl_rx_pm_debug_statistics_notif
[ 2366.862760] iwlagn: Unknown symbol iwl_tt_exit
[ 2366.862818] iwlagn: disagrees about version of symbol iwl_rxq_stop
[ 2366.862820] iwlagn: Unknown symbol iwl_rxq_stop

---

### Post by gekkos on 2010-04-12
Hi,

Many thanks
after installing linux-backports-modules-karmic-generic and rebott my wireless lan card was recognized.

---

### Post by zakeen on 2010-04-21
Installing the backports dont work for me :(

Any idea's please? Sony Vaio Z, 9.10, advanced-N 6200 intel

me@ubuntu-z:~$ dmesg | grep iwl
[    6.100940] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    6.100943] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    6.103081] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.103089] iwlagn 0000:02:00.0: setting latency timer to 64
[    6.103140] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[    6.130046] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    6.130124] iwlagn 0000:02:00.0: irq 35 for MSI/MSI-X
[    6.144342] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.150704] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[    6.154198] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[    6.154204] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[    6.157156] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[    6.157160] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[    6.160892] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[    6.160897] iwlagn 0000:02:00.0: Could not read microcode: -2
[    6.163070] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[    6.164698] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[    6.164702] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[    6.168454] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[    6.168460] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[    6.172092] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[    6.172097] iwlagn 0000:02:00.0: Could not read microcode: -2
me@ubuntu-z:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
me@ubuntu-z:~$ sudo apt-get install linux-backports-modules-karmic-generic
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-karmic-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by bkratz on 2010-04-21
@zakeen

Your dmesg output looks just like the one in this bug, which was supposedly taken care of a long time ago.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926)

I don't have any answers but several of the respondents did several different things. #7 looks particularly interesting.

---

### Post by chili555 on 2010-04-21
The firmware you need is here:```
sudo apt-get install linux-firmware
sudo rmmod -f iwlagn && sudo modprobe iwlagn
```If you dont have an internet connection, you can get it here and transfer it on a USB key:  [http://packages.ubuntu.com/karmic/linux-firmware](http://packages.ubuntu.com/karmic/linux-firmware)

---

### Post by zakeen on 2010-04-21
thanks guys. Whats strange is when I have the switch flicked off "enable wireless" is no high lighted. When its on, then I can unclick the box. still cant see a network.


> **bkratz said:**
> @zakeen

Your dmesg output looks just like the one in this bug, which was supposedly taken care of a long time ago.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926)

I don't have any answers but several of the respondents did several different things. #7 looks particularly interesting.

Thanks, Im looking into this and it seems like that link you have is a bit of mess in there, as in whats correct and what not. I have to read i again before I start to play :) I like to understand what Im doing, but most things that are stated I have not tried yet. So Im working on it now.

@chili555

I tried what you stated, but same thing:

me@ubuntu-z:~$ sudo apt-get install linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@ubuntu-z:~$ sudo rmmod -f iwlagn && sudo modprobe iwlagn

---

### Post by chili555 on 2010-04-21
Let's see if the file is there and has the correct permissions. Please let us see:```
ls -al /lib/firmware | grep ucode
```

---

### Post by zakeen on 2010-04-21
Just got it working :) Letting you know I followed this:

[http://ubuntuforums.org/showpost.php?p=9127310&postcount=14](http://ubuntuforums.org/showpost.php?p=9127310&postcount=14)

Thanks for your time into this.

---

### Post by Tempcooler on 2011-04-11
I have the same wifi card and its not detected. ive tried all of the above with no luck.
Laptop panasonic toughbook cf-19
OS Ubuntu netbook edition 10.10
wifi advanced-N 6200


im new to linux please help

---

### Post by chili555 on 2011-04-12
> **Tempcooler said:**
> I have the same wifi card and its not detected. ive tried all of the above with no luck.
Laptop panasonic toughbook cf-19
OS Ubuntu netbook edition 10.10
wifi advanced-N 6200


im new to linux please helpPlease post:```
dmesg | grep iwl
ls /lib/firmware | grep ucode
sudo dpkg -s linux-firmware
rfkill list all
```Thanks.

---

### Post by hmehta123 on 2011-05-04
I have the same problem on 11.04, running on the HP 8440P
There is a "on" switch just above the keyboard, but it only glows amber and will not switch to blue, the switch works in windows, but never since I installed 11.04 (clean install, blew away the windows partition)(and by switch i mean one of those soft touch type things, not a mechanical switches)

Here is the out put of the commands you asked for:


hemenm@Gleek:~$ dmesg | grep iwl
[    9.428228] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.428232] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    9.428309] iwlagn 0000:44:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.428320] iwlagn 0000:44:00.0: setting latency timer to 64
[    9.428356] iwlagn 0000:44:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    9.444530] iwlagn 0000:44:00.0: device EEPROM VER=0x436, CALIB=0x6
[    9.444534] iwlagn 0000:44:00.0: Device SKU: 0Xb
[    9.444574] iwlagn 0000:44:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.444655] iwlagn 0000:44:00.0: irq 43 for MSI/MSI-X
[    9.497246] iwlagn 0000:44:00.0: loaded firmware version 9.221.4.1 build 25532
[    9.551610] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  441.750415] iwlagn 0000:44:00.0: PCI INT A disabled
[  441.792584] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  441.792587] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  441.792660] iwlagn 0000:44:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  441.792673] iwlagn 0000:44:00.0: setting latency timer to 64
[  441.792715] iwlagn 0000:44:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[  441.808898] iwlagn 0000:44:00.0: device EEPROM VER=0x436, CALIB=0x6
[  441.808900] iwlagn 0000:44:00.0: Device SKU: 0Xb
[  441.808917] iwlagn 0000:44:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  441.808995] iwlagn 0000:44:00.0: irq 43 for MSI/MSI-X
[  441.813067] iwlagn 0000:44:00.0: loaded firmware version 9.221.4.1 build 25532
[  441.814084] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'




hemenm@Gleek:~$ ls /lib/firmware | grep ucode
iwlwifi-1000-3.ucode
iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2b-5.ucode
iwlwifi-6050-4.ucode
iwlwifi-6050-5.ucode



hemenm@Gleek:~$ sudo dpkg -s linux-firmware
Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 32908
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Version: 1.52
Replaces: atmel-firmware, linux-restricted-common
Provides: atmel-firmware
Conflicts: atmel-firmware
Description: Firmware for Linux kernel drivers
 This package provides firmware used by Linux kernel drivers.




hemenm@Gleek:~$ rfkill list all
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2011-05-04
> hemenm@Gleek:~$ rfkill list all
1: phy1: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]It thinks it's blocked by a hardware switch. Please try:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Now does your wireless work?

---

### Post by hmehta123 on 2011-05-04
nope, I get the following after doing what you suggested

hemenm@Gleek:~$ rfkill list all
1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: yes

---

### Post by chili555 on 2011-05-04
I am getting low on ideas. When you manipulate the wireless button and then run:```
rfkill list all
```Is there no change in hard blocked=yes? Let's see:```
lsmod | grep hp
```

---

### Post by hmehta123 on 2011-05-05
After a restart, it started working, dont know why, but it works!
Thank you!!!

---

