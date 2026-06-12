---
title: "Wireless broken after upgrade to 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by quixote72 on 2010-05-10
Hi there, 

I have a thinkpad using the iwl3945 driver (Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks).

This worked flawless until I upgraded to 10.04. Now after a while my connection drops. Syslog is appended. Any ideas?

TIA.

May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) starting connection 'Auto my-network'
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto my-network' has security, but secrets are required.
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto my-network' has security, and secrets exist.  No new secrets needed.
May 10 20:16:04 gimli NetworkManager: <info>  Config: added 'ssid' value 'my-network'
May 10 20:16:04 gimli NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May 10 20:16:04 gimli NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May 10 20:16:04 gimli NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May 10 20:16:04 gimli NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 10 20:16:04 gimli NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 10 20:16:04 gimli NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 20:16:04 gimli NetworkManager: <info>  Config: set interface ap_scan to 1
May 10 20:16:04 gimli NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 20:16:04 gimli kernel: [36901.341795] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:04 gimli kernel: [36901.341803] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:04 gimli kernel: [36901.341807] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:04 gimli kernel: [36901.341825] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:04 gimli kernel: [36901.341828] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:04 gimli kernel: [36901.341839] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:04 gimli kernel: [36901.341842] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:04 gimli kernel: [36901.341845] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:04 gimli kernel: [36901.341848] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:04 gimli kernel: [36901.341850] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:04 gimli kernel: [36901.341853] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:04 gimli kernel: [36901.341861] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:04 gimli kernel: [36901.341864] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:09 gimli kernel: [36906.347403] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:09 gimli kernel: [36906.347415] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:09 gimli kernel: [36906.347422] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:09 gimli kernel: [36906.347490] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:09 gimli kernel: [36906.347497] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:09 gimli kernel: [36906.347515] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:09 gimli kernel: [36906.347521] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:09 gimli kernel: [36906.347527] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:09 gimli kernel: [36906.347533] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:09 gimli kernel: [36906.347538] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:09 gimli kernel: [36906.347544] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:09 gimli kernel: [36906.347558] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:09 gimli kernel: [36906.347563] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:14 gimli kernel: [36911.352102] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:14 gimli kernel: [36911.352114] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:14 gimli kernel: [36911.352121] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:14 gimli kernel: [36911.352173] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:14 gimli kernel: [36911.352179] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:14 gimli kernel: [36911.352195] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:14 gimli kernel: [36911.352201] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:14 gimli kernel: [36911.352207] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:14 gimli kernel: [36911.352213] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:14 gimli kernel: [36911.352218] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:14 gimli kernel: [36911.352224] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:14 gimli kernel: [36911.352236] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:14 gimli kernel: [36911.352241] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:19 gimli kernel: [36916.356782] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:19 gimli kernel: [36916.356794] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:19 gimli kernel: [36916.356800] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:19 gimli kernel: [36916.356852] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:19 gimli kernel: [36916.356859] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:19 gimli kernel: [36916.356876] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:19 gimli kernel: [36916.356881] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:19 gimli kernel: [36916.356887] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:19 gimli kernel: [36916.356893] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:19 gimli kernel: [36916.356899] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:19 gimli kernel: [36916.356905] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:19 gimli kernel: [36916.356917] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:19 gimli kernel: [36916.356923] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:24 gimli kernel: [36921.361568] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:24 gimli kernel: [36921.361580] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:24 gimli kernel: [36921.361586] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:24 gimli kernel: [36921.361630] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:24 gimli kernel: [36921.361639] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:24 gimli kernel: [36921.361658] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:24 gimli kernel: [36921.361663] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:24 gimli kernel: [36921.361669] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:24 gimli kernel: [36921.361676] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:24 gimli kernel: [36921.361681] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:24 gimli kernel: [36921.361687] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:24 gimli kernel: [36921.361699] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:24 gimli kernel: [36921.361705] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:29 gimli kernel: [36926.365556] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:29 gimli kernel: [36926.365569] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:29 gimli kernel: [36926.365575] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:29 gimli kernel: [36926.365631] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:29 gimli kernel: [36926.365637] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:29 gimli kernel: [36926.365656] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:29 gimli kernel: [36926.365661] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:29 gimli kernel: [36926.365667] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:29 gimli kernel: [36926.365673] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:29 gimli kernel: [36926.365679] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:29 gimli kernel: [36926.365684] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:29 gimli kernel: [36926.365697] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:29 gimli kernel: [36926.365703] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:34 gimli kernel: [36931.372848] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:34 gimli kernel: [36931.372861] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:34 gimli kernel: [36931.372868] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:34 gimli kernel: [36931.372937] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:34 gimli kernel: [36931.372943] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:34 gimli kernel: [36931.372961] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:34 gimli kernel: [36931.372966] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:34 gimli kernel: [36931.372973] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:34 gimli kernel: [36931.372979] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:34 gimli kernel: [36931.372984] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:34 gimli kernel: [36931.372990] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:34 gimli kernel: [36931.373002] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:34 gimli kernel: [36931.373013] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:39 gimli kernel: [36936.376109] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:39 gimli kernel: [36936.376121] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:39 gimli kernel: [36936.376128] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:39 gimli kernel: [36936.376212] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:39 gimli kernel: [36936.376219] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:39 gimli kernel: [36936.376237] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:39 gimli kernel: [36936.376242] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:39 gimli kernel: [36936.376248] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:39 gimli kernel: [36936.376255] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:39 gimli kernel: [36936.376260] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:39 gimli kernel: [36936.376266] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:39 gimli kernel: [36936.376278] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:39 gimli kernel: [36936.376283] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:44 gimli kernel: [36941.382859] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:44 gimli kernel: [36941.382874] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:44 gimli kernel: [36941.382881] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:44 gimli kernel: [36941.382944] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:44 gimli kernel: [36941.382951] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:44 gimli kernel: [36941.382971] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:44 gimli kernel: [36941.382977] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:44 gimli kernel: [36941.382982] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:44 gimli kernel: [36941.382989] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:44 gimli kernel: [36941.382994] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:44 gimli kernel: [36941.383000] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:44 gimli kernel: [36941.383013] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:44 gimli kernel: [36941.383018] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:49 gimli kernel: [36946.388089] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:49 gimli kernel: [36946.388101] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:49 gimli kernel: [36946.388107] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:49 gimli kernel: [36946.388167] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:49 gimli kernel: [36946.388173] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:49 gimli kernel: [36946.388190] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:49 gimli kernel: [36946.388196] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:49 gimli kernel: [36946.388202] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:49 gimli kernel: [36946.388208] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:49 gimli kernel: [36946.388213] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:49 gimli kernel: [36946.388219] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:49 gimli kernel: [36946.388232] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:49 gimli kernel: [36946.388237] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:54 gimli kernel: [36951.393190] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:54 gimli kernel: [36951.393202] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:54 gimli kernel: [36951.393209] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:54 gimli kernel: [36951.393252] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:54 gimli kernel: [36951.393260] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:54 gimli kernel: [36951.393279] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:54 gimli kernel: [36951.393285] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:54 gimli kernel: [36951.393291] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:54 gimli kernel: [36951.393297] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:54 gimli kernel: [36951.393303] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:54 gimli kernel: [36951.393309] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:54 gimli kernel: [36951.393321] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:54 gimli kernel: [36951.393326] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:16:59 gimli kernel: [36956.396110] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:59 gimli kernel: [36956.396122] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:59 gimli kernel: [36956.396129] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:59 gimli kernel: [36956.396186] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:59 gimli kernel: [36956.396192] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
May 10 20:16:59 gimli kernel: [36956.396210] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:59 gimli kernel: [36956.396215] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:59 gimli kernel: [36956.396221] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:59 gimli kernel: [36956.396227] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:59 gimli kernel: [36956.396233] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
May 10 20:16:59 gimli kernel: [36956.396238] iwl3945 0000:03:00.0: Error setting new configuration (-28).
May 10 20:16:59 gimli kernel: [36956.396251] iwl3945 0000:03:00.0: No space for Tx
May 10 20:16:59 gimli kernel: [36956.396256] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
May 10 20:17:01 gimli CRON[4532]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 20:17:04 gimli NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
May 10 20:17:04 gimli NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May 10 20:17:04 gimli NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets

---

### Post by baekgaard on 2010-05-11
I have a similar problem on a T60. As far as I can see, it is a (known) bug in the iwl3945 driver that also exists in other distributions. It appears to be triggered by high load on the network. I can safely browse using firefox, and it appears not to trigger the crash. But as soon as I start to transfer files via e.g. scp from another local machine, it stalls.

"rmmod -r iwl3945; modprobe iwl3945" will bring the driver back again, as will a disable/enable via NetworkManager.

I have not yet found a solution or workaround; still looking hopefully.

It may be related to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317728)


-- Per.

---

