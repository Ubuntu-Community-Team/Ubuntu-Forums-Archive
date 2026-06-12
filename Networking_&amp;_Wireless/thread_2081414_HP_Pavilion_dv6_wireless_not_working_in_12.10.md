---
title: "HP Pavilion dv6 wireless not working in 12.10"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by silverkitsune27 on 2012-11-06
Hi everyone,

I am having wireless problems with my HP Pavilion dv6. I had the same problem in Ubuntu 12.04, so I thought it was a distribution problem, so I uninstalled it and put in 12.10, which is showing the exact same behavior.

Upon system start, my wifi shows it's trying to connect, then it sees my network and asks for the key, after which it tries to connect for about 30 seconds, then asks for the key again, and keeps repeating this. Wired works perfectly fine though. Can someone please help me?  Thanks lots in advance!


The output of the required codes are below:

ye@ubuntu:~$ lspci -nn | grep 0280
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]

ye@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
2: hp-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no

---

### Post by chili555 on 2012-11-06
Be sure the ethernet is disconnected and then do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If that doesn't do it, please post:```
nm-tool
```

---

### Post by silverkitsune27 on 2012-11-06
That didn't work.  The output of nm-tool is:

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        8C:A9:82:72:C6:F8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Kaplinghat Guest:Infra, 06:24:36:A7:74:2D, Freq 2422 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    eduroam:         Infra, 00:13:19:F2:2E:D2, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    UCI Cosmology Center: Infra, 00:24:36:A8:68:71, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    Cooray2174:      Infra, 10:9A:DD:85:F2:0B, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    CollinsLab:      Infra, C0:C1:C0:F9:17:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    UCInet Mobile Access: Infra, 00:13:19:F2:2E:D0, Freq 2462 MHz, Rate 54 Mb/s, Strength 74
    UCInet Mobile Access: Infra, 00:13:19:F2:2C:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 55
    UCInet Mobile Access: Infra, 00:13:1A:59:53:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    eduroam:         Infra, 00:13:1A:59:53:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    HEP Wireless Network: Infra, 00:24:36:A8:C4:93, Freq 2452 MHz, Rate 54 Mb/s, Strength 79
    eduroam:         Infra, 00:13:19:F2:2D:81, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    darkmatter:      Infra, 70:73:CB:BA:05:B5, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA2
    eduroam:         Infra, 00:0E:84:99:E1:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    405:             Infra, 00:02:CF:89:6B:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    eduroam:         Infra, 00:13:19:F2:2C:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    CoorayGroup2165: Infra, 10:9A:DD:86:5E:CB, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    HP-Print-04-LaserJet 400 color: Infra, 60:D8:19:1A:F0:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    UCInet Mobile Access: Infra, 00:13:19:F2:2D:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 52


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:1F:74:0F:C5:71

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


I'm at school now, not at my home, so the networks are different.  But my laptop is doing the exact same thing as it was before.


Sorry about the random smiley faces...

---

### Post by chili555 on 2012-11-06
Boy, oh boy! Every driver-dawg's dream; several access points all with the same SSID! Yippee! 

Which of the several SSIDs are you trying to connect to? Assuming, just as an example, it's this:> UCInet Mobile Access: Infra, 00:13:19:F2:2E:D0, Freq 2462 MHz, Rate 54 Mb/s, Strength 74You could probably get it to connect by specifying it's MAC address in Network Manager like the attached.

---

### Post by silverkitsune27 on 2012-11-06
It didn't work. My wireless still tries hard to connect, then a pop-up says "Disconnected - You are now offline."  The little light on my wifi-toggle key (F12) show's wifi is on...

I'm pretty sure it's something internal with my computer, like maybe the wireless card driver or something, because regardless of whether I'm at home or school, it keeps doing the same thing and shows the same error messages.

---

### Post by chili555 on 2012-11-07
Usually, the wireless driver iwlwifi is solid. I am using it myself right now and have taken my laptop to other locations and had no difficulty. Let's have a look at:```
iwconfig
sudo cat /var/log/syslog | grep etwork | tail -n15
dmesg | grep iwl
```

---

### Post by silverkitsune27 on 2012-11-07
The outputs are:

ye@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



ye@ubuntu:~$ sudo cat /var/log/syslog | grep etwork | tail -n15
Nov  7 17:29:58 ubuntu NetworkManager[849]: <info> Config: added 'key_mgmt' value 'NONE'
Nov  7 17:29:58 ubuntu NetworkManager[849]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  7 17:29:58 ubuntu NetworkManager[849]: <info> Config: set interface ap_scan to 1
Nov  7 17:29:58 ubuntu NetworkManager[849]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  7 17:30:05 ubuntu NetworkManager[849]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  7 17:30:05 ubuntu NetworkManager[849]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov  7 17:30:07 ubuntu NetworkManager[849]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  7 17:30:23 ubuntu NetworkManager[849]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov  7 17:30:23 ubuntu NetworkManager[849]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov  7 17:30:23 ubuntu NetworkManager[849]: <info> Marking connection 'UCInet Mobile Access' invalid.
Nov  7 17:30:23 ubuntu NetworkManager[849]: <warn> Activation (wlan0) failed for connection 'UCInet Mobile Access'
Nov  7 17:30:23 ubuntu NetworkManager[849]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov  7 17:30:23 ubuntu NetworkManager[849]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov  7 17:30:23 ubuntu NetworkManager[849]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Nov  7 17:30:23 ubuntu NetworkManager[849]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.



ye@ubuntu:~$ dmesg | grep iwl
[   23.449809] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   23.449811] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   23.449983] iwlwifi 0000:0d:00.0: >pci_resource_len = 0x00002000
[   23.449985] iwlwifi 0000:0d:00.0: >pci_resource_base = ffffc900117d4000
[   23.449986] iwlwifi 0000:0d:00.0: >HW Revision ID = 0x0
[   23.450380] iwlwifi 0000:0d:00.0: >irq 51 for MSI/MSI-X
[   23.673591] iwlwifi 0000:0d:00.0: >loaded firmware version 39.31.5.1 build 35138
[   23.673681] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEBUG disabled
[   23.673683] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEBUGFS enabled
[   23.673684] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   23.673685] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   23.673687] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_P2P disabled
[   23.673689] iwlwifi 0000:0d:00.0: >Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   23.673924] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[   23.681201] iwlwifi 0000:0d:00.0: >RF_KILL bit toggled to enable radio.
[   23.695161] iwlwifi 0000:0d:00.0: >device EEPROM VER=0x15d, CALIB=0x6
[   23.695163] iwlwifi 0000:0d:00.0: >Device SKU: 0x50
[   23.695165] iwlwifi 0000:0d:00.0: >Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   23.695173] iwlwifi 0000:0d:00.0: >Tunable channels: 13 802.11bg, 0 802.11a channels
[   23.697646] ieee80211 phy0: >Selected rate control algorithm 'iwl-agn-rs'
[   24.882694] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[   24.953398] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[   29.171137] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   37.484463] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   45.805870] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   57.346225] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   60.081275] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   68.354723] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   76.688045] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   79.423115] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   85.317317] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[   93.694774] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  118.875893] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  118.875894] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[  118.876048] iwlwifi 0000:0d:00.0: >pci_resource_len = 0x00002000
[  118.876050] iwlwifi 0000:0d:00.0: >pci_resource_base = ffffc900117d4000
[  118.876051] iwlwifi 0000:0d:00.0: >HW Revision ID = 0x0
[  118.876379] iwlwifi 0000:0d:00.0: >irq 51 for MSI/MSI-X
[  118.878371] iwlwifi 0000:0d:00.0: >loaded firmware version 39.31.5.1 build 35138
[  118.878471] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEBUG disabled
[  118.878474] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEBUGFS enabled
[  118.878475] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  118.878477] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[  118.878478] iwlwifi 0000:0d:00.0: >CONFIG_IWLWIFI_P2P disabled
[  118.878481] iwlwifi 0000:0d:00.0: >Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[  118.878660] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[  118.885979] iwlwifi 0000:0d:00.0: >RF_KILL bit toggled to enable radio.
[  118.900032] iwlwifi 0000:0d:00.0: >device EEPROM VER=0x15d, CALIB=0x6
[  118.900034] iwlwifi 0000:0d:00.0: >Device SKU: 0x50
[  118.900035] iwlwifi 0000:0d:00.0: >Valid Tx ant: 0x1, Valid Rx ant: 0x3
[  118.900044] iwlwifi 0000:0d:00.0: >Tunable channels: 13 802.11bg, 0 802.11a channels
[  118.900305] ieee80211 phy0: >Selected rate control algorithm 'iwl-agn-rs'
[  118.913284] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[  118.977845] iwlwifi 0000:0d:00.0: >L1 Enabled; Disabling L0S
[  122.949295] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  131.258644] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  139.568031] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  144.914310] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  153.259662] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  167.191193] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  173.301267] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  181.630639] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  189.944045] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  201.396404] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  229.299513] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  243.223084] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  274.161144] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[  290.859916] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues

---

### Post by chili555 on 2012-11-07
> [ 37.484463] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[ 45.805870] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[ 57.346225] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queues
[ 60.081275] iwlwifi 0000:0d:00.0: >fail to flush all tx fifo queuesThere's a clue. Googling and you might do so as well.

Edit: Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552)> I switched the router to only G, and so far the problem is gone, so I would guess that is something wrong with the N interface.You might try that or else:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Do either help?

---

### Post by silverkitsune27 on 2012-11-07
How do I switch to G? Sorry if this is a stupid question...

---

### Post by Hadaka on 2012-11-07
@chili555, following along..found this..

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147/comments/16)

---

### Post by silverkitsune27 on 2012-11-08
It WORKS!!! Thank you SO MUCH for your link, Hadaka, and thank you chili555 for all your input.

The temporary solution works but I can't seem to get it to permanently remember the setting.  Guess I'll just always type that command upon login then.

---

### Post by chili555 on 2012-11-08
Let's try the easy way first:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi  bt_coex_active=N
```Proofread, save and close gedit.

@Hadaka--

Note his driver is iwlwifi, not iwlagn and that, according to modinfo, the parameter is boolean (Y or N) and not an integer (0 or 1). We will await silverkitsune27's results.

---

