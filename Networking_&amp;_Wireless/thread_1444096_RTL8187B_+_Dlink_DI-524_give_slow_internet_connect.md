---
title: "RTL8187B + Dlink DI-524 give slow internet connection"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by wzwilliam on 2010-03-31
Hello everybody. I've just installed Ubuntu 9.10 in my laptop. Everything works fine except for my wireless. It works, but much, very much slower the through RJ45, which is perfectly ok. When using wireless i can't even connect to any online messaging service and I need to reload pages oftenly. My security setting is WEP 128 bits ASCII and since I'm trying to follow the format suggested on the thread "HOWTO post a Wireless issue" I'll try to provide the infos like requested on it. Thanks in advance!

Laptop brand and model (I'm from Brasil, so it's a brasilian model)
```
Semp Toshiba IS 1412
```

Wireless Card
```
ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
```

Interface
```
wlan0     Link encap:Ethernet  Endereço de HW **:**:**:**:**:**  
          inet end.: 192.168.0.165  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: ****::***:****:****:****/** Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:8289 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:12531 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:6085904 (6.0 MB) TX bytes:2953997 (2.9 MB)

wmaster0  Link encap:Não Especificado  Endereço de HW **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-*  
          UP RUNNING  MTU:0  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Vila"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Modules
```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
rtl8187                50624  0 
x_tables               16544  1 ip_tables
mac80211              181140  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 rtl8187,mac80211
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
usb_storage            52768  0 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
```

Kernel boot messages
```
[   38.542296] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   38.742906] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   38.941687] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   39.141052] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   42.497321] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   42.696032] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   42.896029] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   43.096031] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   49.769296] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   49.968042] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   50.168036] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   50.368051] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   57.045284] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   57.244038] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   57.444024] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   57.644032] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   64.389237] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   64.588026] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   64.788026] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   64.988030] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   82.405351] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   82.604048] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   82.804068] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   83.005041] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   89.685335] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   89.884048] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   90.084044] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   90.284053] wlan0: direct probe to AP **:**:**:**:**:** timed out
[ 4229.646677] i2c-adapter i2c-2: unable to read EDID block.
[ 4229.646683] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4229.651817] i2c-adapter i2c-2: unable to read EDID block.
[ 4229.651822] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4229.783578] i2c-adapter i2c-2: unable to read EDID block.
[ 4229.783584] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4229.788642] i2c-adapter i2c-2: unable to read EDID block.
[ 4229.788647] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4231.764171] i2c-adapter i2c-2: unable to read EDID block.
[ 4231.764178] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4231.768607] i2c-adapter i2c-2: unable to read EDID block.
[ 4231.768611] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4231.904071] i2c-adapter i2c-2: unable to read EDID block.
[ 4231.904077] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4231.908505] i2c-adapter i2c-2: unable to read EDID block.
[ 4231.908509] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4232.043666] i2c-adapter i2c-2: unable to read EDID block.
[ 4232.043672] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4232.048760] i2c-adapter i2c-2: unable to read EDID block.
[ 4232.048765] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4241.864324] i2c-adapter i2c-2: unable to read EDID block.
[ 4241.864331] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4241.868861] i2c-adapter i2c-2: unable to read EDID block.
[ 4241.868866] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4242.004765] i2c-adapter i2c-2: unable to read EDID block.
[ 4242.004771] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4242.009768] i2c-adapter i2c-2: unable to read EDID block.
[ 4242.009772] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4242.152151] i2c-adapter i2c-2: unable to read EDID block.
[ 4242.152157] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4242.156581] i2c-adapter i2c-2: unable to read EDID block.
[ 4242.156586] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4243.772595] i2c-adapter i2c-2: unable to read EDID block.
[ 4243.772601] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4243.777028] i2c-adapter i2c-2: unable to read EDID block.
[ 4243.777033] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 4252.619948] wlan0: authenticate with AP **:**:**:**:**:**
[ 4252.628330] wlan0: authenticated
[ 4252.628337] wlan0: associate with AP **:**:**:**:**:**
[ 4252.828041] wlan0: associate with AP **:**:**:**:**:**
[ 4252.830827] wlan0: RX AssocResp from **:**:**:**:**:** (capab=0x431 status=0 aid=1)
[ 4252.830832] wlan0: associated
[ 4252.837766] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4263.288022] wlan0: no IPv6 routers present
[ 7328.579478] r8169: eth0: link down
[ 7330.193778] r8169: eth0: link up
[14651.837754] wlan0: disassociated (Reason: 4)
[14652.841305] wlan0: associate with AP **:**:**:**:**:**
[14653.041041] wlan0: associate with AP **:**:**:**:**:**
[14653.241288] wlan0: associate with AP **:**:**:**:**:**
[14653.441038] wlan0: association with AP **:**:**:**:**:** timed out
[14657.515377] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14657.726773] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14657.925047] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14658.130456] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14665.250383] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14665.452320] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14665.653050] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14665.853038] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14671.711379] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14671.909043] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14672.122185] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14672.321038] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14681.342257] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14681.541038] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14681.741057] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14681.943311] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14689.905135] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14690.107453] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14690.305395] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14690.517651] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14698.261034] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14698.465036] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14698.669025] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14698.869040] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14706.192020] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14706.392037] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14706.592039] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14706.792040] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14714.686888] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14714.888040] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14715.088038] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14715.288041] wlan0: direct probe to AP **:**:**:**:**:** timed out
[14722.421389] wlan0: direct probe to AP **:**:**:**:**:** try 1
[14722.624042] wlan0: direct probe to AP **:**:**:**:**:** try 2
[14722.827554] wlan0: direct probe to AP **:**:**:**:**:** try 3
[14723.028040] wlan0: direct probe to AP **:**:**:**:**:** timed out
[24248.786457] r8169: eth0: link down
[24250.570554] r8169: eth0: link up
[34823.242134] r8169: eth0: link down
[34833.540516] r8169: eth0: link up
[37542.598282] wlan0: authenticate with AP **:**:**:**:**:**
[37542.797038] wlan0: authenticate with AP **:**:**:**:**:**
[37542.997048] wlan0: authenticate with AP **:**:**:**:**:**
[37543.197026] wlan0: authentication with AP **:**:**:**:**:** timed out
[37550.022286] wlan0: direct probe to AP **:**:**:**:**:** try 1
[37550.221050] wlan0: direct probe to AP **:**:**:**:**:** try 2
[37550.223297] wlan0 direct probe responded
[37550.223302] wlan0: authenticate with AP **:**:**:**:**:**
[37550.420164] wlan0: authenticate with AP **:**:**:**:**:**
[37550.430160] wlan0: authenticated
[37550.430165] wlan0: associate with AP **:**:**:**:**:**
[37550.435553] wlan0: RX ReassocResp from **:**:**:**:**:** (capab=0x431 status=0 aid=1)
[37550.435559] wlan0: associated
[37585.869462] r8169: eth0: link down
[38458.518578] r8169: eth0: link up
[38563.502593] wlan0: disassociating by local choice (reason=3)
[39643.830281] wlan0: direct probe to AP **:**:**:**:**:** try 1
[39643.832910] wlan0 direct probe responded
[39643.832914] wlan0: authenticate with AP **:**:**:**:**:**
[39643.835785] wlan0: authenticated
[39643.835790] wlan0: associate with AP **:**:**:**:**:**
[39643.848545] wlan0: RX AssocResp from **:**:**:**:**:** (capab=0x431 status=0 aid=1)
[39643.848552] wlan0: associated
[39703.637451] r8169: eth0: link down
```

Network configuration
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: **:**:**:**:**:**
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:5000(size=256) memory:c6000000-c6000fff(prefetchable) memory:c8000000-c8003fff(prefetchable) memory:c6020000-c603ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: **:**:**:**:**:**
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.165 multicast=yes wireless=IEEE 802.11bg
```

Scan
```
wlan0     Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Vila"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001fa48809603
                    Extra: Last beacon: 57764ms ago
                    IE: Unknown: 000456696C61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
```

Kernel
```
2.6.31-20-generic i686
```

Restart
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
```

That's it. I hope it's the way it should and any help e is very much appreciated.

---

### Post by chili555 on 2010-03-31
> wlan0     IEEE 802.11bg  ESSID:"Vila"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          [COLOR="Red"]Bit Rate=1 Mb/s[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0I wonder if the card is not correctly negotiating the highest useful rate. Let's help it a bit. Please open a terminal and do:```
sudo iwlist wlan0 rate 54M
iwconfig
```Did it stick? If not:```
sudo ifconfig wlan0 down
sudo iwlist wlan0 rate 54M
sudo ifconfig wlan0 up
iwconfig
```How about now? Is surfing faster?

---

### Post by wzwilliam on 2010-03-31
Thank you for answeting, chili555.

after
```
sudo iwlist wlan0 rate 54M
```
it gives me
```
iwlist: command `rate' needs fewer arguments (max 0)
```

> Did it stick? If not:```
sudo ifconfig wlan0 down
sudo iwlist wlan0 rate 54M
sudo ifconfig wlan0 up
iwconfig
```How about now? Is surfing faster?

no, still as slow as before and even after this procedure it looks like the same results before:
```
wlan0     IEEE 802.11bg  ESSID:"Vila"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
some relation with the "fewer arguments", maybe?

---

### Post by chili555 on 2010-03-31
Oops! Sorry. I mean:```
sudo iwconfig wlan0 rate 54M
```

---

### Post by wzwilliam on 2010-03-31
now the Bit rate properly changed to 54 Mb/s, but now when i try to connect it only keeps me asking for the password after a few seconds.

---

### Post by chili555 on 2010-04-01
I wonder what the kernel has to say about this. Please post:```
dmesg | grep -e rtl8 -e wlan
```Thanks.

---

### Post by wzwilliam on 2010-04-01
there it is:
```
[   13.829086] phy0: hwaddr **:**:**:**:**:**, RTL8187BvE V0 + rtl8225z2
[   13.850858] rtl8187: Customer ID is 0x00
[   13.850916] Registered led device: rtl8187-phy0::tx
[   13.850944] Registered led device: rtl8187-phy0::rx
[   13.850981] usbcore: registered new interface driver rtl8187
[   20.262654] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.705347] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   41.904037] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   42.104030] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   42.305032] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   49.109350] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   49.308054] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   49.508035] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   49.708032] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   56.381349] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   56.580035] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   56.780030] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   56.980031] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   63.653352] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   63.852050] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   64.052031] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   64.252024] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   70.921351] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   71.120037] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   71.320037] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   71.520033] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   74.285351] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   74.485030] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   74.684033] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   74.884028] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   81.561352] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   81.760059] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   81.960055] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   82.160059] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   88.837353] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   89.036053] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   89.236032] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   89.436024] wlan0: direct probe to AP **:**:**:**:**:** timed out
[   96.105354] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   96.304045] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   96.505028] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   96.704042] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  103.405231] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  103.604031] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  103.804041] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  104.005043] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  110.681355] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  110.880044] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  111.080041] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  111.280041] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  117.953232] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  118.152050] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  118.352052] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  118.552033] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  123.441357] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  123.640035] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  123.841030] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  124.040049] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  130.721358] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  130.920038] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  131.124029] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  131.320058] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  138.006355] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  138.204055] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  138.405790] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  138.604054] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  145.281360] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  145.480028] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  145.680040] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  145.880035] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  152.569374] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  152.768039] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  152.968053] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  153.168069] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  159.861235] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  160.060058] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  160.260073] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  160.460039] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  167.153365] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  167.352048] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  167.552051] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  167.752026] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  174.421364] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  174.621029] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  174.820067] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  175.020063] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  181.729377] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  181.928030] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  182.128049] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  182.328028] wlan0: direct probe to AP **:**:**:**:**:** timed out
[  189.129377] wlan0: direct probe to AP **:**:**:**:**:** try 1
[  189.329062] wlan0: direct probe to AP **:**:**:**:**:** try 2
[  189.528040] wlan0: direct probe to AP **:**:**:**:**:** try 3
[  189.728071] wlan0: direct probe to AP **:**:**:**:**:** timed out
```
It may be obvious but i forgot to tell that since the password request is looping, i can't coneect through wireless at all. Also, I guess you must be expecting that, but since I have little experience with linux, it can be useful pointing out that the terms wlan and rtl8 are in red on the terminal output.

---

### Post by chili555 on 2010-04-01
> wlan0: direct probe to AP **:**:**:**:**:** timed out
[   56.381349] wlan0: direct probe to AP **:**:**:**:**:** try 1
[   56.580035] wlan0: direct probe to AP **:**:**:**:**:** try 2
[   56.780030] wlan0: direct probe to AP **:**:**:**:**:** try 3
[   56.980031] wlan0: direct probe to AP **:**:**:**:**:** timed out
It looks like it is asking the router for a response and the router is silent, so it times out. Have you tried resetting the router by unplugging it and plugging it back in? Is the router set to 802.11 B or G, or even better Auto speeds? Are you being asked for the WEP key? Is there MAC address filtering on the router?

---

### Post by wzwilliam on 2010-04-01
Unplugging and plugging it back won't be possible right now; *doing it through the management interface will cause the same effects?
The router is set to mixed mode, b and g, with tx rates set to auto.
Yes, I'm being asked for the WEP key, which just keeps being asked again after a few seconds in some kind of looping.
No, theres no filter of any kind being used in the router.

* No, it doesn't. I'll try thw unplug/plug as soon as I can and post the results right after that.

---

### Post by wzwilliam on 2010-04-02
I'm sorry for taking too long to answer. Unplugged and plugged back the router's power cable. The strange thing is that the wireless connection  appeared as connected but i had no data transfer. Websites didn't load, messengers didn't connect, nothing. Then I tried the command ifconfig wlan0 down/up and the wireless connection started the looping the WEP key asking again without connecting. Is there a next step?

---

### Post by chili555 on 2010-04-02
How many characters does your WEP key have? I noticed you said it's ASCII, which is a bit rare, but not impossible. Are you trying to connect with the ethernet cable detached? Network Manager will not use wireless if wired is available.

Please run:```
sudo tail -n25 /var/log/syslog
```Try to find where the wireless tries and fails and post about ten lines up to and including that point.

Since your wireless device sees your network and tries to connect, I am fairly sure the card and driver are working properly.

---

### Post by wzwilliam on 2010-04-02
13 characters.
```
Apr  2 14:12:38 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
Apr  2 14:12:39 william-laptop kernel: [  247.028024] eth0: no IPv6 routers present
Apr  2 14:12:45 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
Apr  2 14:12:45 william-laptop wpa_supplicant[1428]: Trying to associate with **:**:**:**:**:** (SSID='.net coronel ezequiel 3481-3762' freq=2457 MHz)
Apr  2 14:12:45 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  2 14:12:45 william-laptop wpa_supplicant[1428]: Association request to the driver failed
Apr  2 14:12:48 william-laptop kernel: [  256.432906] wlan0: direct probe to AP **:**:**:**:**:** try 1
Apr  2 14:12:48 william-laptop kernel: [  256.632045] wlan0: direct probe to AP **:**:**:**:**:** try 2
Apr  2 14:12:48 william-laptop kernel: [  256.833028] wlan0: direct probe to AP **:**:**:**:**:** try 3
Apr  2 14:12:49 william-laptop kernel: [  257.033053] wlan0: direct probe to AP **:**:**:**:**:** timed out
Apr  2 14:12:49 william-laptop wpa_supplicant[1428]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  2 14:12:49 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  2 14:12:50 william-laptop wpa_supplicant[1428]: Authentication with 00:00:00:00:00:00 timed out.
Apr  2 14:12:50 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  2 14:12:53 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
Apr  2 14:12:59 william-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
Apr  2 14:12:59 william-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
Apr  2 14:12:59 william-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (.net coronel ezequiel 3481-3762)
Apr  2 14:12:59 william-laptop NetworkManager: <info>  Marking connection 'Auto .net coronel ezequiel 3481-3762' invalid.
Apr  2 14:12:59 william-laptop NetworkManager: <info>  Activation (wlan0) failed.
Apr  2 14:12:59 william-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Apr  2 14:12:59 william-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Apr  2 14:12:59 william-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr  2 14:13:00 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
Apr  2 14:13:14 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
```
The strange thing is that this AP the laptop is trying to connect to is not mine. Is it normal?

---

### Post by chili555 on 2010-04-02
The whole purpose of Network Manager is for you to specify the known, trusted network you want to connect to. Do you see your network when you click the Network Manager icon? Do you select yours and still try to connect to .net coronel ezequiel 3481-3762? It looks as if that network has WPA and you are saying you have WEP so it's not going to connect. Please see attached. In the example, I know I want to connect to 'GBR1' so that's the network I click.

---

### Post by wzwilliam on 2010-04-02
Yes, my network (Vila) appears on Network Manager, I'm correctly selecting  it and, since it asks for the WEP key for it, I think the wireless card is trying to connect to it, bu after that it takes a while and asks for the key again. I'm attaching the images.

---

### Post by chili555 on 2010-04-02
How many characters is it? ASCII is rare.

---

### Post by wzwilliam on 2010-04-02
13 characters. Do you think I should try to change the type of key?

---

### Post by chili555 on 2010-04-02
> **wzwilliam said:**
> 13 characters. Do you think I should try to change the type of key?Not yet.

Please try right-clicking the Network Manager icon and select Edit Connections. Click the Wireless tab and select your network, Auto Vila. Click Edit and click the Wireless Security tab and fill in your WEP key and make sure the Connect Automatically box is checked. Click Apply and see if you connect.

If not, let's see:```
sudo tail -n25 /var/log/syslog
```Post the part where it fails this time.

13 characters is correct for ASCII. Do you have an option to change to HEX in the router if everything else fails?

---

### Post by wzwilliam on 2010-04-02
Done, but everything is still the same.

```
Apr  2 18:13:25 william-laptop wpa_supplicant[1428]: Authentication with 00:00:00:00:00:00 timed out.
Apr  2 18:13:25 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  2 18:13:27 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
Apr  2 18:13:27 william-laptop wpa_supplicant[1428]: Trying to associate with **:**:**:**:**:** (SSID='Vila' freq=2437 MHz)
Apr  2 18:13:27 william-laptop wpa_supplicant[1428]: Association request to the driver failed
Apr  2 18:13:27 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  2 18:13:27 william-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Apr  2 18:13:28 william-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Apr  2 18:13:28 william-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Apr  2 18:13:28 william-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  2 18:13:28 william-laptop kernel: [14696.154372] wlan0: direct probe to AP **:**:**:**:**:** try 1
Apr  2 18:13:28 william-laptop kernel: [14696.353042] wlan0: direct probe to AP **:**:**:**:**:** try 2
Apr  2 18:13:28 william-laptop kernel: [14696.553051] wlan0: direct probe to AP **:**:**:**:**:** try 3
Apr  2 18:13:28 william-laptop kernel: [14696.753463] wlan0: direct probe to AP **:**:**:**:**:** timed out
Apr  2 18:13:28 william-laptop wpa_supplicant[1428]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  2 18:13:32 william-laptop wpa_supplicant[1428]: Authentication with 00:00:00:00:00:00 timed out.
Apr  2 18:13:43 william-laptop NetworkManager: <info>  wlan0: link timed out.
Apr  2 18:14:14 william-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Apr  2 18:14:14 william-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Vila)
Apr  2 18:14:14 william-laptop NetworkManager: <info>  Marking connection 'Auto Vila' invalid.
Apr  2 18:14:14 william-laptop NetworkManager: <info>  Activation (wlan0) failed.
Apr  2 18:14:14 william-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Apr  2 18:14:14 william-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Apr  2 18:14:14 william-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr  2 18:14:44 william-laptop wpa_supplicant[1428]: CTRL-EVENT-SCAN-RESULTS 
```
And yes, I have the HEX option in my router.

---

### Post by chili555 on 2010-04-02
I suggest you try HEX and, if it fails, just temporarily, unencrypted. Don't leave your system unencrypted for more that a few moments; just long enough to learn if it connects or not.

If you do:```
cat /etc/network/interfaces
```does it contain more than the loopback stanzas?

---

### Post by wzwilliam on 2010-04-02
Hexadecimals give the same results than WEP. No security stablishes connection when the computer starts, but with terribly low speeds. If I disconnect the wireless card in the meantime, I can't reconnect.

Result of cat:```
auto lo
iface lo inet loopback
```

---

### Post by chili555 on 2010-04-02
I feel like we have done everything we can do to coax the native driver to life and it has not responded. I am sorry.

I think the next step is ndiswrapper. I saw this: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)  > The rtl8187 driver is very slow and have some problems but it works for this card in fact. Use ndiswrapper with Win98 driver from here on Hardy or lower. Install instructions here. Ndiswrapper info here (search for 0bda:8189). Linux USB ID here. Inside Gateway ML6720. Apparently connected to USB EHCI.Are you up to trying ndiswrapper?

---

### Post by wzwilliam on 2010-04-02
Whatever works. I just don't wanna have to unninstall ubuntu again just because of wireless.

---

### Post by chili555 on 2010-04-03
For your reference, here is the guide I am following, but I have tried to simplify it a bit and use more modern, Karmic methods.

[http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/](http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/) 

I will boot into Karmic now, be back in a few. In the meantime, do:```
sudo apt-get install ndisgtk
```

---

### Post by chili555 on 2010-04-03
When you installed ndisgtk, it will have added all the dependencies. Now, let's get the native driver blacklisted:```
sudo su
ifconfig wlan0 down
rmmod -f rtl8187
echo "blacklist rtl8187" >> /etc/modprobe.d/blacklist.conf
exit
```Now, let's find and extract the Windows driver files. Go here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

Scroll down to RTL8187**B** and download the Windows driver package.By default, downloads go to your desktop. Right-click the zip file and select Extract Here.

Now, we are ready to install. Open System > Administration > Windows Wireless Drivers and click Install New Driver. Browse to Desktop/RTL8187B_Drv_XP_5.1160.0415.2009_Win7_62.1181.1105.2009_UI_1.00.0145.ALL.L/RTL8187B/WinXP and point to net8187b.inf. Please post back with any errors or problems.

I think you can skip the step of Configure Network; I hope Network Manager will do all that for us.

Does Network Manager see your network now? Can you connect?

---

### Post by wzwilliam on 2010-04-03
Yes, now everything is working perfectly! Connected normally right now using Network Manager, security set to WEP 64bits HEX. I used primarly the info on the link you posted earlier to set things up.
I just have one last question: how can i configure the wlan0 to start automatically with ubuntu?

---

### Post by chili555 on 2010-04-03
Wow! Great! I have a couple of guys watching this thread and they will be helped, too. I am very glad for you.

Right-click the Network manager icon and select Edit Connections. Select Wireless and edit Auto Vila. Make sure that Connect Automatically is checked.

Can you please mark this as Solved?

---

### Post by wzwilliam on 2010-04-03
Perfectly!

chilli555, thank you very much for your time, patience and knowledge!

---

### Post by cayman.n2o on 2010-10-23
Hey guys!
I found this topic googling.
I have the same router and the same problem. My laptop is FSC Amilo pa 3553 with Atheros AR928x.
Since I am total noob when it comes to linux and console, could someone just form commands for me, for solving this problem? Please!!!

---

