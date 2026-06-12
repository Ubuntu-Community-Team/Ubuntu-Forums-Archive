---
title: "Wireless: &quot;Wireless is disabled&quot;"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by And1945 on 2010-04-11
Hello,

Even though I have 10.04 beta 2, I do not believe that, that would be an issue. I had the same problem with 9.10 and 9.04.

There seems to be some issues with wireless drivers lately. I have grepped my system wifi, and it actually says that the unit is:

```
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:23:4D:CC:55:0A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:23:8B:14:DB:1C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```

And my lsmod

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
radeon                673532  0 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
drm                   162599  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd_hda_codec_atihdmi     2367  1 
arc4                    1153  2 
snd_hda_codec_idt      51914  1 
snd_hda_intel          21781  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121824  0 
joydev                  8708  0 
mac80211              204470  1 ath5k
ath                     7611  1 ath5k
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
lirc_ene0100            6536  0 
lirc_dev                8884  1 lirc_ene0100
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
jmb38x_ms               7311  0 
video                  17375  0 
output                  1871  1 video
cfg80211              126517  3 ath5k,mac80211,ath
hp_accel               11144  0 
lis3lv02d               6007  1 hp_accel
input_polldev           2482  1 lis3lv02d
fglrx                2091788  0 
psmouse                62957  0 
serio_raw               3978  0 
lp                      7028  0 
memstick                8237  1 jmb38x_ms
soundcore               6620  1 snd
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 ath5k,hp_accel,sdhci
i2c_piix4               8335  0 
agpgart                31724  3 ttm,drm,fglrx
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
ohci1394               27174  0 
r8169                  34172  0 
ieee1394               81277  1 ohci1394
pata_atiixp             3148  0 
mii                     4381  1 r8169
ahci                   31912  3 

```

Default: no

Well, how do I set it to be enabled pr. default?

From my "sudo lshw -enable pci"

```
*-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:d1200000-d12fffff
           *-network DISABLED
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:4d:cc:55:0a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d1200000-d120ffff

```

---

### Post by chili555 on 2010-04-11
What does this tell us?```
rfkill list
```Thanks.

---

### Post by And1945 on 2010-04-11
> **chili555 said:**
> What does this tell us?```
rfkill list
```Thanks.

That it has been hard blocked.

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

---

### Post by chili555 on 2010-04-11
> Hard blocked: yesThat suggests that the wireless button is not switched on. Please manipulate the button at the upper right and see if you can get it unblocked.

---

### Post by Edge-1337 on 2010-04-22
I have the same problem, with the same WiFi Card.

Says it's hard blocked. The WiFi button does nothing, the LED's indicate that WiFi is off. So how do I fix this? It worked on Vista now it will not work in Linux. I can not get the button to turn WiFi on.

---

### Post by ed-rapley on 2010-05-25
Take a look at this thread, with posts 3 and four, i got my fujitsu amilo wifi working.

[http://ubuntuforums.org/showthread.php?p=9354354#post9354354](http://ubuntuforums.org/showthread.php?p=9354354#post9354354)

good luck.

---

### Post by spartahawk on 2011-03-01
*POTENTIAL SOLUTION*   (WORKED FOR ME)
After looking all over and finding nothing that would work, I found this, and
IT FINALLY WORKED!!!

**[B]Open the terminal (under Applications>Accessories>) and type**
[/B]

**rfkill list all**



You should see both the soft(ware) blocked and hard(ware) blocked  as  no. If either of them is yes then the connection would not be enabled.  To enable type the following
 
**rfkill unblock wifi**

Found this solution at:
[http://vikashazrati.wordpress.com/2011/02/10/ubuntu-10-10-network-adapter-shows-wireless-disabled/](http://vikashazrati.wordpress.com/2011/02/10/ubuntu-10-10-network-adapter-shows-wireless-disabled/)

---

### Post by toron on 2011-08-20
I had the same problem with Dell XPS M1330, Ubuntu 10.04 that I could not connect with Wireless and the Wireless with "rfkill list" was hardblocked. I could not solve the poblem with: rfkill unblock wifi

The cause of the problem was that I had used the battery and Ubuntu had disabled the Wireless to save energy. Then I could not connect to the Wireless eventhough I was not using the battery anymore.

The solution for me was to go to the BIOS and set that the "Wireless Switch" cannot manage the "Wireless", "Bluetooth", etc. Probably by this way, Ubuntu could not disable the Wireless anymore.

---

