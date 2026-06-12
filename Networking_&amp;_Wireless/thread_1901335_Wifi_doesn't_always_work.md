---
title: "Wifi doesn't always work"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by Sluysen on 2011-12-28
I'v posted this problem in Hardware, but I noticed this is more appropriate place of posting it.

[http://ubuntuforums.org/showthread.php?t=1900920](http://ubuntuforums.org/showthread.php?t=1900920)

My Wifi doesn't always work. At the moment i'm at home, using my wifi and that works. But I tried it at some friends (2 different places) and I couldn't connect to their wifi.

The fact that it works at home, really confuses me.

i'v been trying this tutorial: [http://ubuntuforums.org/showthread.php?t=1617380&highlight=brcmsmac+driver+download](http://ubuntuforums.org/showthread.php?t=1617380&highlight=brcmsmac+driver+download)

but i'm stuck at this part:
```
sudo cp brcm80211.ko /lib/modules/`uname -r`/
```
I don't think I have that file, brcm80211.ko
I can't find it on my system.

I'm hoping anyone here can help me (since I don't get responce in the hardware bit of this forum :p)

I am a total linux noob, i know some commands but most the things I read is like Chinese to me :p

---

### Post by wildmanne39 on 2011-12-28
Hi, we need to get some information from you so we can help you, also your wireless goes in and out at your house but does not connect at all at your friends houses correct?

We need to get it working at your house before we try to get it working somewhere else if that is the case.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Sluysen on 2011-12-29
Thx for your reply.

At home, the wifi works excellent. The minute I log on to ubuntu, i'm connected.
At other places, he keeps asking for the wifi key.

The hardware button is off, but i'm connected at home, at other places, he finds networks but can't connect

The output:
```
sluysen@Slubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Slubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
sluysen@Slubuntu:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1521]
	Kernel driver in use: e1000e
--
44:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1510]
	Kernel driver in use: brcmsmac
sluysen@Slubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"PolleThuis"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:09:85:28   
          Bit Rate=3.2 Mb/s   Tx-Power=21 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:50   Missed beacon:0

sluysen@Slubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
sluysen@Slubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
vesafb                 13809  1 
pata_pcmcia            17074  1 
nvidia              11713772  52 
snd_hda_codec_hdmi     32040  4 
bcma                   20219  0 
arc4                   12529  2 
tpm_infineon           17536  0 
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
pcmcia                 49378  1 pata_pcmcia
mxm_wmi                12979  0 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
parport_pc             36962  1 
snd_seq_midi           13324  0 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
yenta_socket           28084  0 
hp_accel               21880  0 
psmouse                73882  0 
r592                   18144  0 
pcmcia_rsrc            18430  1 yenta_socket
lis3lv02d              19888  1 hp_accel
video                  19412  0 
serio_raw              13166  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
tpm_tis                18546  0 
input_polldev          13896  1 lis3lv02d
memstick               16569  1 r592
snd_seq_midi_event     14899  1 snd_seq_midi
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
wmi                    19256  2 hp_wmi,mxm_wmi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
mac80211              462092  1 brcmsmac
mei                    41480  0 
cfg80211              199587  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
intel_ips              18089  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 
e1000e                160582  0

```

---

### Post by wildmanne39 on 2011-12-29
Hi, I have been doing some research and this is not the best driver for your card, I also noticed that your connection speed is slow according to the information we can switch drivers and see if that fixes the problems you are having.

Please do:
```
sudo apt-get install bcmwl-kernel-source
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d
/blacklist.conf
```
Reboot, Thanks

---

### Post by Sluysen on 2011-12-29
I think this did the trick.

The wifi switch is now blue and active. haven't dared putting it out tho :p

I'm gonna try wifi with other connections tomorrow.
If it works, i'll mark this as solved (and the other one too)

Thx a lot!

---

### Post by wildmanne39 on 2011-12-29
Hi, your welcome!
Enjoy

---

### Post by Sluysen on 2011-12-30
Things are getting more and more odd.

I'm at my girlfriends house, about 3 meters away from their router.
I'v been using their wifi on windows today, no problems.

Then I booted to linux, and it didn't show their network at all. Only some from their neighbourhood wich are secured ofc :p

I'm now using a Dlink wifi stick (delivered with their router) and that works like a charm. Why doesn't my built in wifi work like that :(

---

### Post by Sluysen on 2011-12-30
more code, as I see it requested in other topics with wireless issues

```
sluysen@Slubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:AC:BC:21

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:26:82:AC:BB:F5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Belkin_N_Wireless_7EA9A7: Infra, 00:1C:DF:7E:A9:A7, Freq 2437 MHz, Rate 0 Mb/s, Strength 15
    telenet-4384B:   Infra, 00:24:A0:E6:9A:F4, Freq 2437 MHz, Rate 0 Mb/s, Strength 14 WPA
    USR5461:         Infra, 00:14:C1:34:25:E8, Freq 2462 MHz, Rate 0 Mb/s, Strength 14 WEP
    pmn:             Infra, 5C:D9:98:2B:D1:78, Freq 2422 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2


- Device: wlan1  [dlink 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        00:1B:11:13:D5:7E

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    USR5461:         Infra, 00:14:C1:34:25:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    pmn:             Infra, 5C:D9:98:2B:D1:78, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *dlink:          Infra, 00:1B:11:69:83:91, Freq 2472 MHz, Rate 54 Mb/s, Strength 71 WEP
    telenet-4384B:   Infra, 00:24:A0:E6:9A:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA

  IPv4 Settings:
    Address:         192.168.0.196
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```
```
sluysen@Slubuntu:~$ sudo iwlist scan
[sudo] password for sluysen: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 5C:D9:98:2B:D1:78
                    ESSID:"pmn"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/5  Signal level:-92 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:24:A0:E6:9A:F4
                    ESSID:"telenet-4384B"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

wlan1     Scan completed :
          Cell 01 - Address: 00:1B:11:69:83:91
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004bba184ed88
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD1E00904C334E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D050500000000000000000000000000000000000000
                    IE: Unknown: 2D1A6E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D180D0500000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00
          Cell 02 - Address: 00:24:A0:E6:9A:F4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"telenet-4384B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012916ffb188
                    Extra: Last beacon: 1004ms ago
                    IE: Unknown: 000D74656C656E65742D3433383442
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

Connected with dlink stick atm, don't know it it's good for amount of output :p

---

### Post by wildmanne39 on 2011-12-30
Hi, is there network hidden?

The information you posted is that at her house? if so we need to see it without the usb adapter plugged in.

Also with the usb adapter plugged in it is conflicting with the internal card but it is probably an encryption issue, but to troubleshoot it you will need to be at here house when you post information.

What is the name of the network you are tying to connect too?
Thanks

---

### Post by Sluysen on 2011-12-31
This is the output at her house, without the  wifi stick plugged in:

```

 nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:AC:BC:21

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:26:82:AC:BB:F5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    USR5461:         Infra, 00:14:C1:34:25:E8, Freq 2462 MHz, Rate 0 Mb/s, Strength 12 WEP
    Belkin_N_Wireless_7EA9A7: Infra, 00:1C:DF:7E:A9:A7, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    pmn:             Infra, 5C:D9:98:2B:D1:78, Freq 2422 MHz, Rate 0 Mb/s, Strength 15 WPA WPA2
    telenet-4384B:   Infra, 00:24:A0:E6:9A:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA

sudo iwlist scan
[sudo] password for sluysen: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:24:A0:E6:9A:F4
                    ESSID:"telenet-4384B"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 5C:D9:98:2B:D1:78
                    ESSID:"pmn"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s




sluysen@Slubuntu:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
Dec 31 15:35:11 Slubuntu wpa_supplicant[1109]: Association request to the driver failed
Dec 31 15:35:16 Slubuntu wpa_supplicant[1109]: Authentication with 5c:d9:98:2b:d1:78 timed out.
Dec 31 15:35:18 Slubuntu wpa_supplicant[1109]: Trying to associate with 5c:d9:98:2b:d1:78 (SSID='pmn' freq=2422 MHz)
Dec 31 15:35:18 Slubuntu wpa_supplicant[1109]: Association request to the driver failed
Dec 31 15:35:23 Slubuntu wpa_supplicant[1109]: Authentication with 5c:d9:98:2b:d1:78 timed out.
Dec 31 15:35:49 Slubuntu wpa_supplicant[1109]: Trying to associate with 00:1c:df:7e:a9:a7 (SSID='Belkin_N_Wireless_7EA9A7' freq=2437 MHz)
Dec 31 15:35:49 Slubuntu wpa_supplicant[1109]: Association request to the driver failed
Dec 31 15:35:54 Slubuntu wpa_supplicant[1109]: Authentication with 00:1c:df:7e:a9:a7 timed out.

```

For the sake of it, i did the same on my gf's Vaio also running ubuntu 11.10 (no wifi issues at all)

The network it should connect to is "dlink" There are 2 around, but mine doesn't find either of them. And mine always tries to connect with that belkin, I have no clue where it's from :p

```

sudo iwlist scan
[sudo] password for stephanie: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:69:83:91
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004ca78b69168
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD1E00904C334E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D050500000000000000000000000000000000000000
                    IE: Unknown: 2D1A6E101DFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D180D0500000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00


```

```
stephanie@stephanie-VPCEB1J1E:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0/wireless): connection 'dlink 1' has security, and secrets exist.  No new secrets needed.
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 31 15:30:52 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec 31 15:30:53 stephanie-VPCEB1J1E wpa_supplicant[969]: Trying to authenticate with 00:1b:11:69:83:91 (SSID='dlink' freq=2472 MHz)
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 31 15:30:53 stephanie-VPCEB1J1E wpa_supplicant[969]: Trying to associate with 00:1b:11:69:83:91 (SSID='dlink' freq=2472 MHz)
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.370934] wlan0: authenticate with 00:1b:11:69:83:91 (try 1)
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.372665] wlan0: authenticated
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.401062] wlan0: associate with 00:1b:11:69:83:91 (try 1)
Dec 31 15:30:53 stephanie-VPCEB1J1E wpa_supplicant[969]: Associated with 00:1b:11:69:83:91
Dec 31 15:30:53 stephanie-VPCEB1J1E wpa_supplicant[969]: CTRL-EVENT-CONNECTED - Connection to 00:1b:11:69:83:91 completed (auth) [id=0 id_str=]
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.403522] wlan0: RX AssocResp from 00:1b:11:69:83:91 (capab=0x431 status=0 aid=1)
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.403529] wlan0: associated
Dec 31 15:30:53 stephanie-VPCEB1J1E kernel: [   20.404125] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): supplicant interface state: associating -> completed
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dlink'.
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 31 15:30:53 stephanie-VPCEB1J1E dhclient: Listening on LPF/wlan0/2c:81:58:f6:da:99
Dec 31 15:30:53 stephanie-VPCEB1J1E dhclient: Sending on   LPF/wlan0/2c:81:58:f6:da:99
Dec 31 15:30:53 stephanie-VPCEB1J1E dhclient: DHCPREQUEST of 192.168.0.122 on wlan0 to 255.255.255.255 port 67
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 31 15:30:53 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 31 15:30:53 stephanie-VPCEB1J1E avahi-daemon[854]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.122.
Dec 31 15:30:53 stephanie-VPCEB1J1E avahi-daemon[854]: New relevant interface wlan0.IPv4 for mDNS.
Dec 31 15:30:53 stephanie-VPCEB1J1E avahi-daemon[854]: Registering new address record for 192.168.0.122 on wlan0.IPv4.
Dec 31 15:30:54 stephanie-VPCEB1J1E avahi-daemon[854]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2e81:58ff:fef6:da99.
Dec 31 15:30:54 stephanie-VPCEB1J1E avahi-daemon[854]: New relevant interface wlan0.IPv6 for mDNS.
Dec 31 15:30:54 stephanie-VPCEB1J1E avahi-daemon[854]: Registering new address record for fe80::2e81:58ff:fef6:da99 on wlan0.*.
Dec 31 15:30:54 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 31 15:30:54 stephanie-VPCEB1J1E NetworkManager[853]: <info> Policy set 'dlink 1' (wlan0) as default for IPv4 routing and DNS.
Dec 31 15:30:54 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) successful, device activated.
Dec 31 15:30:54 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 31 15:30:54 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 31 15:31:03 stephanie-VPCEB1J1E kernel: [   30.617473] wlan0: no IPv6 routers present
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 31 15:31:13 stephanie-VPCEB1J1E NetworkManager[853]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.

```

---

### Post by wildmanne39 on 2011-12-31
Hi, the networks you are detecting are very weak, and I wonder if you can not see your girl friends because it is on a channel you can not use please post:
```
iwlist chan
```

Also there is an error message > Association request to the driver failedI have done a lot of research on it but I have not found anything useful.

I am going to ask a friend to take a look.
Thanks

---

### Post by wildmanne39 on 2011-12-31
Hi, we have conflicting information please run these two commands again.
```
iwconfig
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```

Did you manually set up your wireless connection? with the driver you are using it should be eth1 not wlan0, if you did please remove that connection and reboot and let network manager find your connection and name it.

Then run the above commands and make sure everything you post here is without a usb adapter plugged in.
Thanks

---

### Post by Sluysen on 2012-01-01
```
sluysen@Slubuntu:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

sluysen@Slubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:222
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sluysen@Slubuntu:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
[sudo] password for sluysen: 
Jan  1 21:51:36 Slubuntu kernel: [   16.449571] wl 0000:44:00.0: setting latency timer to 64
Jan  1 21:51:36 Slubuntu kernel: [   16.647741] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.100.82.38
Jan  1 21:51:36 Slubuntu NetworkManager[1027]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1, iface: eth1)
Jan  1 21:51:36 Slubuntu NetworkManager[1027]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1/rfkill0) (driver (unknown))
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <error> [1325451096.510742] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): now managed
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): bringing up device.
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): preparing device.
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan  1 21:51:36 Slubuntu dbus[1013]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  1 21:51:36 Slubuntu dbus[1013]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> wpa_supplicant started
Jan  1 21:51:36 Slubuntu wpa_supplicant[1144]: nl80211: 'nl80211' generic netlink not found
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): supplicant interface state: starting -> ready
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  1 21:51:36 Slubuntu NetworkManager[1027]: <info> (eth1): supplicant interface state: ready -> inactive
Jan  1 21:51:37 Slubuntu avahi-daemon[1025]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::226:82ff:feac:bbf5.
Jan  1 21:51:37 Slubuntu avahi-daemon[1025]: New relevant interface eth1.IPv6 for mDNS.
Jan  1 21:51:37 Slubuntu avahi-daemon[1025]: Registering new address record for fe80::226:82ff:feac:bbf5 on eth1.*.
Jan  1 21:51:46 Slubuntu kernel: [   28.790904] eth1: no IPv6 routers present
Jan  1 21:53:52 Slubuntu kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 8540p (WT025ES)/1521, BIOS 68CVD Ver. F.20 09/07/2011
Jan  1 21:53:52 Slubuntu kernel: [   16.839350] wl: module license 'MIXED/Proprietary' taints kernel.
Jan  1 21:53:52 Slubuntu kernel: [   16.846294] wl 0000:44:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan  1 21:53:52 Slubuntu kernel: [   16.846304] wl 0000:44:00.0: setting latency timer to 64
Jan  1 21:53:52 Slubuntu kernel: [   16.992534] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.100.82.38
Jan  1 21:53:52 Slubuntu NetworkManager[993]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1, iface: eth1)
Jan  1 21:53:52 Slubuntu NetworkManager[993]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/eth1/rfkill0) (driver (unknown))
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <error> [1325451232.499800] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): now managed
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): bringing up device.
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): preparing device.
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan  1 21:53:52 Slubuntu dbus[982]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  1 21:53:52 Slubuntu dbus[982]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> wpa_supplicant started
Jan  1 21:53:52 Slubuntu wpa_supplicant[1101]: nl80211: 'nl80211' generic netlink not found
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): supplicant interface state: starting -> ready
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  1 21:53:52 Slubuntu NetworkManager[993]: <info> (eth1): supplicant interface state: ready -> inactive
Jan  1 21:53:53 Slubuntu avahi-daemon[994]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::226:82ff:feac:bbf5.
Jan  1 21:53:53 Slubuntu avahi-daemon[994]: New relevant interface eth1.IPv6 for mDNS.
Jan  1 21:53:53 Slubuntu avahi-daemon[994]: Registering new address record for fe80::226:82ff:feac:bbf5 on eth1.*.
Jan  1 21:54:02 Slubuntu kernel: [   28.977700] eth1: no IPv6 routers present


```

this is after a reboot (i first deleted all the saved networks, and rebooted)

Also, it found 1 of the 2 dlinks around, but couldn't connect (also didn't ask for a wifi key, so it wasn't the one I need)

---

### Post by wildmanne39 on 2012-01-01
Hi, go to the top right corner of the screen and click on the internet icon then click on edit connections, wireless and make sure your wireless connection looks like the screenshots but you do not need to enter the numbers next to dns server under ipv4 settings.

You have new error messages I think one of them is related to encryption that might be able to be fixed by installing wicd.

Also we could use the b43 driver for your card if you were using the 3.1 kernel but you are using the 3.0 and I am not the best person to tell you how to upgrade kernels.
Thanks

---

### Post by Sluysen on 2012-01-05
How can I edit that connection, while he doesn't find it?

I don't really get it :p

Also is there a guide for a kernel update from 3 to 3.1 (don't wanna screw it up)

---

### Post by wildmanne39 on 2012-01-05
Hi, you can deactivate ipv6 with this command:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
I did not find a guide for upgrading from 3.0 to 3.1, I did find other guides but I am not going to post a link because I do not want to be responsible for you breaking your system.
Thanks

---

