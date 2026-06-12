---
title: "Zonet ZEW2500P module issues"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by ifraser on 2010-05-02
After upgrading to Lucid said adapter is nonfunctional - NetworkManager won't start on booting (I'm using 2870sta module) and it finds no networks - neither does WICD.

The device itself is identified: "lsusb" gives a line "Bus 001 Device 005: ID 148f:3070 Ralink Technology Corp."

"iwconfig" gives nothing under lo and eth0 and this under wlan0:

```
RTxx70 Wireless  ESSID:""
Mode:Auto  Frequency=2.412GHz
Link Quality=10/100 Signal level:0 dbBm Noise level:-143 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

And a "lsmod | grep -e rt2 -e rt3" gives:
```
rt2870sta                   525366  0 
```

Any ideas from the very helpful community?  I've perused a bunch of recent posts along similar lines but haven't had any luck.  

(Note: I had a similar problem going from Jaunty to Karmic, but blacklisting rt2800usb in my blacklist.conf fixed it.  No such luck this time.)

Using a Zonet ZEW2500P.  x86-64 Lucid.

---

### Post by chili555 on 2010-05-02
Please try:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```If the [ifupdown] managed=false set it to true.

Proofread carefully, save and close gedit. Reboot and give us your report.

---

### Post by ifraser on 2010-05-02
> **chili555 said:**
> Please try:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```If the [ifupdown] managed=false set it to true.

Proofread carefully, save and close gedit. Reboot and give us your report.

It was set to false, and a setting to true + reboot now correctly displays available wireless networks in NetworkManager.  However, it is unable to connect to any networks.

Here's output for "sudo iwlist wlan0 scan" for the network I use:
```
Cell 07 - Address: 00:24:B2:60:A2:AF
Protocol:802.11g/n
ESSID:"[I'll redact its name but it's there properly]"
Mode:Managed
Channel:4
Quality:68/100 Signal level:-63 dBm Noise level:-97 dBm
Encryption key:on
Bit Rates: 18 Mb/s
IE: Wpa Version 1
Group Cipher: TKIP
Pairwise Ciphers (2): CCMP TKIP
Authentication Suites (1): PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher: TKIP
Pairwise Ciphers (2): CCMP TKIP
Authentication Suites (1): PSK

```

...if it's any help at all.

---

### Post by chili555 on 2010-05-03
When you select your network, does it ask for your WPA-PSK password? Can you right-click the NM icon and Edit Connections and input your details? Be sure to check off Connect Automatically.

---

### Post by ifraser on 2010-05-04
No, NM does NOT ask for the password - it's like it can't get any response whatsoever.

Appreciating the continued investigative help - there's no wired net at my place here, so having my box be down like this leaves me with only my laptop (Windows 7) for Net use.

---

### Post by chili555 on 2010-05-04
Please open System > Administration > Synaptic and verify that wpa_supplicant is installed; install it if it's not. I can't imagine it would be missing, but I have seen stranger things.

Next, do:```
sudo cat /var/log/syslog | grep -i network
```Find the ten or so lines that seem to show where it tries to connect and fails. Copy and paste them into Applications > Accessories > gedit. Save the document and transfer it on a USB key so it can be posted here. Thanks.

---

### Post by ifraser on 2010-05-04
Yes, wpasupplicant was installed.

Here's the output of "sudo cat /var....." as given in your post:
```

May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto taiwanrocks'
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto taiwanrocks' has security, but secrets are required.
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto taiwanrocks' has security, and secrets exist.  No new secrets needed.
May  4 07:59:54 ian-desktop NetworkManager: <info>  Config: added 'ssid' value 'taiwanrocks'
May  4 07:59:54 ian-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  4 07:59:54 ian-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  4 07:59:54 ian-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  4 07:59:54 ian-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 07:59:54 ian-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 07:59:54 ian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  4 07:59:54 ian-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  4 07:59:54 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 07:59:59 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  4 08:00:04 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  4 08:00:04 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 08:00:09 ian-desktop NetworkManager: <info>  wlan0: link timed out.
May  4 08:00:09 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  4 08:00:14 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  4 08:00:14 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 08:00:19 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  4 08:00:24 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  4 08:00:24 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 08:00:29 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  4 08:00:34 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  4 08:00:34 ian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

```

This seems to repeat several times to form the output of the command.

---

### Post by chili555 on 2010-05-04
> nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedI am not sure this is keeping you from connecting but I am very suspicious. I am Googling and suggest you do the same.

---

### Post by ifraser on 2010-05-06
So, I've Googled it and found various solutions that don't seem to be working very well.  I'm currently attempting to get only "rt3070sta" working with the ZEW2500P (lsusb shows it as a 3070 chipset) but keep getting the "unknown symbol in module" error when modprobing.  Any luck in your Googling?

---

### Post by chili555 on 2010-05-06
> get only "rt3070sta" working with the ZEW2500PIn Lucid, I think rt3070sta is rt2870sta:```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
[COLOR="Red"]alias:          rt3070sta[/COLOR]
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
```There is no native rt3070sta in Lucid.

No luck Googling. It is clearly a Network Manager issue. Are you game to replace it with Wicd?

---

### Post by saxamo on 2010-06-11
I was curious as to whether or not the OP had made any progress. My issues are the same, down to the error logs. wicd has been no help. it hangs under "Validating Authentication" and ultimately comes up with a "wrong password." When the password is right.

The adapter can connect to an unsecured network. WPA authentication seems to be broken.

---

