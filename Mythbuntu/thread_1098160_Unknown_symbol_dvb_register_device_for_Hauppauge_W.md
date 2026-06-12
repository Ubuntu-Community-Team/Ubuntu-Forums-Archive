---
title: "Unknown symbol dvb_register_device for Hauppauge WinTV Nova-T(D) 500 in 8.04"
date: 2009-03-16
forum: Mythbuntu
---

### Post by Tux+ on 2009-03-16
I got the Nova-T(D) 500 installed and ready to go. Unfortunately I got the card with 2 arial ports with the label SL-287-V2.0-UK but no diversity sticker with rev 84109.

From my understanding it is supported in 8.10 but I thought I'd try and build the drivers to work under 8.04 like this person has:

[http://www.djcnet.co.uk/howto-mythtv-and-the-nova-td-500-tv-card.html]("http://www.djcnet.co.uk/howto-mythtv-and-the-nova-td-500-tv-card.html")

I followed the guide on MythTV's wiki:
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

dmesg | grep -i dvb gives me this (couldn't attach as file because it was too big):

```
] budget_core: Unknown symbol dvb_unregister_adapter
[  880.383575] dvb_usb_dibusb_common: disagrees about version of symbol dvb_usb_nec_rc_key_to_event
[  880.383582] dvb_usb_dibusb_common: Unknown symbol dvb_usb_nec_rc_key_to_event
[  880.383610] dvb_usb_dibusb_common: disagrees about version of symbol dvb_usb_generic_rw
[  880.383612] dvb_usb_dibusb_common: Unknown symbol dvb_usb_generic_rw
[  880.383653] dvb_usb_dibusb_common: disagrees about version of symbol dib3000mc_set_config
[  880.383654] dvb_usb_dibusb_common: Unknown symbol dib3000mc_set_config
[  880.383683] dvb_usb_dibusb_common: disagrees about version of symbol dib3000mc_get_tuner_i2c_master
[  880.383685] dvb_usb_dibusb_common: Unknown symbol dib3000mc_get_tuner_i2c_master
[  880.383715] dvb_usb_dibusb_common: disagrees about version of symbol dib3000mc_pid_control
[  880.383717] dvb_usb_dibusb_common: Unknown symbol dib3000mc_pid_control
[  880.383744] dvb_usb_dibusb_common: disagrees about version of symbol dvb_usb_generic_write
[  880.383746] dvb_usb_dibusb_common: Unknown symbol dvb_usb_generic_write
[  880.383772] dvb_usb_dibusb_common: disagrees about version of symbol dib3000mc_pid_parse
[  880.383773] dvb_usb_dibusb_common: Unknown symbol dib3000mc_pid_parse
[  880.386511] dvb_usb_ttusb2: disagrees about version of symbol dvb_usb_generic_rw
[  880.386517] dvb_usb_ttusb2: Unknown symbol dvb_usb_generic_rw
[  880.386647] dvb_usb_ttusb2: disagrees about version of symbol dvb_usb_device_init
[  880.386648] dvb_usb_ttusb2: Unknown symbol dvb_usb_device_init
[  880.453966] dvb_usb_af9015: disagrees about version of symbol dvb_usb_device_init
[  880.453972] dvb_usb_af9015: Unknown symbol dvb_usb_device_init
[  880.484582] dvb_usb_af9005: disagrees about version of symbol dvb_usb_device_init
[  880.484589] dvb_usb_af9005: Unknown symbol dvb_usb_device_init
[  880.524032] dvb_usb_gp8psk: disagrees about version of symbol dvb_usb_device_init
[  880.524038] dvb_usb_gp8psk: Unknown symbol dvb_usb_device_init
[  880.524090] dvb_usb_gp8psk: disagrees about version of symbol dvb_usb_generic_write
[  880.524091] dvb_usb_gp8psk: Unknown symbol dvb_usb_generic_write
[  880.526184] budget_ci: disagrees about version of symbol dvb_ca_en50221_init
[  880.526190] budget_ci: Unknown symbol dvb_ca_en50221_init
[  880.526692] budget_ci: disagrees about version of symbol dvb_frontend_detach
[  880.526693] budget_ci: Unknown symbol dvb_frontend_detach
[  880.526810] budget_ci: disagrees about version of symbol dvb_unregister_frontend
[  880.526812] budget_ci: Unknown symbol dvb_unregister_frontend
[  880.526983] budget_ci: disagrees about version of symbol dvb_register_frontend
[  880.526985] budget_ci: Unknown symbol dvb_register_frontend
[  880.555318] budget: disagrees about version of symbol dvb_frontend_detach
[  880.555319] budget: Unknown symbol dvb_frontend_detach
[  880.555356] budget: disagrees about version of symbol dvb_unregister_frontend
[  880.555357] budget: Unknown symbol dvb_unregister_frontend
[  880.555505] budget: disagrees about version of symbol dvb_register_frontend
[  880.555506] budget: Unknown symbol dvb_register_frontend
[  880.557865] dvb_usb_digitv: disagrees about version of symbol dvb_usb_generic_rw
[  880.557870] dvb_usb_digitv: Unknown symbol dvb_usb_generic_rw
[  880.557962] dvb_usb_digitv: disagrees about version of symbol dvb_usb_device_init
[  880.557964] dvb_usb_digitv: Unknown symbol dvb_usb_device_init
[  880.558015] dvb_usb_digitv: disagrees about version of symbol dvb_usb_generic_write
[  880.558016] dvb_usb_digitv: Unknown symbol dvb_usb_generic_write
[  880.604410] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_nec_rc_key_to_event
[  880.604417] dvb_usb_dtt200u: Unknown symbol dvb_usb_nec_rc_key_to_event
[  880.604509] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_generic_rw
[  880.604510] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_rw
[  880.604587] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_device_init
[  880.604588] dvb_usb_dtt200u: Unknown symbol dvb_usb_device_init
[  880.604640] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_generic_write
[  880.604641] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_write
[  880.614646] dvb_usb_gl861: disagrees about version of symbol dvb_usb_device_init
[  880.614654] dvb_usb_gl861: Unknown symbol dvb_usb_device_init
[  880.651883] dvb_usb_vp7045: disagrees about version of symbol dvb_usb_device_init
[  880.651889] dvb_usb_vp7045: Unknown symbol dvb_usb_device_init
[  880.739573] dvb_usb_dtv5100: disagrees about version of symbol dvb_usb_device_init
[  880.739581] dvb_usb_dtv5100: Unknown symbol dvb_usb_device_init
[  880.776261] dvb_usb_opera: disagrees about version of symbol dvb_usb_device_init
[  880.776268] dvb_usb_opera: Unknown symbol dvb_usb_device_init
[  880.805470] dvb_usb_cxusb: disagrees about version of symbol dib7000p_set_gpio
[  880.805476] dvb_usb_cxusb: Unknown symbol dib7000p_set_gpio
[  880.805501] dvb_usb_cxusb: disagrees about version of symbol dib7000p_get_i2c_master
[  880.805503] dvb_usb_cxusb: Unknown symbol dib7000p_get_i2c_master
[  880.805624] dvb_usb_cxusb: disagrees about version of symbol dvb_usb_generic_rw
[  880.805625] dvb_usb_cxusb: Unknown symbol dvb_usb_generic_rw
[  880.805654] dvb_usb_cxusb: disagrees about version of symbol dib7000p_i2c_enumeration
[  880.805655] dvb_usb_cxusb: Unknown symbol dib7000p_i2c_enumeration
[  880.805760] dvb_usb_cxusb: disagrees about version of symbol dib7000p_set_wbd_ref
[  880.805761] dvb_usb_cxusb: Unknown symbol dib7000p_set_wbd_ref
[  880.805883] dvb_usb_cxusb: disagrees about version of symbol dib0070_wbd_offset
[  880.805884] dvb_usb_cxusb: Unknown symbol dib0070_wbd_offset
[  880.805926] dvb_usb_cxusb: disagrees about version of symbol dvb_usb_device_init
[  880.805928] dvb_usb_cxusb: Unknown symbol dvb_usb_device_init
[  880.805981] dvb_usb_cxusb: disagrees about version of symbol dvb_usb_generic_write
[  880.805983] dvb_usb_cxusb: Unknown symbol dvb_usb_generic_write
[  880.961267] dvb_usb_vp702x: disagrees about version of symbol dvb_usb_device_init
[  880.961273] dvb_usb_vp702x: Unknown symbol dvb_usb_device_init
[  880.995042] dvb_usb_m920x: disagrees about version of symbol dvb_usb_device_init
[  880.995050] dvb_usb_m920x: Unknown symbol dvb_usb_device_init
[  880.996853] dvb_usb_au6610: disagrees about version of symbol dvb_usb_device_init
[  880.996859] dvb_usb_au6610: Unknown symbol dvb_usb_device_init
[  881.006070] dvb_usb_cinergyT2: disagrees about version of symbol dvb_usb_nec_rc_key_to_event
[  881.006076] dvb_usb_cinergyT2: Unknown symbol dvb_usb_nec_rc_key_to_event
[  881.006168] dvb_usb_cinergyT2: disagrees about version of symbol dvb_usb_generic_rw
[  881.006169] dvb_usb_cinergyT2: Unknown symbol dvb_usb_generic_rw
[  881.006246] dvb_usb_cinergyT2: disagrees about version of symbol dvb_usb_device_init
[  881.006248] dvb_usb_cinergyT2: Unknown symbol dvb_usb_device_init
[  881.130421] dvb_usb_anysee: disagrees about version of symbol dvb_usb_generic_rw
[  881.130427] dvb_usb_anysee: Unknown symbol dvb_usb_generic_rw
[  881.130601] dvb_usb_anysee: disagrees about version of symbol dvb_usb_device_init
[  881.130602] dvb_usb_anysee: Unknown symbol dvb_usb_device_init
[  881.137740] dvb_usb_dw2102: disagrees about version of symbol dvb_usb_device_init
[  881.137748] dvb_usb_dw2102: Unknown symbol dvb_usb_device_init
[  881.177500] budget_patch: disagrees about version of symbol dvb_frontend_detach
[  881.177501] budget_patch: Unknown symbol dvb_frontend_detach
[  881.177535] budget_patch: disagrees about version of symbol dvb_unregister_frontend
[  881.177537] budget_patch: Unknown symbol dvb_unregister_frontend
[  881.177685] budget_patch: disagrees about version of symbol dvb_register_frontend
[  881.177686] budget_patch: Unknown symbol dvb_register_frontend
[  881.560897] dvb_usb_a800: Unknown symbol dibusb_pid_filter_ctrl
[  881.560942] dvb_usb_a800: Unknown symbol dibusb_i2c_algo
[  881.560972] dvb_usb_a800: disagrees about version of symbol dvb_usb_nec_rc_key_to_event
[  881.560973] dvb_usb_a800: Unknown symbol dvb_usb_nec_rc_key_to_event
[  881.561053] dvb_usb_a800: Unknown symbol dibusb2_0_streaming_ctrl
[  881.561094] dvb_usb_a800: Unknown symbol dibusb_dib3000mc_tuner_attach
[  881.561134] dvb_usb_a800: Unknown symbol dibusb_dib3000mc_frontend_attach
[  881.561254] dvb_usb_a800: Unknown symbol dibusb_pid_filter
[  881.561286] dvb_usb_a800: disagrees about version of symbol dvb_usb_device_init
[  881.561287] dvb_usb_a800: Unknown symbol dvb_usb_device_init
[  881.895415] budget_av: disagrees about version of symbol dvb_ca_en50221_init
[  881.895416] budget_av: Unknown symbol dvb_ca_en50221_init
[  881.895725] budget_av: disagrees about version of symbol dvb_frontend_reinitialise
[  881.895727] budget_av: Unknown symbol dvb_frontend_reinitialise
[  881.895918] budget_av: disagrees about version of symbol dvb_frontend_detach
[  881.895919] budget_av: Unknown symbol dvb_frontend_detach
[  881.895996] budget_av: disagrees about version of symbol dvb_unregister_frontend
[  881.895997] budget_av: Unknown symbol dvb_unregister_frontend
[  881.896145] budget_av: disagrees about version of symbol dvb_register_frontend
[  881.896146] budget_av: Unknown symbol dvb_register_frontend
[  881.929640] dvb_usb_dibusb_mb: Unknown symbol dibusb_pid_filter_ctrl
[  881.929688] dvb_usb_dibusb_mb: Unknown symbol dibusb_i2c_algo
[  881.929771] dvb_usb_dibusb_mb: Unknown symbol dibusb2_0_streaming_ctrl
[  881.929813] dvb_usb_dibusb_mb: Unknown symbol dibusb_streaming_ctrl
[  881.929853] dvb_usb_dibusb_mb: Unknown symbol dibusb_power_ctrl
[  881.929908] dvb_usb_dibusb_mb: Unknown symbol dibusb_rc_keys
[  881.929948] dvb_usb_dibusb_mb: Unknown symbol dibusb2_0_power_ctrl
[  881.930030] dvb_usb_dibusb_mb: Unknown symbol dibusb_pid_filter
[  881.930114] dvb_usb_dibusb_mb: Unknown symbol dibusb_rc_query
[  881.930140] dvb_usb_dibusb_mb: disagrees about version of symbol dvb_usb_device_init
[  881.930141] dvb_usb_dibusb_mb: Unknown symbol dvb_usb_device_init
[  882.072396] dvb_ttpci: disagrees about version of symbol dvb_dmxdev_init
[  882.072404] dvb_ttpci: Unknown symbol dvb_dmxdev_init
[  882.072521] dvb_ttpci: Unknown symbol saa7146_vv_init
[  882.072722] dvb_ttpci: Unknown symbol saa7146_vv_release
[  882.072748] dvb_ttpci: disagrees about version of symbol dvb_register_adapter
[  882.072750] dvb_ttpci: Unknown symbol dvb_register_adapter
[  882.072974] dvb_ttpci: disagrees about version of symbol dvb_ringbuffer_read
[  882.072975] dvb_ttpci: Unknown symbol dvb_ringbuffer_read
[  882.073019] dvb_ttpci: Unknown symbol saa7146_start_preview
[  882.073087] dvb_ttpci: disagrees about version of symbol dvb_unregister_device
[  882.073088] dvb_ttpci: Unknown symbol dvb_unregister_device
[  882.073158] dvb_ttpci: disagrees about version of symbol dvb_net_init
[  882.073160] dvb_ttpci: Unknown symbol dvb_net_init
[  882.073202] dvb_ttpci: Unknown symbol saa7146_unregister_device
[  882.073236] dvb_ttpci: disagrees about version of symbol dvb_dmxdev_release
[  882.073237] dvb_ttpci: Unknown symbol dvb_dmxdev_release
[  882.073305] dvb_ttpci: Unknown symbol saa7146_register_device
[  882.073362] dvb_ttpci: disagrees about version of symbol dvb_frontend_detach
[  882.073363] dvb_ttpci: Unknown symbol dvb_frontend_detach
[  882.073449] dvb_ttpci: disagrees about version of symbol dvb_net_release
[  882.073451] dvb_ttpci: Unknown symbol dvb_net_release
[  882.073502] dvb_ttpci: Unknown symbol saa7146_set_hps_source_and_sync
[  882.073544] dvb_ttpci: Unknown symbol saa7146_stop_preview
[  882.073588] dvb_ttpci: disagrees about version of symbol dvb_unregister_frontend
[  882.073589] dvb_ttpci: Unknown symbol dvb_unregister_frontend
[  882.073637] dvb_ttpci: Unknown symbol dvb_ringbuffer_read_user
[  882.073667] dvb_ttpci: disagrees about version of symbol dvb_register_device
[  882.073669] dvb_ttpci: Unknown symbol dvb_register_device
[  882.073728] dvb_ttpci: disagrees about version of symbol dvb_register_frontend
[  882.073729] dvb_ttpci: Unknown symbol dvb_register_frontend
[  882.073854] dvb_ttpci: disagrees about version of symbol dvb_unregister_adapter
[  882.073855] dvb_ttpci: Unknown symbol dvb_unregister_adapter
[  882.238594] dvb_usb_dibusb_mc: Unknown symbol dibusb_pid_filter_ctrl
[  882.238639] dvb_usb_dibusb_mc: Unknown symbol dibusb_i2c_algo
[  882.238722] dvb_usb_dibusb_mc: Unknown symbol dibusb2_0_streaming_ctrl
[  882.238763] dvb_usb_dibusb_mc: Unknown symbol dibusb_dib3000mc_tuner_attach
[  882.238804] dvb_usb_dibusb_mc: Unknown symbol dibusb_dib3000mc_frontend_attach
[  882.238844] dvb_usb_dibusb_mc: Unknown symbol dibusb_rc_keys
[  882.238884] dvb_usb_dibusb_mc: Unknown symbol dibusb2_0_power_ctrl
[  882.238966] dvb_usb_dibusb_mc: Unknown symbol dibusb_pid_filter
[  882.239011] dvb_usb_dibusb_mc: Unknown symbol dibusb_rc_query
[  882.239036] dvb_usb_dibusb_mc: disagrees about version of symbol dvb_usb_device_init
[  882.239038] dvb_usb_dibusb_mc: Unknown symbol dvb_usb_device_init
[  882.518078] dvb_usb_nova_t_usb2: Unknown symbol dibusb_pid_filter_ctrl
[  882.518123] dvb_usb_nova_t_usb2: Unknown symbol dibusb_i2c_algo
[  882.518207] dvb_usb_nova_t_usb2: Unknown symbol dibusb2_0_streaming_ctrl
[  882.518247] dvb_usb_nova_t_usb2: Unknown symbol dibusb_dib3000mc_tuner_attach
[  882.518274] dvb_usb_nova_t_usb2: disagrees about version of symbol dvb_usb_generic_rw
[  882.518275] dvb_usb_nova_t_usb2: Unknown symbol dvb_usb_generic_rw
[  882.518315] dvb_usb_nova_t_usb2: Unknown symbol dibusb_dib3000mc_frontend_attach
[  882.518356] dvb_usb_nova_t_usb2: Unknown symbol dibusb2_0_power_ctrl
[  882.518438] dvb_usb_nova_t_usb2: Unknown symbol dibusb_pid_filter
[  882.518470] dvb_usb_nova_t_usb2: disagrees about version of symbol dvb_usb_device_init
[  882.518471] dvb_usb_nova_t_usb2: Unknown symbol dvb_usb_device_init
[  882.518537] dvb_usb_nova_t_usb2: Unknown symbol dibusb_read_eeprom_byte
[  882.520965] dvb_usb_umt_010: Unknown symbol dibusb_i2c_algo
[  882.521053] dvb_usb_umt_010: Unknown symbol dibusb2_0_streaming_ctrl
[  882.521095] dvb_usb_umt_010: Unknown symbol dibusb_power_ctrl
[  882.521187] dvb_usb_umt_010: disagrees about version of symbol dvb_usb_device_init
[  882.521189] dvb_usb_umt_010: Unknown symbol dvb_usb_device_init
[  883.027669] pvrusb2: disagrees about version of symbol dvb_dmxdev_init
[  883.027675] pvrusb2: Unknown symbol dvb_dmxdev_init
[  883.028059] pvrusb2: disagrees about version of symbol dvb_register_adapter
[  883.028060] pvrusb2: Unknown symbol dvb_register_adapter
[  883.028692] pvrusb2: disagrees about version of symbol dvb_net_init
[  883.028693] pvrusb2: Unknown symbol dvb_net_init
[  883.028865] pvrusb2: disagrees about version of symbol dvb_dmxdev_release
[  883.028867] pvrusb2: Unknown symbol dvb_dmxdev_release
[  883.029059] pvrusb2: disagrees about version of symbol dvb_frontend_detach
[  883.029061] pvrusb2: Unknown symbol dvb_frontend_detach
[  883.029121] pvrusb2: disagrees about version of symbol dvb_net_release
[  883.029123] pvrusb2: Unknown symbol dvb_net_release
[  883.029277] pvrusb2: disagrees about version of symbol dvb_unregister_frontend
[  883.029278] pvrusb2: Unknown symbol dvb_unregister_frontend
[  883.029421] pvrusb2: disagrees about version of symbol dvb_register_frontend
[  883.029423] pvrusb2: Unknown symbol dvb_register_frontend
[  883.029524] pvrusb2: disagrees about version of symbol dvb_unregister_adapter
[  883.029525] pvrusb2: Unknown symbol dvb_unregister_adapter
[  883.034421] em28xx_dvb: disagrees about version of symbol dvb_dmxdev_init
[  883.034430] em28xx_dvb: Unknown symbol dvb_dmxdev_init
[  883.034502] em28xx_dvb: Unknown symbol em28xx_set_mode
[  883.034528] em28xx_dvb: disagrees about version of symbol dvb_register_adapter
[  883.034530] em28xx_dvb: Unknown symbol dvb_register_adapter
[  883.034568] em28xx_dvb: Unknown symbol em28xx_uninit_isoc
[  883.034610] em28xx_dvb: Unknown symbol em28xx_init_isoc
[  883.034692] em28xx_dvb: Unknown symbol em28xx_unregister_extension
[  883.034757] em28xx_dvb: disagrees about version of symbol dvb_net_init
[  883.034758] em28xx_dvb: Unknown symbol dvb_net_init
[  883.034811] em28xx_dvb: disagrees about version of symbol dvb_dmxdev_release
[  883.034812] em28xx_dvb: Unknown symbol dvb_dmxdev_release
[  883.034838] em28xx_dvb: disagrees about version of symbol dvb_frontend_detach
[  883.034839] em28xx_dvb: Unknown symbol dvb_frontend_detach
[  883.034865] em28xx_dvb: disagrees about version of symbol dvb_net_release
[  883.034866] em28xx_dvb: Unknown symbol dvb_net_release
[  883.034909] em28xx_dvb: Unknown symbol em28xx_register_extension
[  883.034937] em28xx_dvb: disagrees about version of symbol dvb_unregister_frontend
[  883.034938] em28xx_dvb: Unknown symbol dvb_unregister_frontend
[  883.034981] em28xx_dvb: Unknown symbol em28xx_tuner_callback
[  883.035007] em28xx_dvb: disagrees about version of symbol dvb_register_frontend
[  883.035008] em28xx_dvb: Unknown symbol dvb_register_frontend
[  883.035034] em28xx_dvb: disagrees about version of symbol dvb_unregister_adapter
[  883.035035] em28xx_dvb: Unknown symbol dvb_unregister_adapter
[  883.078446] saa7134_dvb: Unknown symbol videobuf_dvb_alloc_frontend
[  883.078493] saa7134_dvb: Unknown symbol saa7134_tuner_callback
[  883.078536] saa7134_dvb: Unknown symbol saa7134_ts_register
[  883.078591] saa7134_dvb: Unknown symbol videobuf_dvb_get_frontend
[  883.078664] saa7134_dvb: Unknown symbol saa7134_set_gpio
[  883.078706] saa7134_dvb: Unknown symbol saa7134_ts_qops
[  883.078799] saa7134_dvb: Unknown symbol videobuf_dvb_unregister_bus
[  883.078844] saa7134_dvb: Unknown symbol videobuf_dvb_register_bus
[  883.078895] saa7134_dvb: Unknown symbol videobuf_dvb_dealloc_frontends
[  883.078977] saa7134_dvb: Unknown symbol saa7134_ts_unregister
[  883.081181] cx88_dvb: disagrees about version of symbol cx88_call_i2c_clients
[  883.081188] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[  883.081271] cx88_dvb: Unknown symbol cx8802_get_driver
[  883.081314] cx88_dvb: Unknown symbol videobuf_dvb_alloc_frontend
[  883.081354] cx88_dvb: Unknown symbol cx8802_unregister_driver
[  883.081394] cx88_dvb: Unknown symbol cx8802_register_driver
[  883.081449] cx88_dvb: Unknown symbol videobuf_dvb_get_frontend
[  883.081517] cx88_dvb: Unknown symbol cx8802_buf_prepare
[  883.081550] cx88_dvb: disagrees about version of symbol cx88_setup_xc3028
[  883.081551] cx88_dvb: Unknown symbol cx88_setup_xc3028
[  883.081577] cx88_dvb: disagrees about version of symbol dvb_frontend_detach
[  883.081578] cx88_dvb: Unknown symbol dvb_frontend_detach
[  883.081618] cx88_dvb: Unknown symbol videobuf_dvb_unregister_bus
[  883.081662] cx88_dvb: Unknown symbol videobuf_dvb_register_bus
[  883.081691] cx88_dvb: disagrees about version of symbol cx88_free_buffer
[  883.081692] cx88_dvb: Unknown symbol cx88_free_buffer
[  883.081725] cx88_dvb: disagrees about version of symbol dvb_unregister_frontend
[  883.081726] cx88_dvb: Unknown symbol dvb_unregister_frontend
[  883.081769] cx88_dvb: Unknown symbol cx8802_buf_queue
[  883.081811] cx88_dvb: Unknown symbol videobuf_dvb_dealloc_frontends
[  883.081851] cx88_dvb: Unknown symbol videobuf_dvb_find_frontend
[  883.081900] cx88_dvb: disagrees about version of symbol cx88_tuner_callback
[  883.081901] cx88_dvb: Unknown symbol cx88_tuner_callback
[  883.162577] cx231xx_dvb: disagrees about version of symbol dvb_dmxdev_init
[  883.162585] cx231xx_dvb: Unknown symbol dvb_dmxdev_init
[  883.162648] cx231xx_dvb: Unknown symbol cx231xx_unregister_extension
[  883.162689] cx231xx_dvb: Unknown symbol cx231xx_tuner_callback
[  883.162738] cx231xx_dvb: Unknown symbol cx231xx_init_isoc
[  883.162778] cx231xx_dvb: Unknown symbol cx231xx_set_mode
[  883.162804] cx231xx_dvb: disagrees about version of symbol dvb_register_adapter
[  883.162806] cx231xx_dvb: Unknown symbol dvb_register_adapter
[  883.162849] cx231xx_dvb: Unknown symbol cx231xx_uninit_isoc
[  883.162956] cx231xx_dvb: disagrees about version of symbol dvb_net_init
[  883.162957] cx231xx_dvb: Unknown symbol dvb_net_init
[  883.163010] cx231xx_dvb: disagrees about version of symbol dvb_dmxdev_release
[  883.163012] cx231xx_dvb: Unknown symbol dvb_dmxdev_release
[  883.163038] cx231xx_dvb: disagrees about version of symbol dvb_frontend_detach
[  883.163039] cx231xx_dvb: Unknown symbol dvb_frontend_detach
[  883.163079] cx231xx_dvb: Unknown symbol cx231xx_register_extension
[  883.163105] cx231xx_dvb: disagrees about version of symbol dvb_net_release
[  883.163107] cx231xx_dvb: Unknown symbol dvb_net_release
[  883.163139] cx231xx_dvb: disagrees about version of symbol dvb_unregister_frontend
[  883.163140] cx231xx_dvb: Unknown symbol dvb_unregister_frontend
[  883.163170] cx231xx_dvb: disagrees about version of symbol dvb_register_frontend
[  883.163171] cx231xx_dvb: Unknown symbol dvb_register_frontend
[  883.163197] cx231xx_dvb: disagrees about version of symbol dvb_unregister_adapter
[  883.163198] cx231xx_dvb: Unknown symbol dvb_unregister_adapter
[  883.275592] cx18: disagrees about version of symbol dvb_dmxdev_init
[  883.275598] cx18: Unknown symbol dvb_dmxdev_init
[  883.275952] cx18: disagrees about version of symbol dvb_register_adapter
[  883.275954] cx18: Unknown symbol dvb_register_adapter
[  883.276467] cx18: disagrees about version of symbol dvb_net_init
[  883.276469] cx18: Unknown symbol dvb_net_init
[  883.276562] cx18: disagrees about version of symbol dvb_dmxdev_release
[  883.276564] cx18: Unknown symbol dvb_dmxdev_release
[  883.276806] cx18: disagrees about version of symbol dvb_frontend_detach
[  883.276807] cx18: Unknown symbol dvb_frontend_detach
[  883.276841] cx18: disagrees about version of symbol dvb_net_release
[  883.276842] cx18: Unknown symbol dvb_net_release
[  883.276963] cx18: disagrees about version of symbol dvb_unregister_frontend
[  883.276965] cx18: Unknown symbol dvb_unregister_frontend
[  883.277100] cx18: disagrees about version of symbol dvb_register_frontend
[  883.277101] cx18: Unknown symbol dvb_register_frontend
[  883.277309] cx18: disagrees about version of symbol dvb_unregister_adapter
[  883.277310] cx18: Unknown symbol dvb_unregister_adapter
[  883.372308] cx23885: disagrees about version of symbol dvb_ca_en50221_init
[  883.372309] cx23885: Unknown symbol dvb_ca_en50221_init
[  883.372630] cx23885: Unknown symbol videobuf_dvb_alloc_frontend
[  883.372904] cx23885: Unknown symbol videobuf_dvb_get_frontend
[  883.373481] cx23885: Unknown symbol videobuf_dvb_unregister_bus
[  883.373661] cx23885: Unknown symbol videobuf_dvb_register_bus
[  883.380953] dst: disagrees about version of symbol dvb_unregister_device
[  883.380958] dst: Unknown symbol dvb_unregister_device
[  883.382635] dvb_bt8xx: disagrees about version of symbol dvb_dmxdev_init
[  883.382643] dvb_bt8xx: Unknown symbol dvb_dmxdev_init
[  883.382697] dvb_bt8xx: disagrees about version of symbol bttv_sub_unregister
[  883.382698] dvb_bt8xx: Unknown symbol bttv_sub_unregister
[  883.382740] dvb_bt8xx: disagrees about version of symbol dvb_register_adapter
[  883.382742] dvb_bt8xx: Unknown symbol dvb_register_adapter
[  883.382827] dvb_bt8xx: disagrees about version of symbol bttv_sub_register
[  883.382828] dvb_bt8xx: Unknown symbol bttv_sub_register
[  883.382896] dvb_bt8xx: disagrees about version of symbol bttv_get_pcidev
[  883.382898] dvb_bt8xx: Unknown symbol bttv_get_pcidev
[  883.382932] dvb_bt8xx: disagrees about version of symbol dvb_net_init
[  883.382933] dvb_bt8xx: Unknown symbol dvb_net_init
[  883.382987] dvb_bt8xx: disagrees about version of symbol dvb_dmxdev_release
[  883.382989] dvb_bt8xx: Unknown symbol dvb_dmxdev_release
[  883.383014] dvb_bt8xx: disagrees about version of symbol dvb_frontend_detach
[  883.383016] dvb_bt8xx: Unknown symbol dvb_frontend_detach
[  883.383058] dvb_bt8xx: disagrees about version of symbol dvb_net_release
[  883.383059] dvb_bt8xx: Unknown symbol dvb_net_release
[  883.383124] dvb_bt8xx: disagrees about version of symbol dvb_unregister_frontend
[  883.383126] dvb_bt8xx: Unknown symbol dvb_unregister_frontend
[  883.383246] dvb_bt8xx: disagrees about version of symbol dvb_register_frontend
[  883.383248] dvb_bt8xx: Unknown symbol dvb_register_frontend
[  883.383273] dvb_bt8xx: disagrees about version of symbol dvb_unregister_adapter
[  883.383275] dvb_bt8xx: Unknown symbol dvb_unregister_adapter
[  883.398607] dst_ca: disagrees about version of symbol dvb_register_device
[  883.398609] dst_ca: Unknown symbol dvb_register_device
```

What is this unknown symbol and how can I solve it?

---

### Post by Tux+ on 2009-03-16
Update:
When I do a cold boot it doesn't look like the module loads automatically. When I do a dmesg grepping dvb it doesn't print anything out till I do a command modprobe dvb-usb-dib0700. After doing a modprove I get a new output from dmesg | grep -i dvb:

```
[  159.732919] usbcore: registered new interface driver dvb_usb_dib0700

```

Looking at other people's dmesg, this is their last dvb dmesg so I'm missing the loading and initializing parts. Doing an lsusb it does see a Hauppauge "card" (I do have the PCI version):

```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 2040:8400 Hauppauge 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0471:0815 Philips 
Bus 001 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 002: ID 050d:0084 Belkin Components 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by DannyBoy99 on 2010-01-13
Hi, I have almost the exact same issue (only in v 9.10). Did you manage to resove this?

---

### Post by hrobinson on 2010-01-13
Hi Everyone.

I don't have a direct answer that will solve this, but it looks like the driver is missing a library that needs to be loaded.  I have seen these errors when building drivers.  I have found that another "sub driver" needs to be loaded along with your WinTV Nova driver to allow the driver to work correctly.  Which "Sub Driver" I could not tell you.  but reading the INSTALL or README files might help.

Sincerely,

Harold Robinson

---

### Post by Tux+ on 2010-01-13
> **hrobinson said:**
> Hi Everyone.

I don't have a direct answer that will solve this, but it looks like the driver is missing a library that needs to be loaded.  I have seen these errors when building drivers.  I have found that another "sub driver" needs to be loaded along with your WinTV Nova driver to allow the driver to work correctly.  Which "Sub Driver" I could not tell you.  but reading the INSTALL or README files might help.

Sincerely,

Harold Robinson

I did not manage to resolve it and hrobinson is right but I gave up after finding driver after driver in 8.04.

I'm currently running a box with 9.10 with the TD500 and it works fine. It was a stock Desktop install and the only additional software I installed was Mythbuntu (mythbuntu control centre to be exact) which verified it was working.

Sorry I can't be more of help but I hope this next LTS will solve the problem.

---

