---
title: "Need Help Troubleshooting WLAN (3945ABG)"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by icevonshredula on 2012-04-18
Hello! I just decided to install Ubuntu 11.10 on my Dell Latitude D430 about a week ago, so I'm pretty fresh to the world of Linux. The more comfortable I get with it, the more I find myself wanting to put it on all my computers and use it for school/development. This brings me to my problem: my wireless connection is disconnecting about every 5-10 minutes. Often times the connection is repaired automatically, but sometimes the network manager will repeatedly reject my encryption key (which of course is correct). After a few disconnects, the wireless network fails to show up at all. The only way I can solve this seems to be by completely restarting Ubuntu or just waiting. I am using **WPA/WPA2** encryption, which I've read can cause problems with network-manager, but I experience the exact same issues with **WICD**. I should probably note that I haven't experienced any of these issues using Windows 7 on my other partition.

That being said, I have been able to identify my device and some information I think would be useful in troubleshooting this, but I have no idea where the source of the issue lies. Here's some more detailed information I thought might be useful:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:   oneiric
```

```
~$ lspci -nnk0
9:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
        Subsystem: Dell Device [1028:0201]
        Kernel driver in use: tg3
        Kernel modules: tg3
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
        Subsystem: Intel Corporation Device [8086:1020]
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945
```

```
~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: dell-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: no
```

I have created the file, **/etc/modprobe.d/iwl3945.conf**, and added this line:

```
options iwl3945 disable_hw_scan=1
```

I've also installed **linux-backports-modules-cw-3.2-oneiric-generic** and **linux-backports-modules-cw-3.2-3.0.0-17-generic**. None of these fixes seem to have solved anything, so I was wondering if I should undo these changes? Thanks! :)

---

### Post by chili555 on 2012-04-18
> I am using WPA/WPA2 encryption, which I've read can cause problems with network-manager,Actually, I believe mixed mode WPA and WPA2 causes problems with wpa_supplicant; used by both NM and Wicd. Can you change the router to WPA2 only?

What kind of signal strength do you have?```
sudo iwlist wlan0 scan
```>  Scan completed :
          Cell 01 - Address: xx:13:10:62:8D:zz
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="Red"]Quality=48/70[/COLOR]  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
<snip>

---

### Post by icevonshredula on 2012-04-18
> **chili555 said:**
> Actually, I believe mixed mode WPA and WPA2 causes problems with wpa_supplicant; used by both NM and Wicd. Can you change the router to WPA2 only?

What kind of signal strength do you have?

Ah yes I've read that before. I changed my router setting to WPA2-PSK (AES) only, but after still getting frequent disconnects and the "Wireless Network Authentication Required" dialogue, I decided to reboot. After the reboot, nothing seems to have changed. I got disconnected after about 30 seconds lol.

The signal seems decent, although it was the fifth one listed:

```
Cell 05 - Address: xx:0F:28:8D:30:xx
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=44/70  Signal level=-66 dBm
Encryption key:on
ESSID:"Treehouse"
```

I will say that I have yet to see download speeds reach above 150 kB/s when it is connected. On the Windows 7 partition though, I'll often see speeds over 1 MB/s.

---

### Post by Bucky Ball on 2012-04-18
Does the channel (11) match the one set on the router?

---

### Post by icevonshredula on 2012-04-18
> **Bucky Ball said:**
> Does the channel (11) match the one set on the router?

Yes, but the setting is actually on automatic:

> Wireless Channel: Auto
Current Wireless Channel: 11

I've never seen it on anything but 11, though.

---

### Post by chili555 on 2012-04-18
> Does the channel (11) match the one set on the router?
Yes, but the setting is actually on automatic:
I suggest you set it on *fixed* at channel 11.

Please do:```
sudo rm /etc/modprobe.d/iwl3945.conf
```Reboot and tell us if there is any improvement.

---

### Post by icevonshredula on 2012-04-18
I've set the channel to be fixed on 11, removed the iwl3945.conf file, and rebooted. It's still disconnecting and requiring authentication. :( Thanks for all the help, btw!

---

### Post by chili555 on 2012-04-18
I wonder what Network Manager is doing all this time. Please let us see:```
sudo cat /var/log/syslog | grep -e etwork -e iwl
```Off for the evening; see y'all tomorrow.

---

### Post by Bucky Ball on 2012-04-19
> **chili555 said:**
> ```
sudo cat /var/log/syslog | grep -e etwork -e iwl
```

I'm imagining that would be:

```
sudo cat /var/log/syslog | grep -e network -e iwl
```

... but maybe not ... ;)

---

### Post by icevonshredula on 2012-04-19
Well, here it is:

> Apr 18 20:12:17 Latitude-D430 NetworkManager[713]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Treehouse'.
Apr 18 20:16:22 Latitude-D430 kernel: [  262.354734] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Apr 18 20:16:22 Latitude-D430 kernel: [  262.354807] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdff000)
Apr 18 20:16:22 Latitude-D430 kernel: [  262.354823] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing
0x10)
Apr 18 20:16:22 Latitude-D430 kernel: [  262.354844] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
Apr 18 20:16:51 Latitude-D430 NetworkManager[713]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Treehouse'.
Apr 18 21:34:54 Latitude-D430 kernel: [ 1265.202666] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Apr 18 21:34:54 Latitude-D430 kernel: [ 1265.202739] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdff000)
Apr 18 21:34:54 Latitude-D430 kernel: [ 1265.202755] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 18 21:34:54 Latitude-D430 kernel: [ 1265.202776] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
Apr 18 21:35:22 Latitude-D430 NetworkManager[713]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Treehouse'.
Apr 18 21:36:53 Latitude-D430 kernel: [   22.253131] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Apr 18 21:36:53 Latitude-D430 kernel: [   22.253138] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Apr 18 21:36:53 Latitude-D430 kernel: [   22.257557] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 18 21:36:53 Latitude-D430 kernel: [   22.257577] iwl3945 0000:0c:00.0: setting latency timer to 64
Apr 18 21:36:53 Latitude-D430 kernel: [   22.317201] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 18 21:36:53 Latitude-D430 kernel: [   22.317208] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr 18 21:36:53 Latitude-D430 kernel: [   22.318526] iwl3945 0000:0c:00.0: irq 43 for MSI/MSI-X
Apr 18 21:36:53 Latitude-D430 kernel: [   22.357151] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Apr 18 21:36:54 Latitude-D430 NetworkManager[669]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Apr 18 21:36:54 Latitude-D430 kernel: [   23.773047] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
Apr 18 21:46:30 Latitude-D430 NetworkManager[669]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Treehouse'.
Apr 19 00:50:22 Latitude-D430 kernel: [  608.146758] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Apr 19 00:50:22 Latitude-D430 kernel: [  608.146831] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdff000)
Apr 19 00:50:22 Latitude-D430 kernel: [  608.146847] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 19 00:50:22 Latitude-D430 kernel: [  608.146868] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
Apr 19 00:53:41 Latitude-D430 kernel: [   22.112138] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Apr 19 00:53:41 Latitude-D430 kernel: [   22.112146] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Apr 19 00:53:41 Latitude-D430 kernel: [   22.122594] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 19 00:53:41 Latitude-D430 kernel: [   22.122614] iwl3945 0000:0c:00.0: setting latency timer to 64
Apr 19 00:53:41 Latitude-D430 kernel: [   22.283775] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 19 00:53:41 Latitude-D430 kernel: [   22.283782] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr 19 00:53:41 Latitude-D430 kernel: [   22.283951] iwl3945 0000:0c:00.0: irq 43 for MSI/MSI-X
Apr 19 00:53:41 Latitude-D430 kernel: [   22.346345] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Apr 19 00:53:41 Latitude-D430 NetworkManager[692]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Apr 19 00:53:42 Latitude-D430 kernel: [   23.496685] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9

That's not the whole thing, but everything prior just looked like repetition. I'm guessing the "restoring config space at offset" are my connection attempts, but not sure. Thanks guys.

---

### Post by chili555 on 2012-04-19
> **Bucky Ball said:**
> I'm imagining that would be:

```
sudo cat /var/log/syslog | grep -e network -e iwl
```

... but maybe not ... ;)Had the OP typed that, we would not have seen '**N**etworkManager' because it's not the same as 'network.' Using 'etwork' is a quick and lazy way to include both. Yes, I know I can grep -i network but that's a few extra keystrokes.

Hey, if you're on your way to 15,000 posts, you take shortcuts!

---

### Post by chili555 on 2012-04-19
> I'm guessing the "restoring config space at offset" are my connection attempts, but not sure.I am thinking that config space gets restored for all devices upon resume from suspend. Here is a grep of 'space' from my computer. 15:56 coincides, the best that I can recall, when I returned from lunch and shopping:> Apr 18 15:56:43 LAPTOP60 kernel: [550011.216257] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xf2828400)
Apr 18 15:56:43 LAPTOP60 kernel: [550011.216264] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
Apr 18 15:56:43 LAPTOP60 kernel: [550011.216394] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Apr 18 15:56:43 LAPTOP60 kernel: [550011.216466] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x400, writing 0x40b)
Apr 18 15:56:43 LAPTOP60 kernel: [550011.216489] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
Apr 18 15:56:43 LAPTOP60 kernel: [550011.216572] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
I am not at all sure your reading is at all alarming.

What we do not see is anything like 'NetworkManager[713]: <info> **de**activation (wlan0/wireless) Reason=whatever.' Can you try again? Can you reboot so we have a clean slate and as soon as practical after a disconnect, try:```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n20
```So far, I don't see anything wrong.

---

### Post by icevonshredula on 2012-04-19
> **chili555 said:**
> What we do not see is anything like 'NetworkManager[713]: <info> **de**activation (wlan0/wireless) Reason=whatever.' Can you try again? Can you reboot so we have a clean slate and as soon as practical after a disconnect, try:```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n20
```So far, I don't see anything wrong.

Here's the result from immediately after a disconnect. It successfully reconnected a few seconds later:

> Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0/wireless): access point 'Treehouse' has security, but secrets are required.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0/wireless): connection 'Treehouse' has security, and secrets exist.  No new secrets needed.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'ssid' value 'Treehouse'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'scan_ssid' value '1'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'psk' value '<omitted>'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: set interface ap_scan to 1
Apr 19 10:18:46 Latitude-D430 NetworkManager[692]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 19 10:18:56 Latitude-D430 NetworkManager[692]: <info> (wlan0): supplicant interface state: scanning -> authenticating

And here's the result from a disconnect followed by the authentication dialogue, followed by a failure to connect and then another authentication dialogue:

> Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0/wireless): access point 'Treehouse' has security, but secrets are required.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0/wireless): connection 'Treehouse' has security, and secrets exist.  No new secrets needed.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'ssid' value 'Treehouse'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'scan_ssid' value '1'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: added 'psk' value '<omitted>'
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 19 10:18:45 Latitude-D430 NetworkManager[692]: <info> Config: set interface ap_scan to 1
Apr 19 10:18:46 Latitude-D430 NetworkManager[692]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 19 10:18:56 Latitude-D430 NetworkManager[692]: <info> (wlan0): supplicant interface state: scanning -> authenticating

As a side note, I just had a solid connection for about an hour on my university's network while in class this morning. They use WPA & WPA2 Enterprise with a Tunneled TLS authentication (as well as an inner MSCHAPv2).

---

### Post by icevonshredula on 2012-04-26
Bump. Disregard the last note. I'm experiencing disconnects on every wireless network I try. I've been using a LAN connection directly for the last few days, and I can't seem to reach download speeds above 60 kB/s. It seems like this is definitely a client issue. Can anyone help me?

---

