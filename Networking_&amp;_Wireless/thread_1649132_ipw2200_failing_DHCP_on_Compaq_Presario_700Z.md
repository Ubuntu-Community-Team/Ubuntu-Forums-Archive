---
title: "ipw2200 failing DHCP on Compaq Presario 700Z"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by neurophyre on 2010-12-19
Hello all, I've just installed Xubuntu 10.10 on a Compaq Presario 700Z.  Unfortunately the wireless is not working on it, and I know it was working in the last LTS release of Ubuntu because that's how the laptop was sold to me.

Doing some Googling it seems that some bugs might have been introduced with kernel 2.6.35 but I'm not sure whether I should downgrade, try compiling my own kernel, or whether there is another solution to get wireless working.  802.11 with WPA support is essential for what I'm doing with this laptop.

I've found threads talking about firmware versions (included with the kernel??? Not familiar with this) and about a possible issue with wpa_supplicant.  I'm trying to get the wireless to connect or even scan available networks via Network Manager in Xubuntu, but it won't do so.

From dmesg:

```
[   23.258430] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.258446] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.259599] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
[   23.259608] PCI: setting IRQ 4 as level-triggered
[   23.259621] ipw2200 0000:00:09.0: PCI INT A -> Link[LNKA] -> GSI 4 (level, low) -> IRQ 4
[   23.264260] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
```

From daemon.log:

```
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) starting connection 'Wireless con
nection 1'
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) sch
eduled...
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) sta
rted...
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) s
cheduled...
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) com
plete.
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) s
tarting...
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1/wireless): connection 'Wireless co
nnection 1' has security, and secrets exist.  No new secrets needed.
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Config: added 'ssid' value 'nexus'
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Config: added 'scan_ssid' value '1'
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Config: added 'psk' value '<omitted>'
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS
_SETTING_802_1X (setting)' failed
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS
_SETTING_802_1X (setting)' failed
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) c
omplete.
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> Config: set interface ap_scan to 1
Dec 19 05:07:33 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): supplicant connection state:  inactive -> s
canning
Dec 19 05:07:34 bruce-Presario-702N-470037-512 wpa_supplicant[687]: Trying to associate with 00:13:10:62:62:aa (SSID='nexus' freq=2462 MHz)
Dec 19 05:07:34 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 19 05:07:34 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 19 05:07:34 bruce-Presario-702N-470037-512 wpa_supplicant[687]: Associated with 00:13:10:62:62:aa
Dec 19 05:07:34 bruce-Presario-702N-470037-512 NetworkManager[651]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Dec 19 05:07:37 bruce-Presario-702N-470037-512 NetworkManager[651]: <error> [1292760457.263951] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 19 05:07:37 bruce-Presario-702N-470037-512 NetworkManager[651]: <error> [1292760457.377357] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 19 05:07:37 bruce-Presario-702N-470037-512 NetworkManager[651]: <error> [1292760457.263951] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 19 05:07:37 bruce-Presario-702N-470037-512 NetworkManager[651]: <error> [1292760457.377357] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name

```

And so forth.  If it does get past the handshake, DHCPDISCOVER will often time out.  Once it managed to successfully get an IP but the connection was not usable.

Any advice on how I can get this beast working?  I'm passingly familiar with building kernels using make-kpkg on Debian but haven't done it in a long time ... if I could get the settings that correspond with linux-generic and build a kernel that has a working ipw2200 driver, I'd be happy to try it.

---

