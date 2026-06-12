---
title: "Huge realtek RTL8188CE speed problem"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by DariusZelvys on 2011-11-25
Hi,
I have a big problem with my acer aspire laptop wifi speed. I have router at home which works in b/g wireless modes. My internet speed is about 20mbit/s (that speed i get when i work on the same network with my dell laptop). The problem is i get only 1mbit/s speed with acer laptop. lspci terminal output says i have RTL8188CE wireless card. No matter what i tried, i have a terribly slow internet. If i connect to the internet with wired cable with the same computer, my internet speed is flying..
Would appreciate if any of you could help me. I use 3.0 kernel, and use ubuntu 11.10 . Tried clean install of 11.04 ubuntu, got the same results.BTW signal strength is excelent, but the speed is not..

---

### Post by DariusZelvys on 2011-11-25
more info: lspci

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

sudo iwconfig wlan0

wlan0     IEEE 802.11bgn  ESSID:"DAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:33:F1:05:E3   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10077   Missed beacon:0


any help would be appreciated

---

### Post by praseodym on 2011-11-25
Hi,

add the nameservers of you ISP or the google public NS 8.8.8.8 and 8.8.4.4 in the network-manager applet. See picture (here for LAN)

---

### Post by DariusZelvys on 2011-11-26
Hi, i get name servers through dhcp, why should i add them?

---

### Post by DariusZelvys on 2011-11-26
Got your point and tried your suggestion, but still no success. I noticed that when i connect to the internet i get a full speed about 20mbit, and then in 30 seconds - 1 min time the speed slows down misserably and doesnt go above 1 mbit. No other software is running that could cause speed regression... I'm desperate..

---

### Post by praseodym on 2011-11-26
Ok, please show:

```
ifconfig -a
iwlist chan sudo iwlist scan
dmesg | egrep 'rtl8|r8'
route -n
lsmod
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by DariusZelvys on 2011-11-26
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 38:60:77:78:3d:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:37:03:6e  
          inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:689448 (689.4 KB)  TX bytes:136069 (136.0 KB)


iwlist chan


lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)


sudo iwlist scan


[sudo] password for naminukas: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: F0:7D:68:9A:C5:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Aivaras & Deividas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015acae815f
                    Extra: Last beacon: 652ms ago
                    IE: Unknown: 0012416976617261732026204465697669646173
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001024C93FF94BD16B9D8416F07D689AC57210210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
          Cell 02 - Address: 00:22:33:F1:05:E3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"DAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000150f8d428
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 0003444152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: C8:3A:35:30:38:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Tenda"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a95e893fc
                    Extra: Last beacon: 472ms ago
                    IE: Unknown: 000554656E6461
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001D127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434E20010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000101103B000103104700102880288028801880A880C83A353038A01021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 04 - Address: 08:10:74:53:A1:56
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Balticum7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8f18177fe
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 000942616C746963756D37
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:18:F8:D8:49:87
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"linksys_SES_29616"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009b793b868
                    Extra: Last beacon: 148ms ago
                    IE: Unknown: 00116C696E6B7379735F5345535F3239363136
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 20D767B31BD71BCD7600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000

dmesg | egrep 'rtl8|r8'


[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880157c00000 s81344 r8192 d21056 u262144
[    0.000000] pcpu-alloc: s81344 r8192 d21056 u262144 alloc=1*2097152
[   17.581062] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.581071] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   19.167508] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   19.664545] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin


 route -n


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

lsmod


Module                  Size  Used by
bnep                   18190  2 
rfcomm                 47010  0 
bluetooth             170535  10 bnep,rfcomm
parport_pc             36830  0 
ppdev                  17180  0 
snd_hda_codec_hdmi     31961  1 
snd_hda_codec_realtek   315796  1 
binfmt_misc            17498  1 
snd_hda_intel          32995  1 
snd_hda_codec         106029  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13652  1 snd_hda_codec
snd_pcm                96468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30323  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68011  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  541788  8 
joydev                 17597  0 
arc4                   12529  2 
soundcore              12680  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
usbhid                 46754  0 
hid                    95075  1 usbhid
drm_kms_helper         42261  1 i915
drm                   236064  4 i915,drm_kms_helper
uvcvideo               71880  0 
videodev              101845  1 uvcvideo
rtl8192ce              84590  0 
rtl8192c_common        75719  1 rtl8192ce
rtlwifi               110241  1 rtl8192ce
psmouse                69287  0 
serio_raw              13208  0 
sparse_keymap          13890  0 
mac80211              479012  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              198633  2 rtlwifi,mac80211
ums_realtek            17933  0 
usb_storage            57484  1 ums_realtek
uas                    17891  0 
i2c_algo_bit           13368  1 i915
intel_ips              18040  0 
wmi                    19141  0 
mei                    40867  0 
v4l2_compat_ioctl32    17201  1 videodev
video                  19280  1 i915
lp                     17789  0 
parport                46360  3 parport_pc,ppdev,lp
ahci                   25868  2 
libahci                31087  1 ahci
atl1c                  40948  0 

cat /etc/resolv.conf
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.254


cat /etc/network/interfaces
auto lo
iface lo inet loopback


Thank you in advance

---

### Post by praseodym on 2011-11-26
The network "DAR" works with mixed WPA/WPA2-encryption, better use pure WPA2-AES if possible, thats safer and more stable. The nameserver change should be done, too.

---

### Post by DariusZelvys on 2011-11-26
Another weird notification...
If i reboot computer and work with browser, the speed is normal for a while... 
For example i start a download from ubuntu.com , and i'm downloading ubuntu iso in high speed as it should be (about 20 mbits). I leave the download running, and as soon as i start any new connection the speed drops. For example, if i start a ftp or torrent download ALL MY DOWNLOADS DROP TO 1M SPEED. Even if i stop ftp and torrent downloads and quit programs, my download of ubuntu cd is running at 1 mbit speed. Speed comes back if i restart a system or reconnect to wireless lan. 
Hope i made this situation clear.
Sometimes speed drops just without any reason, but my example described above happens all the time. I'm a big fan of ubuntu, but this is driving me crazy, i can't use it properly.
BTW , i tried a linux mint 12 rc live cd, and the same thing happens, and no need to initiate any ftp or torrent download

---

### Post by DariusZelvys on 2011-11-26
> **praseodym said:**
> The network "DAR" works with mixed WPA/WPA2-encryption, better use pure WPA2-AES if possible, thats safer and more stable. The nameserver change should be done, too.

Will try that in a minute

---

### Post by DariusZelvys on 2011-11-26
No results, same thing happens after suggested changes. I'm ataching my router settings

---

### Post by DariusZelvys on 2011-11-26
btw it happens only with wireless card, if i connect ethernet cable from the same router to my laptop then my internet is working without any problems

---

### Post by DariusZelvys on 2011-11-26
This is getting pretty ridiculous...
I start a torrent download on my acer laptop, speeds drops down to 1 mbit.
Then i take my work laptop dell studio with ubuntu 11.10 and connect to the same network... guess what? Dell laptop works at 1mbit speed. 
As soon as i stop torrent download on acer laptop which is running at 1mbit, the dell studio laptop starts to fly and can use 20 mbit speed...

:confused::confused::confused:

---

### Post by DariusZelvys on 2011-11-27
bump

---

### Post by snowball1288 on 2012-04-06
I know this is a little old but here's hope for those looking:

I have a lenovo x120e with the same card: (lspci below)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

For me, I notice the speed drops considerably when using network manager, I presume due to regular scanning for nearby networks.  I think I read somewhere about a bug in the driver which makes this behavior problematic and some back and forth about whether network manager should stop doing this or provide a switch to disable it.  I think they decided it was a failing of the driver and not network manager though.  

Try using Wicd, for example, which doesn't do this.  Mine behaves much better this way.

---

