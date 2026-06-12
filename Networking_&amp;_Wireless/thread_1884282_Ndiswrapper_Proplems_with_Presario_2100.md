---
title: "Ndiswrapper Proplems with Presario 2100"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2011-11-21
I can't get wifi to work on a Compaq Presario 2100 (US2195) with a Broadcom 4306 (rev2) wireless interface.  I am running lucid lynx.  I have tried installing the driver with System>Administration>Hardware Drivers and it doesn't work.  Now I have installed ndiswrapper, but and it seems to come closer, but still doesn't won't completely sync up, even though it shows a very strong wifi signal.  If I go to /etc/ndiswrapper I see a folder called "bcmwl5".  I presume this is the driver that ndiswrapper is using.

If I disable and then re-enable networking using NetworkManager and left-click the panel applet, I can see the network Olancha (my wifi network) under Wireless Networks.  It shows with a lock and a very strong signal.  The NetworkManager icon in the panel shows an arrow going in a circle indicating it is trying to connect to Olancha, but it never succeeds in connecting.  I ran the ip monitor in a Terminal and got the following messages:

[PHP]ralph@presario-lucid:~$ sudo ip monitor all
[LINK]4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]4: wlan0: <BROADCAST,MULTICAST,UP> 
    link/ether 
[NEIGH]224.0.0.22 dev eth0 lladdr 01:00:5e:00:00:16 NOARP[/PHP]

Any help would be appreciated.

Thank you
Ralph

I went back and installed the default driver using System>Administration>Hardware Drivers (nidiswrapper was not installed. I then used 'ip monitor all' to record what happens when I try to connect to the wifi.  Here are the results:

> sudo ip monitor all
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 


---

### Post by Sonsum on 2011-11-21
I'm forever traumatized by my ndiswrapper experiences with ubuntu 7.10. Since then, I've luckily had full wireless support.

Have you tried following the instructions on [this page?]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_Internet_access") It seems much simpler than ndiswrapper.

---

### Post by Ralph L on 2011-12-06
Sonsum, Thank you for your reply.  Yes, I tried everything on that page, but none of it worked so I installed ndiswrapper.  I will try some more, but for now I am pursing the ndiswrapper approach.

I finally got ndiswrapper to work by unistalling Network Manager as specified on this web site [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)  Apparently there is some conflict between Network Manager and ndiswrapper for my particular Broadcom 4306 rev 2 wireless interface. I used the WEP configuration specified in the web page and entered the following:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "olancha"
sudo iwconfig wlan0 key 4481b676498e9a95b5c00fd90e
sudo iwconfig mode Managed
sudo dhclient wlan0
```

The connection seems to work reasonably well, although if it sits idle for a while (sometimes a few minutes, sometimes an hour or more), I need to re-enter the code above.  Then it runs fine again. Can anybody tell me what is wrong??????????

My other problem is that now that I now longer have Network Manager I have no easy way of selecting wifis to log into.  In fact if I walk into Starbucks (or other free wifi place) I can't see what wifis are available.  Does anyone know of another gui other than Network Manager that would work????????

Thanks
Ralph

PS.  This site discussed the problems between ndiswrapper and Network Manager, but the script recommended did not seem to work for me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763).  Also, note that the last entry says the problem exists in lucid lynx and I would guess in all later versions, since there is no indication that it has ever been fixed.

---

### Post by Ralph L on 2011-12-06
I don't know the Ubuntu forum etiquette, but I really could use some help on this.  Somebody must know something about this.

Maybe I should start a new thread.

Ralph

---

### Post by Sonsum on 2011-12-06
Again, I'm not sure of its compatibility with Ndiswrapper, but WICD is a good network-manager alternative.

---

### Post by wildmanne39 on 2011-12-06
Hi, you do not need ndiswrapper for starters.

Please post the results of these commands.
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
Thank you

---

### Post by Ralph L on 2011-12-08
Sonsum,

Thank you for responding again.  I will try wicd if I can get ndiswrapper to work, unless Wildmanne39 (below) has a solution that doesn't require ndiswrapper.

Wildmanne39,
Thank you for responding.  Here are the results from the items you asked me to run:

Again,  thank you both for responding.  I have been working on this problem for a couple months and have made little progress.  I really do need your help.

```
ralph@presario-lucid:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux presario-lucid 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

```

```
ralph@presario-lucid:~$ lspci -nnk | grep -iA2 net
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Kernel driver in use: ndiswrapper
	Kernel modules: ssb
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Kernel driver in use: natsemi
	Kernel modules: natsemi

```

```
ralph@presario-lucid:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"olancha"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:6A:10:7E   
          Bit Rate=54 Mb/s   Tx-Power:14 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
ralph@presario-lucid:~$ rfkill list all
Note:  this command gave no output

```

```
ralph@presario-lucid:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ndiswrapper           184677  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_ali5451            15799  2 
vga16fb                11385  0 
snd_ac97_codec        100646  1 snd_ali5451
vgastate                8961  1 vga16fb
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                678735  2 
snd_timer              19098  2 snd_pcm,snd_seq
pcmcia                 30784  0 
ttm                    50103  1 radeon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                    1153  0 
lp                      7028  0 
joydev                  8740  0 
drm_kms_helper         29329  1 radeon
soundcore               6620  1 snd
yenta_socket           20408  1 
video                  17375  0 
drm                   162377  4 radeon,ttm,drm_kms_helper
ppdev                   5259  0 
parport_pc             25962  1 
rsrc_nonstatic         10015  1 yenta_socket
ati_agp                 5094  1 
i2c_ali15x3             5050  0 
parport                32635  3 lp,ppdev,parport_pc
snd_page_alloc          7076  1 snd_pcm
i2c_ali1535             4725  0 
agpgart                31724  3 ttm,drm,ati_agp
i2c_algo_bit            5028  1 radeon
output                  1871  1 video
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63677  0 
serio_raw               3978  0 
shpchp                 28835  0 
ohci1394               26950  0 
floppy                 53016  0 
natsemi                23934  0 
ieee1394               81181  1 ohci1394
pata_ali                7932  1 
```

---

### Post by wildmanne39 on 2011-12-08
Hi, if this text looks strange it is because my computer is not working right and I am trying to fix it so I will not be on much until it is fixed.

The following commands should get you going.

Run these commands one at a time.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```
Then unplug your wired connection and reboot.

---

### Post by Ralph L on 2011-12-08
Wildmanne39
Thank you for replying again.

I have another lucid partition set up that has never had ndiswrapper installed.  In fact it was set up using System>Administration>Hardware Drivers and uses b43legacy.  Is it ok if I apply your solution to this partition so that I don't destroy my ndiswrapper partition???

And here are the outputs of running those same commands on the b43legacy partition:

```
ralph@presario-lucid-b:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux presario-lucid-b 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux

```

```
ralph@presario-lucid-b:~$ lspci -nnk | grep -iA2 net
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Kernel driver in use: natsemi
	Kernel modules: natsemi

```

```
ralph@presario-lucid-b:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"olancha"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
ralph@presario-lucid-b:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
ralph@presario-lucid-b:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_ali5451            15799  2 
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
arc4                    1153  2 
pcmcia                 30784  0 
radeon                678735  2 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 radeon
b43legacy             115152  0 
drm_kms_helper         29329  1 radeon
ppdev                   5259  0 
mac80211              205434  1 b43legacy
yenta_socket           20408  1 
snd                    54244  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163651  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
video                  17375  0 
ati_agp                 5094  1 
parport_pc             25962  1 
rsrc_nonstatic         10015  1 yenta_socket
cfg80211              126112  2 b43legacy,mac80211
output                  1871  1 video
psmouse                63677  0 
i2c_ali15x3             5050  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,ati_agp
led_class               2864  1 b43legacy
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
snd_page_alloc          7076  1 snd_pcm
i2c_ali1535             4725  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
floppy                 53016  0 
natsemi                23934  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43legacy
pata_ali                7932  3 
```

---

### Post by wildmanne39 on 2011-12-08
Hi, it looks like your driver is installed with the information you posted so lets run these commands in the one without ndiswrapper and post the results here:
```
nm-tool
sudo iwlist scan

```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etwork | tail -n55
```
```
lsmod | grep b43
```
Thank you

---

### Post by Ralph L on 2011-12-09
Here are the results of running the various commands you requested:

```
ralph@presario-lucid-b:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0  [Auto olancha] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:90:4B:44:7F:66

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    olancha:         Infra, 00:0F:66:6A:10:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WEP
    linksys:         Infra, 00:13:10:BC:10:46, Freq 2437 MHz, Rate 54 Mb/s, Strength 58
    linksys:         Infra, 00:12:17:36:69:7F, Freq 2437 MHz, Rate 54 Mb/s, Strength 52


- Device: eth0  [static ip wired] ----------------------------------------------
  Type:              Wired
  Driver:            natsemi
  State:             connected
  Default:           yes
  HW Address:        00:0B:CD:7A:61:53

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.210
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             97.64.183.164
    DNS:             97.64.209.37

```

```
ralph@presario-lucid-b:~$ sudo iwlist scan
[sudo] password for ralph: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:36:69:7F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004677ec517f
                    Extra: Last beacon: 1000ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:0F:66:6A:10:7E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"olancha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cbd0150cf
                    Extra: Last beacon: 192ms ago
                    IE: Unknown: 00076F6C616E636861
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860

```

```
ralph@presario-lucid-b:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etwork | tail -n55
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0/wireless): connection 'static_ip_wireless' has security, and secrets exist.  No new secrets needed.
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'ssid' value 'olancha'
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Dec  8 22:29:00 presario-lucid-b NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  8 22:29:00 presario-lucid-b NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  Config: set interface ap_scan to 1
Dec  8 22:29:00 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:01 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:01 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:29:11 presario-lucid-b wpa_supplicant[887]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  8 22:29:11 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:11 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:12 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:12 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:29:15 presario-lucid-b NetworkManager: <info>  wlan0: link timed out.
Dec  8 22:29:22 presario-lucid-b wpa_supplicant[887]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  8 22:29:22 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:22 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:23 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:23 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:29:33 presario-lucid-b wpa_supplicant[887]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  8 22:29:33 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:33 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:35 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:35 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:29:45 presario-lucid-b wpa_supplicant[887]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  8 22:29:45 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:45 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:46 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:46 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:29:53 presario-lucid-b NetworkManager: <info>  wlan0: link timed out.
Dec  8 22:29:56 presario-lucid-b wpa_supplicant[887]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  8 22:29:56 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  8 22:29:56 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  8 22:29:57 presario-lucid-b wpa_supplicant[887]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  8 22:29:57 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) failed for access point (olancha)
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  Marking connection 'static_ip_wireless' invalid.
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  Activation (wlan0) failed.
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Dec  8 22:30:00 presario-lucid-b NetworkManager: <info>  Policy set 'static ip wired' (eth0) as default for routing and DNS.
Dec  8 22:30:07 presario-lucid-b wpa_supplicant[887]: Authentication with 00:00:00:00:00:00 timed out.

```


```
ralph@presario-lucid-b:~$ lsmod | grep b43
b43legacy             115152  0 
mac80211              205434  1 b43legacy
cfg80211              126112  2 b43legacy,mac80211
led_class               2864  1 b43legacy
ssb                    38934  1 b43legacy
```

---

### Post by wildmanne39 on 2011-12-09
Hi, you are having trouble with encryption, see if you can change your encryption in your router to wpa2 and not mixed mode if possible, then we will go from there.
Thank you

---

### Post by Ralph L on 2011-12-09
My Linksys router only supports WEP so I disabled encryption.  Here are the results of your previous request for data.

```
ralph@presario-lucid-b:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             disconnected
  Default:           no
  HW Address:        00:90:4B:44:7F:66

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    olancha:         Infra, 00:0F:66:6A:10:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 88
    linksys:         Infra, 00:12:17:36:69:7F, Freq 2437 MHz, Rate 54 Mb/s, Strength 54


- Device: eth0  [static ip wired] ----------------------------------------------
  Type:              Wired
  Driver:            natsemi
  State:             connected
  Default:           yes
  HW Address:        00:0B:CD:7A:61:53

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.210
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             97.64.183.164
    DNS:             97.64.209.37

```

```
ralph@presario-lucid-b:~$ sudo iwlist scan
[sudo] password for ralph: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:6A:10:7E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"olancha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000048530ab6
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 00076F6C616E636861
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860

```

```
ralph@presario-lucid-b:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etwork | tail -n55
Dec  9 12:33:03 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:08 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:08 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:08 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:10 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:10 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:10 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:15 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:15 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:15 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:16 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:16 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:16 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:21 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:21 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:21 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:22 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:22 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:22 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:27 presario-lucid-b NetworkManager: <info>  wlan0: link timed out.
Dec  9 12:33:27 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:27 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:27 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:29 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:29 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:29 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:34 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:34 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:34 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:35 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:35 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:35 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:40 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:40 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:40 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:41 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:41 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:41 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:43 presario-lucid-b NetworkManager: <info>  wlan0: link timed out.
Dec  9 12:33:46 presario-lucid-b wpa_supplicant[907]: Authentication with 00:0f:66:6a:10:7e timed out.
Dec  9 12:33:46 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  9 12:33:46 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  9 12:33:47 presario-lucid-b wpa_supplicant[907]: Trying to associate with 00:0f:66:6a:10:7e (SSID='olancha' freq=2462 MHz)
Dec  9 12:33:47 presario-lucid-b wpa_supplicant[907]: Association request to the driver failed
Dec  9 12:33:47 presario-lucid-b NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  Activation (wlan0) failed for access point (olancha)
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  Marking connection 'Auto olancha' invalid.
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  Activation (wlan0) failed.
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Dec  9 12:33:50 presario-lucid-b NetworkManager: <info>  Policy set 'static ip wired' (eth0) as default for routing and DNS.
Dec  9 12:33:52 presario-lucid-b wpa_supplicant[907]: Authentication with 00:00:00:00:00:00 timed out.
Dec  9 12:47:33 presario-lucid-b kernel: [48717.779075] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

```

```
ralph@presario-lucid-b:~$ lsmod | grep b43
b43legacy             115152  0 
mac80211              205434  1 b43legacy
cfg80211              126112  2 b43legacy,mac80211
led_class               2864  1 b43legacy
ssb                    38934  1 b43legacy

```

---

### Post by wildmanne39 on 2011-12-09
Hi, let's try to get past the encryption problem by installing wicd then uninstall network manager.

Start at post 2 in this thread and run the codes one line at a time some will take a little while to complete so give it time.
[http://ubuntuforums.org/showthread.php?t=1890972&highlight=wicd](http://ubuntuforums.org/showthread.php?t=1890972&highlight=wicd)

Also your wireless connection can only connect when you have your wired connection unplugged.

---

### Post by Ralph L on 2011-12-09
When I brought up wicd I got "Connection Failed: Unable to Get IP Address"  It just sat with the message "Obtaining IP address".  

I have to leave for several hours now, but I will be back later.

Thanks again

Ralph

---

### Post by wildmanne39 on 2011-12-09
Hi, run: 
```
iwconfig
``` 
to see what shows as wireless interface wlan0 for example, then set it up as that wireless interface and use wext as driver in wicd manager.

Thank you

---

### Post by Ralph L on 2011-12-10
Configured it as wlan0 in accordance with iwconfig (see below) Still won't work.  Hangs waiting for IP address.  Finally t```
imes  out.  Here are some outputs that might be useful.  Tell me what else you need.

[CODE]ralph@presario-lucid-b:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"olancha"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
ralph@presario-lucid-b:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etwork | tail -n55
[sudo] password for ralph: 
Dec  9 22:18:13 presario-lucid-b kernel: [23109.344417] b43legacy-phy0 debug: Adding Interface type 2
Dec  9 22:18:13 presario-lucid-b kernel: [23109.471978] b43legacy-phy0 debug: Removing Interface type 2
Dec  9 22:18:13 presario-lucid-b kernel: [23109.473534] b43legacy-phy0 debug: Wireless interface stopped
Dec  9 22:18:13 presario-lucid-b kernel: [23109.482869] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
Dec  9 22:18:13 presario-lucid-b kernel: [23109.482981] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec  9 22:18:13 presario-lucid-b kernel: [23109.483062] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.488131] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.496115] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.504066] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.512053] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.520051] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec  9 22:18:13 presario-lucid-b kernel: [23109.528406] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:13 presario-lucid-b kernel: [23109.528426] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:13 presario-lucid-b kernel: [23109.976128] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec  9 22:18:14 presario-lucid-b kernel: [23110.040629] b43legacy-phy0 debug: Chip initialized
Dec  9 22:18:14 presario-lucid-b kernel: [23110.041275] b43legacy-phy0 debug: 30-bit DMA initialized
Dec  9 22:18:14 presario-lucid-b kernel: [23110.050635] Registered led device: b43legacy-phy0::radio
Dec  9 22:18:14 presario-lucid-b kernel: [23110.050705] b43legacy-phy0 debug: Wireless interface started
Dec  9 22:18:14 presario-lucid-b kernel: [23110.056394] b43legacy-phy0 debug: Adding Interface type 2
Dec  9 22:18:14 presario-lucid-b kernel: [23110.550183] b43legacy-phy0 debug: Removing Interface type 2
Dec  9 22:18:14 presario-lucid-b kernel: [23110.550235] b43legacy-phy0 debug: Wireless interface stopped
Dec  9 22:18:14 presario-lucid-b kernel: [23110.568202] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
Dec  9 22:18:14 presario-lucid-b kernel: [23110.568324] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec  9 22:18:14 presario-lucid-b kernel: [23110.568426] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.576094] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.584139] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.592139] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.600163] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 8/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.608104] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec  9 22:18:14 presario-lucid-b kernel: [23110.616144] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:14 presario-lucid-b kernel: [23110.616171] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:14 presario-lucid-b kernel: [23111.004063] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec  9 22:18:15 presario-lucid-b kernel: [23111.068589] b43legacy-phy0 debug: Chip initialized
Dec  9 22:18:15 presario-lucid-b kernel: [23111.069132] b43legacy-phy0 debug: 30-bit DMA initialized
Dec  9 22:18:15 presario-lucid-b kernel: [23111.079259] Registered led device: b43legacy-phy0::radio
Dec  9 22:18:15 presario-lucid-b kernel: [23111.079330] b43legacy-phy0 debug: Wireless interface started
Dec  9 22:18:15 presario-lucid-b kernel: [23111.084434] b43legacy-phy0 debug: Adding Interface type 2
Dec  9 22:18:36 presario-lucid-b kernel: [23132.510186] b43legacy-phy0 debug: Removing Interface type 2
Dec  9 22:18:36 presario-lucid-b kernel: [23132.516824] b43legacy-phy0 debug: Wireless interface stopped
Dec  9 22:18:36 presario-lucid-b kernel: [23132.527858] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
Dec  9 22:18:36 presario-lucid-b kernel: [23132.527960] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec  9 22:18:36 presario-lucid-b kernel: [23132.528134] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.540670] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.548097] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.556112] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.564074] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 8/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.572041] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec  9 22:18:36 presario-lucid-b kernel: [23132.580153] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:36 presario-lucid-b kernel: [23132.580173] b43legacy-phy0 debug: Radio initialized
Dec  9 22:18:37 presario-lucid-b kernel: [23133.094082] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec  9 22:18:37 presario-lucid-b kernel: [23133.156628] b43legacy-phy0 debug: Chip initialized
Dec  9 22:18:37 presario-lucid-b kernel: [23133.157153] b43legacy-phy0 debug: 30-bit DMA initialized
Dec  9 22:18:37 presario-lucid-b kernel: [23133.164674] Registered led device: b43legacy-phy0::radio
Dec  9 22:18:37 presario-lucid-b kernel: [23133.164741] b43legacy-phy0 debug: Wireless interface started
Dec  9 22:18:37 presario-lucid-b kernel: [23133.172392] b43legacy-phy0 debug: Adding Interface type 2

```

```
ralph@presario-lucid-b:~$ dmesg | grep -e b43 -e firmware -e wpa -e etwork -e wlan0
[23109.976128] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[23110.040629] b43legacy-phy0 debug: Chip initialized
[23110.041275] b43legacy-phy0 debug: 30-bit DMA initialized
[23110.050635] Registered led device: b43legacy-phy0::radio
[23110.050705] b43legacy-phy0 debug: Wireless interface started
[23110.056394] b43legacy-phy0 debug: Adding Interface type 2
[23110.076694] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23110.077099] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[23110.276104] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[23110.476121] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[23110.550070] wlan0: deauthenticating from 00:0f:66:6a:10:7e by local choice (reason=3)
[23110.550183] b43legacy-phy0 debug: Removing Interface type 2
[23110.550235] b43legacy-phy0 debug: Wireless interface stopped
[23110.568202] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[23110.568324] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[23110.568426] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[23110.576094] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[23110.584139] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[23110.592139] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[23110.600163] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 8/128
[23110.608104] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[23110.616144] b43legacy-phy0 debug: Radio initialized
[23110.616171] b43legacy-phy0 debug: Radio initialized
[23111.004063] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[23111.068589] b43legacy-phy0 debug: Chip initialized
[23111.069132] b43legacy-phy0 debug: 30-bit DMA initialized
[23111.079259] Registered led device: b43legacy-phy0::radio
[23111.079330] b43legacy-phy0 debug: Wireless interface started
[23111.084434] b43legacy-phy0 debug: Adding Interface type 2
[23111.105081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23111.105473] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[23111.304111] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[23111.504069] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[23111.704120] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out
[23132.510186] b43legacy-phy0 debug: Removing Interface type 2
[23132.516824] b43legacy-phy0 debug: Wireless interface stopped
[23132.527858] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[23132.527960] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[23132.528134] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[23132.540670] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[23132.548097] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[23132.556112] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[23132.564074] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 8/128
[23132.572041] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[23132.580153] b43legacy-phy0 debug: Radio initialized
[23132.580173] b43legacy-phy0 debug: Radio initialized
[23133.094082] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[23133.156628] b43legacy-phy0 debug: Chip initialized
[23133.157153] b43legacy-phy0 debug: 30-bit DMA initialized
[23133.164674] Registered led device: b43legacy-phy0::radio
[23133.164741] b43legacy-phy0 debug: Wireless interface started
[23133.172392] b43legacy-phy0 debug: Adding Interface type 2
[23133.192646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23133.376275] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[23133.576084] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[23133.776580] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[23133.976404] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out
[23602.401823] b43legacy-phy0 debug: Removing Interface type 2
[23602.401873] b43legacy-phy0 debug: Wireless interface stopped
[23602.414115] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 7/64
[23602.414208] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[23602.414286] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[23602.420172] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[23602.428051] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[23602.436043] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[23602.444134] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 14/128
[23602.452091] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[23602.460046] b43legacy-phy0 debug: Radio initialized
[23602.460059] b43legacy-phy0 debug: Radio initialized
[23602.856080] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[23602.920588] b43legacy-phy0 debug: Chip initialized
[23602.921173] b43legacy-phy0 debug: 30-bit DMA initialized
[23602.928855] Registered led device: b43legacy-phy0::radio
[23602.928922] b43legacy-phy0 debug: Wireless interface started
[23602.936409] b43legacy-phy0 debug: Adding Interface type 2
[23602.956546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23602.956881] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[23603.156279] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[23603.356073] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[23603.556149] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out
[23753.644478] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

```

---

### Post by wildmanne39 on 2011-12-10
Hi, I am going to do some research on the error messages, did you use the wext driver?
Thank you

---

### Post by wildmanne39 on 2011-12-10
Hi, also please post the results of:
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep b43
```
Thank you

---

### Post by Ralph L on 2011-12-10
1.  Yes, I used the wext driver.

2.  Here are the items you asked for:

```
ralph@presario-lucid-b:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
ralph@presario-lucid-b:~$ sudo iwlist scan
[sudo] password for ralph: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:6A:10:7E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"olancha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016c1627185
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 00076F6C616E636861
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860

```

```
ralph@presario-lucid-b:~$ lsmod | grep b43
b43legacy             115152  0 
mac80211              205434  1 b43legacy
cfg80211              126080  2 b43legacy,mac80211
led_class               2864  1 b43legacy
ssb                    38934  1 b43legacy

```

---

### Post by wildmanne39 on 2011-12-10
Hi, manually set your ip address and see if that helps.
Thanks

---

### Post by Ralph L on 2011-12-11
I set it up for a static IP address.  Hopefully I did it correctly.  I got this message after it searched for a while: "Connection failed: Could not contact the wireless access point."

So I took some more data (after the static wireless connection was attempted, but before I plugged in the wired lan.  A lot of this did not change with the selection of a static ip, so is probably redundant.  Are there any other messages I can get for you????:

```
ralph@presario-lucid-b:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
ralph@presario-lucid-b:~$ sudo iwlist scan
[sudo] password for ralph: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:6A:10:7E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"olancha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cdb049188
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 00076F6C616E636861
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860

```

```
ralph@presario-lucid-b:~$ lsmod | grep b43
b43legacy             115152  0 
mac80211              205434  1 b43legacy
cfg80211              126080  2 b43legacy,mac80211
led_class               2864  1 b43legacy
ssb                    38934  1 b43legacy

```

```
ralph@presario-lucid-b:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"olancha"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
ralph@presario-lucid-b:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etwork | tail -n55
Dec 10 22:49:10 presario-lucid-b kernel: [85288.448536] b43legacy-phy0 debug: Adding Interface type 2
Dec 10 22:49:10 presario-lucid-b kernel: [85288.631515] b43legacy-phy0 debug: Removing Interface type 2
Dec 10 22:49:10 presario-lucid-b kernel: [85288.631560] b43legacy-phy0 debug: Wireless interface stopped
Dec 10 22:49:10 presario-lucid-b kernel: [85288.639790] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
Dec 10 22:49:10 presario-lucid-b kernel: [85288.639882] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec 10 22:49:10 presario-lucid-b kernel: [85288.639960] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.646034] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.652090] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.660174] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.668082] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.676102] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec 10 22:49:10 presario-lucid-b kernel: [85288.684164] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:10 presario-lucid-b kernel: [85288.684185] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:11 presario-lucid-b kernel: [85289.120065] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec 10 22:49:11 presario-lucid-b kernel: [85289.184694] b43legacy-phy0 debug: Chip initialized
Dec 10 22:49:11 presario-lucid-b kernel: [85289.185288] b43legacy-phy0 debug: 30-bit DMA initialized
Dec 10 22:49:11 presario-lucid-b kernel: [85289.194036] Registered led device: b43legacy-phy0::radio
Dec 10 22:49:11 presario-lucid-b kernel: [85289.194108] b43legacy-phy0 debug: Wireless interface started
Dec 10 22:49:11 presario-lucid-b kernel: [85289.200388] b43legacy-phy0 debug: Adding Interface type 2
Dec 10 22:49:11 presario-lucid-b kernel: [85289.292289] b43legacy-phy0 debug: Removing Interface type 2
Dec 10 22:49:11 presario-lucid-b kernel: [85289.300092] b43legacy-phy0 debug: Wireless interface stopped
Dec 10 22:49:11 presario-lucid-b kernel: [85289.300465] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
Dec 10 22:49:11 presario-lucid-b kernel: [85289.300565] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec 10 22:49:11 presario-lucid-b kernel: [85289.300663] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.308549] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.316112] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.324121] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.332138] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.340167] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec 10 22:49:11 presario-lucid-b kernel: [85289.348112] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:11 presario-lucid-b kernel: [85289.348139] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:11 presario-lucid-b kernel: [85289.792090] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec 10 22:49:12 presario-lucid-b kernel: [85289.864624] b43legacy-phy0 debug: Chip initialized
Dec 10 22:49:12 presario-lucid-b kernel: [85289.865227] b43legacy-phy0 debug: 30-bit DMA initialized
Dec 10 22:49:12 presario-lucid-b kernel: [85289.872553] Registered led device: b43legacy-phy0::radio
Dec 10 22:49:12 presario-lucid-b kernel: [85289.872619] b43legacy-phy0 debug: Wireless interface started
Dec 10 22:49:12 presario-lucid-b kernel: [85289.880395] b43legacy-phy0 debug: Adding Interface type 2
Dec 10 22:49:55 presario-lucid-b kernel: [85332.839757] b43legacy-phy0 debug: Removing Interface type 2
Dec 10 22:49:55 presario-lucid-b kernel: [85332.839806] b43legacy-phy0 debug: Wireless interface stopped
Dec 10 22:49:55 presario-lucid-b kernel: [85332.852464] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
Dec 10 22:49:55 presario-lucid-b kernel: [85332.852556] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
Dec 10 22:49:55 presario-lucid-b kernel: [85332.852636] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.860052] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.868075] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.876039] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.884038] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 14/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.892090] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Dec 10 22:49:55 presario-lucid-b kernel: [85332.900049] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:55 presario-lucid-b kernel: [85332.900062] b43legacy-phy0 debug: Radio initialized
Dec 10 22:49:55 presario-lucid-b kernel: [85333.314389] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Dec 10 22:49:55 presario-lucid-b kernel: [85333.376573] b43legacy-phy0 debug: Chip initialized
Dec 10 22:49:55 presario-lucid-b kernel: [85333.377170] b43legacy-phy0 debug: 30-bit DMA initialized
Dec 10 22:49:55 presario-lucid-b kernel: [85333.386221] Registered led device: b43legacy-phy0::radio
Dec 10 22:49:55 presario-lucid-b kernel: [85333.386295] b43legacy-phy0 debug: Wireless interface started
Dec 10 22:49:55 presario-lucid-b kernel: [85333.400409] b43legacy-phy0 debug: Adding Interface type 2

```

Note:  I included only the last few messages on this dmesg search:

```
ralph@presario-lucid-b:~$ dmesg | grep -e b43 -e firmware -e wpa -e etwork -e wlan0
[85289.120065] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[85289.184694] b43legacy-phy0 debug: Chip initialized
[85289.185288] b43legacy-phy0 debug: 30-bit DMA initialized
[85289.194036] Registered led device: b43legacy-phy0::radio
[85289.194108] b43legacy-phy0 debug: Wireless interface started
[85289.200388] b43legacy-phy0 debug: Adding Interface type 2
[85289.220613] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85289.221014] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[85289.292162] wlan0: deauthenticating from 00:0f:66:6a:10:7e by local choice (reason=3)
[85289.292289] b43legacy-phy0 debug: Removing Interface type 2
[85289.300092] b43legacy-phy0 debug: Wireless interface stopped
[85289.300465] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[85289.300565] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[85289.300663] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[85289.308549] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[85289.316112] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[85289.324121] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[85289.332138] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
[85289.340167] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[85289.348112] b43legacy-phy0 debug: Radio initialized
[85289.348139] b43legacy-phy0 debug: Radio initialized
[85289.792090] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[85289.864624] b43legacy-phy0 debug: Chip initialized
[85289.865227] b43legacy-phy0 debug: 30-bit DMA initialized
[85289.872553] Registered led device: b43legacy-phy0::radio
[85289.872619] b43legacy-phy0 debug: Wireless interface started
[85289.880395] b43legacy-phy0 debug: Adding Interface type 2
[85289.892703] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85289.893076] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[85290.092101] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[85290.292211] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[85290.493219] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out
[85292.100310] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[85292.300078] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[85292.500131] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[85292.700476] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out
[85332.839757] b43legacy-phy0 debug: Removing Interface type 2
[85332.839806] b43legacy-phy0 debug: Wireless interface stopped
[85332.852464] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[85332.852556] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[85332.852636] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[85332.860052] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[85332.868075] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[85332.876039] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[85332.884038] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 14/128
[85332.892090] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[85332.900049] b43legacy-phy0 debug: Radio initialized
[85332.900062] b43legacy-phy0 debug: Radio initialized
[85333.314389] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[85333.376573] b43legacy-phy0 debug: Chip initialized
[85333.377170] b43legacy-phy0 debug: 30-bit DMA initialized
[85333.386221] Registered led device: b43legacy-phy0::radio
[85333.386295] b43legacy-phy0 debug: Wireless interface started
[85333.400409] b43legacy-phy0 debug: Adding Interface type 2
[85333.420601] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85333.604311] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 1)
[85333.804108] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 2)
[85334.004113] wlan0: direct probe to AP 00:0f:66:6a:10:7e (try 3)
[85334.204106] wlan0: direct probe to AP 00:0f:66:6a:10:7e timed out

```

---

### Post by wildmanne39 on 2011-12-11
Hi, here is what I want you to do please.

```
sudo apt-get --purge remove b43-fwcutter firmware-b43legacy-installer
```
Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Than you

---

### Post by Ralph L on 2011-12-11
Hi

I performed the last set of operations.  Unfortunately I now get No wireless networks found.  I include below the results from lsmod with a grep for what I thought might be useful, and also a complete lsmod.

```
ralph@presario-lucid-b:~$ !319
lsmod | egrep 'b43|cfg|mac'
b43legacy             115152  0 
b43                   163556  0 
ssb                    38934  2 b43legacy,b43
mac80211              205434  2 b43legacy,b43
cfg80211              126080  3 b43legacy,b43,mac80211
led_class               2864  2 b43legacy,b43

```

```
ralph@presario-lucid-b:~$ lsmod
Module                  Size  Used by
b43legacy             115152  0 
b43                   163556  0 
ssb                    38934  2 b43legacy,b43
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_ali5451            15799  2 
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
joydev                  8740  0 
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
radeon                678735  2 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 radeon
pcmcia                 30784  0 
drm_kms_helper         29329  1 radeon
snd                    54244  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
mac80211              205434  2 b43legacy,b43
drm                   163747  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
parport_pc             25962  1 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
video                  17375  0 
psmouse                63677  0 
serio_raw               3978  0 
ati_agp                 5094  1 
cfg80211              126080  3 b43legacy,b43,mac80211
output                  1871  1 video
i2c_ali15x3             5050  0 
i2c_ali1535             4725  0 
snd_page_alloc          7076  1 snd_pcm
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  2 b43legacy,b43
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
floppy                 53016  0 
natsemi                23934  0 
pata_ali                7932  4 
ieee1394               81181  1 ohci1394
```

---

### Post by wildmanne39 on 2011-12-11
Hi, please run this command then reboot with the wired connection unplugged.
```
sudo apt-get remove firmware-b43-installer
```
I am sorry I have been slow at responding, I have a family issue that is taking up time until Wednesday afternoon.
Thank you

---

### Post by Ralph L on 2011-12-12
Wildmanne39

I want to thank you for everything you have done.  Don't worry if you are slow to respond.  I can wait.

Anyway, I ran the command line you asked me to, but I got this response.

```
ralph@presario-lucid-b:~$ sudo apt-get remove firmware-b43-installer
[sudo] password for ralph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

```

When I restarted without wired internet plugged in I got "No wireless networks found".  I ran some status commands:

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

```
ralph@presario-lucid-b:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

It appears to me that I have goofed the setup and wlan0 is no longer defined.

---

### Post by wildmanne39 on 2011-12-12
Hi, let's get you back where you were apparently your computer did not like the new firmware.

Open synaptic type broadcom into the search window remove any boxes with a green square by it except bcmwl-modaliases make sure it is installed then reboot your computer and run just this command.
```
sudo apt-get install b43-fwcutter
```
then unplug wired connection and reboot.
Thank you

---

### Post by Ralph L on 2011-12-12
Wildmanne39,

I followed your direction reinstalling the default driver and firmware, and guess what, it worked!!!  But it is flaky.  Sometimes it will sync up and sometimes not.  However, once it syncs up it does not seem to drop out like happened with ndiswrapper.  Also, I changed the channel number on the router.  I originally had it set to Channel 11, but I changed it to Channel 1.  I have been fiddling trying different channel numbers, and I have had it run on Channels 1-6.  It seems to run best on Channel 1, but won't always sync up even on that channel.  I have not been able to get it to sync even once, when I go back to Channel 11.

Also, sometimes, when it won't sync up, I unplug the Ethernet, reboot, and then it will likely sync up--but not always.  And once it syncs to a channel, in all likelyhood (but not always) I can click disconnect and then reconnect, and it will sync up again.

So the thing will work, but not always.  Moreover, I have not taken it to a Starbucks (or some other place) to see if it will sync there.  

I can't thank you enough for your patience and your time in working with me.  But if you can think of anything to make it less flaky, please let me know.  Also, I wonder if I should submit a bug report.  I don't think a driver/firmware should be this flaky.  If it continues this way I may buy a newer wireless card that is recommended for linux.

Thanks again,

Ralph

PS.  Here are the outputs of ip monitor all--the first one on Channel 1, which worked; and the second one on Channel 11, which failed. Everything is pretty much the same up to the point where all the "FAILED" messages start.  I don't understand the messages, but hopefully you do (or maybe somebody else).

```
ralph@presario-lucid-b:~$ !!
sudo ip monitor all
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state UNKNOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[ADDR]3: wlan0    inet 192.168.0.209/24 brd 192.168.0.255 scope global wlan0
[ROUTE]local 192.168.0.209 dev wlan0  table local  proto kernel  scope host  src 192.168.0.209 
[ROUTE]broadcast 192.168.0.255 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.209 
[ROUTE]broadcast 192.168.0.0 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]default via 192.168.0.1 dev wlan0 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[ROUTE]ff00::/8 dev wlan0  table local  metric 256  mtu 1500 advmss 1440 hoplimit 0
[ROUTE]fe80::/64 dev wlan0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
[LINK]3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 
    link/ether 00:90:4b:44:7f:66
[LINK]3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> 
    link/ether 
[NEIGH]192.168.0.1 dev wlan0 lladdr 00:0f:66:67:37:5e REACHABLE
[ADDR]3: wlan0    inet6 fe80::290:4bff:fe44:7f66/64 scope link 
       valid_lft forever preferred_lft forever
[ROUTE]local fe80::290:4bff:fe44:7f66 via :: dev lo  table local  proto none  metric 0  mtu 16436 advmss 16376 hoplimit 0

```

```
ralph@presario-lucid-b:~$ !!
sudo ip monitor all
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> 
    link/ether 
[ADDR]3: wlan0    inet 192.168.0.209/24 brd 192.168.0.255 scope global wlan0
[ROUTE]local 192.168.0.209 dev wlan0  table local  proto kernel  scope host  src 192.168.0.209 
[ROUTE]broadcast 192.168.0.255 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.209 
[ROUTE]broadcast 192.168.0.0 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]default via 192.168.0.1 dev wlan0 
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[NEIGH]192.168.0.1 dev wlan0  FAILED
[ADDR]Deleted 3: wlan0    inet 192.168.0.209/24 brd 192.168.0.255 scope global wlan0
[ROUTE]Deleted 192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.209 
[ROUTE]Deleted broadcast 192.168.0.255 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]Deleted broadcast 192.168.0.0 dev wlan0  table local  proto kernel  scope link  src 192.168.0.209 
[ROUTE]Deleted local 192.168.0.209 dev wlan0  table local  proto kernel  scope host  src 192.168.0.209 
[NEIGH]224.0.0.251 dev wlan0 lladdr 01:00:5e:00:00:fb NOARP
[NEIGH]224.0.0.22 dev wlan0 lladdr 01:00:5e:00:00:16 NOARP
[NEIGH]192.168.0.1 dev wlan0 
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[NEIGH]224.0.0.22 dev wlan0 lladdr 01:00:5e:00:00:16 NOARP
[LINK]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:90:4b:44:7f:66 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff
[LINK]2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN 
    link/ether 00:0b:cd:7a:61:53 brd ff:ff:ff:ff:ff:ff

```

---

### Post by wildmanne39 on 2011-12-12
Hi, when you want to connect with your wireless connection make sure you have your wired connection unplugged or it will override the wireless connection.

Also while you are having trouble connecting run the syslog command and the dmesg again while unplugged from the wired connection and post here.

I have the same card, I have used it for years and have never had any trouble with it but it is an older card and a little outdated now.
Thank you

---

### Post by Ralph L on 2011-12-14
A couple more questions.  

What is the wicd addon for wicd 1.6. Should I run it or just the standard version 

I see there are newer versions of wicd all the way up to version 1.7+ds1-9.  Will the newer versions of wicd run in lucid? Or should I use the 1.6 addon, or the 1.7+ds1-2 standard lucid version without the addon?

What does +ds1-2 stand for?  Is it customization for the different versions of Ubuntu, or just minor updates, or something else?

Right now most of the time I have to start wicd and select a network to get it to work.  I have the Automatic connect box checked but it doesn't automatically connect when I boot the computer up. Is there some way to fix this?

---

### Post by wildmanne39 on 2011-12-15
Hi, the addon has additional packages that helps with encryption.

I do not know about the updated version, I would imagine it would work if it is listed in synaptic but I am not sure about that.

I will ask a friend to take a look here and see if he can answer your questions.

---

### Post by praseodym on 2011-12-16
Hi there,

if I see it right on page 3 there were 2 drivers loaded, b43 and b43legacy. From [here]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices") the device with the ID 14e4:4320 needs the b43legacy:

```
sudo modprobe -rfv b43 b43legacy
sudo modprobe -v b43legacy
```
Check:
```
dmesg | grep b43
iwconfig
sudo iwlist scan
iwlist chan
```
In 10.04 you can update the driver via the backport-modules:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```and reboot.

The firmware file was extracted without errors? In Wicd you use **wlan0** as inteface name and **wext** as driver?

Ndiswrapper was removed completely?

```
locate ndiswrapper
```

---

### Post by Ralph L on 2013-01-11
I now have it working.  See [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

