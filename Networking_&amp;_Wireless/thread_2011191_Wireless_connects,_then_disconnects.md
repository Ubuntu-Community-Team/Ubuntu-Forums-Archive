---
title: "Wireless connects, then disconnects"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by Palemoonrider on 2012-06-26
Hello,
Was instructed to post new thread to help me with my wireless issue.
Dell Latitude 610. Just upgraded to 12.04 and cannot connect to wireless. Connects stays for about 10 secs then ask for key again.
Ran the requested script in terminal and got this:

bill@bill-Latitude-D610:~$ dmesg | greb ipw
No command 'greb' found, did you mean:
 Command 'grep' from package 'grep' (main)
 Command 'grub' from package 'grub' (main)
greb: command not found
bill@bill-Latitude-D610:~$ sudo iwlist eth1 scan
[sudo] password for bill: 
eth1      Scan completed :
          Cell 01 - Address: C0:C1:C0:A3:F4:A5
                    ESSID:"StudioBlueWest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 204ms ago
          Cell 02 - Address: C0:C1:C0:A3:F4:A7
                    ESSID:"StudioBlueWest-guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    Extra: Last beacon: 236ms ago
          Cell 03 - Address: 00:12:17:B5:D2:EF
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 92ms ago
          Cell 04 - Address: 00:1B:2F:0D:C0:84
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 76ms ago
          Cell 05 - Address: 94:44:52:5C:4D:24
                    ESSID:"William"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-32 dBm  
                    Extra: Last beacon: 68ms ago
          Cell 06 - Address: 00:22:75:ED:73:BF
                    ESSID:"Belkin_N_Wireless_ED73BF"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    Extra: Last beacon: 116ms ago
          Cell 07 - Address: C0:C1:C0:84:7A:BA
                    ESSID:"Yaquina Bay Bridge"
                    Protocol:IEEE 802.11bg
                    Mode:Master
I am wired right now.

---

### Post by wildmanne39 on 2012-06-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Palemoonrider on 2012-06-26
Hi, thanks for the reply. Can't find the "#"
But here are the results;

[Cbill@bill-Latitude-D610:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200
bill@bill-Latitude-D610:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200
bill@bill-Latitude-D610:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
bill@bill-Latitude-D610:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

bill@bill-Latitude-D610:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bill@bill-Latitude-D610:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
dell_laptop            17767  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                729591  3 
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
rfcomm                 38139  0 
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                87213  0 
serio_raw              13027  0 
bnep                   17830  2 
snd_timer              28931  2 snd_pcm,snd_seq
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146176  0 
parport_pc             32114  1 
binfmt_misc            17292  1 
libipw                 46701  1 ipw2200
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
mac_hid                13077  0 
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 ipw2200,libipw
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
drm                   197692  5 radeon,ttm,drm_kms_helper
lib80211               14040  2 ipw2200,libipw
video                  19068  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
tg3                   137273  0 
bill@bill-Latitude-D610:~$ 
ODE][/CODE]

---

### Post by Palemoonrider on 2012-06-26
Ok.
Now I figured out the between the brackets, Sorry

---

### Post by wildmanne39 on 2012-06-26
Hi, please set power management to off permanently if you have not already like this:

```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.
Does it connect now? if not post the output of:
```
nm-tool
```
Thanks

---

### Post by Palemoonrider on 2012-06-27
Not sure I am doing this correctly.
Followed the instructions and created the file. saved it then ran the code. reboot. Still same result.

[bill@bill-Latitude-D610:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:13:CE:2A:02:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    StudioBlueWest:  Infra, C0:C1:C0:A3:F4:A5, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    NETGEAR:         Infra, 00:1B:2F:0D:C0:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA
    linksys:         Infra, 00:12:17:B5:D2:EF, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    Yaquina Bay Bridge: Infra, C0:C1:C0:84:7A:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Kerson:          Infra, E0:46:9A:70:88:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    StudioBlueWest-guest: Infra, C0:C1:C0:A3:F4:A7, Freq 2412 MHz, Rate 54 Mb/s, Strength 59
    William:         Infra, 94:44:52:5C:4D:24, Freq 2437 MHz, Rate 54 Mb/s, Strength 96 WEP
    Belkin_N_Wireless_ED73BF: Infra, 00:22:75:ED:73:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    SandyHome:       Infra, 20:AA:4B:2D:57:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    SandyHome-guest: Infra, 20:AA:4B:2D:57:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    zoom:            Infra, 00:01:38:58:B8:FB, Freq 2457 MHz, Rate 54 Mb/s, Strength 32


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:1A:86:51

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


bill@bill-Latitude-D610:~$ gksudo gedit/etc/pm/power.d/wireless
bill@bill-Latitude-D610:~$ gksudo gedit/etc/pm/power.d/wireless
bill@bill-Latitude-D610:~$ /sbin/iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.
bill@bill-Latitude-D610:~$ 

I appreciate the effort, feel a little stupid right now.

---

### Post by wildmanne39 on 2012-06-27
Hi, is your network name William?

Please post output of:
```
sudo cat /var/log/syslog | grep -e ipw -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Palemoonrider on 2012-06-27
Hi, yes it is William. Here is the result:[bill@bill-Latitude-D610:~$ sudo cat /var/log/syslog | grep -e ipw -e firmware -e wpa -e wlan -e etork | tail -n55
[sudo] password for bill: 
Jun 26 21:37:34 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 21:37:34 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (auth) [id=0 id_str=]
Jun 26 21:37:54 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 21:43:03 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 21:43:03 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 21:43:03 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 21:43:03 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=1 id_str=]
Jun 26 21:43:23 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 21:48:29 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 21:48:29 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 21:48:29 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 21:48:29 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=2 id_str=]
Jun 26 21:48:49 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 21:55:50 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 21:55:50 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 21:55:50 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 21:55:50 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=3 id_str=]
Jun 26 21:56:10 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 22:03:11 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 22:03:11 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 22:03:11 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 22:03:11 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=3 id_str=]
Jun 26 22:03:30 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 22:10:30 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 22:10:30 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 22:10:31 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 22:10:31 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=3 id_str=]
Jun 26 22:10:51 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 22:17:52 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 22:17:52 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 22:17:52 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 22:17:52 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=3 id_str=]
Jun 26 22:18:12 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 26 22:23:20 bill-Latitude-D610 wpa_supplicant[1688]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 22:23:20 bill-Latitude-D610 wpa_supplicant[1688]: Association request to the driver failed
Jun 26 22:23:20 bill-Latitude-D610 wpa_supplicant[1688]: Associated with 94:44:52:5c:4d:24
Jun 26 22:23:20 bill-Latitude-D610 wpa_supplicant[1688]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (reauth) [id=4 id_str=]
Jun 26 22:24:24 bill-Latitude-D610 kernel: [   22.870114] libipw: 802.11 data/management/control stack, git-1.1.13
Jun 26 22:24:24 bill-Latitude-D610 kernel: [   22.870119] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jun 26 22:24:24 bill-Latitude-D610 kernel: [   22.907074] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jun 26 22:24:24 bill-Latitude-D610 kernel: [   22.907081] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jun 26 22:24:25 bill-Latitude-D610 kernel: [   23.809464] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 26 22:24:25 bill-Latitude-D610 kernel: [   23.809497] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jun 26 22:24:25 bill-Latitude-D610 NetworkManager[668]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 26 22:24:25 bill-Latitude-D610 kernel: [   24.431945] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jun 26 22:24:25 bill-Latitude-D610 NetworkManager[668]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Jun 26 22:24:25 bill-Latitude-D610 dbus[506]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun 26 22:24:25 bill-Latitude-D610 dbus[506]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun 26 22:24:25 bill-Latitude-D610 NetworkManager[668]: <info> wpa_supplicant started
Jun 26 22:24:25 bill-Latitude-D610 wpa_supplicant[818]: nl80211: Driver does not support authentication/association or connect commands
Jun 26 22:24:39 bill-Latitude-D610 wpa_supplicant[818]: Trying to associate with 94:44:52:5c:4d:24 (SSID='William' freq=2437 MHz)
Jun 26 22:24:39 bill-Latitude-D610 wpa_supplicant[818]: Association request to the driver failed
Jun 26 22:24:39 bill-Latitude-D610 wpa_supplicant[818]: Associated with 94:44:52:5c:4d:24
Jun 26 22:24:39 bill-Latitude-D610 wpa_supplicant[818]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5c:4d:24 completed (auth) [id=0 id_str=]
Jun 26 22:25:02 bill-Latitude-D610 wpa_supplicant[818]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
bill@bill-Latitude-D610:~$ 
Thanks again]

---

### Post by wildmanne39 on 2012-06-27
Hi, you are having trouble with encryption, please go into router settings and change encryption to wpa2 only if that option is available, then in network manager set the security to wpa/wpa2.
Reboot
Thanks

---

### Post by Palemoonrider on 2012-06-27
Thank you, Thank you, Thank you. Fixed my issue. I appreciate all the help and the timely replies. 
Now to go have some fun.

Would like to play with the display, so will go to that forum and read.

Thanks again, Palemoonrider

PS: Can't find how to mark solved.

---

### Post by wildmanne39 on 2012-06-27
Hi, your welcome! be careful playing with the display settings.
Thanks

---

