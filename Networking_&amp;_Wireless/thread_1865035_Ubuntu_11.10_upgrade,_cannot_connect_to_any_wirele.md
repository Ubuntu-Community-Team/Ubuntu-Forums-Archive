---
title: "Ubuntu 11.10 upgrade, cannot connect to any wireless networks."
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by conlon5 on 2011-10-19
Hey,

I upgraded to ubuntu 11.10 from 11.04 over the weekend and three days later the wireless would not connect to the internet for me. The signal icon would flicker slightly and would continuously ask me for the WEP code. Very similar to what I have been reading all over the web but I can't find a solution.

I have an Acer aspire 6920 with a intel corporation pro/wireless 4965 AG(N) card from what I could make out. I have been searching everywhere for info on how to resolve this problem and fallowing tutorials on how to fix it using the terminal but keep hitting road block such as my own lack of IT knowledge and not getting the correct response from the terminal. I hope someone can help. 

Thanks

Conlon5

P.S. Sorry about leaving out a lot of info but I don't currently have the laptop with me so I can't up load the info I get from the terminal.

---

### Post by pdc on 2011-10-19
some forums run on love.....

......this one runs on information......

help the helpers.......

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by conlon5 on 2011-10-20
Acer Aspire 6920 running Ubuntu 11.10 (I think it's 32 bit but the laptop is definantly 64 bit)


Graphics card

-[Intel Corporation PRO/Wireless 4965 AG or AGN]


$ lspci -nn | grep 'Intel Corporation PRO/Wireless 4965 AG or AGN'

-[08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)]


$ iwconfig wlan0

-[wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off]


$ lsmod

-[Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
usbnet                 25214  2 rndis_host,cdc_ether
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
mxm_wmi                12859  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                63474  0 
serio_raw              12990  0 
ir_rc6_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_rc5_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_nec_decoder         12490  0 
ite_cir                24743  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
iwl4965               121795  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  2 mxm_wmi,acer_wmi
iwl_legacy             71499  1 iwl4965
mac80211              272785  2 iwl4965,iwl_legacy
i915                  505143  3 
cfg80211              172392  3 iwl4965,iwl_legacy,mac80211
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   196322  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
atl1e                  32809  0 ]


$ dmesg | grep wlan

-[[   19.542422] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.090503] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[   24.092389] wlan0: authenticated
[   24.111319] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[   24.113881] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[   24.113887] wlan0: associated
[   24.144459] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.282017] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[   31.604272] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.017294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.342186] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.381888] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[   34.384447] wlan0: authenticated
[   34.384678] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[   34.399567] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[   34.399574] wlan0: associated
[   34.427159] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.184124] wlan0: no IPv6 routers present
[   55.025823] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[   58.438614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.764104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.377725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.727109] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.251634] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.523839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.621467] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[   76.629876] wlan0: authenticated
[   76.629938] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[   76.632410] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[   76.632413] wlan0: associated
[   76.658090] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.049314] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[  117.727936] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  118.011727] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  275.284984] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  277.544608] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  278.203956] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  280.349825] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[  280.366842] wlan0: authenticated
[  280.366918] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[  280.370223] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[  280.370230] wlan0: associated
[  280.399222] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  290.496128] wlan0: no IPv6 routers present
[ 2047.849226] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 2048.152090] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2049.479636] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2049.760854] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2050.392629] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2052.526182] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 2052.538337] wlan0: authenticated
[ 2052.538412] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 2052.541401] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 2052.541407] wlan0: associated
[ 2052.570136] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2063.536151] wlan0: no IPv6 routers present
[ 2365.300989] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 2365.617829] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3282.236107] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3284.036102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3284.404768] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3284.930500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3285.224443] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3286.976955] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 3286.978743] wlan0: authenticated
[ 3286.978979] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 3286.981484] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 3286.981490] wlan0: associated
[ 3287.006543] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3287.253653] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 3328.528359] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3328.818270] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3329.180814] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3502.086759] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3502.444070] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3502.927792] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3503.231955] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3519.251441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3539.182119] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3539.534396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3540.030512] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3540.322458] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3578.133533] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3578.431855] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3578.792493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3723.545438] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 3723.547380] wlan0: authenticated
[ 3723.547601] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 3723.551125] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 3723.551133] wlan0: associated
[ 3723.579427] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3734.320160] wlan0: no IPv6 routers present
[ 3744.028555] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 3838.611298] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3838.958509] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3839.448220] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3839.731672] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3877.572625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3877.873812] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3878.217527] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4092.158918] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4092.516002] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4093.015551] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4093.304350] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4095.631168] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4095.709862] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 4095.710354] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=2)
[ 4095.710425] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 4095.712613] wlan0: authenticated
[ 4095.712900] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 4095.717082] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 4095.717089] wlan0: associated
[ 4095.742673] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4106.384040] wlan0: no IPv6 routers present
[ 4116.019819] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 4166.482923] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4611.656968] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 4611.658909] wlan0: authenticated
[ 4611.659221] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 4611.661905] wlan0: RX AssocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 4611.661912] wlan0: associated
[ 4611.692612] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4622.304105] wlan0: no IPv6 routers present
[ 4632.023258] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 5151.624615] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 5151.627151] wlan0: authenticated
[ 5151.627488] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 5151.630657] wlan0: RX ReassocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 5151.630664] wlan0: associated
[ 5161.840157] wlan0: no IPv6 routers present
[ 5172.019683] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)
[ 5631.624426] wlan0: authenticate with 00:0e:8e:7e:2b:b1 (try 1)
[ 5631.626368] wlan0: authenticated
[ 5631.626646] wlan0: associate with 00:0e:8e:7e:2b:b1 (try 1)
[ 5631.630022] wlan0: RX ReassocResp from 00:0e:8e:7e:2b:b1 (capab=0x411 status=0 aid=3)
[ 5631.630029] wlan0: associated
[ 5677.218804] wlan0: deauthenticating from 00:0e:8e:7e:2b:b1 by local choice (reason=3)]


$ sudo lshw -C network

-[*-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:a0:d1:a6:ff:57
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:49 memory:f6000000-f603ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:9e:75:b7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-12-generic-pae firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:c0000000-c0001fff]


$ iwlist scan wlan0

-[iwlist: unknown command `wlan0' (check 'iwlist --help').]


$ iwlist scan

-[lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0E:8E:7E:2B:BF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"BGRM058"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bbd4ff019b
                    Extra: Last beacon: 2680ms ago
                    IE: Unknown: 00074247524D303538
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:0E:8E:7F:47:CD
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"BGRM061"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c2b19319b
                    Extra: Last beacon: 2132ms ago
                    IE: Unknown: 00074247524D303631
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 00:0E:8E:7E:2B:B1
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"BGRM060"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000134931ae19b
                    Extra: Last beacon: 2260ms ago
                    IE: Unknown: 00074247524D303630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C]


$ lsb_release -d

-[Description:    Ubuntu 11.10]


$ uname -mr

-[3.0.0-12-generic-pae i686]


$ sudo /etc/init.d/networking restart

-[* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] ]

---

### Post by conlon5 on 2011-10-20
Just some more info.

I have installed wicd on the laptop using 3G from my mobile connected via usb. The latest message I get is that it can't obtain an IP address or if it dose it will say bad password. The password is not bad as I am using the same one on this computer and I am obviously connected o.0

---

### Post by ben_T on 2011-10-25
Hi. I'm running Ubuntu 11.10 on an Acer Aspire 5250-BZ873, and have a similar problem. Your description "The signal icon would flicker slightly and would continuously ask me for the WEP code" describes my situation exactly, HOWEVER I found that if I move the laptop closer to the wireless router, it is able to connect.

So my issue isn't that it can't connect, but rather that it is not connecting at a distance that it should. At the distance where I am having trouble, the same laptop connects without difficulty under Windows 7.

So perhaps it is more of a case of an under-performing driver than of a failing driver?

Any help will be appreciated. :)

---

### Post by ben_T on 2011-10-25
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:a6:a2:4b
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:37:4b:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:90100000-9010ffff

---

### Post by yan_sukran on 2011-10-26
Hi there

try using ndiswrapper for driver wlan, it's simple and easy way to manage your connections.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by yan_sukran on 2011-10-26
Hi there

try using ndiswrapper for driver wlan, it's simple and easy way to manage your connections.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

