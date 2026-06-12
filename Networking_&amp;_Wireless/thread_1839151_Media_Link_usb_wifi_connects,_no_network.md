---
title: "Media Link usb wifi connects, no network"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by doyleman on 2011-09-05
I use a media link usb wifi adapter, and it connects to our ssid off/on repeatedly, but even when it is connected, there's little (10-12 bits) - 0 connection.
lsmod shows the following:

Module         Used by
rt2800lib      rt2800usb
crc_ccitt      rt2870sta, rt2800lib
rt2x00usb      rt2800usb
rt2x00lib      rt2800usb, rt2800lib, rt2x00usb
mac80211       rt2800lib, rt2x00usb, rt2x00lib
cfg80211       rt2800lib, rt2x00usb, rt2x00lib


please note that i had to copy from my desktop to my netbook (what i'm on now) via eye, and only typed up the modules that seem important. any information on how i can maybe restore my wifi?

---

### Post by northd_tech on 2011-09-05
Can you also post the results of the following terminal commands:

```
nm-tool
rfkill list all
lsusb
iwconfig
ifconfig
sudo iwlist scan
```Are you able to cable into a good Ethernet connection somewhere?  That might make it a lot easier to fix things.

EDIT:  It might be a good idea to also post the full output of **lsmod**- there might be some conflicting modules that may need blacklisting.

---

### Post by doyleman on 2011-09-05
hi northd_tech, thanks for the reply. I can't -readily- get hardwired into the net, no; i live in an apartment complex that broadcasts it. I ran all of the following terminal commands, copied them over to a text file on my jump drive, and copied them to this post from my netbook (using w7 on it), lol. Here are the results:

```
 nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:62:6D:42:21:D9

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto FBI Surveillance van] -----------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        C8:3A:35:CA:2A:A5

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    334a:            Infra, 00:1E:4C:9D:FD:CD, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WEP
    *FBI Surveillance van: Infra, C0:C1:C0:0D:03:90, Freq 2422 MHz, Rate 54 Mb/s, Strength 84 WPA2
    79ae:            Infra, 00:23:4E:20:D3:93, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    444a:            Infra, C4:46:19:2C:F8:9F, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WEP
    LinksysAB:       Infra, 98:FC:11:47:20:B7, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    sammylou:        Infra, C0:C1:C0:AC:A5:93, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    db7928:          Infra, E0:69:95:36:A9:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    Jilliian:        Infra, 00:25:5E:C2:19:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA

  IPv4 Settings:
    Address:         192.168.1.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             216.221.96.37
    DNS:             172.16.1.1
    DNS:             216.221.96.36
```

```

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FBI Surveillance van"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: C0:C1:C0:0D:03:90   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:42:21:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:ca:2a:a5  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5804 (5.8 KB)  TX bytes:14553 (14.5 KB)
```

```

sudo iwlist scan
[sudo] password for nathan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

```
lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
hid_apple              13124  0 
nvidia               9766978  38 
snd_hda_codec_hdmi     27535  4 
cfg80211              156212  2 rt2x00lib,mac80211
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
usbhid                 41704  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
hid                    77084  2 hid_apple,usbhid
ppdev                  12849  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
r8169                  42534  0 
```

---

### Post by doyleman on 2011-09-05
quick update: tried turning the power management for the wifi off, as per some users' suggestions on other topics; still no good. though, apparently the power management keeps turning back on upon restarting.

---

### Post by doyleman on 2011-09-05
sorry to double post, by the way. forgot i could edit. OT: bump.

---

### Post by wildmanne39 on 2011-09-05
Hi, please run this command with your wired connection disconnected.
```
sudo su
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
exit
```
Then
```
sudo modprobe rt2800usb
```
and it should be working if not post back and if you don't mind when we are done would you click on ubuntu membership in my signature and post there if you support me for ubuntu membership.
Thank you

---

### Post by doyleman on 2011-09-05
hi, wildmanne39, my linux is very new, but perchance did you mean to run:

sudo su
echo "blacklist 2870sta" >> /etc/modprobe.d/blacklist.conf ? from what i've seen in other posts, a 'blacklist' is usually thrown in front.

I did what you had originally said, but got a complaint about line 56 having the bad line starting with 'rt2870sta'; so i had tossed blacklist in front, and now it wont complain.
From there, I still remained to have problems, but remembered i needed to turn power management off for my wifi, manually, with:

sudo iwconfig wlan0 power off.

Might there be a way to have that automatically take effect upon logging in?

And certainly, I'd be glad to help you out with your membership :)

edit:
darn. it worked for a few minutes, now it's at dial-up speeds, and hangs again...

---

### Post by wildmanne39 on 2011-09-05
Hi, you are pretty sharp I did leave out blacklist I guess that that is what happens when I am in the ER until all most day break then up two hours later.

To make the power off persistent do this please:
```
gksu gedit /etc/pm/power.d/wireless
```
and then add
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
``` 
Then
```
sudo chmod +x /etc/pm/power.d/wireless
```
and it should be off for good.
Thank you

---

### Post by doyleman on 2011-09-05
> **wildmanne39 said:**
> Hi, you are pretty sharp I did leave out blacklist I guess that that is what happens when I am in the ER until all most day break then up two hours later.

To make the power off persistent do this please:
```
gksu gedit /etc/pm/power.d/wireless
```
and then add
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
``` 
Then
```
sudo chmod +x /etc/pm/power.d/wireless
```
and it should be off for good.
Thank you

Sorry to hear there are problems with you or another person you know. :(

Thank you for the commands for auto disabling the power config. Upon running all of your commands, the wifi will stay up and strong for around 10 seconds, and then it dies back down into terrible 31-44 bps connection, and break entire connection every 5 minutes; then reconnect. I wish I knew more about things so I could take a few swings at cracking this myself, but I'm too new to the whole linux system; I wouldn't know where to begin.
Any other ideas I could try, perhaps?

---

### Post by wildmanne39 on 2011-09-05
Hi, I have a few more things to check post the results of these commands please:
```
sudo iwlist scan
```
```
dmesg | grep rt2
```
```
lsmod | grep rt2
```
you are connecting to the FBI network correct?

---

### Post by doyleman on 2011-09-05
yes, I am connected to the fbi one, lol. my room mate decided to be funny with his ssid. I suppose I should correct my mistake above, in that it's not the issue that i'm in an apartment complex, more so that i'm a room mate and the direct connection is already taken, so we use wifi for the other devices. Anyway, here are the results:

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:5E:C2:19:8E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Jilliian"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000099706b73672
                    Extra: Last beacon: 1868ms ago
                    IE: Unknown: 00084A696C6C6969616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 02 - Address: C0:C1:C0:0D:03:90
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"FBI Surveillance van"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b9b25998be
                    Extra: Last beacon: 6088ms ago
                    IE: Unknown: 0014464249205375727665696C6C616E63652076616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B0001031047001026CF7621E95DE3C69522A3ECA909FA1810210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403080400000000000000000000000000000000000000
          Cell 03 - Address: C4:46:19:2C:F8:9F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"444a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ca89b523d
                    Extra: Last beacon: 7156ms ago
                    IE: Unknown: 000434343461
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

```
dmesg | grep rt2
[   10.937670] Registered led device: rt2800usb-phy0::radio
[   10.937689] Registered led device: rt2800usb-phy0::assoc
[   10.937708] Registered led device: rt2800usb-phy0::quality
[   10.948086] usbcore: registered new interface driver rt2800usb
```

```
lsmod | grep rt2
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
```

---

### Post by wildmanne39 on 2011-09-05
Hi, I just wanted to let you know I am research this so I will be back in a few minutes.
Thank you

---

### Post by doyleman on 2011-09-05
thank you for your extreme patience with me. i feel like i've been difficult. i have no rush on my end.

---

### Post by wildmanne39 on 2011-09-05
Hi, your welcome! and you have not been difficult I am here to help and when there are issues it challenges me to become better and that is good.

I believe this will fix the problem even though it says you should use the usb driver the 2870sta almost always works better even for usb devices so we are going to black list the usb drivers and load the sta driver.

Run this command please:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add a hash (#) mark in the beginning of any line which you want to disable (ineffective). So in your case, after opening that file with above command, look for the line that says blacklist rt2870sta(it would most probably be in the last) and add the '#' mark in its beginning. So now it should look like this:
> # blacklist rt2870
save and exit.

Then 
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then
```
sudo modprobe rt2870sta
```
that should fix it.
Thank you

---

### Post by doyleman on 2011-09-05
Yes, I believe that solution does work now. I seem to have a stable connection. :)

A new problem came up in that gnome starts up in a very aged look ( similar to windows 98 ), but fixes itself within seconds, then it takes about 30 seconds for the wireless panel/daemon to come up, and from there wireless seems to be disabled for 1 minute, and then it enables itself, and starts up.

I suppose I'd only like to know if it's possible to have the wireless start up any faster?
Thank you for all your help. I have cast a vote to your membership page, and wish you luck in that! :)

---

### Post by wildmanne39 on 2011-09-05
Hi, thank you I appreciate you voting for me.

I do not know of a way to make it faster but here is a link for the theme issue.

Maybe it will help the starting up of your wireless faster if it is being slowed down by the theme issue.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)
Thank you

---

### Post by nm_geo on 2011-09-05
> **doyleman said:**
> Yes, I believe that solution does work now. I seem to have a stable connection. :)

A new problem came up in that gnome starts up in a very aged look ( similar to windows 98 ), but fixes itself within seconds, then it takes about 30 seconds for the wireless panel/daemon to come up, and from there wireless seems to be disabled for 1 minute, and then it enables itself, and starts up.

I suppose I'd only like to know if it's possible to have the wireless start up any faster?
Thank you for all your help. I have cast a vote to your membership page, and wish you luck in that! :)

Been following this link and would like to see 

```
sudo iwconfig 
```Again and 

```
sudo iwlist scan
```wildmanne has done a good job here and I did not want to disturb..

---

### Post by doyleman on 2011-09-05
Thanks for the link, wildmanne39, I have applied that modification just now. I'm confident that it will fix the theme issue.

hello nm_geo; sure. here are my results:

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"FBI Surveillance van"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: C0:C1:C0:0D:03:90   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:-------------------------
          Link Quality=90/100  Signal level:-41 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:4E:20:D3:93
                    Protocol:802.11b/g
                    ESSID:"79ae"
                    Mode:Managed
                    Channel:1
                    Quality:42/100  Signal level:-73 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 02 - Address: C4:46:19:2C:F8:9F
                    Protocol:802.11b/g
                    ESSID:"444a"
                    Mode:Managed
                    Channel:1
                    Quality:52/100  Signal level:-69 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:1E:4C:9D:FD:CD
                    Protocol:802.11b/g
                    ESSID:"334a"
                    Mode:Managed
                    Channel:1
                    Quality:31/100  Signal level:-77 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:22:68:A0:12:6E
                    Protocol:802.11b/g
                    ESSID:"bf83"
                    Mode:Managed
                    Channel:1
                    Quality:47/100  Signal level:-71 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 05 - Address: C0:C1:C0:AC:A5:93
                    Protocol:802.11b/g/n
                    ESSID:"sammylou"
                    Mode:Managed
                    Channel:6
                    Quality:37/100  Signal level:-75 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 98:FC:11:47:20:B7
                    Protocol:802.11b/g
                    ESSID:"LinksysAB"
                    Mode:Managed
                    Channel:6
                    Quality:31/100  Signal level:-77 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: E0:69:95:36:A9:12
                    Protocol:802.11b/g/n
                    ESSID:"db7928"
                    Mode:Managed
                    Channel:6
                    Quality:18/100  Signal level:-83 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 80:A1:D7:0A:A2:96
                    Protocol:802.11b/g/n
                    ESSID:"Wally"
                    Mode:Managed
                    Channel:6
                    Quality:23/100  Signal level:-81 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by nm_geo on 2011-09-05
Good strong signal and Bit rate

Bit Rate=54 Mb/s              
RTS thr:off   Fragment thr:off
Encryption key:xxxxxxxxxxxxxxxxxxxxxxx
Link Quality=90/100  Signal level:-41 dBm  Noise level:-83 dBm

You are Golden..

---

### Post by wildmanne39 on 2011-09-05
Yes in deed it looks good.

---

### Post by doyleman on 2011-09-05
thanks both for your help, it is working fully now! :D

---

### Post by wildmanne39 on 2011-09-05
Hi, I am glad we could help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

