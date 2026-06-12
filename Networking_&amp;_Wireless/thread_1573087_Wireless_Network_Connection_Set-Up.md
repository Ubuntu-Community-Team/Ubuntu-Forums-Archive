---
title: "Wireless Network Connection Set-Up"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by electrox73 on 2010-09-12
Hi, I can't find a way how to connect to my Wi-Fi from Ubuntu, but my Vista does it well...
I have found many ways to do it, but none worked. I am a extreme begginer in Ubuntu.

Regards

---

### Post by MaindotC on 2010-09-12
Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.

---

### Post by miyu123 on 2010-09-12
I'm new to Ubuntu and I have a similar problem. Any help is highly appreciated. I installed  Ubuntu 10.4 and used Update Manager to get any missed updates on an old Gateway laptop and it looks great. I can't seem to get my Wifi connection working. The wired connection works fine, but the wifi gives me headaches. My Network Manager reads all the available networks in range, but it won't connect to any. I used the instructions in the Ubuntu Wireless Troubleshooting Guide. I ran the nm-  tool, lshw -C network, and then the lshw command. It looks like a driver is installed. Then I ran the lsmod to see if driver is loaded and it looks like it to me- I see it listed a few times. Anyway, next I ran sudo iwconfig and this is where I am stuck, because it looks like the driver is not identifying the device as a wireless device to the kernel ( whatever that means) and I don't know what to do next.

I pasted below the results of the commands I ran.
If someone could point me in the right direction, I'd appreciated. 
Thanks,
Miyu


miyu@ubuntu-rocks:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:E0:B8:53:87:25

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:B0:3C:C3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    ifysco45:        Infra, 00:23:69:52:16:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    linksys:         Infra, 00:18:39:73:71:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 58
    USR5461:         Infra, 00:14:C1:0B:02:14, Freq 2462 MHz, Rate 54 Mb/s, Strength 88
    Backupoffme:     Infra, 00:23:69:03:A5:45, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Fat boy:         Infra, 00:16:B6:23:88:4E, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA
    Dandis Home:     Infra, 00:22:75:E6:16:8D, Freq 2412 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    ARJU:            Infra, 00:18:E7:C5:C1:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA


miyu@ubuntu-rocks:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:e0:b8:53:87:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:10 memory:e8207000-e8207fff ioport:5c00(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:b0:3c:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
miyu@ubuntu-rocks:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
michael_mic             1732  4 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126517  1 orinoco
snd_maestro3           15898  2 
snd_ac97_codec        100646  1 snd_maestro3
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
pcmcia                 33024  1 orinoco_cs
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm                70662  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  1 snd_pcm
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                674824  4 
ttm                    49943  1 radeon
snd                    54148  14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 radeon
yenta_socket           20408  5 
ppdev                   5259  0 
drm                   162409  6 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24119  1 
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,intel_agp
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
e100                   28211  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 e100
floppy                 53016  0 
miyu@ubuntu-rocks:~$ sudo iwconfig
[sudo] password for miyu: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:219
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0
miyu@ubuntu-rocks:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
michael_mic             1732  4 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126517  1 orinoco
snd_maestro3           15898  2 
snd_ac97_codec        100646  1 snd_maestro3
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
pcmcia                 33024  1 orinoco_cs
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm                70662  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  1 snd_pcm
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                674824  4 
ttm                    49943  1 radeon
snd                    54148  14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 radeon
yenta_socket           20408  5 
ppdev                   5259  0 
drm                   162409  6 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24119  1 
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,intel_agp
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
e100                   28211  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 e100
floppy                 53016  0 
miyu@ubuntu-rocks:~$ sudo iwconfig
[sudo] password for miyu: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:256
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

miyu@ubuntu-rocks:~$

---

### Post by MaindotC on 2010-09-12
Thank you so much for following the guide and replying with relevant information - that tells me you actually looked at it.  +1 for you!  

As you can see, your wireless card is definitely detected so we know it's not a hardware issue:
```
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:b0:3c:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes [SIZE="6"]driver=orinoco [/SIZE]driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
```

However, I haven't seen that card before and I'm not sure if that is the proper driver.  You'll have to determine if it is by searching a little more on the orinoco driver.

Here you can definitely see, as you stated, that the driver (or module) is in use:```

miyu@ubuntu-rocks:~$ lsmod
Module                  Size  Used by
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126517  1 orinoco
orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

And here we can see it's not associated with an access point:```
eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:256
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

```

It looks to me like you have everything you can at this point.  If you cannot connect to an AP then you can't use dhclient to request an ip address and other information so right now you need to work on getting your card associated to the AP.  You can try it via command line with the directions in the guide (just skip to the iwconfig section).

Find out more on that driver (see if they have a supported hardware list) and then if you're sure you have the right driver then try connecting using iwconfig.

---

### Post by electrox73 on 2010-09-14
> **strAlan said:**
> Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.

Thanks but as I tryed, I can't even connect to LAN (wired)!
So I have no Internet acces on my Ubuntu OS. And I have a HP Pavilion dv7 1130-eg, and I have touch buttons above the keyboard, and one is a Wi-Fi button that can disable/enable the wireless card, it is always blue (enabled) on Vista and if it is red (disabled), I enable it by a single tap. But on Ubuntu, I always get the button red and can't make it blue, but all other buttons work, such as mute and so...can it still be something whith the wireless card, even if LAN doesn't work? PS: when I try to connect in any way, it says disconected instead of connect, always when i try to connect, after like 2 minutes, it says disconnected.

---

