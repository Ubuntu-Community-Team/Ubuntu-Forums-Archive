---
title: "Toshina WEP-PEAP Connection Error"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by boc1580 on 2009-02-10
I have a Toshiba A215-S6804 Laptop with an AMD Turion 64 X2 chip and an Atheros AT5007AG chip.  The Wireless Controller:  Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)  The model is AT5007AG.  I am running Ubuntu 8.10.  The kernel is 2.6.27-11-generic x86 64.  I am using the ath5k driver from the backtools module.

I am having trouble setting up my connection to the college's network.  I have no problems conneting at open hotspots, WPA, WPA2-Personal, and WEP connections.  The college's technical support department is not very technical savy and simply says we only support Windows XP (which is what is on the campus computers).

The settings provided to me from the college are as follows:
SSID: NCC_Wireless
Network Authentication: Open
Data encryption: WEP
The key is provided automatically.

For authentication, use IEEE 802.1x.
EAP type: Protected EAP (PEAP)
Authenticate as computer when computer information is available and Authenticate as guest when user or computer information is unavailable should NOT be checked.
Validate Server Certificate should be unchecked.
We are using the Secured Password (EAP-MSCHAP v2) option.
Do not enable Fast Reconnect.

I have to enter my network (UDAP) username and password to gain access to the network.

I tried to auto connect and received this setting in the Network Connections window:
Under wireless:  (Blank fields omitted)
SSID: NCC_Wireless
Mode: Infrastructure
MTU: Automatic

Under Security:
WEP 40/128-bit key
Key is blank and show key is unchecked
WEP Index: 1 (Default)
Authentication: Open System

I received this errror message from the logs:

Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto NCC_Wireless' 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto NCC_Wireless' has security, but secrets are required. 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  9 10:03:03 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Feb  9 10:03:12 ubuntu NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (NCC_Wireless) 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  Marking connection 'Auto NCC_Wireless' invalid. 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  Activation (wlan0) failed. 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Feb  9 10:03:12 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

Any suggestions would be appreciated!  Thanks, Andy

---

