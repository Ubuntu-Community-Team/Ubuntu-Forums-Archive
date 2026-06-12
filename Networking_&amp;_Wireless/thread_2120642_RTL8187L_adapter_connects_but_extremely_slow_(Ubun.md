---
title: "RTL8187L adapter connects but extremely slow (Ubuntu 12.10)"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by bellaseem on 2013-02-27
Hi there, First off, I'm using Ubuntu 12.10 with all the latest updates installed. I recently bought an adapter with RTL8187L chipset, it is connecting fine to all networks(WEP & WPA), however the internet is extremely slow (like 1-3 kb/s , I can barely open google.com). Sometimes the adapter works when I first plug it in (though slow) then stops after a few seconds... Also the signal to the networks I'm connecting to is quite strong (-40 db to -50 on average), and the adapter works perfectly fine on windows 7 with the drivers from the website.

So I tried downloading the drivers from the realtek website ( [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true))  but they only listed versions for kernels 3.0, 3.1, and 3.2 and my kernel is 3.5 if I'm not mistaken... *but I downloaded and installed them anyway*... but still had the same issue though [nothing really changed apparently, I think the drivers the come with ubuntu are the same?]).

I had a look at the supported drivers page here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

and it had these instructions:

"The rtl8187 driver is very slow and have some problems but it works for this card in fact. Use ndiswrapper with Win98 driver from here on Hardy or lower. Install instructions here. Ndiswrapper info here (search for 0bda:8189). Linux USB ID here. Inside Gateway ML6720. Apparently connected to USB EHCI. **_These instructions will NOT work for the 8187L chipset, which will only stagger along on the native r8187 driver in Hardy_**."

So it specifically mentions that the instructions won't work for the 8187L chipset (mine)... What do they mean that it will only stagger along on the native r8187 driver in hardy? I didn't really understand that completely...

So, what are my options? Also, I'll try to post everything requested on the "HOWTO post a thread" thread, can't now because I'm using a computer at my university...

---

### Post by varunendra on 2013-02-27
Let us take a look at a detailed report of your wireless setup. Please follow the "Wireless Script" link in my signature below and post back the result of the script as mentioned in the linked post.

---

### Post by bellaseem on 2013-02-27
Hi there, and thank you for responding! I was reading through your other posts, you seem to be very knowledgeable, I'm hoping you can help... Here's the netinfo.txt file:

```

*************** info trace ****************



**** uname -a ****


Linux Internet 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:28:26 UTC 2013 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fd3c]
	Kernel driver in use: r8169
--
14:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: bcma-pci-bridge


**** lsusb ****


Bus 001 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 002: ID 0930:0214 Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"x"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
r8187l                143393  0 
rtl8187                56225  0 
eeprom_93cx6           13169  1 rtl8187
joydev                 17162  0 
snd_hda_codec_realtek    63579  1 
btusb                  17987  0 
arc4                   12474  4 
brcmsmac              503700  0 
mac80211              461261  2 rtl8187,brcmsmac
brcmutil               14356  1 brcmsmac
coretemp               13169  0 
cfg80211              175574  3 rtl8187,brcmsmac,mac80211
cordic                 12519  1 brcmsmac
parport_pc             31969  0 
rfcomm                 37277  12 
ppdev                  12818  0 
bnep                   17708  2 
bluetooth             183270  22 btusb,rfcomm,bnep
binfmt_misc            17261  1 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
microcode              18210  0 
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84878  0 
lpc_ich                16926  0 
serio_raw              13032  0 
bcma                   34484  1 brcmsmac
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i915                  457241  3 
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
toshiba_acpi           18239  0 
sparse_keymap          13659  1 toshiba_acpi
wmi                    18591  1 toshiba_acpi
toshiba_bluetooth      12712  0 
video                  18895  1 i915
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan1  [x] -----------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    hmaydan_net 70.692794 HH: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    yassine:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    mawla-net 70.692794: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    ghezzawy:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Blink589566:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    mimo-net 70.692794 H: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    worldnet_roudayna: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Thomson1911EC:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA
    mimo_net 70.692794 M: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    mimo_net 70.692794 K: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    NYK-MS:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    SSSSSS:          Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    Blink3b7a5:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WEP
    mimo_net 70.692794 h: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WEP
    DPL 70-224589:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 61 WEP
    housam:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    zebaraaa:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    mimo_net 70.692794K: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    haidar:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Ahmad hub :      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    skynet:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    barbie:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    HRMNJ:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    zlink:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA
    MC:              Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    rahhal:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    mimo_net 70.692794 W: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    My Network:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Tala:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    Ali:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Blink7025BB:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    *x:              Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    AMMARNET:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Blink0EB850:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WEP

  IPv4 Settings:
    Address:         192.168.2.125
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    housam:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    hmaydan_net 70.692794 HH: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    mawla-net 70.692794: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    yassine:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    mimo-net 70.692794 H: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Blink3b7a5:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WEP
    DPL 70-224589:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
    Blink589566:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    skiespro 3G 70070450: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA
    mimo_net 70.692794K: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ghezzawy:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    mimo_net 70.692794 h: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    zebaraaa:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    skynet:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Worldnet_01274199_space2013: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    mimo_net 70.692794 K: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SSSSSS:          Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    internet: 01/271509: Infra, <MAC address removed>, Freq 2412 MHz, Rate 11 Mb/s, Strength 22
    Blink0EB850:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    sammouri:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    WNC_01274199_Fakha: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Ali:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    zlink:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    x:               Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA
    mimo_net 70.692794 W: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    worldnet_roudayna: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    default:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    debek:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    mimo_net 70/692794 S: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FiberNet 03005371 Rida: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Saab:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    kibreet:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Thomson1911EC:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"x"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000041d08134
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000178
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Blink3b7a5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000175bfc9183
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 000A426C696E6B3362376135
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"yassine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000692aa8180
                    Extra: Last beacon: 916ms ago
                    IE: Unknown: 000779617373696E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"mawla-net 70.692794"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000011a94a462
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 00136D61776C612D6E65742037302E363932373934
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002586D54BCC022586D54BCC64002C010808
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"internet: 01/271509"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c9d5960e6
                    Extra: Last beacon: 29776ms ago
                    IE: Unknown: 0013696E7465726E65743A2030312F323731353039
                    IE: Unknown: 010482040B16
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: DD2A000C42000000011E0400000000660B040000303038303438373336333836000000000000000005026C09
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"DPL 70-224589"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000065ec7b181
                    Extra: Last beacon: 29492ms ago
                    IE: Unknown: 000D44504C2037302D323234353839
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000D85D4CBAA39EDA5D4CBAA39E64002C010808
          Cell 07 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"hmaydan_net 70.692794 HH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000336affb31
                    Extra: Last beacon: 696ms ago
                    IE: Unknown: 0018686D617964616E5F6E65742037302E363932373934204848
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1605051700000000000000000000000000000000000000
                    IE: Unknown: 341605051700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A00011010440001021057000101103B0001031047001000000000000010000000A0F3C15F39BE1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"housam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000095d12181
                    Extra: Last beacon: 624ms ago
                    IE: Unknown: 0006686F7573616D
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000027191DA8A20227191DA8A264002C010808

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"x"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000042072181
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 000178
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"ghezzawy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000069340f620
                    Extra: Last beacon: 3164ms ago
                    IE: Unknown: 00086768657A7A617779
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Blink3b7a5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000175c0a7858
                    Extra: Last beacon: 3168ms ago
                    IE: Unknown: 000A426C696E6B3362376135
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
          Cell 04 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"hmaydan_net 70.692794 HH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000336d357a1
                    Extra: Last beacon: 1644ms ago
                    IE: Unknown: 0018686D617964616E5F6E65742037302E363932373934204848
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1605051700000000000000000000000000000000000000
                    IE: Unknown: 341605051700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A00011010440001021057000101103B0001031047001000000000000010000000A0F3C15F39BE1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"mawla-net 70.692794"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000011abc395c
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 00136D61776C612D6E65742037302E363932373934
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002586D54BCC022586D54BCC64002C010808
          Cell 06 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"mimo-net 70.692794 H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002be20cd2d
                    Extra: Last beacon: 8540ms ago
                    IE: Unknown: 00146D696D6F2D6E65742037302E3639323739342048
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1607071100000000000000000000000000000000000000
                    IE: Unknown: 341607071100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A00011010440001021057000101103B00010310470010000000000000100000006470026473761021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"zlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003117623a0
                    Extra: Last beacon: 8120ms ago
                    IE: Unknown: 00057A6C696E6B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"DPL 70-224589"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000660b7710e
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000D44504C2037302D323234353839
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000D85D4CBAA39EDA5D4CBAA39E64002C010808
          Cell 09 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"SSSSSS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006930a4c1a
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0006535353535353
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010658727A0A76CACD353751CAFF784CAF810210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"worldnet_roudayna"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000693a83d59
                    Extra: Last beacon: 3160ms ago
                    IE: Unknown: 0011776F726C646E65745F726F756461796E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Tala"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000338f06186
                    Extra: Last beacon: 8092ms ago
                    IE: Unknown: 000454616C61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Thomson1911EC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000068c6a5244
                    Extra: Last beacon: 7884ms ago
                    IE: Unknown: 000D54686F6D736F6E313931314543
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"yassine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006925dd18a
                    Extra: Last beacon: 7752ms ago
                    IE: Unknown: 000779617373696E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Blink0EB850"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000142b683a142
                    Extra: Last beacon: 8452ms ago
                    IE: Unknown: 000B426C696E6B304542383530
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 15 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"AMMARNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000050d912180
                    Extra: Last beacon: 8228ms ago
                    IE: Unknown: 0008414D4D41524E4554
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160A071100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD2B0050F204104A00011010440001021057000101104900140024E26002000101600000020001600100020001
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"mimo_net 70.692794K"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000217740e5d
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00136D696D6F5F6E65742037302E3639323739344B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B00000000000000000000000000000000000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   27.569861] wmi: Mapper loaded
[   27.661610] bcma: Found chip with id 0x4313, rev 0x01 and package 0x08
[   27.661641] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   27.661664] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   27.661715] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   27.686521] bcma: Bus registered
[   28.145496] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 19
[   28.715943] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   28.715960] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   28.716473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.717831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.352886] wlan0: authenticate with <MAC address removed>
[   30.355785] wlan0: direct probe to <MAC address removed> (try 1/3)
[   30.556029] wlan0: send auth to <MAC address removed> (try 2/3)
[   30.557502] wlan0: authenticated
[   30.560048] wlan0: associate with <MAC address removed> (try 1/3)
[   30.562027] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   30.562654] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   30.562659] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   30.562662] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   30.562669] wlan0: associated
[   30.562832] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.400948] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[   34.432527] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   34.432537] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[   34.432540] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   35.402708] wlan0: authenticate with <MAC address removed>
[   35.402773] wlan0: send auth to <MAC address removed> (try 1/3)
[   35.604031] wlan0: send auth to <MAC address removed> (try 2/3)
[   35.605518] wlan0: authenticated
[   35.608044] wlan0: associate with <MAC address removed> (try 1/3)
[   35.610048] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   35.610666] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   35.610670] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[   35.610673] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   35.610680] wlan0: associated
[  143.968072] WARNING: at /build/buildd/linux-3.5.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:7953 brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]()
[  143.968075] Modules linked in: joydev snd_hda_codec_realtek btusb arc4 brcmsmac mac80211 brcmutil coretemp cfg80211 cordic parport_pc rfcomm ppdev bnep bluetooth binfmt_misc snd_hda_intel snd_hda_codec snd_hwdep microcode snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse lpc_ich serio_raw bcma uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops snd soundcore snd_page_alloc i915 drm_kms_helper drm i2c_algo_bit toshiba_acpi sparse_keymap wmi toshiba_bluetooth video mac_hid lp parport r8169
[  143.968131]  [<c1044cc2>] warn_slowpath_common+0x72/0xa0
[  143.968141]  [<f8fd7e2a>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  143.968150]  [<f8fd7e2a>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  143.968153]  [<c1044d12>] warn_slowpath_null+0x22/0x30
[  143.968162]  [<f8fd7e2a>] brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  143.968169]  [<f8fca550>] brcms_ops_flush+0x30/0x50 [brcmsmac]
[  144.136190] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  144.136202] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[  144.136204] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  145.169376] wlan0: authenticate with <MAC address removed>
[  145.186059] wlan0: send auth to <MAC address removed> (try 1/3)
[  145.190498] wlan0: authenticated
[  145.192049] wlan0: associate with <MAC address removed> (try 1/3)
[  145.194128] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[  145.194789] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  145.194796] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  145.194799] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  145.194812] wlan0: associated
[ 1337.020815] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1337.020828] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 1337.020833] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1337.985759] wlan0: authenticate with <MAC address removed>
[ 1337.986157] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1337.987667] wlan0: authenticated
[ 1337.988392] wlan0: associate with <MAC address removed> (try 1/3)
[ 1337.990600] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1337.991744] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1337.991751] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 1337.991757] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1337.991770] wlan0: associated
[ 1458.008865] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1458.008879] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 1458.008884] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1458.973825] wlan0: authenticate with <MAC address removed>
[ 1458.975812] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1459.176043] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1459.177559] wlan0: authenticated
[ 1459.180099] wlan0: associate with <MAC address removed> (try 1/3)
[ 1459.182101] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1459.182937] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1459.182945] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 1459.182950] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1459.182961] wlan0: associated
[ 2233.309002] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2233.309016] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2233.309022] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2240.145669] wlan0: authenticate with <MAC address removed>
[ 2240.147707] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2240.348045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2240.552034] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2240.756040] wlan0: authentication with <MAC address removed> timed out
[ 2247.592870] wlan0: authenticate with <MAC address removed>
[ 2247.593908] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2247.796042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2248.000039] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2248.204040] wlan0: authentication with <MAC address removed> timed out
[ 2249.168708] wlan0: authenticate with <MAC address removed>
[ 2249.169809] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2249.254477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2249.372032] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2249.576039] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2249.780027] wlan0: authentication with <MAC address removed> timed out
[ 2252.885093] wlan0: authenticate with <MAC address removed>
[ 2252.889357] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2253.092036] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2253.296037] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2253.500047] wlan0: authentication with <MAC address removed> timed out
[ 2266.217064] wlan0: authenticate with <MAC address removed>
[ 2266.218161] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2266.420021] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2266.624047] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2266.828042] wlan0: authentication with <MAC address removed> timed out
[ 2267.794941] wlan0: authenticate with <MAC address removed>
[ 2267.795032] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2267.996053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2268.200023] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2268.404036] wlan0: authentication with <MAC address removed> timed out
[ 2275.236605] wlan0: authenticate with <MAC address removed>
[ 2275.237813] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2275.440032] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2275.644044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2275.848031] wlan0: authentication with <MAC address removed> timed out
[ 2276.813044] wlan0: authenticate with <MAC address removed>
[ 2276.813899] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2277.016037] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2277.220029] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2277.424031] wlan0: authentication with <MAC address removed> timed out
[ 2291.599720] ieee80211 phy1: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 2291.621524] rtl8187: Customer ID is 0x00
[ 2291.621601] Registered led device: rtl8187-phy1::radio
[ 2291.621645] Registered led device: rtl8187-phy1::tx
[ 2291.621683] Registered led device: rtl8187-phy1::rx
[ 2291.623526] rtl8187: wireless switch is on
[ 2291.624214] usbcore: registered new interface driver rtl8187
[ 2291.625979] rtl8187L: Initializing module
[ 2291.625982] rtl8187L: Wireless extensions version 22
[ 2291.625985] rtl8187L: Initializing proc filesystem
[ 2291.626051] usbcore: registered new interface driver rtl8187L
[ 2293.965747] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2293.966552] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2345.225227] wlan1: authenticate with <MAC address removed>
[ 2345.349691] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2345.352074] wlan1: authenticated
[ 2345.408105] wlan1: associate with <MAC address removed> (try 1/3)
[ 2345.413934] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2345.415014] wlan1: associated
[ 2345.415225] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2374.993290] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2376.972867] wlan1: authenticate with <MAC address removed>
[ 2377.086501] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2377.090524] wlan1: authenticated
[ 2377.152072] wlan1: associate with <MAC address removed> (try 1/3)
[ 2377.154739] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2377.155566] wlan1: associated
[ 2409.602640] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2414.885048] wlan1: authenticate with <MAC address removed>
[ 2414.997904] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2414.999597] wlan1: authenticated
[ 2415.056041] wlan1: associate with <MAC address removed> (try 1/3)
[ 2415.059032] wlan1: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=2)
[ 2415.059872] wlan1: associated
[ 2444.340285] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2453.864785] wlan1: authenticate with <MAC address removed>
[ 2453.974640] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2453.976586] wlan1: authenticated
[ 2454.036076] wlan1: associate with <MAC address removed> (try 1/3)
[ 2454.039408] wlan1: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[ 2454.040121] wlan1: associated
[ 2593.344061] ieee80211 phy1: wlan1: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2595.289676] wlan1: authenticate with <MAC address removed>
[ 2595.422860] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2595.433797] wlan1: authenticated
[ 2595.492044] wlan1: associate with <MAC address removed> (try 1/3)
[ 2595.504618] wlan1: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[ 2595.505339] wlan1: associated
[ 2603.757287] wlan0: authenticate with <MAC address removed>
[ 2603.757869] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2603.960022] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2604.164183] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2604.368039] wlan0: authentication with <MAC address removed> timed out
[ 2611.204952] wlan0: authenticate with <MAC address removed>
[ 2611.205883] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2611.408051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2611.612038] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2611.816028] wlan0: authentication with <MAC address removed> timed out
[ 2618.654607] wlan0: authenticate with <MAC address removed>
[ 2618.654693] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2618.856305] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2619.060045] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2619.264116] wlan0: authentication with <MAC address removed> timed out
[ 2623.849713] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2629.149556] wlan1: authenticate with <MAC address removed>
[ 2629.265927] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2629.270003] wlan1: authenticated
[ 2629.328032] wlan1: associate with <MAC address removed> (try 1/3)
[ 2629.332395] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2629.333265] wlan1: associated
[ 2793.492109] ieee80211 phy1: wlan1: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2795.433113] wlan1: authenticate with <MAC address removed>
[ 2795.546854] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2795.748040] wlan1: send auth to <MAC address removed> (try 2/3)
[ 2795.952041] wlan1: send auth to <MAC address removed> (try 3/3)
[ 2796.156039] wlan1: authentication with <MAC address removed> timed out
[ 2809.244722] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2893.220690] wlan1: authenticate with <MAC address removed>
[ 2893.342501] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2893.544037] wlan1: send auth to <MAC address removed> (try 2/3)
[ 2893.748031] wlan1: send auth to <MAC address removed> (try 3/3)
[ 2893.771166] wlan1: authenticated
[ 2893.836067] wlan1: associate with <MAC address removed> (try 1/3)
[ 2894.040061] wlan1: associate with <MAC address removed> (try 2/3)
[ 2894.244121] wlan1: associate with <MAC address removed> (try 3/3)
[ 2894.260343] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2894.261168] wlan1: associated
[ 2894.261364] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3019.384192] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3031.841660] wlan0: authenticate with <MAC address removed>
[ 3031.843505] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3031.848062] wlan0: authenticated
[ 3031.852037] wlan0: associate with <MAC address removed> (try 1/3)
[ 3031.855089] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3031.855783] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3031.855789] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 3031.855792] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3031.855805] wlan0: associated
[ 3031.855995] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3034.937042] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 3072.889223] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3072.896315] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3072.896328] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 3072.896333] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3079.557057] wlan1: authenticate with <MAC address removed>
[ 3079.669767] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3079.671731] wlan1: authenticated
[ 3079.728053] wlan1: associate with <MAC address removed> (try 1/3)
[ 3079.731723] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3079.732725] wlan1: associated
[ 3113.438135] wlan0: authenticate with <MAC address removed>
[ 3113.438231] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3113.441910] wlan0: authenticated
[ 3113.448063] wlan0: associate with <MAC address removed> (try 1/3)
[ 3113.456040] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3113.456811] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3113.456818] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 3113.456820] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3113.456831] wlan0: associated
[ 3114.547474] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 3170.136382] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3182.138007] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3183.901232] wlan1: authenticate with <MAC address removed>
[ 3184.015071] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3184.024113] wlan1: authenticated
[ 3184.084048] wlan1: associate with <MAC address removed> (try 1/3)
[ 3184.089880] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3184.090975] wlan1: associated
[ 3184.091294] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3211.390476] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3350.803261] ieee80211 phy2: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 3350.825713] rtl8187: Customer ID is 0x00
[ 3350.825796] Registered led device: rtl8187-phy2::radio
[ 3350.825840] Registered led device: rtl8187-phy2::tx
[ 3350.825884] Registered led device: rtl8187-phy2::rx
[ 3350.826470] rtl8187: wireless switch is on
[ 3353.257751] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3353.258824] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3365.584466] wlan0: disassociated from <MAC address removed> (Reason: 8)
[ 3365.588214] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3365.588226] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 3365.588231] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3365.592133] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3381.256856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3384.908824] wlan0: authenticate with <MAC address removed>
[ 3384.909833] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3384.912217] wlan0: authenticated
[ 3384.916035] wlan0: associate with <MAC address removed> (try 1/3)
[ 3384.924046] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3384.926009] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3384.926015] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 3384.926018] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3384.926024] wlan0: associated
[ 3384.926218] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3385.001960] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 3416.673703] wlan1: authenticate with <MAC address removed>
[ 3416.786031] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3416.791463] wlan1: authenticated
[ 3416.848030] wlan1: associate with <MAC address removed> (try 1/3)
[ 3416.857374] wlan1: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3416.858215] wlan1: associated
[ 3416.858425] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3545.080468] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3554.321540] wlan1: authenticate with <MAC address removed>
[ 3554.429759] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3554.433835] wlan1: authenticated
[ 3554.496116] wlan1: associate with <MAC address removed> (try 1/3)
[ 3554.500362] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3554.501083] wlan1: associated
[ 3711.733982] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3723.906965] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3725.422770] wlan1: authenticate with <MAC address removed>
[ 3725.546424] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3725.551838] wlan1: authenticated
[ 3725.612032] wlan1: associate with <MAC address removed> (try 1/3)
[ 3725.616381] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3725.617499] wlan1: associated
[ 3725.617826] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3769.983181] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3776.634017] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3778.157595] wlan1: authenticate with <MAC address removed>
[ 3778.280222] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3778.284865] wlan1: authenticated
[ 3778.348040] wlan1: associate with <MAC address removed> (try 1/3)
[ 3778.352744] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3778.353628] wlan1: associated
[ 3778.353962] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3789.643638] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3794.749230] wlan1: authenticate with <MAC address removed>
[ 3794.865773] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3794.869094] wlan1: authenticated
[ 3794.924036] wlan1: associate with <MAC address removed> (try 1/3)
[ 3794.930977] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3794.931733] wlan1: associated
[ 3866.301110] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 3866.302279] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3866.328205] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3866.328223] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[ 3866.328226] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3956.771339] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3967.257169] wlan0: authenticate with <MAC address removed>
[ 3967.257844] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3967.264405] wlan0: authenticated
[ 3967.268057] wlan0: associate with <MAC address removed> (try 1/3)
[ 3967.272358] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3967.274379] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3967.274385] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 3967.274387] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3967.274401] wlan0: associated
[ 3967.351785] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 4115.673166] wlan1: authenticate with <MAC address removed>
[ 4115.793892] wlan1: send auth to <MAC address removed> (try 1/3)
[ 4115.799823] wlan1: authenticated
[ 4115.860089] wlan1: associate with <MAC address removed> (try 1/3)
[ 4115.866728] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 4115.867677] wlan1: associated
[ 4381.311378] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4475.937442] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4475.948306] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 4475.948320] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 4475.948325] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4480.033476] wlan1: authenticate with <MAC address removed>
[ 4480.145681] wlan1: send auth to <MAC address removed> (try 1/3)
[ 4480.153499] wlan1: authenticated
[ 4480.208126] wlan1: associate with <MAC address removed> (try 1/3)
[ 4480.211622] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4480.212373] wlan1: associated


**************** done ********************


```

---

### Post by bellaseem on 2013-02-27
I wanted to mention also, that the network I'm having trouble with is the wlan1 one... it was connected at the time and working but to my router which is really close (like 2 meters away) from it... 

I also wanted to note that the adapter worked when I first plugged it into Ubuntu, but it was not working well so I installed the RTL8187L drivers from realtek.com using their instructions...

One other thing I noted with this USB adapter is that it gives very good signals for many networks... but it can't connect to many that have signals in the -50 dB range...


** I also wanted to ask about something:
1. When I change the txpower of the adapter, the signal strength does not vary... (I tried a txpower of 1 and a maximum of 30 and nothing changed using iwconfig txpower and the signal stays in the range of -19 to -21 for my router for both txpowers ) Why is that?
2. Should this adapter use ieee802.11 or mac802.11? ( I don't really understand what they mean but out of curiousity...)
3. On windows, the adapter works fine, but it still has trouble connecting to some networks even though the signal shows up as 4 bars and is excellent (in the -40 to -50 dB range...). Why could that be? Is it because I the routers I'm trying to connect to are not hearing me or I'm not hearing them well? Could it be that the adapter is not giving the real signal strength and instead a fake strength? [I think this might be because its packaging says it's 5800mW and 32dBi antenna and other crazy things, which turned out to be a lie...)
4. Since many of you know alot in this field... What is the best way to disable my built-in broadcom wlan adapter and only use the usb adapter? I saw like 4 ways to do it so far (using wicd, using iwconfig down, blacklisting the module, etc...) Which one do you recommend?
5. Will reducing my rate (say from 54Mb to 1Mb increase my range?) How do I change it? using iwconfig wlan1 rate 54M or rate 1M?) and could this create problems when I try to connect? Like I think 802.11n type networks need high rates right?
6. If this USB adapter is not of the best quality, would it be better to let my software do the encrpytion on the computer instead of the hardware of the adapter? (I saw something about this by chili somewhere...)
7. I've read much about DNS servers, is it better to always use google's DNS (8.8.8.8) instead of my default DNS? DNS will only affect how long it takes to resolve the IP when I first open a page in a browser right?

----

Also when I connect with my built-in adapter to the internet, pages load quickly without an initial delay,
however when I connect with this USB adapter there seems to be like a 5-15 second delay before the page starts to load or its name shows up in the tab of the browser. What could possibly be causing this?

---

### Post by bellaseem on 2013-02-27
Update: I have messed around with the USB adapter and it seems that if I use iwconfig wlan1 rate 54M and iwconfig wlan1 rate 1M, there is a big difference in speed... when the rate is set to 1Mb/s browsing becomes faster, but when it's 54Mb/s it almost stops completely... so It seems that there's a problem negotiating the rate if I am correct, right?

Also, on the side note I wanted to know, what parameters should I play around with in order to increase my _range_ on this adapter, the main reason I bought it was to increase my range... I know txpower should help right? and the rate? what else ?

Any help would be greatly appreciated and thank you!

---

### Post by varunendra on 2013-02-27
> **bellaseem said:**
> I was reading through your other posts, you seem to be very knowledgeable
Yeah, sometimes I succeed in fooling people that I am very knowledgeable ;)

Whatever I suggest in wireless issues are mostly stolen ideas from others' threads :P

You have asked so many questions and I like your curiosity. Unfortunately, most of your questions are way beyond my (stolen) knowledge or expertise. So let's just focus on your problem first.

It seems that the proprietary driver you compiled isn't being used at all -
> **bellaseem said:**
> 
```
**** lsmod ****

Module                  Size  Used by
**[COLOR="Navy"]r8187l[/COLOR]**                143393  0 
**[COLOR="Red"]rtl8187[/COLOR]**                56225  0 
eeprom_93cx6           13169  1 [COLOR="Red"]**rtl8187**[/COLOR]
..
**mac80211 **             461261  2 **[COLOR="Red"]rtl8187[/COLOR]**,brcmsmac
..
cfg80211              175574  3 **[COLOR="Red"]rtl8187[/COLOR]**,brcmsmac,**[COLOR="Red"]mac80211[/COLOR]**

**** nm-tool ****

NetworkManager Tool

State: connected (global)

- Device: wlan1  [x] -----------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            **[COLOR="Red"]rtl8187[/COLOR]**
  State:             connected

```

So although your compiled driver (highlighted in Blue) is loaded, the native one is loaded first and is still being used for that interface.

As a test, please try -
```
sudo modprobe -rfv rtl8187
sudo modprobe -rfv r8187l
sudo modprobe -v r8187l
```
..and try to connect. Does it get any better?

This is a temporary change and will be lost on reboot. If it works, we can  blacklist the rtl8187 to make it permanent.

PS:
To answer a few of your questions that I *believe* I can (and I may be giving a wrong advice!),
[LIST=1]
[*]The best way to disable the internal wireless adapter, in my personal, non-professional opinion, is to blacklist the brcmsmac driver
[*]Hardware encryption is a good thing if the driver can handle it. Software encryption is a compromise.
[*]Data rate is best to be left in auto mode. It is fixed only in case of problems which are rare. (By the way, 1M means 1Mb = 1Mega **Bit** per second, which is obviously too slow.)
[*]Likewise, the rest of the options in iwconfig (or other similar commands) are just available tools. They should only be used in case of problems, otherwise the defaults are usually the best and tampering them oftem creates problems.
[/LIST]
I may try to answer the rest of your questions at the risk of confusing you :P, but let's first get your main problem solved.

---

### Post by Lisiano on 2013-02-27
Could you try moving away from the router? The signal could be too strong. You should also try to switch to a different channel as the one you are currently on, is the most popular in your area (Around half of the APs are using that channel). As far as a better signal, any WiFi adapter with an external antennae is heaps better than a WiFi adapter with an integrated one. You may try to purchase stronger antennaes if you wish, or even get a directional antennae (Tons better but it does mean you have to aim at the AP).

As varunendra said, you shouldn't mess with any options, almost always the defaults/automatic values are the best ones.

I'm no expert on the driver front btw.

Note: If you want to really want to make your WiFi adapter work at a higher output power, you may change your WiFi adapters regulatory domain... But since that, depending on your country, will make your device work outside the law, I'm not going to tell you how to do it. Google is your friend though.

EDIT: Just noticed the question list.
1. Changing txpower changes the power rating at which your device operates, it however will not change what you receive as the signal strength from the AP is the same. This will change the power at which YOU send stuff at, the AP stays at the same power and you still receive at the same power. Side note: the T in TX means Transmission or Sending stuff, RX means Receiving.
2. Those are different drivers, I'll leave this one to varunendra but I think you want the mac one.
3. -40 - -50 dB is quite a good signal, but considering you have a highly sensitive adapter, the APs are probably very far away and they can't operate at higher power levels, or maybe it's just overly high network congesting (Again, try to find a vacant channel). [If my quick research is right, it can do up to 1W and the antennae is a 2dBi]
4. Blacklisting. This will prevent the device from even powering up (AFAIK).
5. Leave it at defaults, your adapter and the AP should negotiate the correct rate depending on your signal and will increase/decrease the rate as needed.
6. Alfa adapters are awesome. They are very powerful and can be used for some... Interesting projects.
7. Yes and no. It's a good idea to use Google DNS and/or OpenDNS when possible but you should remember to add your default (Router/ISP) DNS as your ISP might have stuff accessible only to subscribers, which will only be resolved by using their DNS. Remember, Linux is not Windows, you are not limited to only having 2 DNS entries. You can configure how many DNS entries you want, for example, my desktop is currently using the Google Primary (8.8.8.8) and Secondary (8.8.4.4) DNS while also using my router in that order. Also having multiple DNS entries works as a kind of failsafe, for example the Primary Google one dies, your PC will try the Secondary, which for example also dies, your PC will then try the OpenDNS servers, then your router (5 points of failure, all of which failing at the same time is very low). Also, Google has the fastest servers in the world, so using them as a DNS can increase the speed of DNS resolution quite a bit.

> One other thing I noted with this USB adapter is that it gives very good signals for many networks... but it can't connect to many that have signals in the -50 dB range...
Your adapter is sensitive enough to receive signals from APs that are quite far. My router is in the range of -60 from my desktop and a few other networks at -80.

---

### Post by bellaseem on 2013-02-27
EDIT: Ok I did the things you asked for but then I couldn't connect, then a "kernel panic" so I restarted... and 3 things happened basically after I restarted and did the suggested things...
1- The Network manager works better now (before it was not showing networks sometimes and took long to refresh the list)
2- I am seeing many more networks (about 15 more!)
3- I can't connect anymore except to a network that very close... also a "Kernel panic" thing occured, screen turned into a terminal-like full screen and I can't do anything so I rebooted again... the kernel panic says this on the last 2 lines
"Kernel panic - not syncing: Fatal exception in interrupt
panic occured, switching back to text console"

Also thanks for answering the questions you could varunendra! much appreciated :).

---

### Post by varunendra on 2013-02-27
> **bellaseem said:**
> however, I can't connect to them for some reason anymore.
Can you provide the exact link of the driver you have compiled?

As of now, I get a database error on the site if I follow the link to RTL8187 driver. I could really use an output of -
```
modinfo r8187l
```
It will give me, among some other things, a detail of parameters that can be used with the driver. May be we'll need one to make the connectivity easier.

---

### Post by bellaseem on 2013-02-27
[[COLOR=#000000]Lisiano[/COLOR]]("http://ubuntuforums.org/member.php?u=1108763"), thanks for the tip about the router and adapter being too close... I actually noticed a difference! (though it's counterintuitive lol)
-but how do I switch to a different channel? I have to do it on the router also right? My noise level is showing at -125 btw, is that bad or good?
-have you tried any directional antennas that you would suggest? how precisely do I have to aim (I know it's more precise for higher gain right?
- Also when I connect with my built-in adapter to the internet, pages load quickly without an initial delay,
however when I connect with this USB adapter there seems to be like a 5-15 second delay before the page starts to load or its name shows up in the tab of the browser. What could possibly be causing this?

Thank you so much for answering the questions!!! Greatly appreciated :)

here's the modinfo!
```
 modinfo r8187l
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/r8187l.ko
description:    Linux driver for Realtek RTL8187 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
version:        V 1.1
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     E1E15894BD1429E2987D5B8
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.5.0-25-generic SMP mod_unload modversions 686 
parm:           ifname:charp
parm:           devname: Net interface name,ath%d=default
parm:           channels: Channel bitmask for specific locales. NYI (int)

```

The exact driver link is this:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true)

it has a description saying : "Linux driver for Kernel 3.0.0/3.1.0/3.2.0" [not for my kernel is it? I guess that's why I got a kernel panic o.o]
version "1041" Update time: "2012/2/9"	size "1753k"

-Btw, one question, my adapter's package says 8187L but I'm not sure if they're correct, how can I know if that is really the driver that is needed?

and thanks again :)

---

### Post by Lisiano on 2013-02-27
The fact being close to an AP is bad is due to packet collision (Think of 2 people throwing a ball and they collide mid air, the closer they are, the higher the chance the balls will collide)
You can change the channel from your router settings. Also, never rely on Automatic channel selection, most of the time it fails and selects the first channel.
For noise levels, no idea. Guessing since it's noise, it's a good thing it's low.
Nope, I have not tried any directional antennaes, but they work in a cone like shape, so you don't have to be exactly precise, probably "General direction of" precise will be good enough, of course the more precise you are the better.
Again, Linux decides at what power to work at. Usually it is correct in it's assumptions (Why use more power than needed?). Changing the regulatory domain only changes the power level limits (upper limit). 
Yet Again. Signal level does not depend on **TX**power. It only affects the power at which YOU send data at. How good the signal is depends on the adapters sensitivity. (Which you can't change)

EDIT: > Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

---

### Post by bellaseem on 2013-02-27
Hey I noticed that you answered the question about the txpower in the first post just now... So I edited the post and replaced the question with this:

"When I connect with my built-in adapter to the internet, pages load quickly without an initial delay,
however when I connect with this USB adapter there seems to be like a 5-15 second delay before the page starts to load or its name shows up in the tab of the browser. What could possibly be causing this?"

Also, I posted the modinfo and link to the realtek driver in the older post... (for varunendra)

---

### Post by Lisiano on 2013-02-27
> **bellaseem said:**
> "When I connect with my built-in adapter to the internet, pages load quickly without an initial delay,
however when I connect with this USB adapter there seems to be like a 5-15 second delay before the page starts to load or its name shows up in the tab of the browser. What could possibly be causing this?"This is probably due to the driver part of your problem.

---

### Post by bellaseem on 2013-02-27
Lisiano, I'll take your word for it :). Thank you for taking the time to answer all those questions, your help is much appreciated. I'll PM you if anything else pops up seeing that you know so much more than me. Thanks again!

---

### Post by Lisiano on 2013-02-27
I don't know everything, I do know a lot of stuff but... Driver stuff... Nope. I'm bad at those. Also, I'd prefer you post your questions here so that anyone who has the same question can find the answer easily and if I'm wrong somewhere, some could correct me.

---

### Post by bellaseem on 2013-03-01
Any updates on this varunendra? Should I try to set ubuntu to use the other drivers permanently and see how it goes after a reboot? Also, I noticed that when I set the rate to 1M, I can connect much more easily and the speed is faster as compared to other rates...But everytime I reboot, the settings return to the defaults, how can I change them so that the rate is permanently 1Mb/s?

---

### Post by varunendra on 2013-03-03
> **bellaseem said:**
> Any updates on this varunendra?
First of all, sorry for not being able to reply before. I got too busy to focus.

Now, let me first address a few previous posts of yours -
> **bellaseem said:**
> [URL="http://ubuntuforums.org/member.php?u=1108763"]
- Also when I connect with my built-in adapter to the internet, pages load quickly without an initial delay,
however when I connect with this USB adapter there seems to be like a 5-15 second delay before the page starts to load or its name shows up in the tab of the browser. What could possibly be causing this?
I have been wondering why do you want to use an external adapter if the internal one is working fine? Most people prefer the opposite. Sorry if I missed any explanation to this in your posts.

As for the delay, I'm not sure, but most probably it is because of the poor connection quality with the usb adapter's driver.

> **bellaseem said:**
> ..
-Btw, one question, my adapter's package says 8187L but I'm not sure if they're correct, how can I know if that is really the driver that is needed?
Like Lisiano quoted, your lsusb gives-
> Bus 002 Device 003: ID **[COLOR="#B22222"]0bda[/COLOR]:[COLOR="#000080"]8187[/COLOR]** Realtek Semiconductor Corp. **RTL8187 Wireless Adapter**
However, the name of the chip alone can sometimes be misleading. The guaranteed identification is **[COLOR="#B22222"]VID[/COLOR][COLOR="#000080"][noparse]:PID[/noparse][/COLOR]** (Vendor ID : Product ID), which is confirmed for the driver in modinfo-
> ```
 modinfo r8187l
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/r8187l.ko
....
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v**[COLOR="#B22222"]0BDA[/COLOR]**p**[COLOR="#000080"]8187[/COLOR]**d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*
```

> **bellaseem said:**
> Hey I noticed that you answered the question about the txpower in the first post just now... So I edited the post and replaced the question.. 
**[COLOR="#FF0000"]Please refrain from doing this.[/COLOR]** As far as I know, editing posts to 'change' questions/facts is frowned upon here, as it confuses those who are answering you and obviously those who would look at the thread later.
You can edit your posts to simply add 'Updates' in it, but in most cases it is better to just ask the questions in a new post.

> **Lisiano said:**
> Also, I'd prefer you post your questions here so that anyone who has the same question can find the answer easily and if I'm wrong somewhere, some could correct me.
A BIG +1 to this. :)

Asking and answering in thread posts has double-side advantage. The question will have more chance of getting more and accurate answers, and the answers will be able to help more people. That's why support questions in PM are generally discouraged on forums.

Now the answer to your last question-
> **bellaseem said:**
> Should I try to set ubuntu to use the other drivers permanently and see how it goes after a reboot? Also, I noticed that when I set the rate to 1M, I can connect much more easily and the speed is faster as compared to other rates...But everytime I reboot, the settings return to the defaults, how can I change them so that the rate is permanently 1Mb/s?
If the driver performance is definitively better than the native one, then it is better we block the native ones and make the compiled one permanent. Ane be aware that you will have to compile it again whenever you get a kernel update. (Oh, btw it is no problem in realtek advertising the driver as meant for an older kernel version than your current one - as long as it can be successfully compiled on it.)

I thought the "rate" option for iwconfig is permanent. But if it is not, you can add the following line in your /etc/rc.local file to make it permanent -
```
iwconfig wlan1 rate 1M
```
Make sure the above line is added 'Before' the last line in the script that says "**exit 0**"

I would suggest to make it as higher as possible without performance loss, then append "auto" after that fixed speed. For example -
```
iwconfig wlan1 rate 24M auto
```
This will force it to use a speed of 24M, and lower as suitable. Although using "auto" with 1M (if that turned out to be the only rate with best speed) doesn't make sense as there is no lower speed than 1M.
You can find the speeds supported by the router(s) with -
```
iwlist scan
```

Some additional/alternate ways to make speeds better -
[LIST]
[*]If your router uses N channel, turn it off from its management console.
[*]Set IPv6 Method to "Ignore" in Network Manager. You can also permanently disable it by following this post - [http://ubuntuforums.org/showthread.php?t=2083341&p=12351792#post12351792](http://ubuntuforums.org/showthread.php?t=2083341&p=12351792#post12351792)
[/LIST]

---

### Post by bellaseem on 2013-03-03
Thank varunendra, you helped me understand modules and how they work... I blacklisted the the rtl8187 module and let the r8187l one load, and set the rate lower, and disabled IPv6, and things have improved alot. Marked as solved.

---

