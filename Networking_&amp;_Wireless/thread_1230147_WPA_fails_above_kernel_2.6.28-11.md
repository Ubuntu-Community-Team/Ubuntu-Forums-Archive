---
title: "WPA fails above kernel 2.6.28-11"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by camason on 2009-08-03
Hi all,

I've had a problem for a while since applying the regular system updates via Update Manager. For kernels above 2.6.28-11 (including 2.6.28-13 & 2.6.28-14) I cannot connect to WPA/WPA2 networks.

Model: Asus Eee 901
Wifi device: RT2860
OS: Ubuntu 9.04

wpa_supplicant log shows:

> Trying to authenticate with 00:1b:11:69:18:3f
Authentication with 00:1b:11:69:18:3f timed out
Trying to authenticate with 00:1b:11:69:18:3f
Authentication with 00:1b:11:69:18:3f timed out
Trying to authenticate with 00:1b:11:69:18:3f
Authentication with 00:1b:11:69:18:3f timed out
Trying to authenticate with 00:1b:11:69:18:3f
Authentication with 00:00:00:00:00:00 timed out

note the last line shows 00:00:00:00:00:00. Not sure if this is important.

syslog shows:

> Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) starting connection 'Manual MyNetwork' 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0) 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0/wireless): access point 'Manual MyNetwork' has security, but secrets are required. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0) 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0) 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0/wireless): connection 'Manual MyNetwork' has security, and secrets exist.  No new secrets needed. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Config: added 'ssid' value 'MyNetwork' 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug  3 06:59:46 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 06:59:46 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
Aug  3 06:59:46 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 06:59:51 camason-eee kernel: [   80.369123] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 06:59:55 camason-eee kernel: [   80.726803] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 06:59:55 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:00:02 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:00:02 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:00:07 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:00:07 camason-eee kernel: [   95.744088] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:00:07 camason-eee kernel: [   95.744594] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:00:17 camason-eee NetworkManager: <info>  ra0: link timed out. 
Aug  3 07:00:17 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:00:17 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:00:22 camason-eee kernel: [  110.760128] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:00:22 camason-eee kernel: [  110.760946] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:00:22 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:00:32 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:00:32 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:00:37 camason-eee kernel: [  125.780197] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:00:37 camason-eee kernel: [  125.780956] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:00:37 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:00:47 camason-eee NetworkManager: <info>  Activation (ra0/wireless): association took too long. 
Aug  3 07:00:47 camason-eee NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0) 
Aug  3 07:00:47 camason-eee NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
Aug  3 07:00:47 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:00:49 camason-eee NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1545 (get_secrets_dialog_response_cb): canceled. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 6 -> 9 (reason 7) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) failed for access point (MyNetwork) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Marking connection 'Manual MyNetwork' invalid. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) failed. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 9 -> 3 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) starting connection 'Auto MyNetwork' 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto MyNetwork' has security, but secrets are required. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto MyNetwork' has security, and secrets exist.  No new secrets needed. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Config: added 'ssid' value 'MyNetwork' 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug  3 07:00:49 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 07:00:49 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug  3 07:00:49 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:00:59 camason-eee kernel: [  147.480275] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:00:59 camason-eee kernel: [  147.481009] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:00:59 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:01:09 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:01:09 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:01:14 camason-eee kernel: [  162.498251] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:01:14 camason-eee kernel: [  162.499019] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:01:14 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:01:24 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:01:24 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:01:29 camason-eee kernel: [  177.515930] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:01:29 camason-eee kernel: [  177.516644] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:01:29 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:01:38 camason-eee NetworkManager: <info>  ra0: link timed out. 
Aug  3 07:01:39 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:01:39 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:01:44 camason-eee kernel: [  192.536284] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:01:44 camason-eee kernel: [  192.537030] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:01:44 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:01:50 camason-eee NetworkManager: <info>  Activation (ra0/wireless): association took too long. 
Aug  3 07:01:50 camason-eee NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0) 
Aug  3 07:01:50 camason-eee NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
Aug  3 07:01:50 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:01:51 camason-eee NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1545 (get_secrets_dialog_response_cb): canceled. 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  (ra0): device state change: 6 -> 9 (reason 7) 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  Activation (ra0) failed for access point (MyNetwork) 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  Marking connection 'Auto MyNetwork' invalid. 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  Activation (ra0) failed. 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  (ra0): device state change: 9 -> 3 (reason 0) 
Aug  3 07:01:51 camason-eee NetworkManager: <info>  (ra0): deactivating device (reason: 0). 
Aug  3 07:01:59 camason-eee kernel: [  207.479234] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 376
Aug  3 07:03:19 camason-eee kernel: [  287.477843] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:04:39 camason-eee kernel: [  367.472159] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:05:59 camason-eee kernel: [  447.480407] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:07:19 camason-eee kernel: [  527.476793] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 403
Aug  3 07:08:39 camason-eee kernel: [  607.478831] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:09:59 camason-eee kernel: [  687.481027] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) starting connection 'Auto MyNetwork' 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0) 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto MyNetwork' has security, but secrets are required. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0) 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0) 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0) 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto MyNetwork' has security, and secrets exist.  No new secrets needed. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Config: added 'ssid' value 'MyNetwork' 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug  3 07:10:52 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 07:10:52 camason-eee NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
Aug  3 07:10:52 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:10:57 camason-eee kernel: [  746.157453] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:10:57 camason-eee kernel: [  746.158100] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:10:57 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:11:07 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:11:07 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:11:08 camason-eee NetworkManager: <info>  ra0: link timed out. 
Aug  3 07:11:12 camason-eee kernel: [  761.174705] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:11:12 camason-eee kernel: [  761.175335] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)
Aug  3 07:11:12 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:11:19 camason-eee kernel: [  767.579176] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:11:22 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug  3 07:11:22 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug  3 07:11:27 camason-eee NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug  3 07:11:27 camason-eee kernel: [  776.192523] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 284
Aug  3 07:11:27 camason-eee kernel: [  776.193161] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=12)


I hope somebody can help, as I currently have to keep booting into an old kernel, which isn't great.

Thanks!

---

### Post by camason on 2009-08-06
I've managed to fix this issue by compiling the driver from ralink, and using a patch from launchpad.

Here's a forum post that explains the process:

[http://ubuntuforums.org/showpost.php?p=7274349&postcount=102](http://ubuntuforums.org/showpost.php?p=7274349&postcount=102)

---

