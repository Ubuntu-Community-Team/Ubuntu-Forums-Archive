---
title: "wireless halts after a time of high network activity"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by svaens on 2009-05-16
wireless halts after a time of high network activity. Only a reboot seems to fix it. Here below are the steps for reproduction. 

Ubuntu seems to load the orinoco modules to get my wireless going. I had no problems on Hardy  (from which i updated, clean).

1. first i start the computer,
2. second, wireless connects
3. use internet, high data usage
4. random amount of time, wireless cuts out
5. attempt to re-connect causes authentication dialog to pop up.
6. re typing the key details results in behavior which seems from outward appearances the same as if i had typed in the wrong authentication key.

No amount of attempts allows me to reconnect. Only a reboot fixes it.

Anyone had the same problem, and know how to fix it? 

I have read someone say to use the  linux-backport-modules-jaunty
But wherever i read this, the users seem to have no clue about it. They talk about 'installing' the linux-backport-modules, as if it were a magic fix. But it is a repository. And it would mean that you should first remove the old modules you suspect are not working, and replace it with the working versions. Presumably from the backport repository. But to be honest, I am not sure how to go about installing and removing modules. And if the problem exists actually in the orinoco module anyway. I have read that some people have had the very same problem, but are using other modules! 

Here are some details from my computer:

Thanks in advance for any help.

```
sean@svUbuntuX:~$ iwconfig eth1
eth1 IEEE 802.11b ESSID:"HoneyPie" Nickname:"HERMES I"
          Mode:Managed Frequency:2.462 GHz Access Point: 00:16:E3:6C:1C:7C
          Bit Rate:11 Mb/s Sensitivity:1/3
          Retry limit:4 RTS thr:off Fragment thr:off
          Power Management:off
          Link Quality=51/92 Signal level=-48 dBm Noise level=-99 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:2141
          Tx excessive retries:9 Invalid misc:0 Missed beacon:0
```

```

sean@svUbuntuX:~$ cat /proc/modules |grep or
orinoco_cs 21004 1 - Live 0xf7dfa000
orinoco 61716 1 orinoco_cs, Live 0xf7e3b000
hermes_dld 15232 1 orinoco, Live 0xf7d21000
hermes 15360 3 orinoco_cs,orinoco,hermes_dld, Live 0xf7cd3000
pcmcia 44748 1 orinoco_cs, Live 0xf81fe000
iTCO_vendor_support 11652 1 iTCO_wdt, Live 0xf7dcf000
soundcore 15200 2 snd, Live 0xf7cee000
pcmcia_core 43540 4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic, Live 0xf7cb5000
parport_pc 40100 1 - Live 0xf7ce2000
parport 42220 3 lp,ppdev,parport_pc, Live 0xf7ca8000
softcursor 9984 1 bitblit, Live 0xf7c21000
sean@svUbuntuX:~$
```


Here's some syslog
```

May 4 21:58:25 svUbuntuX kernel: [ 2134.244451] eth1: Lucent/Agere firmware doesn't support manual roaming
May 4 21:58:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: associating -> associated
May 4 21:58:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: associated -> completed
May 4 21:58:25 svUbuntuX NetworkManager: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'HoneyPie'.
May 4 21:58:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 4 21:58:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 4 21:58:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 5 -> 7
May 4 21:58:25 svUbuntuX NetworkManager: <info> Activation (eth1) Beginning DHCP transaction.
May 4 21:58:25 svUbuntuX dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 4 21:58:25 svUbuntuX dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 4 21:58:25 svUbuntuX dhclient: All rights reserved.
May 4 21:58:25 svUbuntuX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 4 21:58:25 svUbuntuX dhclient:
May 4 21:58:25 svUbuntuX kernel: [ 2134.332390] eth1: New link status: Connected (0001)
May 4 21:58:25 svUbuntuX NetworkManager: <info> dhclient started with pid 5839
May 4 21:58:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 4 21:58:25 svUbuntuX NetworkManager: <info> DHCP: device eth1 state changed normal exit -> preinit
May 4 21:58:25 svUbuntuX dhclient: Listening on LPF/eth1/00:02:2d:81:93:eb
May 4 21:58:25 svUbuntuX dhclient: Sending on LPF/eth1/00:02:2d:81:93:eb
May 4 21:58:25 svUbuntuX dhclient: Sending on Socket/fallback
May 4 21:58:27 svUbuntuX dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
May 4 21:58:30 svUbuntuX dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
May 4 21:58:35 svUbuntuX dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
May 4 21:58:45 svUbuntuX dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
May 4 21:59:05 svUbuntuX dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
May 4 21:59:11 svUbuntuX NetworkManager: <info> Device 'eth1' DHCP transaction took too long (>45s), stopping it.
May 4 21:59:11 svUbuntuX NetworkManager: <info> eth1: canceled DHCP transaction, dhcp client pid 5839
May 4 21:59:11 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled...
May 4 21:59:11 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started...
May 4 21:59:11 svUbuntuX NetworkManager: <info> Activation (eth1/wireless): could not get IP configuration for connection 'Auto HoneyPie'.
May 4 21:59:11 svUbuntuX NetworkManager: <info> (eth1): device state change: 7 -> 6
May 4 21:59:11 svUbuntuX NetworkManager: <info> Activation (eth1/wireless): asking for new secrets
May 4 21:59:11 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete.
May 4 21:59:15 svUbuntuX NetworkManager: <WARN> get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled.
May 4 21:59:15 svUbuntuX NetworkManager: <info> (eth1): device state change: 6 -> 9
May 4 21:59:15 svUbuntuX NetworkManager: <info> Activation (eth1) failed for access point (HoneyPie)
May 4 21:59:15 svUbuntuX NetworkManager: <info> Marking connection 'Auto HoneyPie' invalid.
May 4 21:59:15 svUbuntuX NetworkManager: <info> Activation (eth1) failed.
May 4 21:59:15 svUbuntuX NetworkManager: <info> (eth1): device state change: 9 -> 3
May 4 21:59:15 svUbuntuX NetworkManager: <info> (eth1): deactivating device (reason: 0).
May 4 21:59:15 svUbuntuX kernel: [ 2183.898997] eth1: New link status: Disconnected (0002)
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) starting connection 'Auto HoneyPie'
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 3 -> 4
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 4 -> 5
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1/wireless): access point 'Auto HoneyPie' has security, but secrets are required.
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 5 -> 6
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 6 -> 4
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 4 -> 5
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1/wireless): connection 'Auto HoneyPie' has security, and secrets exist. No new secrets needed.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'ssid' value 'HoneyPie'
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'scan_ssid' value '1'
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'key_mgmt' value 'NONE'
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'auth_alg' value 'OPEN'
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'wep_key0' value '<omitted>'
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: added 'wep_tx_keyidx' value '0'
May 4 21:59:25 svUbuntuX NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 4 21:59:25 svUbuntuX NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Config: set interface ap_scan to 1
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: disconnected -> scanning
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: scanning -> associating
May 4 21:59:25 svUbuntuX kernel: [ 2194.494866] eth1: Lucent/Agere firmware doesn't support manual roaming
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: associating -> associated
May 4 21:59:25 svUbuntuX kernel: [ 2194.646264] eth1: New link status: Connected (0001)
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): supplicant connection state: associated -> completed
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'HoneyPie'.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 4 21:59:25 svUbuntuX NetworkManager: <info> (eth1): device state change: 5 -> 7
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Beginning DHCP transaction.
May 4 21:59:25 svUbuntuX dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 4 21:59:25 svUbuntuX dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 4 21:59:25 svUbuntuX dhclient: All rights reserved.
May 4 21:59:25 svUbuntuX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 4 21:59:25 svUbuntuX dhclient:
May 4 21:59:25 svUbuntuX NetworkManager: <info> dhclient started with pid 5903
May 4 21:59:25 svUbuntuX NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 4 21:59:25 svUbuntuX NetworkManager: <info> DHCP: device eth1 state changed normal exit -> preinit
May 4 21:59:25 svUbuntuX dhclient: Listening on LPF/eth1/00:02:2d:81:93:eb
May 4 21:59:25 svUbuntuX dhclient: Sending on LPF/eth1/00:02:2d:81:93:eb
May 4 21:59:25 svUbuntuX dhclient: Sending on Socket/fallback

```

---

