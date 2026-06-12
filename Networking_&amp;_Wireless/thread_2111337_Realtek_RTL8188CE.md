---
title: "Realtek RTL8188CE"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by Tom6153 on 2013-02-01
the wireless keeps disconnecting even though the symbol in the top right of the desktop says they are connected

i had no wireless at all when i first installed ubuntu and so i ran the command
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
that got me connected but now it keeps failing even though its telling me its connected
please help

---

### Post by praseodym on 2013-02-01
Can you show the outputs of
```

lspci -nnk | grep -iA2 net
uname -a
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by Tom6153 on 2013-02-02
ok first one....

tom@tom-Monza-T200:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8175]
    Kernel driver in use: rtl8192ce
--
02:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:2027]
    Kernel driver in use: jme
tom@tom-Monza-T200:~$ 

tom@tom-Monza-T200:~$ uname -a
Linux tom-Monza-T200 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
tom@tom-Monza-T200:~$ 

tom@tom-Monza-T200:~$ lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    89521  1 
crc_itu_t              12708  1 udf
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78048  1 
parport_pc             32689  0 
snd_hda_intel          33492  3 
joydev                 17458  0 
ppdev                  17074  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bnep                   18141  2 
rfcomm                 42652  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             205000  10 bnep,rfcomm
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
arc4                   12530  2 
i915                  520621  3 
snd_timer              29426  2 snd_pcm,snd_seq
uvcvideo               76750  0 
rtl8192ce              53546  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
coretemp               13401  0 
nls_iso8859_1          12714  1 
videobuf2_core         32852  1 uvcvideo
rtl8192c_common        48656  1 rtl8192ce
videodev              120310  2 uvcvideo,videobuf2_core
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
rtlwifi                74703  1 rtl8192ce
mac80211              549341  3 rtl8192ce,rtl8192c_common,rtlwifi
drm_kms_helper         49113  1 i915
kvm                   414071  0 
cfg80211              211134  2 rtlwifi,mac80211
drm                   288721  4 i915,drm_kms_helper
psmouse                95595  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
jmb38x_ms              17417  0 
memstick               16555  1 jmb38x_ms
mei                    40691  0 
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
i2c_algo_bit           13414  1 i915
sparse_keymap          13891  0 
microcode              22804  0 
compat                 14950  7 bnep,rfcomm,bluetooth,rtl8192ce,rtlwifi,mac80211,cfg80211
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
video                  19336  1 i915
lpc_ich                17062  0 
wmi                    19071  0 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
jme                    44274  0 
tom@tom-Monza-T200:~
tom@tom-Monza-T200:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
tom@tom-Monza-T200:~$ 

tom@tom-Monza-T200:~$ sudo iwlist scan
[sudo] password for tom: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

tom@tom-Monza-T200:~$ 

and thats it....

---

### Post by praseodym on 2013-02-02
```
wlan0 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=[COLOR="Red"]0 dBm[/COLOR]
Retry long limit:7 RTS thr=2347 B Fragment thrff
Power Management: [COLOR="Red"]on[/COLOR]
```
The card is off. Any button/switch/key/key combination? If its "on", deactivate the power management:

```
sudo iwconfig wlan0 power off
```

---

### Post by Tom6153 on 2013-02-02
ok actually when i did all the above i had the wireless thingy disactivated because it just keeps popping up and anoying me all the time
so i reactivated it

tom@tom-Monza-T200:~$  iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"arabella"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:AD:9F:24   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

it also shows that i have a connection
so im going to unplug now and see if the connection holds up....

ok connection is working.......wireless
sorry for wasting your time but it was like this before and it kept failing,,,,,,,,,,, let me see if it stays on for an hour without falling

---

### Post by Tom6153 on 2013-02-03
yeah its still messed up a day later.....
its strange because the computer tells me that its connected but then i try and open firefox and i get no connection
i have been thinking that it may be a location issue because it seems to work better when i am closer to the router but my other laptop which uses windows works fine at a distance and just now i opened up firefox when i was close to the router and then moved away from it and opened another tab and it worked
so its a bit tempromental.......which is anoying because it means that whatever the problem is its going to be difficult to pin down.

anyway i will run all those commands again with the wireless switched on (its working on wireless now)

tom@tom-Monza-T200:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8175]
    Kernel driver in use: rtl8192ce
--
02:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:2027]
    Kernel driver in use: jme
tom@tom-Monza-T200:~$ uname -a
Linux tom-Monza-T200 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
tom@tom-Monza-T200:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78048  1 
bnep                   18141  2 
joydev                 17458  0 
rfcomm                 42652  0 
bluetooth             205000  10 bnep,rfcomm
parport_pc             32689  0 
ppdev                  17074  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12530  2 
nls_iso8859_1          12714  1 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
coretemp               13401  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
i915                  520621  3 
snd_timer              29426  2 snd_pcm,snd_seq
uvcvideo               76750  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192ce              53546  0 
rtl8192c_common        48656  1 rtl8192ce
rtlwifi                74703  1 rtl8192ce
drm_kms_helper         49113  1 i915
mac80211              549341  3 rtl8192ce,rtl8192c_common,rtlwifi
drm                   288721  4 i915,drm_kms_helper
kvm                   414071  0 
psmouse                95595  0 
videobuf2_core         32852  1 uvcvideo
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              211134  2 rtlwifi,mac80211
videodev              120310  2 uvcvideo,videobuf2_core
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
i2c_algo_bit           13414  1 i915
jmb38x_ms              17417  0 
sparse_keymap          13891  0 
memstick               16555  1 jmb38x_ms
compat                 14950  7 bnep,rfcomm,bluetooth,rtl8192ce,rtlwifi,mac80211,cfg80211
mei                    40691  0 
ghash_clmulni_intel    13221  0 
lpc_ich                17062  0 
cryptd                 20404  1 ghash_clmulni_intel
videobuf2_vmalloc      12861  1 uvcvideo
microcode              22804  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
wmi                    19071  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
video                  19336  1 i915
mac_hid                13206  0 
jme                    44274  0 
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
tom@tom-Monza-T200:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"arabella"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:AD:9F:24   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

tom@tom-Monza-T200:~$ sudo iwlist scan
[sudo] password for tom: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:AD:9F:24
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"arabella"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000426e4ddc3
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000861726162656C6C61
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: A4:B1:E9:40:9F:E9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"OneBillTelecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12452ms ago
                    IE: Unknown: 000E4F6E6542696C6C54656C65636F6D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B00010310470010625AA22A247C5FC091584001AC6EFF781021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E10420009313233335A464541301054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:14:6C:38:EC:46
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"ctn systems"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014bfab00d37
                    Extra: Last beacon: 12452ms ago
                    IE: Unknown: 000B63746E2073797374656D73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:0F:B5:9F:D8:58
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ctnsystems"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051661352df
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000A63746E73797374656D73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000

tom@tom-Monza-T200:~$ 

there you go....
if anybody out there has any solutions to this annoyingly fickle connection i will be very gratefull

---

### Post by praseodym on 2013-02-03
Try pure WPA2-AES (CCMP) encryption instead of WEP.

---

### Post by Tom6153 on 2013-02-04
im sorry but i have no idea how to change my encyption

---

### Post by Tom6153 on 2013-02-04
I did find this webpage
bernaerts.dyndns.org/linux/230-ubuntu-setup-wifi-commandline

and it says there is a bug
tom@tom-Monza-T200:~$ hwinfo --netcard
> hal.1: read hal dataprocess 2190: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
20: PCI 100.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: y9sn._tVvgqJ+UX8
  Parent ID: z8Q3.M9dVvmDgtX9
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Realtek WLAN controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8176 
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8175 
  Revision: 0x01
  Driver: "rtl8192ce"
  Driver Modules: "rtl8192ce"
  Device File: wlan0
  Features: WLAN
  I/O Ports: 0xe000-0xefff (rw)
  Memory Range: 0xf7200000-0xf7203fff (rw,non-prefetchable)
  IRQ: 16 (61 events)
  HW Address: e0:91:53:82:4b:a7
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000010ECd00008176sv000010ECsd00008175bc02sc80i00"
  Driver Info #0:
    Driver Status: rtl8192ce is active
    Driver Activation Cmd: "modprobe rtl8192ce"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

24: PCI 200.5: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.7WGhidpOz2C
  Parent ID: qTvu.O_V+svS4xIA
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.5
  SysFS BusID: 0000:02:00.5
  Hardware Class: network
  Model: "JMicron JMC250 PCI Express Gigabit Ethernet"
  Vendor: pci 0x197b "JMicron Technologies, Inc."
  Device: pci 0x0250 "JMC250 PCI Express Gigabit Ethernet"
  SubVendor: pci 0x1297 "Holco Enterprise Co, Ltd/Shuttle Computer"
  SubDevice: pci 0x2027 
  Revision: 0x03
  Driver: "jme"
  Driver Modules: "jme"
  Device File: eth0
  Memory Range: 0xf6800000-0xf6803fff (rw,non-prefetchable)
  I/O Ports: 0xd100-0xd17f (rw)
  I/O Ports: 0xd000-0xdfff (rw)
  IRQ: 43 (26387 events)
  HW Address: 80:ee:73:4b:a5:df
  Link detected: yes
  Module Alias: "pci:v0000197Bd00000250sv00001297sd00002027bc02sc00i00"
  Driver Info #0:
    Driver Status: jme is active
    Driver Activation Cmd: "modprobe jme"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)
tom@tom-Monza-T200:~$

---

### Post by Tom6153 on 2013-02-04
should i type in this???
sudo apt-get install wpasupplicant

---

### Post by kurt18947 on 2013-02-04
This is really for praseodym rather than Tom6153.  This behavior sounds rather like how my RTL8188CUs device behaves using the 'native' driver.  The driver downloaded from RealTek works perfectly.  Would it be wise for Tom6153 to blacklist the native driver and install the RealTek version, or is that not likely to cure the problem?

---

### Post by praseodym on 2013-02-04
wpasupplicant is installed by default. You need to change the encryption in your router interface, check the manual for it.

---

### Post by Tom6153 on 2013-02-05
I found a dongle and plugged it in and now it seems to be working better but its slower and it still crashes and reconnects itself every 5 mins
is there a way i can tell it not to bother asking me if i want to reconnect or not?
it did keep trying to connect me to a whole bunch of other networks that i dont know the password for but i deleted them which was a relief
i found a way to switch the wireless to wan using the gui, i go to systems then sellect network then i select wireless and then click on options, there in the security section i can change it to wan
however it asks me for a password
am i supposed to use my user password or my network password?
also half the time the gui doesnt let me click on the options button to fiddle with it
would be better if i had a command line........

---

