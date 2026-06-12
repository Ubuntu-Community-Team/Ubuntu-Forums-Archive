---
title: "Help me prevent my IBM T60 from disconnecting"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by taste of mint on 2011-08-08
Hi I have a problem with an IBM Thinkpad T60, its a 2007 model. The wireless keeps alive for about 20 seconds then it disconnects, then i have to turn the wireless off and on again then it works for another 20 seconds. I think its the wrong driver or something.

I have the Ubuntu 10.4 version and I have almost no experience with linux so I have no idea how to fix it.
There are about 100 threads thaqt turns up when I search for T60 and I don't know where to start. All I know it seems like a fairly popular computer so I guess someone must have had the same problem before.

First I need to find out what wlan card I have, I guess. And I don't know how to do that yet.
I tried Mint 9 too and its the same problem. :(

---

### Post by wildmanne39 on 2011-08-08
Hi, please run these commands in a terminal:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by taste of mint on 2011-08-09
[SIZE=2]Ok here we go I'm typing this form another computer since the other one cannot be used on the internet yet.

[/SIZE]```
xxx@xxx:~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: numbers
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: numbers
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.83 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:edf00000-edf00fff
xxx@xxx:~$ 

```

```
xxx@xxx:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
xxx@xxx:~$

```

(Its red in the brackets [280])


```
xxx@xxx:~$ iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"xxx"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: numbers   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xxx@xxx:~$ 

and when its turned off/disconnected

iwconfig 


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


```

xxx@xxx:~$ lsmod
Module                  Size  Used by
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_analog    58598  1 
snd_hda_intel          21941  2 
pcmcia                 33024  0 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
thinkpad_acpi          68083  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwl3945                68727  0 
iwlcore               105922  1 iwl3945
mac80211              205146  2 iwl3945,iwlcore
led_class               2864  3 thinkpad_acpi,iwl3945,iwlcore
lp                      7028  0 
psmouse                63245  0 
nvram                   6171  1 thinkpad_acpi
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126517  3 iwl3945,iwlcore,mac80211
parport                32635  2 ppdev,lp
sha256_generic         11191  4 
aes_i586                7268  238 
aes_generic            26863  1 aes_i586
dm_crypt               11331  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                674824  3 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
intel_agp              24119  0 
ahci                   32200  2 
drm                   162377  5 radeon,ttm,drm_kms_helper
video                  17375  0 
output                  1871  1 video
e1000e                119824  0 
agpgart                31724  3 ttm,intel_agp,drm
i2c_algo_bit            5028  1 radeon
xxx@xxx:~$ 
```

I also have some type of graphics artifacts and I have read these are common, the graphics card is the X1300, but thats a minor problem and I'll try to find out how to fix that my self later today.

---

### Post by wildmanne39 on 2011-08-09
Hi,try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig iwlagn up

```
if this works we will need to write a config file to make it persistent.
Thank you

---

### Post by taste of mint on 2011-08-09
> **wildmanne39 said:**
> Hi,try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig iwlagn up

```if this works we will need to write a config file to make it persistent.
Thank you

After I typed rmmod -f iwlagn
it says ERROR: removing 'iwlagn': No such file or directory.

I still went ahead with the rest of them and on the last one "iwlagn up"
I says 

iwlagn: ERROR while getting interface flags: No such device

---

### Post by taste of mint on 2011-08-09
I can also confirm that it still disconnects. If I let the computer sit idle not using the internet it never seems to cut the connection but as soon as I start using a browser and click around to generate som traffic it disconnects, could be anything from 5 sec to 1 min. And it does not automatically reconnect its just tries and tries (that little symbol) but it never actually makes it until I manually turn of wlan and then on again.
Until it gives up trying.

It the best description of the problem I can give. As soon as some traffic is generated it won't take long before it shuts down.

---

### Post by wildmanne39 on 2011-08-09
Hi,post the results of these commands please:
```
dmesg | grep wlan0
```
```
dmesg | grep iwl
```
```
lsmod | grep iwl
```
```
sudo iwlist scan
```
```
nm-tool
```
Thank you

---

### Post by taste of mint on 2011-08-09
first one 

```
grep wlan0
[  786.265254] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  796.601073] wlan0: deauthenticating from xxxxxxxxxx by local choice (reason=3)
[  796.602467] wlan0: direct probe to AP xxxxxxxxxxx (try 1)
[  796.606070] wlan0: direct probe responded
[  796.606077] wlan0: authenticate with xxxxxxxxxxxxxx (try 1)
[  796.607826] wlan0: authenticated
[  796.607843] wlan0: associate with AP xxxxxxxxxxxxxx (try 1)
[  796.611432] wlan0: RX AssocResp from xxxxxxxxxxxxx (capab=0x431 status=0 aid=4)
[  796.611437] wlan0: associated
[  796.623151] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  806.896040] wlan0: no IPv6 routers present
[  889.564155] wlan0: deauthenticating from xxxxxxxxxxxx by local choice (reason=3)
[  905.409351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  966.202263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  972.422378] wlan0: direct probe to AP xxxxxxxxxxxxx (try 1)
[  972.426249] wlan0: direct probe responded
[  972.426257] wlan0: authenticate with AP xxxxxxxxxxxxxx (try 1)
[  972.427970] wlan0: authenticated
[  972.428248] wlan0: associate with AP xxxxxxxxxxxxxxx (try 1)
[  972.431603] wlan0: RX AssocResp from xxxxxxxxxxxxxxxx (capab=0x431 status=0 aid=4)
[  972.431611] wlan0: associated
[  972.443447] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  983.228066] wlan0: no IPv6 routers present
[ 5792.706203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5824.107017] wlan0: deauthenticating from xxxxxxxxxxxxxx by local choice (reason=3)
[ 5824.107101] wlan0: direct probe to AP xxxxxxxxxxxxxxxx (try 1)
[ 5824.111423] wlan0: direct probe responded
[ 5824.111431] wlan0: authenticate with AP xxxxxxxxxxxxxxxxxx (try 1)
[ 5824.115924] wlan0: authenticated
[ 5824.115961] wlan0: associate with AP xxxxxxxxxxxxxxxxxxx (try 1)
[ 5824.119379] wlan0: RX AssocResp from xxxxxxxxxxxxxxxxx (capab=0x431 status=0 aid=1)
[ 5824.119386] wlan0: associated
[ 5824.130341] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5834.504058] wlan0: no IPv6 routers present
```

second one 

```
dmesg | grep iwl

[ 1947.345246] iwl3945 0000:03:00.0: No space for Tx
[ 1947.345252] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1947.345258] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1947.345264] iwl3945 0000:03:00.0: No space for Tx
[ 1947.345269] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1947.345275] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1947.345287] iwl3945 0000:03:00.0: No space for Tx
[ 1947.345293] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1952.348103] iwl3945 0000:03:00.0: No space for Tx
[ 1952.348115] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1952.348122] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1952.348170] iwl3945 0000:03:00.0: No space for Tx
[ 1952.348178] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1952.348194] iwl3945 0000:03:00.0: No space for Tx
[ 1952.348199] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1952.348205] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1952.348212] iwl3945 0000:03:00.0: No space for Tx
[ 1952.348217] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1952.348223] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1952.348235] iwl3945 0000:03:00.0: No space for Tx
[ 1952.348241] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1957.353665] iwl3945 0000:03:00.0: No space for Tx
[ 1957.353676] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1957.353683] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1957.353731] iwl3945 0000:03:00.0: No space for Tx
[ 1957.353739] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1957.353756] iwl3945 0000:03:00.0: No space for Tx
[ 1957.353762] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1957.353768] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1957.353774] iwl3945 0000:03:00.0: No space for Tx
[ 1957.353780] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1957.353786] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1957.353800] iwl3945 0000:03:00.0: No space for Tx
[ 1957.353806] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1962.359254] iwl3945 0000:03:00.0: No space for Tx
[ 1962.359266] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1962.359273] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1962.359319] iwl3945 0000:03:00.0: No space for Tx
[ 1962.359328] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1962.359343] iwl3945 0000:03:00.0: No space for Tx
[ 1962.359349] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1962.359355] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1962.359361] iwl3945 0000:03:00.0: No space for Tx
[ 1962.359367] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1962.359373] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1962.359385] iwl3945 0000:03:00.0: No space for Tx
[ 1962.359391] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1967.364813] iwl3945 0000:03:00.0: No space for Tx
[ 1967.364825] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1967.364831] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1967.364878] iwl3945 0000:03:00.0: No space for Tx
[ 1967.364886] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1967.364902] iwl3945 0000:03:00.0: No space for Tx
[ 1967.364907] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1967.364914] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1967.364920] iwl3945 0000:03:00.0: No space for Tx
[ 1967.364925] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1967.364931] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1967.364943] iwl3945 0000:03:00.0: No space for Tx
[ 1967.364949] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1972.370246] iwl3945 0000:03:00.0: No space for Tx
[ 1972.370258] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1972.370265] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1972.370312] iwl3945 0000:03:00.0: No space for Tx
[ 1972.370321] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1972.370337] iwl3945 0000:03:00.0: No space for Tx
[ 1972.370342] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1972.370349] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1972.370355] iwl3945 0000:03:00.0: No space for Tx
[ 1972.370360] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1972.370366] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1972.370378] iwl3945 0000:03:00.0: No space for Tx
[ 1972.370384] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1977.375684] iwl3945 0000:03:00.0: No space for Tx
[ 1977.375696] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1977.375702] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1977.375749] iwl3945 0000:03:00.0: No space for Tx
[ 1977.375758] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1977.375774] iwl3945 0000:03:00.0: No space for Tx
[ 1977.375779] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1977.375785] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1977.375792] iwl3945 0000:03:00.0: No space for Tx
[ 1977.375797] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1977.375803] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1977.375815] iwl3945 0000:03:00.0: No space for Tx
[ 1977.375821] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 1982.379491] iwl3945 0000:03:00.0: No space for Tx
[ 1982.379503] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1982.379509] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1982.379557] iwl3945 0000:03:00.0: No space for Tx
[ 1982.379565] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 1982.379581] iwl3945 0000:03:00.0: No space for Tx
[ 1982.379587] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1982.379593] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1982.379600] iwl3945 0000:03:00.0: No space for Tx
[ 1982.379605] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 1982.379611] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 1982.379624] iwl3945 0000:03:00.0: No space for Tx
[ 1982.379630] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2106.119956] iwl3945 0000:03:00.0: No space for Tx
[ 2106.119966] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2106.119973] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2106.120342] iwl3945 0000:03:00.0: No space for Tx
[ 2106.120349] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2106.120365] iwl3945 0000:03:00.0: No space for Tx
[ 2106.120370] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2106.120376] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2106.120383] iwl3945 0000:03:00.0: No space for Tx
[ 2106.120388] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2106.120394] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2106.120406] iwl3945 0000:03:00.0: No space for Tx
[ 2106.120412] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2226.118407] iwl3945 0000:03:00.0: No space for Tx
[ 2226.118418] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2226.118424] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2226.118476] iwl3945 0000:03:00.0: No space for Tx
[ 2226.118482] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2226.118497] iwl3945 0000:03:00.0: No space for Tx
[ 2226.118503] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2226.118509] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2226.118515] iwl3945 0000:03:00.0: No space for Tx
[ 2226.118520] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2226.118526] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2226.118539] iwl3945 0000:03:00.0: No space for Tx
[ 2226.118545] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2346.117556] iwl3945 0000:03:00.0: No space for Tx
[ 2346.117567] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2346.117574] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2346.117734] iwl3945 0000:03:00.0: No space for Tx
[ 2346.117741] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2346.117755] iwl3945 0000:03:00.0: No space for Tx
[ 2346.117761] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2346.117767] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2346.117773] iwl3945 0000:03:00.0: No space for Tx
[ 2346.117779] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2346.117785] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2346.117797] iwl3945 0000:03:00.0: No space for Tx
[ 2346.117803] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2466.114588] iwl3945 0000:03:00.0: No space for Tx
[ 2466.114597] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2466.114604] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2466.114656] iwl3945 0000:03:00.0: No space for Tx
[ 2466.114663] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2466.114677] iwl3945 0000:03:00.0: No space for Tx
[ 2466.114683] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2466.114689] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2466.114695] iwl3945 0000:03:00.0: No space for Tx
[ 2466.114700] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2466.114706] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2466.114719] iwl3945 0000:03:00.0: No space for Tx
[ 2466.114725] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2586.117819] iwl3945 0000:03:00.0: No space for Tx
[ 2586.117829] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2586.117835] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2586.117887] iwl3945 0000:03:00.0: No space for Tx
[ 2586.117893] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2586.117908] iwl3945 0000:03:00.0: No space for Tx
[ 2586.117913] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2586.117919] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2586.117925] iwl3945 0000:03:00.0: No space for Tx
[ 2586.117931] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2586.117937] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2586.117949] iwl3945 0000:03:00.0: No space for Tx
[ 2586.117955] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2706.114808] iwl3945 0000:03:00.0: No space for Tx
[ 2706.114819] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2706.114826] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2706.114869] iwl3945 0000:03:00.0: No space for Tx
[ 2706.114877] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2706.114894] iwl3945 0000:03:00.0: No space for Tx
[ 2706.114900] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2706.114906] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2706.114913] iwl3945 0000:03:00.0: No space for Tx
[ 2706.114918] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2706.114924] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2706.114936] iwl3945 0000:03:00.0: No space for Tx
[ 2706.114942] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2826.114416] iwl3945 0000:03:00.0: No space for Tx
[ 2826.114426] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2826.114433] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2826.114483] iwl3945 0000:03:00.0: No space for Tx
[ 2826.114489] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2826.114504] iwl3945 0000:03:00.0: No space for Tx
[ 2826.114510] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2826.114516] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2826.114522] iwl3945 0000:03:00.0: No space for Tx
[ 2826.114527] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2826.114533] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2826.114545] iwl3945 0000:03:00.0: No space for Tx
[ 2826.114551] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 2946.119300] iwl3945 0000:03:00.0: No space for Tx
[ 2946.119311] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2946.119317] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2946.119381] iwl3945 0000:03:00.0: No space for Tx
[ 2946.119388] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 2946.119402] iwl3945 0000:03:00.0: No space for Tx
[ 2946.119408] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2946.119414] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2946.119420] iwl3945 0000:03:00.0: No space for Tx
[ 2946.119425] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 2946.119431] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 2946.119445] iwl3945 0000:03:00.0: No space for Tx
[ 2946.119451] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3066.117128] iwl3945 0000:03:00.0: No space for Tx
[ 3066.117136] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3066.117140] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3066.117175] iwl3945 0000:03:00.0: No space for Tx
[ 3066.117179] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3066.117188] iwl3945 0000:03:00.0: No space for Tx
[ 3066.117191] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3066.117194] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3066.117197] iwl3945 0000:03:00.0: No space for Tx
[ 3066.117200] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3066.117204] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3066.117212] iwl3945 0000:03:00.0: No space for Tx
[ 3066.117215] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3186.117912] iwl3945 0000:03:00.0: No space for Tx
[ 3186.117922] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3186.117929] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3186.117990] iwl3945 0000:03:00.0: No space for Tx
[ 3186.117996] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3186.118011] iwl3945 0000:03:00.0: No space for Tx
[ 3186.118017] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3186.118023] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3186.118029] iwl3945 0000:03:00.0: No space for Tx
[ 3186.118035] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3186.118041] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3186.118053] iwl3945 0000:03:00.0: No space for Tx
[ 3186.118059] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3306.119779] iwl3945 0000:03:00.0: No space for Tx
[ 3306.119789] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3306.119796] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3306.119845] iwl3945 0000:03:00.0: No space for Tx
[ 3306.119852] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3306.119866] iwl3945 0000:03:00.0: No space for Tx
[ 3306.119872] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3306.119878] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3306.119884] iwl3945 0000:03:00.0: No space for Tx
[ 3306.119889] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3306.119895] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3306.119908] iwl3945 0000:03:00.0: No space for Tx
[ 3306.119913] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3426.117820] iwl3945 0000:03:00.0: No space for Tx
[ 3426.117831] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3426.117837] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3426.117895] iwl3945 0000:03:00.0: No space for Tx
[ 3426.117902] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3426.117917] iwl3945 0000:03:00.0: No space for Tx
[ 3426.117922] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3426.117928] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3426.117934] iwl3945 0000:03:00.0: No space for Tx
[ 3426.117939] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3426.117945] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3426.117958] iwl3945 0000:03:00.0: No space for Tx
[ 3426.117964] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3546.117263] iwl3945 0000:03:00.0: No space for Tx
[ 3546.117273] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3546.117279] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3546.117330] iwl3945 0000:03:00.0: No space for Tx
[ 3546.117336] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3546.117351] iwl3945 0000:03:00.0: No space for Tx
[ 3546.117357] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3546.117363] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3546.117369] iwl3945 0000:03:00.0: No space for Tx
[ 3546.117374] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3546.117380] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3546.117392] iwl3945 0000:03:00.0: No space for Tx
[ 3546.117397] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3666.117062] iwl3945 0000:03:00.0: No space for Tx
[ 3666.117073] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3666.117080] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3666.117131] iwl3945 0000:03:00.0: No space for Tx
[ 3666.117138] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3666.117152] iwl3945 0000:03:00.0: No space for Tx
[ 3666.117158] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3666.117164] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3666.117170] iwl3945 0000:03:00.0: No space for Tx
[ 3666.117175] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3666.117181] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3666.117223] iwl3945 0000:03:00.0: No space for Tx
[ 3666.117229] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3786.115062] iwl3945 0000:03:00.0: No space for Tx
[ 3786.115072] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3786.115079] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3786.115129] iwl3945 0000:03:00.0: No space for Tx
[ 3786.115135] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3786.115150] iwl3945 0000:03:00.0: No space for Tx
[ 3786.115155] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3786.115161] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3786.115167] iwl3945 0000:03:00.0: No space for Tx
[ 3786.115172] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3786.115178] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3786.115190] iwl3945 0000:03:00.0: No space for Tx
[ 3786.115196] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 3906.119184] iwl3945 0000:03:00.0: No space for Tx
[ 3906.119195] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3906.119201] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3906.119264] iwl3945 0000:03:00.0: No space for Tx
[ 3906.119271] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 3906.119286] iwl3945 0000:03:00.0: No space for Tx
[ 3906.119291] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3906.119297] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3906.119303] iwl3945 0000:03:00.0: No space for Tx
[ 3906.119309] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3906.119314] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 3906.119330] iwl3945 0000:03:00.0: No space for Tx
[ 3906.119336] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4026.116885] iwl3945 0000:03:00.0: No space for Tx
[ 4026.116896] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4026.116902] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4026.116979] iwl3945 0000:03:00.0: No space for Tx
[ 4026.116985] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4026.117000] iwl3945 0000:03:00.0: No space for Tx
[ 4026.117009] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4026.117015] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4026.117021] iwl3945 0000:03:00.0: No space for Tx
[ 4026.117026] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4026.117032] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4026.117044] iwl3945 0000:03:00.0: No space for Tx
[ 4026.117050] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4146.116833] iwl3945 0000:03:00.0: No space for Tx
[ 4146.116843] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4146.116850] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4146.116902] iwl3945 0000:03:00.0: No space for Tx
[ 4146.116908] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4146.116949] iwl3945 0000:03:00.0: No space for Tx
[ 4146.116954] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4146.116960] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4146.116967] iwl3945 0000:03:00.0: No space for Tx
[ 4146.116972] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4146.116978] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4146.116990] iwl3945 0000:03:00.0: No space for Tx
[ 4146.116996] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4266.118804] iwl3945 0000:03:00.0: No space for Tx
[ 4266.118814] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4266.118821] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4266.118880] iwl3945 0000:03:00.0: No space for Tx
[ 4266.118887] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4266.118902] iwl3945 0000:03:00.0: No space for Tx
[ 4266.118907] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4266.118913] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4266.118919] iwl3945 0000:03:00.0: No space for Tx
[ 4266.118924] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4266.118930] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4266.118943] iwl3945 0000:03:00.0: No space for Tx
[ 4266.118949] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4386.117788] iwl3945 0000:03:00.0: No space for Tx
[ 4386.117798] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4386.117805] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4386.117965] iwl3945 0000:03:00.0: No space for Tx
[ 4386.117973] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4386.117990] iwl3945 0000:03:00.0: No space for Tx
[ 4386.117996] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4386.118002] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4386.118008] iwl3945 0000:03:00.0: No space for Tx
[ 4386.118013] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4386.118019] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4386.118031] iwl3945 0000:03:00.0: No space for Tx
[ 4386.118037] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4506.116842] iwl3945 0000:03:00.0: No space for Tx
[ 4506.116853] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4506.116859] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4506.116910] iwl3945 0000:03:00.0: No space for Tx
[ 4506.116917] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4506.116931] iwl3945 0000:03:00.0: No space for Tx
[ 4506.116937] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4506.116943] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4506.116949] iwl3945 0000:03:00.0: No space for Tx
[ 4506.116954] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4506.116960] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4506.116972] iwl3945 0000:03:00.0: No space for Tx
[ 4506.116978] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4626.117459] iwl3945 0000:03:00.0: No space for Tx
[ 4626.117470] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4626.117476] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4626.117507] iwl3945 0000:03:00.0: No space for Tx
[ 4626.117515] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4626.117533] iwl3945 0000:03:00.0: No space for Tx
[ 4626.117538] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4626.117545] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4626.117551] iwl3945 0000:03:00.0: No space for Tx
[ 4626.117556] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4626.117562] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4626.117574] iwl3945 0000:03:00.0: No space for Tx
[ 4626.117580] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4746.116983] iwl3945 0000:03:00.0: No space for Tx
[ 4746.116993] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4746.117000] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4746.117080] iwl3945 0000:03:00.0: No space for Tx
[ 4746.117090] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4746.117107] iwl3945 0000:03:00.0: No space for Tx
[ 4746.117115] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4746.117123] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4746.117131] iwl3945 0000:03:00.0: No space for Tx
[ 4746.117138] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4746.117145] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4746.117159] iwl3945 0000:03:00.0: No space for Tx
[ 4746.117167] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4866.117898] iwl3945 0000:03:00.0: No space for Tx
[ 4866.117908] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4866.117915] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4866.117966] iwl3945 0000:03:00.0: No space for Tx
[ 4866.117972] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4866.117987] iwl3945 0000:03:00.0: No space for Tx
[ 4866.117992] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4866.117998] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4866.118004] iwl3945 0000:03:00.0: No space for Tx
[ 4866.118009] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4866.118015] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4866.118027] iwl3945 0000:03:00.0: No space for Tx
[ 4866.118033] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 4986.117889] iwl3945 0000:03:00.0: No space for Tx
[ 4986.117899] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4986.117905] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4986.117956] iwl3945 0000:03:00.0: No space for Tx
[ 4986.117962] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4986.117977] iwl3945 0000:03:00.0: No space for Tx
[ 4986.117982] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4986.117988] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4986.117994] iwl3945 0000:03:00.0: No space for Tx
[ 4986.118000] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4986.118006] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 4986.118017] iwl3945 0000:03:00.0: No space for Tx
[ 4986.118023] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5106.119124] iwl3945 0000:03:00.0: No space for Tx
[ 5106.119134] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5106.119141] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5106.119191] iwl3945 0000:03:00.0: No space for Tx
[ 5106.119198] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5106.119212] iwl3945 0000:03:00.0: No space for Tx
[ 5106.119218] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5106.119224] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5106.119230] iwl3945 0000:03:00.0: No space for Tx
[ 5106.119235] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5106.119241] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5106.119253] iwl3945 0000:03:00.0: No space for Tx
[ 5106.119259] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5226.119066] iwl3945 0000:03:00.0: No space for Tx
[ 5226.119077] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5226.119083] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5226.119136] iwl3945 0000:03:00.0: No space for Tx
[ 5226.119142] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5226.119157] iwl3945 0000:03:00.0: No space for Tx
[ 5226.119162] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5226.119168] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5226.119174] iwl3945 0000:03:00.0: No space for Tx
[ 5226.119180] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5226.119186] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5226.119198] iwl3945 0000:03:00.0: No space for Tx
[ 5226.119204] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5346.116268] iwl3945 0000:03:00.0: No space for Tx
[ 5346.116279] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5346.116286] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5346.116317] iwl3945 0000:03:00.0: No space for Tx
[ 5346.116325] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5346.116342] iwl3945 0000:03:00.0: No space for Tx
[ 5346.116348] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5346.116354] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5346.116361] iwl3945 0000:03:00.0: No space for Tx
[ 5346.116366] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5346.116372] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5346.116386] iwl3945 0000:03:00.0: No space for Tx
[ 5346.116392] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5466.116878] iwl3945 0000:03:00.0: No space for Tx
[ 5466.116888] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5466.116894] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5466.116952] iwl3945 0000:03:00.0: No space for Tx
[ 5466.116958] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5466.116973] iwl3945 0000:03:00.0: No space for Tx
[ 5466.116978] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5466.116984] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5466.116990] iwl3945 0000:03:00.0: No space for Tx
[ 5466.116996] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5466.117002] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5466.117019] iwl3945 0000:03:00.0: No space for Tx
[ 5466.117024] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5586.115646] iwl3945 0000:03:00.0: No space for Tx
[ 5586.115656] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5586.115663] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5586.115800] iwl3945 0000:03:00.0: No space for Tx
[ 5586.115807] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5586.115821] iwl3945 0000:03:00.0: No space for Tx
[ 5586.115827] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5586.115833] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5586.115839] iwl3945 0000:03:00.0: No space for Tx
[ 5586.115844] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5586.115850] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5586.115862] iwl3945 0000:03:00.0: No space for Tx
[ 5586.115868] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5706.117747] iwl3945 0000:03:00.0: No space for Tx
[ 5706.117757] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5706.117764] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5706.117814] iwl3945 0000:03:00.0: No space for Tx
[ 5706.117820] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5706.117835] iwl3945 0000:03:00.0: No space for Tx
[ 5706.117840] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5706.117846] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5706.117852] iwl3945 0000:03:00.0: No space for Tx
[ 5706.117858] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5706.117864] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5706.117876] iwl3945 0000:03:00.0: No space for Tx
[ 5706.117882] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 5786.500093] iwl3945 0000:03:00.0: No space for Tx
[ 5786.500106] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5786.500113] iwl3945 0000:03:00.0: Error setting new configuration (-28).
[ 5786.500124] iwl3945 0000:03:00.0: No space for Tx
[ 5786.500130] iwl3945 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -28
[ 5792.687421] Registered led device: iwl-phy0::radio
[ 5792.690678] Registered led device: iwl-phy0::assoc
[ 5792.691956] Registered led device: iwl-phy0::RX
[ 5792.693526] Registered led device: iwl-phy0::TX
```

I don't know how much of that is missing but something is missing, and the "terminal window" won't let me see whats above it, so this is all I get and its obviously the bottom of whatever were supposed to be there, the rest I cannot access.

```
lsmod | grep iwl
iwlagn                105694  0 
iwl3945                68727  0 
iwlcore               105922  2 iwlagn,iwl3945
mac80211              205146  3 iwlagn,iwl3945,iwlcore
led_class               2864  3 iwl3945,iwlcore,thinkpad_acpi
cfg80211              126517  4 iwlagn,iwl3945,iwlcore,mac80211

```


```

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xxxxxxxxxxxxx
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c75f7d4f42
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0006646477727432
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F202010185000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A001B00000000000000000000000000000000000000
                    IE: Unknown: 3D160A001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E00156D000000010202E402021200

```

```
nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        xxxxxxxxxxxxxxxx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto "my router"] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        xxxxxxxxxxxxxxxxx

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *my router:         Infra, xxxxxxxxxxxxxxx, Freq 2457 MHz, Rate 54 Mb/s, Strength 84 WPA2

  IPv4 Settings:
    Address:         192.168.1.83
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```

---

### Post by taste of mint on 2011-08-09
Litteraly as soon as I try to stream something, whatever it might be, it takes 5 seconds and then it just disconnects, sometime i have been getting a full minute. I dont know if this helps. but thatnks for trying to help me. If I get this working I will be installing a really good WD black drive, but I really have to get it working first. and then just redo it when I know how its done.

---

### Post by wildmanne39 on 2011-08-09
Hi, try this please:
```
sudo rmmod -f led_class
```
disconnect yuour wired connection but do not restart your computer, if this works we will need to blacklist it.
Thank you

---

### Post by taste of mint on 2011-08-09
I have no wired connection to the computer

The only thing except my "enable wireless" box is the "enable networking", but if I uncheck that the wireless seems dead too, no nothing.

If I go to network connections I find wired and wireless, wired= auto eth0. Should I try to disable it before I do anything (like that command)?

---

### Post by wildmanne39 on 2011-08-09
Hi, you do not need to disable it, but if you had a wired connection, you would unplug it. 
Try that command and let me know what happens.
Thank you

---

### Post by taste of mint on 2011-08-12
> **wildmanne39 said:**
> Hi, try this please:
```
sudo rmmod -f led_class
```disconnect yuour wired connection but do not restart your computer, if this works we will need to blacklist it.
Thank you

Hi sorry for the delay. I tried that one and it looks like this:

```
xxx@xxx:~$ sudo rmmod -f led_class
ERROR: Removing 'led_class': Resource temporarily unavailable
xxx@xxx:~$ sudo rmmod -f led_class
ERROR: Removing 'led_class': Resource temporarily unavailable

```

Had to check twice to be sure :)

---

### Post by taste of mint on 2011-08-12
I can also confirm it did not do anything. Lasted for about 2 minutes this time. I might also add that about 5 minutes ago when the computer had tried to connect for quite some time and then just showed no connection, I checked if it had found any other networks (should be several) but in the list it showed no networks at all, this leads me to believe the wlan card itself somehow shuts down but the computer does not understand this and tries to connect to something that isn't there because the card is turned off or something. Like the left hand isn't talking to the right. Otherwise at least 1 network would show up or?

---

### Post by taste of mint on 2011-08-14
Hello again. Ihave now read about 100 threads about Thinkpad T60's, some people have problems with wifi not working at all and some with the graphics cards. Many people report that they have no problems with network when they use 8.04 and 8.10 so I thought maybe I should try one of those instead, is that a good idea?

I have also read about Centos, Clearos and Scientific linux, those are aimed at companies and they are based on Red hat which is payware. Do you think its more likely everything will just work from the start with a Red hat clone? 

Maybe I should try a newer Ubuntu?

---

