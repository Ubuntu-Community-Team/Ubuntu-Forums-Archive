---
title: "Issues with network authentication [12.10]"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by morgendorffer on 2013-01-06
So, we're having issues connecting to a wireless network on our ubuntu computer. At first after installing the os, there were no issues and the network worked as properly. Then after some days, loads of "authenticate network password" (don't know exact wording in english) prompts started popping up, and regardless of writing in the correct password it would not go away. Internet still worked.

After restarting the computer, the network is inaccessible - the "authenticate password" windows still show up but writing in the correct password does not make them go away and one can't reach internet.

We've never had this issue on any other computer, nor on that comp when it ran Windows, so I think the issue is in the OS, not in hardware or server.

Anyone has any idea what the issue is/how it is solved? We're new to linux, so we don't really know what to do and thus has been unable to test much besides checking the configuration window settings for anything obvious and restarting the computer.

---

### Post by gonenowhere on 2013-01-07
I am having this same exact issue did it get solved for you? I did a wirelesslog.txt and here is what Mine says:

an  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0/wireless): access point 'Buck you fitch' has security, but secrets are required.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0/wireless): connection 'Buck you fitch' has security, and secrets exist.  No new secrets needed.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'ssid' value 'Buck you fitch'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'scan_ssid' value '1'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'auth_alg' value 'OPEN'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'psk' value '<omitted>'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: set interface ap_scan to 1
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  7 08:58:40 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Activation (wlan0/wireless): association took too long.
Jan  7 08:59:33 WTF NetworkManager[799]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan  7 08:59:33 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.



Do you know what type of wireless card is equipped with your pc?

---

### Post by morgendorffer on 2013-01-07
We have not gotten the issue to go away, but sometimes when the computer has started, after some time the network works. This seems to happen randomly, and after a while it goes away again and won't be accessible until we restart the computer, wait for a while and then maybe it works (until it shuts down again).

I do not know that, and neither do I know how to check it on Ubuntu. The computer was bought as a package and I dare not open it without checking with the company if that breaks the contract. How do I check that within ubuntu?

If there's any information that should be posted in the thread I'll gladly do so, but I would need instructions for how to get it.

Again, thanks for any aid.

---

