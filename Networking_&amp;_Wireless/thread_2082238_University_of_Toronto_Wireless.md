---
title: "University of Toronto Wireless"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by mabubakr94 on 2012-11-08
Hello.

I am a new Ubuntu user looking to get familiar with how Unix operating systems work. I really like the operating system even though I had to mess with a lot of stuff to get it working optimally. One issue I cannot seem to fix is the ability to connect to my universities wireless.

They use username and password security, it worked on the same laptop on Windows, but on Ubuntu the authentication screen continously pops up.

It works on the Comp Sci wireless which uses simple WEP security and then SSH login but that's not good enough for me as that wireless is only available in the engineering and comp sci buildings.

Links of interest for wireless: (Works on Windows, Mac, and even Android, so should work on Ubuntu).
[http://help.ic.utoronto.ca/index.php?action=artikel&lang=en&cat=20&id=704&artlang=en#UofT](http://help.ic.utoronto.ca/index.php?action=artikel&lang=en&cat=20&id=704&artlang=en#UofT) -- UofT wireless doesn't work.
[http://help.ic.utoronto.ca/content/20/1806/en/connecting-to-the-uoft-wireless-network-with-your-android-device-233-and-higher.html](http://help.ic.utoronto.ca/content/20/1806/en/connecting-to-the-uoft-wireless-network-with-your-android-device-233-and-higher.html) -- The Android configuration page is the one that shows most settings, as other OS do them automatically.

**_Computer Information:_**

**Machine Brand and Model:** Acer Aspire V5-471 (Laptop)

**Wireless Brand, Model and Wireless Chipset:**
Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

**Interface:**
wlan0 IEEE 802.11abgn ESSID:"Abubakr"
Mode: Managed Frequency: 2.412GHz Bit Rate: 1 Mb/s Tx-Power = 16dBm

Let me know if you need more information. Thanks!

---

### Post by howefield on 2012-11-08
> **mabubakr94 said:**
> Let me know if you need more information. Thanks!

What was the advice from the University IT support ?

---

### Post by mabubakr94 on 2012-11-08
Unfortunately they do not offer support for Linux when it comes to the UofT Wireless. We use Linux for our CS computers but we have our own CS wireless in those buildings. It would be amazing if this issue and the issue of not shutting down at times is solved as then I could easily switch 100% to Ubuntu for my laptop.

---

### Post by varunendra on 2012-11-09
Please try:
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
It's a temporary test that will be reset after reboot. If it works, we'll make it permanent.

If it doesn't work, please run (just copy-paste in the terminal)-
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download and run 'wireless_script' which would create a detailed summary of your wireless settings and save it in a file named 'netinfo.txt' in your home directory. Copy-paste its contents in your next post (paste it between 'Code' tags using **#** at the top of edit box in which you create new posts).

---

### Post by mabubakr94 on 2012-11-09
Awesome, it has worked. If you don't mind me asking, can you explain what exactly those commands do? I tried to read up on it a little bit and all I got was the manprobe allows us to add or remove modules from the kernel.

How can I go about making this permanent? 

Also, if it isn't too much trouble, would you also know how to fix this shutdown bug? When I shutdown, everything turns off but after about 2-3 seconds, it boots up again. Or should I just make another thread in the hardware section?

Thanks a lot, once again.

Edit: Judging by the command names, I guess it makes the software handle encryption instead of hardware?

---

### Post by mabubakr94 on 2012-11-09
It stopped working again...

Edit: OK, so it works occasionally by restarting laptop and trying again. Here is the file you requested, I generated it while I was connected to the UofT wireless, when it worked.

```

*************** info trace ****************



**** uname -a ****


Linux Abubakr-Laptop 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
	Subsystem: Acer Incorporated [ALI] Device [1025:0724]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e052]
	Kernel driver in use: ath9k


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 12cf:0200  
Bus 003 Device 003: ID 04f2:b335 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:"UofT"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC address removed>   
          Bit Rate=162 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0



**** rfkill ****


1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
ath9k                 131308  0 
mac80211              539908  1 ath9k
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              206566  3 ath9k,mac80211,ath
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
ext2                   72880  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  2 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12529  2 
wmi                    19070  1 acer_wmi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
psmouse                95552  0 
serio_raw              13215  0 
joydev                 17457  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
lpc_ich                17061  0 
i915                  520629  3 
microcode              22803  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
video                  19335  2 acer_wmi,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
r8169                  61650  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [UofT] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           162 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 80 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    Mobile APL:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 77 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 85 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 85 WEP
    cslab:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 82 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 80 WEP
    cslab:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 72 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 74 WEP
    cslab:           Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 82 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 84 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 47 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 47 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 54 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 52 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 27 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 19 WEP
    UofT:            Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 67 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 80 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5745 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WEP
    *UofT:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 78 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 47 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP

  IPv4 Settings:
    Address:         142.1.188.93
    Prefix:          22 (255.255.252.0)
    Gateway:         142.1.188.1

    DNS:             142.1.208.1
    DNS:             128.100.96.34


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
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014af6c2036
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010008
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B8465040402000000050400A00000090881086BAF140000000A04090000000B04040000000C03002800
          Cell 02 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002621b1a71e9
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010E00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E20000000106000CE60B5720040402000000050400180000090869D0181B620200000A040F0000000B04020000000C03002800
          Cell 03 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003844d26036
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040402000000050400080000090869B0D044380000000A04090000000B04020000000C03002800
          Cell 04 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000240c2017b
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E040402000000050400AC00000908EE8E3C3E020000000A04090000000B04040000000C03002800
          Cell 05 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139dac705c
                    Extra: Last beacon: 336ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 05050001000080
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC890404020000000504008401000908713CAC9D130000000A04090000000B04010000000C03002800
          Cell 06 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125bbff036
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010500036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB04040200000005040030000009087368BE5B120000000A040F0000000B04020000000C03002800
          Cell 07 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e6ea5b443
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B00000000106000CE60B7253040402000000050400E00000090868D8A46E0E0000000A04090000000B04040000000C03002800
          Cell 08 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd76d1e82
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE040402000000050400BC00000908F1236CD73B0000000A04090000000B04040000000C03002800
          Cell 09 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002819d39036
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004220000000106000CE60AFC54040402000000050400380000090894116919280000000A040B0000000B04070000000C03002800
          Cell 10 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000260f5c1bd
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D0404020000000504006401000908836CF560020000000A04090000000B04010000000C03002800
          Cell 11 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000119211780ff
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B30000000106000CE60B71FE040402000000050400EC0000090869B41621190100000A04090000000B04040000000C03002800
          Cell 12 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff9b21a2
                    Extra: Last beacon: 324ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E040402000000050400880100090875F09AFF260000000A04090000000B04010000000C03002800
          Cell 13 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002621b1a7036
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E20000000106000CE60B572004040200000005040068000009086C20191B620200000A040F0000000B04030000000C03002800
          Cell 14 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000240c202db
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E040402000000050400FC000009086B44C140020000000A04090000000B04050000000C03002800
          Cell 15 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139dae05f9
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010900026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC890404020000000504004400000908858CAC9D130000000A04090000000B04020000000C03002800
          Cell 16 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125bbff43a
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB040402000000050400800000090874B8BE5B120000000A040F0000000B04030000000C03002800
          Cell 17 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e6ea42308
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B00000000106000CE60B725304040200000005040030010009086598A36E0E0000000A04090000000B04050000000C03002800
          Cell 18 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016b34d75036
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BC0000000106000CE60B8492040402000000050400C0000009086658D6346B0100000A04090000000B04040000000C03002800
          Cell 19 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd7d941ba
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404020000000504000C01000908D54A55D53B0000000A04090000000B04050000000C03002800
          Cell 20 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000260f5c056
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101090003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D04040200000005040024000009085EE0705E020000000A04090000000B04020000000C03002800
          Cell 21 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000234a17a3128
                    Extra: Last beacon: 304ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E90000000106000CE60B5799040402000000050400740100090889C8829D340200000A040F0000000B04010000000C03002800
          Cell 22 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff91c1b5
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010008
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010800026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E04040200000005040048000009086C5090FF260000000A04090000000B04020000000C03002800
          Cell 23 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002456373036
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404020000000504007C010009081B91B353240000000A040B0000000B04100000000C03002800
          Cell 24 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002456328145
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404020000000504007C010009087791B353240000000A040B0000000B040B0000000C03002800
          Cell 25 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024563733f5
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404020000000504007C01000908BB91B353240000000A040B0000000B04060000000C03002800
          Cell 26 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000240c07036
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E0404020000000504004C010009082F8F3C3E020000000A04090000000B04010000000C03002800
          Cell 27 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003844d0d549
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040402000000050400A8000009086DC0CF44380000000A04090000000B04040000000C03002800
          Cell 28 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c9406c374
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010048
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA040402000000050400C80000090889D005941C0100000A04090000000B04040000000C03002800
          Cell 29 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e6ea29041
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 05050001000008
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B00000000106000CE60B725304040200000005040080010009086958A26E0E0000000A04090000000B04010000000C03002800
          Cell 30 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016b34d5c088
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010002
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BC0000000106000CE60B849204040200000005040010010009086B18D5346B0100000A04090000000B04050000000C03002800
          Cell 31 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd76c92db
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404020000000504005C01000908C8246CD73B0000000A04090000000B04010000000C03002800
          Cell 32 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000234a10ef8cd
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E90000000106000CE60B579904040200000005040034000009085A680DA1340200000A040F0000000B04020000000C03002800
          Cell 33 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000119211462f0
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B30000000106000CE60B71FE0404020000000504008C0100090863341421190100000A04090000000B04010000000C03002800
          Cell 34 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000245638c14f
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404020000000504003C000009089B91B353240000000A040B0000000B04070000000C03002800
          Cell 35 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014af6c2750
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B84650404020000000504000000000908BCB2E6AC140000000A04090000000B04020000000C03002800
          Cell 36 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003844cf40e9
                    Extra: Last beacon: 376ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040402000000050400F8000009087580CE44380000000A04090000000B04050000000C03002800
          Cell 37 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000240c202ec
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E0404020000000504000C000009080D8F3C3E020000000A04090000000B04020000000C03002800
          Cell 38 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139da950dc
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 05050001000001
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010900026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC89040402000000050400E400000908967CA89D130000000A04090000000B04040000000C03002800
          Cell 39 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e6ea100be
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010100
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B00000000106000CE60B725304040200000005040040000009086D889F6E0E0000000A04090000000B04020000000C03002800
          Cell 40 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd7dad252
                    Extra: Last beacon: 264ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404020000000504001C00000908424B55D53B0000000A04090000000B04020000000C03002800
          Cell 41 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000260f5c086
                    Extra: Last beacon: 264ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D040402000000050400C4000009086ACCF460020000000A04090000000B04040000000C03002800
          Cell 42 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000234a17bc4be
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E90000000106000CE60B57990404020000000504008400000908678C7AA1340200000A040F0000000B04030000000C03002800
          Cell 43 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001192112d036
                    Extra: Last beacon: 568ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B30000000106000CE60B71FE0404020000000504004C000009086D641121190100000A04090000000B04020000000C03002800
          Cell 44 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff93791d
                    Extra: Last beacon: 864ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010800026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E040402000000050400E800000908738092FF260000000A04090000000B04040000000C03002800
          Cell 45 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000151993b6099
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010200036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B04040200000005040018000009086CC03999510100000A04090000000B04020000000C03002800
          Cell 46 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003844cf416e
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0506000100220010
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040402000000050400480100090889D0CE44380000000A04090000000B04010000000C03002800
          Cell 47 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125bc4a083
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB04040200000005040070010009086C58C45B120000000A040F0000000B04010000000C03002800
          Cell 48 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000281969634f
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004220000000106000CE60AFC54040402000000050400780100090821116919280000000A040B0000000B04100000000C03002800
          Cell 49 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000281969648c
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004220000000106000CE60AFC54040402000000050400780100090872116919280000000A040B0000000B040B0000000C03002800
          Cell 50 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028196967d0
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004220000000106000CE60AFC540404020000000504007801000908B3116919280000000A040B0000000B04060000000C03002800
          Cell 51 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff9cb04b
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E04040200000005040038010009086B309CFF260000000A04090000000B04050000000C03002800
          Cell 52 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001519938409e
                    Extra: Last beacon: 400ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010200036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B04040200000005040008010009086A903799510100000A04090000000B04050000000C03002800
          Cell 53 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002621b18e3fc
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E20000000106000CE60B572004040200000005040058010009086D80181B620200000A040F0000000B04010000000C03002800
          Cell 54 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139dae0036
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010900026400002486000044425E0062422F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC8904040200000005040034010009087A7CAD9D130000000A04090000000B04050000000C03002800
          Cell 55 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014af65e0bc
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B84650404020000000504004001000908DFB2E6AC140000000A04090000000B04010000000C03002800
          Cell 56 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b710678658
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004270000000106000CE60A830F0404020000000504008C0100090868546710B70000000A04090000000B04010000000C03002800
          Cell 57 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014af6c2351
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B8465040402000000050400F00000090851B2E6AC140000000A04090000000B04050000000C03002800
          Cell 58 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036f3eb8238
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004300000000106000CE60A8561040402000000050400C0000009087088EAF3360000000A04090000000B04040000000C03002800
          Cell 59 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000151993520f9
                    Extra: Last beacon: 584ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 05050001000010
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010200036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B040402000000050400580100090873C03499510100000A04090000000B04010000000C03002800
          Cell 60 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001519939d1b4
                    Extra: Last beacon: 320ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010200036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B040402000000050400B8000009086DD03899510100000A04090000000B04040000000C03002800
          Cell 61 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d84fa73036
                    Extra: Last beacon: 4816ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010500036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004F00000000106000CE60B571F04040200000005040050000009086FC8A54FD80000000A040F0000000B04030000000C03002800
          Cell 62 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c93f40036
                    Extra: Last beacon: 1500ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010004
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA04040200000005040018010009088360F3931C0100000A04090000000B04050000000C03002800
          Cell 63 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b710727426
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010002
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004270000000106000CE60A830F0404020000000504003C010009086CF47110B70000000A04090000000B04050000000C03002800
          Cell 64 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000260f43036
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D04040200000005040014010009086A8CF360020000000A04090000000B04050000000C03002800
          Cell 65 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016b34d5c083
                    Extra: Last beacon: 372ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BC0000000106000CE60B849204040200000005040060010009087068D5346B0100000A04090000000B04010000000C03002800
          Cell 66 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7106148af
                    Extra: Last beacon: 1496ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004270000000106000CE60A830F040402000000050400EC0000090885746010B70000000A04090000000B04040000000C03002800
          Cell 67 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000119210b0036
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B30000000106000CE60B71FE0404020000000504003C0100090873840A21190100000A04090000000B04050000000C03002800
          Cell 68 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c9406c1c0
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA04040200000005040028000009086B3005941C0100000A04090000000B04020000000C03002800
          Cell 69 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d84fb6d0d1
                    Extra: Last beacon: 3812ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004F00000000106000CE60B571F04040200000005040000000009086F18B54FD80000000A040F0000000B04020000000C03002800
          Cell 70 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d84fc99036
                    Extra: Last beacon: 2504ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010500036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004F00000000106000CE60B571F04040200000005040040010009086E18C94FD80000000A040F0000000B04010000000C03002800
          Cell 71 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036f3e9f09f
                    Extra: Last beacon: 380ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010008
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004300000000106000CE60A856104040200000005040010010009086E48E9F3360000000A04090000000B04050000000C03002800
          Cell 72 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c9406c0dc
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 05050001000080
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA0404020000000504006801000908737006941C0100000A04090000000B04010000000C03002800
          Cell 73 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051b1df9036
                    Extra: Last beacon: 6420ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010002
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BD0000000106000CE60B71E8040402000000050400C400000908699CDEB1510000000A04090000000B04040000000C03002800
          Cell 74 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016b34d75036
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BC0000000106000CE60B8492040402000000050400200000090872B8D5346B0100000A04090000000B04020000000C03002800
          Cell 75 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c553a036
                    Extra: Last beacon: 944ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE60004330000000106000CE60863230404020000000504001C01000908740453C5000000000A04090000000B04050000000C03002800
          Cell 76 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051b1fa2036
                    Extra: Last beacon: 4720ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010002
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BD0000000106000CE60B71E804040200000005040024000009086A8CF8B1510000000A04090000000B04020000000C03002800
          Cell 77 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7107409a1
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004270000000106000CE60A830F0404020000000504004C000009086D947210B70000000A04090000000B04020000000C03002800
          Cell 78 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036f3da5824
                    Extra: Last beacon: 1464ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004300000000106000CE60A8561040402000000050400200000090883B8D8F3360000000A04090000000B04020000000C03002800
          Cell 79 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001fc54850181
                    Extra: Last beacon: 10256ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 80 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001fc565b6faf
                    Extra: Last beacon: 10244ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 81 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024559c8180
                    Extra: Last beacon: 10240ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010700023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404010000000504003C0000090884049B55240000000A040B0000000B04100000000C03002800
          Cell 82 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024559c82d8
                    Extra: Last beacon: 10240ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404010000000504003C00000908A5049B55240000000A040B0000000B040B0000000C03002800
          Cell 83 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024559c8468
                    Extra: Last beacon: 10240ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0506000104000201
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010700023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404010000000504003C00000908B3049B55240000000A040B0000000B04060000000C03002800
          Cell 84 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024559c8180
                    Extra: Last beacon: 10220ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010402
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004230000000106000CE60AFCF70404010000000504008C000009087E549B55240000000A040B0000000B04070000000C03002800
          Cell 85 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c5585036
                    Extra: Last beacon: 616ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE60004330000000106000CE60863230404020000000504006C01000908790458C5000000000A04090000000B04010000000C03002800
          Cell 86 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c5d470901bc
                    Extra: Last beacon: 9988ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 87 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000490ff935ad8
                    Extra: Last beacon: 9972ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 88 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002487e9d85fe
                    Extra: Last beacon: 9988ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 89 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c55d0036
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE60004330000000106000CE6086323040402000000050400CC000009086F145CC5000000000A04090000000B04040000000C03002800
          Cell 90 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c5553066
                    Extra: Last beacon: 904ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600025300002475000044425E0062422F00
                    IE: Unknown: DD38000CE60004330000000106000CE60863230404020000000504002C000009086DA453C5000000000A04090000000B04020000000C03002800
          Cell 91 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001331f3ae352
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010000036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004FD0000000106000CE60B73BA04040200000005040034000009086F5C391F330100000A04090000000B04020000000C03002800
          Cell 92 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000384448e095
                    Extra: Last beacon: 9244ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B604040200000005040008000009086E304744380000000A04090000000B04020000000C03002800
          Cell 93 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036f3dd71ab
                    Extra: Last beacon: 1180ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0506000100040808
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004300000000106000CE60A856104040200000005040060010009088018DDF3360000000A04090000000B04010000000C03002800
          Cell 94 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c93725300
                    Extra: Last beacon: 8988ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010010
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA0404010000000504007800000908781071931C0100000A04090000000B04020000000C03002800
          Cell 95 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038447e0291
                    Extra: Last beacon: 8988ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F202010108000786000029A8000044755E0062532F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040401000000050400F80000090878407D44380000000A04090000000B04040000000C03002800
          Cell 96 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002608543f8
                    Extra: Last beacon: 8988ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D040401000000050400640100090887EC8460020000000A04090000000B04050000000C03002800
          Cell 97 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d84f546531
                    Extra: Last beacon: 8976ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010008
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010F00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004F00000000106000CE60B571F04040100000005040050000009087AF8524FD80000000A040F0000000B04020000000C03002800
          Cell 98 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015198f9dfc3
                    Extra: Last beacon: 8972ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010040
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600076400002986000044755E0062532F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B04040100000005040018000009088420F898510100000A04090000000B04010000000C03002800
          Cell 99 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff2aa2d1
                    Extra: Last beacon: 8968ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010008
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010C00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E040401000000050400380100090885202AFF260000000A04090000000B04040000000C03002800
          Cell 100 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014aef0c781
                    Extra: Last beacon: 8968ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 05050001000001
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010900036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B8465040401000000050400000000090888F8EEAE140000000A04090000000B04010000000C03002800
          Cell 101 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd78a1069
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404010000000504005C010009086E9289D73B0000000A04090000000B04050000000C03002800
          Cell 102 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000119201d8180
                    Extra: Last beacon: 8968ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B30000000106000CE60B71FE0404010000000504009C000009087A641C20190100000A04090000000B04020000000C03002800
          Cell 103 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000234a038bac5
                    Extra: Last beacon: 8956ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E90000000106000CE60B5799040401000000050400D40000090803C237A0340200000A040F0000000B04030000000C03002800
          Cell 104 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000026086d4db
                    Extra: Last beacon: 8964ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 05080001001000000009
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D0404010000000504002400000908833C8560020000000A04090000000B04010000000C03002800
          Cell 105 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024050274d
                    Extra: Last beacon: 8952ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E0404010000000504005C0000090888D54E40020000000A04090000000B04020000000C03002800
          Cell 106 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038447e11d4
                    Extra: Last beacon: 8960ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010002
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F202010107000786000029A8000044755E0062532F00
                    IE: Unknown: DD38000CE600042A0000000106000CE60A81B6040401000000050400480100090877907D44380000000A04090000000B04050000000C03002800
          Cell 107 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015198f9c562
                    Extra: Last beacon: 8960ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010600076400002986000044755E0062532F00
                    IE: Unknown: DD38000CE600041A0000000106000CE608736B04040100000005040068000009087570F898510100000A04090000000B04020000000C03002800
          Cell 108 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000234a0395d1b
                    Extra: Last beacon: 8956ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E90000000106000CE60B5799040401000000050400340000090828C237A0340200000A040F0000000B04010000000C03002800
          Cell 109 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002404f32d8
                    Extra: Last beacon: 8956ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E0404010000000504004C0100090814D54E40020000000A04090000000B04050000000C03002800
          Cell 110 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002404f852e
                    Extra: Last beacon: 8952ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E040401000000050400FC0000090867D54E40020000000A04090000000B04040000000C03002800
          Cell 111 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000026086dd6e
                    Extra: Last beacon: 8952ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D0404010000000504007400000908DC858560020000000A04090000000B04020000000C03002800
          Cell 112 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125b3c8dd7
                    Extra: Last beacon: 8948ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB0404010000000504003000000908ECDE3A5B120000000A040F0000000B04010000000C03002800
          Cell 113 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125b3bf02b
                    Extra: Last beacon: 8948ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB040401000000050400D0000009083FDF3A5B120000000A040F0000000B04030000000C03002800
          Cell 114 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125b3c427f
                    Extra: Last beacon: 8948ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004E80000000106000CE60B56EB040401000000050400800000090860DF3A5B120000000A040F0000000B04020000000C03002800
          Cell 115 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d84f55282c
                    Extra: Last beacon: 8948ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004F00000000106000CE60B571F0404010000000504000000000908BB70534FD80000000A040F0000000B04010000000C03002800
          Cell 116 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd78a62be
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404010000000504000C01000908BF9289D73B0000000A04090000000B04040000000C03002800
          Cell 117 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd78b04dd
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404010000000504006C00000908E29289D73B0000000A04090000000B04020000000C03002800
          Cell 118 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd78b3cb2
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010090
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010900036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600042F0000000106000CE60888FE0404010000000504001C000009087D8489D73B0000000A04090000000B04010000000C03002800
          Cell 119 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c93725c8a
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 05050001001210
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BE0000000106000CE60BB1CA040401000000050400180100090874B071931C0100000A04090000000B04040000000C03002800
          Cell 120 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026ff2ac156
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010C00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE608737E04040100000005040088010009087C702AFF260000000A04090000000B04050000000C03002800
          Cell 121 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014aef0e6d6
                    Extra: Last beacon: 8944ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010900036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B846504040100000005040050000009087B48EFAE140000000A04090000000B04020000000C03002800
          Cell 122 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139d4041d2
                    Extra: Last beacon: 8940ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC8904040100000005040084010009086BAF3F9D130000000A04090000000B04050000000C03002800
          Cell 123 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139d409427
                    Extra: Last beacon: 8940ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC890404010000000504003401000908BDAF3F9D130000000A04090000000B04040000000C03002800
          Cell 124 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139d413647
                    Extra: Last beacon: 8940ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC890404010000000504009400000908E0AF3F9D130000000A04090000000B04020000000C03002800
          Cell 125 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000139d418932
                    Extra: Last beacon: 8940ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004110000000106000CE608EC89040401000000050400440000090805B03F9D130000000A04090000000B04010000000C03002800
          Cell 126 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016b3411ae4a
                    Extra: Last beacon: 8936ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010F0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004BC0000000106000CE60B849204040100000005040010010009082EC110346B0100000A04090000000B04040000000C03002800
          Cell 127 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002621a6d0616
                    Extra: Last beacon: 8936ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010300036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E20000000106000CE60B5720040401000000050400180000090882606B1A620200000A040F0000000B04010000000C03002800
          Cell 128 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003f8a7262480
                    Extra: Last beacon: 7668ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 129 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003f8a6e600a4
                    Extra: Last beacon: 7676ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 130 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003f8a861fa39
                    Extra: Last beacon: 7928ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 131 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c6fd9c036
                    Extra: Last beacon: 6860ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004250000000106000CE60AFE350404020000000504008401000908698CD96F3C0000000A040B0000000B04100000000C03002800
          Cell 132 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c6fd9c145
                    Extra: Last beacon: 6860ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D162C050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004250000000106000CE60AFE350404020000000504008401000908898CD96F3C0000000A040B0000000B040B0000000C03002800
          Cell 133 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c6fd9c2ba
                    Extra: Last beacon: 6860ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010210
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004250000000106000CE60AFE350404020000000504008401000908988CD96F3C0000000A040B0000000B04060000000C03002800
          Cell 134 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c6fdb5036
                    Extra: Last beacon: 6840ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010008
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D162C050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004250000000106000CE60AFE35040402000000050400440000090872DCD96F3C0000000A040B0000000B04070000000C03002800
          Cell 135 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051b206a036
                    Extra: Last beacon: 3816ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004BD0000000106000CE60B71E80404020000000504006401000908924C06B2510000000A04090000000B04010000000C03002800
          Cell 136 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001191a031da
                    Extra: Last beacon: 4220ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004220000000106000CE60A7DD404040200000005040028010009086DA09F91110000000A04090000000B04050000000C03002800
          Cell 137 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001331f0d9036
                    Extra: Last beacon: 3168ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004FD0000000106000CE60B73BA040402000000050400D40000090869AC0C1F330100000A04090000000B04040000000C03002800
          Cell 138 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c9d80036
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE60AFC50040402000000050400880100090865D0D7C9170000000A040B0000000B04100000000C03002800
          Cell 139 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c9d80144
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1695050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE60AFC5004040200000005040088010009088CD0D7C9170000000A040B0000000B040B0000000C03002800
          Cell 140 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c9d802b9
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE60AFC5004040200000005040088010009089AD0D7C9170000000A040B0000000B04060000000C03002800
          Cell 141 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c9d99036
                    Extra: Last beacon: 1380ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1695050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010600036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004260000000106000CE60AFC5004040200000005040048000009086720D8C9170000000A040B0000000B04070000000C03002800
          Cell 142 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b473c530ec
                    Extra: Last beacon: 1380ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004210000000106000CE60AFD0B040402000000050400740100090864ECC473B40000000A040B0000000B04100000000C03002800
          Cell 143 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b473c531f8
                    Extra: Last beacon: 1380ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1695050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004210000000106000CE60AFD0B04040200000005040074010009088AECC473B40000000A040B0000000B040B0000000C03002800
          Cell 144 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b473c5336e
                    Extra: Last beacon: 1380ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004210000000106000CE60AFD0B040402000000050400740100090898ECC473B40000000A040B0000000B04060000000C03002800
          Cell 145 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001331f2b4a8f
                    Extra: Last beacon: 1200ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004FD0000000106000CE60B73BA040402000000050400240100090872AC2A1F330100000A04090000000B04050000000C03002800



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search wireless.utoronto.ca


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


[    9.538590] wmi: Mapper loaded
[    9.550735] ath: EEPROM regdomain: 0x6c
[    9.550738] ath: EEPROM indicates we should expect a direct regpair map
[    9.550740] ath: Country alpha2 being used: 00
[    9.550742] ath: Regpair used: 0x6c
[    9.569442] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.569736] Registered led device: ath9k-phy0
[    9.690219] acer_wmi: Acer Laptop ACPI-WMI Extras
[    9.690233] acer_wmi: Function bitmap for Communication Button: 0x801
[    9.705228] acer_wmi: Brightness must be controlled by acpi video driver
[   11.530140] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.533497] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.148587] wlan0: authenticate with <MAC address removed>
[   19.151875] wlan0: direct probe to <MAC address removed> (try 1/3)
[   19.353351] wlan0: direct probe to <MAC address removed> (try 2/3)
[   19.557117] wlan0: direct probe to <MAC address removed> (try 3/3)
[   19.760863] wlan0: authentication with <MAC address removed> timed out
[   20.210964] wlan0: authenticate with <MAC address removed>
[   20.222961] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.225677] wlan0: authenticated
[   20.232283] wlan0: associate with <MAC address removed> (try 1/3)
[   20.234931] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=4)
[   20.235013] wlan0: associated
[   20.235802] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.239098] ath: regdomain 0x807c updated by CountryIE
[   20.239099] ath: EEPROM regdomain: 0x807c
[   20.239100] ath: EEPROM indicates we should expect a country code
[   20.239101] ath: doing EEPROM country->regdmn map search
[   20.239102] ath: country maps to regdmn code: 0x3a
[   20.239103] ath: Country alpha2 being used: CA
[   20.239104] ath: Regpair used: 0x3a
[   41.083637] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  163.790152] wlan0: authenticate with <MAC address removed>
[  163.801721] wlan0: send auth to <MAC address removed> (try 1/3)
[  163.806145] wlan0: authenticated
[  163.812465] wlan0: associate with <MAC address removed> (try 1/3)
[  163.813688] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  163.813780] wlan0: associated
[  163.818741] ath: regdomain 0x807c updated by CountryIE
[  163.818742] ath: EEPROM regdomain: 0x807c
[  163.818743] ath: EEPROM indicates we should expect a country code
[  163.818745] ath: doing EEPROM country->regdmn map search
[  163.818746] ath: country maps to regdmn code: 0x3a
[  163.818747] ath: Country alpha2 being used: CA
[  163.818749] ath: Regpair used: 0x3a
[  209.091960] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  215.738577] wlan0: authenticate with <MAC address removed>
[  215.750570] wlan0: send auth to <MAC address removed> (try 1/3)
[  215.954059] wlan0: send auth to <MAC address removed> (try 2/3)
[  215.958900] wlan0: authenticated
[  215.966039] wlan0: associate with <MAC address removed> (try 1/3)
[  215.967619] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=14)
[  215.967688] wlan0: associated
[  215.974156] ath: regdomain 0x807c updated by CountryIE
[  215.974157] ath: EEPROM regdomain: 0x807c
[  215.974157] ath: EEPROM indicates we should expect a country code
[  215.974158] ath: doing EEPROM country->regdmn map search
[  215.974159] ath: country maps to regdmn code: 0x3a
[  215.974160] ath: Country alpha2 being used: CA
[  215.974161] ath: Regpair used: 0x3a
[  236.847962] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  288.852330] wlan0: authenticate with <MAC address removed>
[  288.864187] wlan0: direct probe to <MAC address removed> (try 1/3)
[  289.066625] wlan0: direct probe to <MAC address removed> (try 2/3)
[  289.270328] wlan0: direct probe to <MAC address removed> (try 3/3)
[  289.474130] wlan0: authentication with <MAC address removed> timed out
[  290.113900] wlan0: authenticate with <MAC address removed>
[  290.125626] wlan0: send auth to <MAC address removed> (try 1/3)
[  290.329116] wlan0: send auth to <MAC address removed> (try 2/3)
[  290.330243] wlan0: authenticated
[  290.337041] wlan0: associate with <MAC address removed> (try 1/3)
[  290.338690] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  290.338769] wlan0: associated
[  290.343859] ath: regdomain 0x807c updated by CountryIE
[  290.343862] ath: EEPROM regdomain: 0x807c
[  290.343864] ath: EEPROM indicates we should expect a country code
[  290.343867] ath: doing EEPROM country->regdmn map search
[  290.343870] ath: country maps to regdmn code: 0x3a
[  290.343873] ath: Country alpha2 being used: CA
[  290.343875] ath: Regpair used: 0x3a
[  312.051506] wlan0: authenticate with <MAC address removed>
[  312.054758] wlan0: send auth to <MAC address removed> (try 1/3)
[  312.057475] wlan0: authenticated
[  312.063059] wlan0: associate with <MAC address removed> (try 1/3)
[  312.066083] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  312.066159] wlan0: associated
[  819.959740] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  820.007904] ath9k: ath9k: Driver unloaded
[  832.646245] ath: EEPROM regdomain: 0x6c
[  832.646247] ath: EEPROM indicates we should expect a direct regpair map
[  832.646249] ath: Country alpha2 being used: 00
[  832.646250] ath: Regpair used: 0x6c
[  832.647118] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  832.647665] Registered led device: ath9k-phy0
[  832.666842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  832.670402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  840.359118] wlan0: authenticate with <MAC address removed>
[  840.371140] wlan0: direct probe to <MAC address removed> (try 1/3)
[  840.574593] wlan0: direct probe to <MAC address removed> (try 2/3)
[  840.778345] wlan0: direct probe to <MAC address removed> (try 3/3)
[  840.982085] wlan0: authentication with <MAC address removed> timed out
[  841.430991] wlan0: authenticate with <MAC address removed>
[  841.438922] wlan0: send auth to <MAC address removed> (try 1/3)
[  841.441965] wlan0: authenticated
[  841.445696] wlan0: associate with <MAC address removed> (try 1/3)
[  841.447135] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[  841.447217] wlan0: associated
[  841.448093] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  841.452191] ath: regdomain 0x807c updated by CountryIE
[  841.452192] ath: EEPROM regdomain: 0x807c
[  841.452193] ath: EEPROM indicates we should expect a country code
[  841.452194] ath: doing EEPROM country->regdmn map search
[  841.452195] ath: country maps to regdmn code: 0x3a
[  841.452196] ath: Country alpha2 being used: CA
[  841.452197] ath: Regpair used: 0x3a


**************** done ********************


```

---

### Post by varunendra on 2012-11-10
> **mabubakr94 said:**
> can you explain what exactly those commands do?As you already figured out, the modprobe command loads or (with -r option) 'removes' or unloads a specified module.
The -f and -v options make the process 'forced' and 'verbose' (show everything that happened) respectively.

As for the 'nohwcrypt' option, you correctly guessed it -> **mabubakr94 said:**
> Edit: Judging by the command names, I guess  it makes the software handle encryption instead of hardware?As always in computers or electronics, **1** means 'True' or 'Enabled' and **0** means 'False' or 'Disabled'. By default, the value of that option for ath9k is '0' (disabled). We just 'enabled' it.

You can use *modinfo* command to get the available options for any module, besides other details about it. (e.g., modinfo ath9k). Some modules accept integer (int) values (1 or 0), while some may accept boolean (bool) values (Y or N) for options. However, modprobe will return an error if you supplied an unacceptable option to a module, and based on that behaviour, I've seen that 1 or 0 are also accepted in place of Y or N.

You can see the current options a module is loaded with by looking at the **/sys/module/*<module in question>*/parameters/*<parameter in question>*** file. For example -
```
cat /sys/module/ath9k/parameters/nohwcrypt
```returns '0' in my lappy.


Some additional info you may find useful/interesting :-

**modprobe** actually executes another command '*insmod*' which does the job of 'inserting' a module into the running kernel.
Similarly, the **-r** option actually calls another command '*rmmod*' which does the job of removing a module.
However, it is not recommended to directly use these commands because they do not care about dependencies of a module. They only load/unload the specified module and not the dependencies.

Whereas *modprobe* is an elegant way of doing these jobs. It detects the dependencies, loads/unloads them as well in correct sequence, or returns error messages if there is a problem in loading/unloadiing any of the dependencies or the module itself (e.g., module 'xyz' is in use..). Besides having some advanced options of its own, It also has the capability of using the 'extra' options pertaining to modules which insmod can't (like *nohwcrypt* we just used).

> **mabubakr94 said:**
> How can I go about making this permanent?
Run the following command -
```
echo "options **[COLOR=Red]ath9k[/COLOR]** nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
*[Edited above to include [COLOR=DarkRed]ath9k[/COLOR] in the echo string which I missed earlier :redface:]*
Before you go hide somewhere, I'm very keen to explain the above one too ;)
It is a combination of '*echo*' and '*tee*' commands. '*echo*' simply prints the string supplied in double quotes, which, due to the '*pipe*' (|) operator in front, becomes the 'input' for '*tee*' command instead of being printed on screen. '*[tee]("https://en.wikipedia.org/wiki/Tee_%28Unix%29")*' does what it sounds like -a 'T'. That is - besides forwarding the supplied string to the screen, it also drops (writes) it into a file which is supplied as an argument after the command. The '-a' option makes the output to 'append' instead of overwriting the file if it already exists (if it doesn't, it'll be created). '*sudo*' just gives '*tee*' root access so that it can write the file in /etc/modprobe.d directory, where a normal user can't.

> **mabubakr94 said:**
> would you also know how to fix this shutdown bug?.... Or should I just make another thread in the hardware section? You are smart enough :) Just start a new thread and post a link to it here so I can follow. It has become a common bug now, and to be honest, I'm not aware of any fixes or workarounds yet. Except that for last 4-5 shutdowns (I rarely do that) my 12.04 seems to be shutting down correctly while it had the same bug earlier. Perhaps some update fixed it automatically, or maybe it's just a matter of chance! IDK.


O-oh, I almost forgot we still have a problem to solve -
> **mabubakr94 said:**
> It stopped working again...
```

**** iwconfig ****

wlan0     IEEE 802.11abgn  ESSID:"UofT"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC address removed>   
          Bit Rate=162 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR=Red]on[/COLOR]**

```Please try -
```
sudo iwconfig wlan0 power off
```to turn off the power management for wlan0. Then recheck -
```
iwconfig
```and see if it is turned off now and how long the connection holds.

(Whew..! Where's my glass of water now..)

---

### Post by mabubakr94 on 2012-11-10
Awesome explanation. Much appreciated! I will try your other fix but will have to wait until Wednesday as I am home now and we have been given extra two days off to study for next week's term tests. I'll make that other thread and link ASAP, once again you've been a great help. Thanks! 
;-)

---

### Post by varunendra on 2012-11-10
You're welcome buddy !

---

### Post by mabubakr94 on 2012-11-14
Hi. I have just tried on the UofT connection with power management off and it is still the same. Does not connect but occasionally will if I restart/relogin and keep trying.

Edit: Another thing to note, which might be of interest or just a visual bug, sometimes the icon displaying connection strength (the bars) are all grey and show that no network is connected to when I am connected to a wireless network and using the internet.

Edit 2: This is also showing in terminal now:

```
WARNING: /etc/modprobe.d/ath9k.conf line 1: ignoring bad line starting with 'options'
rmmod /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.5.0-18-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-18-generic/kernel/net/wireless/cfg80211.ko

```

---

### Post by mabubakr94 on 2012-11-14
So it seems the command to make nohwcrypt permanent did not work, only when I set this setting manually does it have a chance to connect to the network. I pasted the error above.

---

### Post by varunendra on 2012-11-14
Aha..!! We just discovered the 'Mistake of the Year' and 'Stupid of the Millennium'.... please welcome.... *drum rolls* - Me !! :D

That command should have been -
```
echo "options [COLOR=Red]**ath9k**[/COLOR] nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```I totally missed the [COLOR=Red]**ath9k**[/COLOR] there! Going to correct it..
You'll actually have to REPLACE the previous incorrect line in /etc/modprobe.d/ath9k.conf file with the correct one (*options **[COLOR=Red]ath9k[/COLOR]** nohwcrypt=1*). You can do it in either gedit with -
```
gksu gedit /etc/modprobe.d/ath9k.conf
```
correct the line, proofread, save and close.
Or in one step using the following command (you may copy-paste it)-
```
sudo sed -i 's/^options nohwcrypt/options ath9k nohwcrypt/' /etc/modprobe.d/ath9k.conf
```
Need explanation what 'sed' does above ? :)

Once done, either reboot or do a -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
to let it take effect.

---

### Post by mabubakr94 on 2012-11-14
Thanks! I'll try it out again at school most likely on Friday. Midterm tomorrow and Friday so will be heading back home to study immediately after Thursday's midterm.

I read up on 'sed' a bit and think I get it. Only thing I could use an explanation for is when you're replacing 'options nohwcrypt' to 'options ath9k nohwcrypt', why did you include a ^ in '^options nohwcrypt'?

I'll post my question about shutting down once I am done midterms on Friday. :D

Edit: Sorry, one more thing, why do you need to use gksu? I think that's like a run command. Just typing gedit also works.

---

### Post by varunendra on 2012-11-14
You must be a really good student ! I like your curiosity.

> **mabubakr94 said:**
> when you're replacing 'options nohwcrypt' to 'options ath9k nohwcrypt', why did you include a ^ in '^options nohwcrypt'?Although it shouldn't be necessary in our case, the '^' makes sure only those lines are picked that 'start' with the word "options". So in general, it indicates the 'beginning' of a line.
[COLOR=DarkRed]*[In the similar way, a '$' indicates the 'End' of a line. It is written 'after' the pattern to search. So a "nature$" will pick only those lines that end at the word "nature". Note that a line ending with "good nature." will NOT be picked, since it ends with a 'dot' (.)]*[/COLOR]

> **mabubakr94 said:**
> one more thing, why do you need to use gksu? I think that's like a run command. Just typing gedit also works.Yes using just gedit will open the file, but you won't be able to save the changes since that requires 'root' access for system files. Gksu or sudo give you just that - the root access (provided you are in the 'sudoers' list - which the first user always is by default).

You should also be aware that it is always recommended to use gksu (or gksudo, or kdesudo in kde) for running GUI programs as root, instead of using 'sudo' (which should be used for commandline programs). The best explanation of 'why so?' is given here - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Best of luck for the midterms !

---

### Post by mabubakr94 on 2012-11-16
Thank you for the great explanations and all your help. Unfortunately the problem is only partially solved. Before disabling hwcrypt, the connection would never go through. Now it seems to work sometimes by continuously logging in and out of Ubuntu. Still better than nothing but not 100% fixed.

Also, I noticed turning off power management is also not permanent. Should that be permanent or was I asked to only try it once to see if it had a impact? Did not seem like it had any impact.

---

### Post by varunendra on 2012-11-16
> **mabubakr94 said:**
> ..I noticed turning off power management is also not permanent. Should that be permanent or was I asked to only try it once to see if it had a impact? Did not seem like it had any impact.
You can make it permanent by adding a script in /etc/pm/power.d/ directory. A single command to do it -
```
echo -e "#!/bin/bash\n/sbin/iwconfig wlan0 power off" | sudo tee -a /etc/pm/power.d/wireless
```
I'd say try it anyway. If it clearly doesn't seem to help, we can revert the change.

If it doesn't help, post back the following outputs immediately after it fails to connect or gets disconnected automatically -
```
dmesg | grep -e wlan -e ath
dmesg | tail -20
iwconfig
iwlist scan
cat /sys/module/ath9k/parameters/nohwcrypt
```

---

### Post by mabubakr94 on 2012-11-19
**dmesg | grep -e wlan -e ath:**
```

[   11.485323] ath: EEPROM regdomain: 0x6c
[   11.485326] ath: EEPROM indicates we should expect a direct regpair map
[   11.485329] ath: Country alpha2 being used: 00
[   11.485330] ath: Regpair used: 0x6c
[   11.513819] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.514111] Registered led device: ath9k-phy0
[   12.923085] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.927464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.626307] wlan0: authenticate with 00:0c:e6:48:b2:00
[   20.630277] wlan0: send auth to 00:0c:e6:48:b2:00 (try 1/3)
[   20.831784] wlan0: send auth to 00:0c:e6:48:b2:00 (try 2/3)
[   21.035565] wlan0: send auth to 00:0c:e6:48:b2:00 (try 3/3)
[   21.239295] wlan0: authentication with 00:0c:e6:48:b2:00 timed out
[   21.468385] wlan0: authenticate with 00:0c:e6:48:b2:40
[   21.480610] wlan0: send auth to 00:0c:e6:48:b2:40 (try 1/3)
[   21.483244] wlan0: authenticated
[   21.487031] wlan0: associate with 00:0c:e6:48:b2:40 (try 1/3)
[   21.488996] wlan0: RX AssocResp from 00:0c:e6:48:b2:40 (capab=0x11 status=0 aid=3)
[   21.489077] wlan0: associated
[   21.489827] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.493137] ath: regdomain 0x807c updated by CountryIE
[   21.493138] ath: EEPROM regdomain: 0x807c
[   21.493139] ath: EEPROM indicates we should expect a country code
[   21.493140] ath: doing EEPROM country->regdmn map search
[   21.493141] ath: country maps to regdmn code: 0x3a
[   21.493142] ath: Country alpha2 being used: CA
[   21.493143] ath: Regpair used: 0x3a
[   42.080348] wlan0: deauthenticating from 00:0c:e6:48:b2:40 by local choice (reason=3)
[   59.068030] wlan0: authenticate with 00:0c:e6:48:26:40
[   59.072264] wlan0: direct probe to 00:0c:e6:48:26:40 (try 1/3)
[   59.273770] wlan0: send auth to 00:0c:e6:48:26:40 (try 2/3)
[   59.477535] wlan0: send auth to 00:0c:e6:48:26:40 (try 3/3)
[   59.681305] wlan0: authentication with 00:0c:e6:48:26:40 timed out
[   59.974270] wlan0: authenticate with 00:0c:e6:48:b2:40
[   59.986644] wlan0: send auth to 00:0c:e6:48:b2:40 (try 1/3)
[   59.989339] wlan0: authenticated
[   59.993003] wlan0: associate with 00:0c:e6:48:b2:40 (try 1/3)
[   59.994855] wlan0: RX AssocResp from 00:0c:e6:48:b2:40 (capab=0x11 status=0 aid=2)
[   59.994937] wlan0: associated
[   59.999888] ath: regdomain 0x807c updated by CountryIE
[   59.999889] ath: EEPROM regdomain: 0x807c
[   59.999890] ath: EEPROM indicates we should expect a country code
[   59.999892] ath: doing EEPROM country->regdmn map search
[   59.999893] ath: country maps to regdmn code: 0x3a
[   59.999895] ath: Country alpha2 being used: CA
[   59.999897] ath: Regpair used: 0x3a
[   80.034563] wlan0: deauthenticating from 00:0c:e6:48:b2:40 by local choice (reason=3)
[   90.882789] wlan0: authenticate with 00:0c:e6:48:b2:41
[   90.886334] wlan0: send auth to 00:0c:e6:48:b2:41 (try 1/3)
[   90.890848] wlan0: authenticated
[   90.895934] wlan0: associate with 00:0c:e6:48:b2:41 (try 1/3)
[   90.897038] wlan0: RX AssocResp from 00:0c:e6:48:b2:41 (capab=0x11 status=0 aid=1)
[   90.897113] wlan0: associated
[   90.901864] ath: regdomain 0x807c updated by CountryIE
[   90.901866] ath: EEPROM regdomain: 0x807c
[   90.901867] ath: EEPROM indicates we should expect a country code
[   90.901868] ath: doing EEPROM country->regdmn map search
[   90.901869] ath: country maps to regdmn code: 0x3a
[   90.901871] ath: Country alpha2 being used: CA
[   90.901872] ath: Regpair used: 0x3a
[  355.566941] wlan0: deauthenticating from 00:0c:e6:48:b2:41 by local choice (reason=3)
[  360.434507] wlan0: authenticate with 00:0c:e6:48:b2:40
[  360.441960] wlan0: direct probe to 00:0c:e6:48:b2:40 (try 1/3)
[  360.645197] wlan0: send auth to 00:0c:e6:48:b2:40 (try 2/3)
[  360.647811] wlan0: authenticated
[  360.653134] wlan0: associate with 00:0c:e6:48:b2:40 (try 1/3)
[  360.654447] wlan0: RX AssocResp from 00:0c:e6:48:b2:40 (capab=0x11 status=0 aid=1)
[  360.654552] wlan0: associated
[  360.662743] ath: regdomain 0x807c updated by CountryIE
[  360.662746] ath: EEPROM regdomain: 0x807c
[  360.662748] ath: EEPROM indicates we should expect a country code
[  360.662751] ath: doing EEPROM country->regdmn map search
[  360.662754] ath: country maps to regdmn code: 0x3a
[  360.662757] ath: Country alpha2 being used: CA
[  360.662759] ath: Regpair used: 0x3a
[  380.676443] wlan0: deauthenticating from 00:0c:e6:48:b2:40 by local choice (reason=3)

```

**dmesg | tail -20:**
```

[  631.813403] CPU1: Package power limit notification (total events = 4556)
[  631.813405] CPU0: Package power limit notification (total events = 4555)
[  631.813430] CPU3: Package power limit notification (total events = 4556)
[  631.813433] CPU2: Package power limit notification (total events = 4555)
[  631.816744] CPU1: Package power limit normal
[  631.816746] CPU3: Package power limit normal
[  631.816748] CPU2: Package power limit normal
[  631.816750] CPU0: Package power limit normal
[  642.367165] wlan0: deauthenticating from 00:0c:e6:48:b2:40 by local choice (reason=3)
[  642.387815] cfg80211: All devices are disconnected, going to restore regulatory settings
[  642.387824] cfg80211: Restoring regulatory settings
[  642.387831] cfg80211: Calling CRDA to update world regulatory domain
[  642.392043] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  642.395106] cfg80211: World regulatory domain updated:
[  642.395108] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  642.395110] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  642.395112] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  642.395113] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  642.395115] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  642.395116] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

[B]iwconfig:
[/B]```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"UofT"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:0C:E6:48:B2:40   
          Bit Rate=216 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

**iwlist scan - Important to note that this was all that was displayed. I assume cell 1 - 46 got cut off? When it connected to the wireless connection, only one cell appeared.**
```
          Cell 47 - Address: 00:0C:E6:48:B2:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000060aca4fc82
                    Extra: Last beacon: 27488ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004B20000000106000CE60B721E0404010000000504004800000908D561A3AC600000000A04090000000B04010000000C03002800
          Cell 48 - Address: 00:0C:E6:48:A9:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cbe2a592e
                    Extra: Last beacon: 27484ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010022
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004A90000000106000CE60B7933040401000000050400240000090877BC28BE6C0000000A04090000000B04010000000C03002800
          Cell 49 - Address: 00:0C:E6:48:AD:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007c4bec268
                    Extra: Last beacon: 27480ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004AD0000000106000CE60B82890404010000000504002401000908752CBEC4070000000A04090000000B04040000000C03002800
          Cell 50 - Address: 00:0C:E6:48:E4:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000650817d180
                    Extra: Last beacon: 27480ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010A00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E40000000106000CE60A82FE040401000000050400200000090878381608650000000A04090000000B04010000000C03002800
          Cell 51 - Address: 00:0C:E6:48:B0:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ac9451180
                    Extra: Last beacon: 27476ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010002
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B00000000106000CE60B7253040401000000050400800100090876D844C94A0000000A04090000000B04050000000C03002800
          Cell 52 - Address: 00:0C:E6:48:AC:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007f4ab877a
                    Extra: Last beacon: 27472ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010700023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004AC0000000106000CE60B81B004040100000005040080000009087E48AAF4070000000A04090000000B04020000000C03002800
          Cell 53 - Address: 00:0C:E6:48:FA:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001fae6a4f46c
                    Extra: Last beacon: 27472ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004FA0000000106000CE60B78D7040401000000050400680100090875A0A4E6FA0100000A04090000000B04050000000C03002800
          Cell 54 - Address: 00:18:4D:AF:E0:4F
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000167104e7181
                    Extra: Last beacon: 27160ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 55 - Address: 00:18:4D:49:76:8F
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000088d338a7181
                    Extra: Last beacon: 27144ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 56 - Address: 00:04:E2:C1:36:52
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"EXTRANEOUSX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005cde2c931db
                    Extra: Last beacon: 27228ms ago
                    IE: Unknown: 000B45585452414E454F555358
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 57 - Address: 00:18:4D:49:76:8E
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000088d37439037
                    Extra: Last beacon: 26108ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03013C
                    IE: Unknown: 050400010000
                    IE: Unknown: 070C55532024041134041795051E
          Cell 58 - Address: 58:6D:8F:2E:C6:97
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fe80ae183
                    Extra: Last beacon: 27736ms ago
                    IE: Unknown: 0006000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD270050F204104A000110104400010210470010B0991992DC1ABB9D4892F7063CAA0306103C000103
                    IE: Unknown: DD090010180200F0240000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 59 - Address: 00:0C:E6:48:E4:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006508164180
                    Extra: Last beacon: 27500ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010A00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004E40000000106000CE60A82FE04040100000005040060010009087BE81508650000000A04090000000B04050000000C03002800
          Cell 60 - Address: 00:0C:E6:48:AA:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000232ff0082d2
                    Extra: Last beacon: 27484ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010300036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004AA0000000106000CE60BB1DF04040100000005040018010009086DE0FFFE320200000A04090000000B04040000000C03002800
          Cell 61 - Address: 00:0C:E6:48:2B:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bd3ab4d1a8
                    Extra: Last beacon: 27484ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600042B0000000106000CE608645E040401000000050400FC000009087E14B43ABD0000000A04090000000B04040000000C03002800
          Cell 62 - Address: 00:18:4D:49:77:3E
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d25178e5037
                    Extra: Last beacon: 26700ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: Unknown: 050400010000
                    IE: Unknown: 070C55532024041134041795051E
          Cell 63 - Address: 00:0C:E6:48:B4:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004cfe1544b4
                    Extra: Last beacon: 27520ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 05050001000201
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B8465040401000000050400F000000908797814FE4C0000000A04090000000B04040000000C03002800
          Cell 64 - Address: 00:0C:E6:48:A9:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cbe28c180
                    Extra: Last beacon: 27508ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004A90000000106000CE60B79330404010000000504006401000908726C28BE6C0000000A04090000000B04050000000C03002800
          Cell 65 - Address: 00:0C:E6:48:B4:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004cfe154260
                    Extra: Last beacon: 27500ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010040
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004B40000000106000CE60B8465040401000000050400400100090875C814FE4C0000000A04090000000B04050000000C03002800
          Cell 66 - Address: 00:0C:E6:48:B8:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000815ba283
                    Extra: Last beacon: 27472ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010800023100002453000044425E0062422F00
                    IE: Unknown: DD38000CE60004B80000000106000CE60B71E1040401000000050400500100090878385B81000000000A04090000000B04050000000C03002800
          Cell 67 - Address: 00:0C:E6:48:A9:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"cslab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cbe2a5180
                    Extra: Last beacon: 27468ms ago
                    IE: Unknown: 000563736C6162
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004A90000000106000CE60B793304040100000005040074000009087B0C29BE6C0000000A04090000000B04020000000C03002800
          Cell 68 - Address: 00:0C:E6:48:1D:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"UTORwin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004cab0d2e4
                    Extra: Last beacon: 27468ms ago
                    IE: Unknown: 000755544F5277696E
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600041D0000000106000CE608633D0404010000000504001401000908792CB0CA040000000A04090000000B04040000000C03002800
```


```
cat /sys/module/ath9k/parameters/nohwcrypt == 1
```

For some reason I seem to be getting better results today. Since I had to keep connecting to try and get it to not authenticate to generate these logs, it connected a lot more often than usual.

Also, when I try the command to make the power management permanent, I get the following error:
```
echo -e "#!/bin/bash\n/sbin/iwconfig wlan0 power off" | sudo tee -a /etc/pm/power.d/wireless
bash: !/bin/bash\n/sbin/iwconfig: event not found

```

Should the newline character be in the middle of the path?

Thanks!

---

### Post by varunendra on 2012-11-19
> **mabubakr94 said:**
> [B]iwconfig:
[/B]```

wlan0     IEEE 802.11abgn  ESSID:"**UofT**"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: **00:0C:E6:48:B2:40**   
          Bit Rate=**216** Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=**70/70**  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```**iwlist scan - Important to note that this was all that was displayed. I assume cell 1 - 46 got cut off? When it connected to the wireless connection, only one cell appeared.**With so many cells in range, the output was obviously larger than the terminal can display at a time, so yes, it got cut off. You may 'pipe' (|) the output with 'less' command, or redirect it (>) to a file to catch all of it. For example -
```
iwlist scan > ~/Desktop/iwlist.txt
```will dump all the output text in a new file "iwlist.txt" on your desktop instead of showing it on the terminal. However, if I understood you correctly, you are only interested in those whose ESSID is "Uoft". So you may skip/delete others while posting.

But looking at the iwconfig output above, everything looks to be pretty good! Still it would be interesting to see the one it got disconnected with. You can identify different ones with same ESSID by their unique MAC Addresses, like **00:0C:E6:48:B2:40** above.

> **mabubakr94 said:**
> Also, when I try the command to make the power management permanent, I get the following error:
```
echo -e "#!/bin/bash\n/sbin/iwconfig wlan0 power off" | sudo tee -a /etc/pm/power.d/wireless
bash: !/bin/bash\n/sbin/iwconfig: event not found

```
Hmm.. I learnt something new !
Turns out that the "!" is 'always' interpreted by bash in a special way and makes bash look for a 'command-history' of the rest of the text. Obviously, there is no event when "/bin/bash\n/sbin/iwconfig" was used as a command, hence the error. In our case, it can be easily circumvented by using single quotes instead of double quotes (tested myself this time) -
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless
```Please try this one.

Anyway, I'd be curious to know if the wireless still finds any difficulty despite such strong signals !

Shall await for your feedback.

---

### Post by mabubakr94 on 2012-11-20
I have tried and generated the logs again today. This time connection for UofT would not go through, keeps asking for username and password over and over again. I tried in a new building which worked on Windows 7 and also tried in the same room as yesterday where the results were great. Today I wasn't able to connect in either location.

First is the **iwlist scan**, I removed all ESSID that I knew were not "UofT".
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 02 - Address: 00:0F:3D:5A:F8:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008d4f0037
                    Extra: Last beacon: 3404ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010017FF7F
                    IE: Unknown: DD0C00037F020101010002A34000
         
          Cell 04 - Address: 00:0C:E6:59:0C:43
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c6548e8
                    Extra: Last beacon: 2968ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071043412024081764051788021795051E00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010C0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600040C0100000106000CE60B55E0040402000000050400C0000009089E320D07000000000A040B0000000B04040000000C03002800
          
          Cell 06 - Address: 00:0C:E6:59:23:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000100bde5b180
                    Extra: Last beacon: 3564ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0506000100480084
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010500036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004230100000106000CE60B56EE0404010000000504001C010009087214E5BD000100000A040B0000000B04040000000C03002800
          Cell 07 - Address: 00:0C:E6:59:19:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"UofT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033d84991180
                    Extra: Last beacon: 3560ms ago
                    IE: Unknown: 0004556F6654
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010010
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F20201010300036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004190100000106000CE60B8458040401000000050400F400000908754C98843D0300000A040B0000000B04040000000C03002800
          
          Cell 10 - Address: 00:0C:E6:59:24:43
                    Channel:36
```

**iwconfig:**
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

**dmesg | grep -e wlan -e ath:**
```
[   12.273491] ath: EEPROM regdomain: 0x6c
[   12.273495] ath: EEPROM indicates we should expect a direct regpair map
[   12.273498] ath: Country alpha2 being used: 00
[   12.273499] ath: Regpair used: 0x6c
[   12.314656] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.315391] Registered led device: ath9k-phy0
[   15.635789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.639782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.297234] wlan0: authenticate with 00:0c:e6:59:29:43
[   23.303015] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[   23.504341] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[   23.708125] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[   23.911856] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[   24.056348] wlan0: authenticate with 00:0c:e6:59:0c:43
[   24.065306] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   24.267425] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   24.471192] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   24.674962] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   24.811497] wlan0: authenticate with 00:0c:e6:59:0a:43
[   24.820286] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[   25.022522] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[   25.226304] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[   25.430033] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[   29.305961] wlan0: authenticate with 00:0c:e6:59:0c:43
[   29.311799] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   29.513185] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   29.716910] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   29.721039] wlan0: authenticated
[   29.724924] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   29.726736] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[   29.726807] wlan0: associated
[   29.727343] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.730178] ath: regdomain 0x807c updated by CountryIE
[   29.730179] ath: EEPROM regdomain: 0x807c
[   29.730180] ath: EEPROM indicates we should expect a country code
[   29.730181] ath: doing EEPROM country->regdmn map search
[   29.730182] ath: country maps to regdmn code: 0x3a
[   29.730183] ath: Country alpha2 being used: CA
[   29.730183] ath: Regpair used: 0x3a
[   45.075327] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[   54.539822] wlan0: authenticate with 00:0c:e6:59:0c:43
[   54.545414] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   54.546289] wlan0: authenticated
[   54.551240] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   54.552524] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[   54.552594] wlan0: associated
[   54.556037] ath: regdomain 0x807c updated by CountryIE
[   54.556038] ath: EEPROM regdomain: 0x807c
[   54.556038] ath: EEPROM indicates we should expect a country code
[   54.556039] ath: doing EEPROM country->regdmn map search
[   54.556040] ath: country maps to regdmn code: 0x3a
[   54.556041] ath: Country alpha2 being used: CA
[   54.556042] ath: Regpair used: 0x3a
[   76.040858] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[   85.603210] wlan0: authenticate with 00:0c:e6:59:0c:43
[   85.608426] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   85.809910] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   86.013732] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   86.217413] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   86.453893] wlan0: authenticate with 00:0c:e6:59:29:43
[   86.462590] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[   86.664882] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[   86.868637] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[   87.072392] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[   87.348577] wlan0: authenticate with 00:0c:e6:59:24:43
[   87.357587] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[   87.559813] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[   87.763641] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[   87.967350] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[   91.921246] wlan0: authenticate with 00:0c:e6:59:0c:43
[   91.926085] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   92.126409] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   92.330168] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   92.533987] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   92.773909] wlan0: authenticate with 00:0c:e6:59:24:43
[   92.786145] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[   92.989355] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[   93.193093] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[   93.396882] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[   97.346262] wlan0: authenticate with 00:0c:e6:59:0c:43
[   97.351473] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   97.551919] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   97.554590] wlan0: authenticated
[   97.559906] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   97.561606] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=57)
[   97.561711] wlan0: associated
[   97.568384] ath: regdomain 0x807c updated by CountryIE
[   97.568385] ath: EEPROM regdomain: 0x807c
[   97.568385] ath: EEPROM indicates we should expect a country code
[   97.568386] ath: doing EEPROM country->regdmn map search
[   97.568387] ath: country maps to regdmn code: 0x3a
[   97.568388] ath: Country alpha2 being used: CA
[   97.568389] ath: Regpair used: 0x3a
[  107.002930] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  113.150102] wlan0: authenticate with 00:0c:e6:59:0c:43
[  113.155506] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  113.357000] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  113.560799] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  113.764514] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  114.069845] wlan0: authenticate with 00:0c:e6:59:29:43
[  114.075585] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  114.275911] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  114.479729] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  114.683433] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  114.976630] wlan0: authenticate with 00:0c:e6:59:0c:03
[  114.985090] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 1/3)
[  115.186813] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  115.390612] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  115.594354] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  115.829198] wlan0: authenticate with 00:0c:e6:59:24:43
[  115.978623] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  116.181647] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  116.385422] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  116.589145] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  120.546852] wlan0: authenticate with 00:0c:e6:59:23:03
[  120.551456] wlan0: direct probe to 00:0c:e6:59:23:03 (try 1/3)
[  120.752163] wlan0: direct probe to 00:0c:e6:59:23:03 (try 2/3)
[  120.955915] wlan0: direct probe to 00:0c:e6:59:23:03 (try 3/3)
[  121.159667] wlan0: authentication with 00:0c:e6:59:23:03 timed out
[  121.296462] wlan0: authenticate with 00:0c:e6:59:0a:03
[  121.308324] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 1/3)
[  121.511248] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 2/3)
[  121.715013] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 3/3)
[  121.918784] wlan0: authentication with 00:0c:e6:59:0a:03 timed out
[  125.866690] wlan0: authenticate with 00:0c:e6:59:0c:43
[  125.872636] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  125.875280] wlan0: authenticated
[  125.882010] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  125.884320] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=2)
[  125.884391] wlan0: associated
[  125.888843] ath: regdomain 0x807c updated by CountryIE
[  125.888845] ath: EEPROM regdomain: 0x807c
[  125.888846] ath: EEPROM indicates we should expect a country code
[  125.888847] ath: doing EEPROM country->regdmn map search
[  125.888848] ath: country maps to regdmn code: 0x3a
[  125.888850] ath: Country alpha2 being used: CA
[  125.888851] ath: Regpair used: 0x3a
[  134.972140] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  141.496061] wlan0: authenticate with 00:0c:e6:59:0c:03
[  141.501514] wlan0: send auth to 00:0c:e6:59:0c:03 (try 1/3)
[  141.703106] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  141.906901] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  142.110625] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  142.348296] wlan0: authenticate with 00:0c:e6:59:0c:43
[  142.353789] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  142.554103] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  142.757905] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  142.961664] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  143.199040] wlan0: authenticate with 00:0c:e6:59:24:43
[  143.207361] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  143.409069] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  143.612863] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  143.816584] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  144.100871] wlan0: authenticate with 00:0c:e6:59:29:43
[  144.113082] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  144.315981] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  144.519750] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  144.723525] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  148.683912] wlan0: authenticate with 00:0c:e6:59:0c:43
[  148.689439] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  148.890577] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  149.094344] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  149.298096] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  149.590733] wlan0: authenticate with 00:0c:e6:59:29:43
[  149.603178] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  149.805496] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  150.009198] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  150.212998] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  150.448847] wlan0: authenticate with 00:0c:e6:59:24:43
[  150.461097] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  150.664484] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  150.868238] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  151.071968] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  155.020783] wlan0: authenticate with 00:0c:e6:59:0c:43
[  155.026409] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  155.030427] wlan0: authenticated
[  155.035196] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  155.238947] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  155.243914] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  155.243999] wlan0: associated
[  155.248787] ath: regdomain 0x807c updated by CountryIE
[  155.248789] ath: EEPROM regdomain: 0x807c
[  155.248790] ath: EEPROM indicates we should expect a country code
[  155.248791] ath: doing EEPROM country->regdmn map search
[  155.248792] ath: country maps to regdmn code: 0x3a
[  155.248794] ath: Country alpha2 being used: CA
[  155.248795] ath: Regpair used: 0x3a
[  162.937993] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  231.327286] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  231.856416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  232.886700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  237.923695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  242.972777] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  248.029570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  253.079822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  259.908618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  264.959489] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  270.012689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  275.074775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  280.109608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  287.865946] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  292.913600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  297.964282] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  303.001766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  308.048602] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  315.829304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  320.875894] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  325.924330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  330.979444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  336.018879] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  350.870163] wlan0: authenticate with 00:0c:e6:59:0c:43
[  350.875496] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  351.076996] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  351.280751] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[  351.484515] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  351.721956] wlan0: authenticate with 00:0c:e6:59:0c:43
[  351.734542] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  351.935924] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  352.139690] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[  352.343514] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  356.295756] wlan0: authenticate with 00:0c:e6:59:29:43
[  356.301571] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  356.502550] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  356.706273] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  356.910014] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  360.859278] wlan0: authenticate with 00:0c:e6:59:0a:43
[  360.864959] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[  361.065057] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[  361.268809] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[  361.472524] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[  365.353022] wlan0: authenticate with 00:0c:e6:59:0c:03
[  365.359013] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 1/3)
[  365.559677] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 2/3)
[  365.763453] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 3/3)
[  365.967151] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  369.848462] wlan0: authenticate with 00:0c:e6:59:0c:43
[  369.854376] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  369.947523] wlan0: authenticated
[  369.954441] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  370.158175] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  370.361937] wlan0: associate with 00:0c:e6:59:0c:43 (try 3/3)
[  370.565686] wlan0: association with 00:0c:e6:59:0c:43 timed out
[  370.865529] wlan0: authenticate with 00:0c:e6:59:0c:03
[  370.878306] wlan0: send auth to 00:0c:e6:59:0c:03 (try 1/3)
[  371.081065] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  371.284810] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  371.488580] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  371.725023] wlan0: authenticate with 00:0c:e6:59:29:43
[  371.731412] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  371.932073] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  372.135827] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  372.339578] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  372.571827] wlan0: authenticate with 00:0c:e6:59:0a:43
[  372.581143] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[  372.782991] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[  372.986749] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[  373.190520] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[  396.543566] wlan0: authenticate with 00:0c:e6:59:0c:43
[  396.549277] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  396.550632] wlan0: authenticated
[  396.554591] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  396.758403] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  396.962168] wlan0: associate with 00:0c:e6:59:0c:43 (try 3/3)
[  396.963481] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  396.963555] wlan0: associated
[  396.964117] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  396.967317] ath: regdomain 0x807c updated by CountryIE
[  396.967318] ath: EEPROM regdomain: 0x807c
[  396.967319] ath: EEPROM indicates we should expect a country code
[  396.967319] ath: doing EEPROM country->regdmn map search
[  396.967320] ath: country maps to regdmn code: 0x3a
[  396.967322] ath: Country alpha2 being used: CA
[  396.967322] ath: Regpair used: 0x3a
[  417.633653] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  425.633425] wlan0: authenticate with 00:0c:e6:59:0c:43
[  425.639549] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  425.641759] wlan0: authenticated
[  425.647832] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  425.649082] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  425.649185] wlan0: associated
[  425.654265] ath: regdomain 0x807c updated by CountryIE
[  425.654267] ath: EEPROM regdomain: 0x807c
[  425.654268] ath: EEPROM indicates we should expect a country code
[  425.654269] ath: doing EEPROM country->regdmn map search
[  425.654270] ath: country maps to regdmn code: 0x3a
[  425.654271] ath: Country alpha2 being used: CA
[  425.654272] ath: Regpair used: 0x3a
[  446.598462] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  640.437299] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  641.489506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  646.541172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  651.600207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  656.640043] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  661.671216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  668.398608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  673.470477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  678.513646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  683.548593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  688.589080] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  696.378403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  701.429456] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  706.479173] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  711.527935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  716.590678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  724.322335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  729.345545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  734.395011] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  739.424602] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  744.476467] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  761.085576] wlan0: authenticate with 00:0c:e6:59:0c:43
[  761.089653] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  761.290844] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  761.494539] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  761.497191] wlan0: authenticated
[  761.502545] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  761.503937] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=28)
[  761.504043] wlan0: associated
[  761.505536] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  761.513928] ath: regdomain 0x807c updated by CountryIE
[  761.513931] ath: EEPROM regdomain: 0x807c
[  761.513933] ath: EEPROM indicates we should expect a country code
[  761.513936] ath: doing EEPROM country->regdmn map search
[  761.513939] ath: country maps to regdmn code: 0x3a
[  761.513942] ath: Country alpha2 being used: CA
[  761.513944] ath: Regpair used: 0x3a
[  782.200407] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  912.462884] ath9k: ath9k: Driver unloaded
[  930.435013] ath: EEPROM regdomain: 0x6c
[  930.435016] ath: EEPROM indicates we should expect a direct regpair map
[  930.435018] ath: Country alpha2 being used: 00
[  930.435019] ath: Regpair used: 0x6c
[  930.435654] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  930.435959] Registered led device: ath9k-phy0
[  930.452345] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  930.454833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1048.944751] wlan0: Selected IBSS BSSID f6:fa:40:2e:02:e9 based on configured SSID
[ 1048.963211] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1100.655473] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1100.667869] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[ 1100.869012] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[ 1101.072765] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[ 1101.276543] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[ 1119.008236] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1119.014120] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[ 1119.017247] wlan0: authenticated
[ 1119.023344] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[ 1119.024772] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=46)
[ 1119.024926] wlan0: associated
[ 1119.035169] ath: regdomain 0x807c updated by CountryIE
[ 1119.035172] ath: EEPROM regdomain: 0x807c
[ 1119.035175] ath: EEPROM indicates we should expect a country code
[ 1119.035177] ath: doing EEPROM country->regdmn map search
[ 1119.035180] ath: country maps to regdmn code: 0x3a
[ 1119.035183] ath: Country alpha2 being used: CA
[ 1119.035185] ath: Regpair used: 0x3a
[ 1121.791798] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[ 1128.968336] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1128.973696] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[ 1129.175214] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[ 1129.178254] wlan0: authenticated
[ 1129.183195] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[ 1129.185025] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=43)
[ 1129.185156] wlan0: associated
[ 1129.192223] ath: regdomain 0x807c updated by CountryIE
[ 1129.192224] ath: EEPROM regdomain: 0x807c
[ 1129.192225] ath: EEPROM indicates we should expect a country code
[ 1129.192226] ath: doing EEPROM country->regdmn map search
[ 1129.192228] ath: country maps to regdmn code: 0x3a
[ 1129.192229] ath: Country alpha2 being used: CA
[ 1129.192230] ath: Regpair used: 0x3a
[ 1150.757034] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[ 1156.825073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1157.857584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1162.901935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1167.953160] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1172.997962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


dmesg | tail -20
[ 1150.783051] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1150.783053] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1150.783054] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1150.783056] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1150.783058] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1156.825073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1157.857584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1162.901935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1167.953160] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1172.997962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1178.045202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.789765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1189.817564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1194.875195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1199.925477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1204.975446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1212.754285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1217.804620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1222.833116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1227.874706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Same test, later time:
```
[   12.273491] ath: EEPROM regdomain: 0x6c
[   12.273495] ath: EEPROM indicates we should expect a direct regpair map
[   12.273498] ath: Country alpha2 being used: 00
[   12.273499] ath: Regpair used: 0x6c
[   12.314656] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.315391] Registered led device: ath9k-phy0
[   15.635789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.639782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.297234] wlan0: authenticate with 00:0c:e6:59:29:43
[   23.303015] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[   23.504341] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[   23.708125] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[   23.911856] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[   24.056348] wlan0: authenticate with 00:0c:e6:59:0c:43
[   24.065306] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   24.267425] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   24.471192] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   24.674962] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   24.811497] wlan0: authenticate with 00:0c:e6:59:0a:43
[   24.820286] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[   25.022522] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[   25.226304] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[   25.430033] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[   29.305961] wlan0: authenticate with 00:0c:e6:59:0c:43
[   29.311799] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   29.513185] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   29.716910] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   29.721039] wlan0: authenticated
[   29.724924] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   29.726736] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[   29.726807] wlan0: associated
[   29.727343] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.730178] ath: regdomain 0x807c updated by CountryIE
[   29.730179] ath: EEPROM regdomain: 0x807c
[   29.730180] ath: EEPROM indicates we should expect a country code
[   29.730181] ath: doing EEPROM country->regdmn map search
[   29.730182] ath: country maps to regdmn code: 0x3a
[   29.730183] ath: Country alpha2 being used: CA
[   29.730183] ath: Regpair used: 0x3a
[   45.075327] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[   54.539822] wlan0: authenticate with 00:0c:e6:59:0c:43
[   54.545414] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   54.546289] wlan0: authenticated
[   54.551240] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   54.552524] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[   54.552594] wlan0: associated
[   54.556037] ath: regdomain 0x807c updated by CountryIE
[   54.556038] ath: EEPROM regdomain: 0x807c
[   54.556038] ath: EEPROM indicates we should expect a country code
[   54.556039] ath: doing EEPROM country->regdmn map search
[   54.556040] ath: country maps to regdmn code: 0x3a
[   54.556041] ath: Country alpha2 being used: CA
[   54.556042] ath: Regpair used: 0x3a
[   76.040858] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[   85.603210] wlan0: authenticate with 00:0c:e6:59:0c:43
[   85.608426] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   85.809910] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   86.013732] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   86.217413] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   86.453893] wlan0: authenticate with 00:0c:e6:59:29:43
[   86.462590] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[   86.664882] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[   86.868637] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[   87.072392] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[   87.348577] wlan0: authenticate with 00:0c:e6:59:24:43
[   87.357587] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[   87.559813] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[   87.763641] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[   87.967350] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[   91.921246] wlan0: authenticate with 00:0c:e6:59:0c:43
[   91.926085] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   92.126409] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   92.330168] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[   92.533987] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[   92.773909] wlan0: authenticate with 00:0c:e6:59:24:43
[   92.786145] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[   92.989355] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[   93.193093] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[   93.396882] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[   97.346262] wlan0: authenticate with 00:0c:e6:59:0c:43
[   97.351473] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[   97.551919] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[   97.554590] wlan0: authenticated
[   97.559906] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[   97.561606] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=57)
[   97.561711] wlan0: associated
[   97.568384] ath: regdomain 0x807c updated by CountryIE
[   97.568385] ath: EEPROM regdomain: 0x807c
[   97.568385] ath: EEPROM indicates we should expect a country code
[   97.568386] ath: doing EEPROM country->regdmn map search
[   97.568387] ath: country maps to regdmn code: 0x3a
[   97.568388] ath: Country alpha2 being used: CA
[   97.568389] ath: Regpair used: 0x3a
[  107.002930] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  113.150102] wlan0: authenticate with 00:0c:e6:59:0c:43
[  113.155506] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  113.357000] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  113.560799] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  113.764514] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  114.069845] wlan0: authenticate with 00:0c:e6:59:29:43
[  114.075585] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  114.275911] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  114.479729] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  114.683433] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  114.976630] wlan0: authenticate with 00:0c:e6:59:0c:03
[  114.985090] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 1/3)
[  115.186813] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  115.390612] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  115.594354] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  115.829198] wlan0: authenticate with 00:0c:e6:59:24:43
[  115.978623] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  116.181647] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  116.385422] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  116.589145] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  120.546852] wlan0: authenticate with 00:0c:e6:59:23:03
[  120.551456] wlan0: direct probe to 00:0c:e6:59:23:03 (try 1/3)
[  120.752163] wlan0: direct probe to 00:0c:e6:59:23:03 (try 2/3)
[  120.955915] wlan0: direct probe to 00:0c:e6:59:23:03 (try 3/3)
[  121.159667] wlan0: authentication with 00:0c:e6:59:23:03 timed out
[  121.296462] wlan0: authenticate with 00:0c:e6:59:0a:03
[  121.308324] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 1/3)
[  121.511248] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 2/3)
[  121.715013] wlan0: direct probe to 00:0c:e6:59:0a:03 (try 3/3)
[  121.918784] wlan0: authentication with 00:0c:e6:59:0a:03 timed out
[  125.866690] wlan0: authenticate with 00:0c:e6:59:0c:43
[  125.872636] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  125.875280] wlan0: authenticated
[  125.882010] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  125.884320] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=2)
[  125.884391] wlan0: associated
[  125.888843] ath: regdomain 0x807c updated by CountryIE
[  125.888845] ath: EEPROM regdomain: 0x807c
[  125.888846] ath: EEPROM indicates we should expect a country code
[  125.888847] ath: doing EEPROM country->regdmn map search
[  125.888848] ath: country maps to regdmn code: 0x3a
[  125.888850] ath: Country alpha2 being used: CA
[  125.888851] ath: Regpair used: 0x3a
[  134.972140] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  141.496061] wlan0: authenticate with 00:0c:e6:59:0c:03
[  141.501514] wlan0: send auth to 00:0c:e6:59:0c:03 (try 1/3)
[  141.703106] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  141.906901] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  142.110625] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  142.348296] wlan0: authenticate with 00:0c:e6:59:0c:43
[  142.353789] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  142.554103] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  142.757905] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  142.961664] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  143.199040] wlan0: authenticate with 00:0c:e6:59:24:43
[  143.207361] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  143.409069] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  143.612863] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  143.816584] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  144.100871] wlan0: authenticate with 00:0c:e6:59:29:43
[  144.113082] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  144.315981] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  144.519750] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  144.723525] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  148.683912] wlan0: authenticate with 00:0c:e6:59:0c:43
[  148.689439] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  148.890577] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[  149.094344] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  149.298096] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  149.590733] wlan0: authenticate with 00:0c:e6:59:29:43
[  149.603178] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  149.805496] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  150.009198] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  150.212998] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  150.448847] wlan0: authenticate with 00:0c:e6:59:24:43
[  150.461097] wlan0: direct probe to 00:0c:e6:59:24:43 (try 1/3)
[  150.664484] wlan0: direct probe to 00:0c:e6:59:24:43 (try 2/3)
[  150.868238] wlan0: direct probe to 00:0c:e6:59:24:43 (try 3/3)
[  151.071968] wlan0: authentication with 00:0c:e6:59:24:43 timed out
[  155.020783] wlan0: authenticate with 00:0c:e6:59:0c:43
[  155.026409] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  155.030427] wlan0: authenticated
[  155.035196] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  155.238947] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  155.243914] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  155.243999] wlan0: associated
[  155.248787] ath: regdomain 0x807c updated by CountryIE
[  155.248789] ath: EEPROM regdomain: 0x807c
[  155.248790] ath: EEPROM indicates we should expect a country code
[  155.248791] ath: doing EEPROM country->regdmn map search
[  155.248792] ath: country maps to regdmn code: 0x3a
[  155.248794] ath: Country alpha2 being used: CA
[  155.248795] ath: Regpair used: 0x3a
[  162.937993] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  231.327286] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  231.856416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  232.886700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  237.923695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  242.972777] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  248.029570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  253.079822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  259.908618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  264.959489] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  270.012689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  275.074775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  280.109608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  287.865946] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  292.913600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  297.964282] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  303.001766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  308.048602] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  315.829304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  320.875894] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  325.924330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  330.979444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  336.018879] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  350.870163] wlan0: authenticate with 00:0c:e6:59:0c:43
[  350.875496] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  351.076996] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  351.280751] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[  351.484515] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  351.721956] wlan0: authenticate with 00:0c:e6:59:0c:43
[  351.734542] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  351.935924] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  352.139690] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[  352.343514] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[  356.295756] wlan0: authenticate with 00:0c:e6:59:29:43
[  356.301571] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  356.502550] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  356.706273] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  356.910014] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  360.859278] wlan0: authenticate with 00:0c:e6:59:0a:43
[  360.864959] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[  361.065057] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[  361.268809] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[  361.472524] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[  365.353022] wlan0: authenticate with 00:0c:e6:59:0c:03
[  365.359013] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 1/3)
[  365.559677] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 2/3)
[  365.763453] wlan0: direct probe to 00:0c:e6:59:0c:03 (try 3/3)
[  365.967151] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  369.848462] wlan0: authenticate with 00:0c:e6:59:0c:43
[  369.854376] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  369.947523] wlan0: authenticated
[  369.954441] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  370.158175] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  370.361937] wlan0: associate with 00:0c:e6:59:0c:43 (try 3/3)
[  370.565686] wlan0: association with 00:0c:e6:59:0c:43 timed out
[  370.865529] wlan0: authenticate with 00:0c:e6:59:0c:03
[  370.878306] wlan0: send auth to 00:0c:e6:59:0c:03 (try 1/3)
[  371.081065] wlan0: send auth to 00:0c:e6:59:0c:03 (try 2/3)
[  371.284810] wlan0: send auth to 00:0c:e6:59:0c:03 (try 3/3)
[  371.488580] wlan0: authentication with 00:0c:e6:59:0c:03 timed out
[  371.725023] wlan0: authenticate with 00:0c:e6:59:29:43
[  371.731412] wlan0: direct probe to 00:0c:e6:59:29:43 (try 1/3)
[  371.932073] wlan0: direct probe to 00:0c:e6:59:29:43 (try 2/3)
[  372.135827] wlan0: direct probe to 00:0c:e6:59:29:43 (try 3/3)
[  372.339578] wlan0: authentication with 00:0c:e6:59:29:43 timed out
[  372.571827] wlan0: authenticate with 00:0c:e6:59:0a:43
[  372.581143] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 1/3)
[  372.782991] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 2/3)
[  372.986749] wlan0: direct probe to 00:0c:e6:59:0a:43 (try 3/3)
[  373.190520] wlan0: authentication with 00:0c:e6:59:0a:43 timed out
[  396.543566] wlan0: authenticate with 00:0c:e6:59:0c:43
[  396.549277] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  396.550632] wlan0: authenticated
[  396.554591] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  396.758403] wlan0: associate with 00:0c:e6:59:0c:43 (try 2/3)
[  396.962168] wlan0: associate with 00:0c:e6:59:0c:43 (try 3/3)
[  396.963481] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  396.963555] wlan0: associated
[  396.964117] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  396.967317] ath: regdomain 0x807c updated by CountryIE
[  396.967318] ath: EEPROM regdomain: 0x807c
[  396.967319] ath: EEPROM indicates we should expect a country code
[  396.967319] ath: doing EEPROM country->regdmn map search
[  396.967320] ath: country maps to regdmn code: 0x3a
[  396.967322] ath: Country alpha2 being used: CA
[  396.967322] ath: Regpair used: 0x3a
[  417.633653] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  425.633425] wlan0: authenticate with 00:0c:e6:59:0c:43
[  425.639549] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[  425.641759] wlan0: authenticated
[  425.647832] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  425.649082] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=34)
[  425.649185] wlan0: associated
[  425.654265] ath: regdomain 0x807c updated by CountryIE
[  425.654267] ath: EEPROM regdomain: 0x807c
[  425.654268] ath: EEPROM indicates we should expect a country code
[  425.654269] ath: doing EEPROM country->regdmn map search
[  425.654270] ath: country maps to regdmn code: 0x3a
[  425.654271] ath: Country alpha2 being used: CA
[  425.654272] ath: Regpair used: 0x3a
[  446.598462] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  640.437299] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  641.489506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  646.541172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  651.600207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  656.640043] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  661.671216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  668.398608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  673.470477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  678.513646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  683.548593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  688.589080] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  696.378403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  701.429456] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  706.479173] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  711.527935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  716.590678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  724.322335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  729.345545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  734.395011] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  739.424602] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  744.476467] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  761.085576] wlan0: authenticate with 00:0c:e6:59:0c:43
[  761.089653] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[  761.290844] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[  761.494539] wlan0: send auth to 00:0c:e6:59:0c:43 (try 3/3)
[  761.497191] wlan0: authenticated
[  761.502545] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[  761.503937] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=28)
[  761.504043] wlan0: associated
[  761.505536] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  761.513928] ath: regdomain 0x807c updated by CountryIE
[  761.513931] ath: EEPROM regdomain: 0x807c
[  761.513933] ath: EEPROM indicates we should expect a country code
[  761.513936] ath: doing EEPROM country->regdmn map search
[  761.513939] ath: country maps to regdmn code: 0x3a
[  761.513942] ath: Country alpha2 being used: CA
[  761.513944] ath: Regpair used: 0x3a
[  782.200407] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[  912.462884] ath9k: ath9k: Driver unloaded
[  930.435013] ath: EEPROM regdomain: 0x6c
[  930.435016] ath: EEPROM indicates we should expect a direct regpair map
[  930.435018] ath: Country alpha2 being used: 00
[  930.435019] ath: Regpair used: 0x6c
[  930.435654] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  930.435959] Registered led device: ath9k-phy0
[  930.452345] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  930.454833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1048.944751] wlan0: Selected IBSS BSSID f6:fa:40:2e:02:e9 based on configured SSID
[ 1048.963211] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1100.655473] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1100.667869] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 1/3)
[ 1100.869012] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 2/3)
[ 1101.072765] wlan0: direct probe to 00:0c:e6:59:0c:43 (try 3/3)
[ 1101.276543] wlan0: authentication with 00:0c:e6:59:0c:43 timed out
[ 1119.008236] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1119.014120] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[ 1119.017247] wlan0: authenticated
[ 1119.023344] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[ 1119.024772] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=46)
[ 1119.024926] wlan0: associated
[ 1119.035169] ath: regdomain 0x807c updated by CountryIE
[ 1119.035172] ath: EEPROM regdomain: 0x807c
[ 1119.035175] ath: EEPROM indicates we should expect a country code
[ 1119.035177] ath: doing EEPROM country->regdmn map search
[ 1119.035180] ath: country maps to regdmn code: 0x3a
[ 1119.035183] ath: Country alpha2 being used: CA
[ 1119.035185] ath: Regpair used: 0x3a
[ 1121.791798] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[ 1128.968336] wlan0: authenticate with 00:0c:e6:59:0c:43
[ 1128.973696] wlan0: send auth to 00:0c:e6:59:0c:43 (try 1/3)
[ 1129.175214] wlan0: send auth to 00:0c:e6:59:0c:43 (try 2/3)
[ 1129.178254] wlan0: authenticated
[ 1129.183195] wlan0: associate with 00:0c:e6:59:0c:43 (try 1/3)
[ 1129.185025] wlan0: RX AssocResp from 00:0c:e6:59:0c:43 (capab=0x11 status=0 aid=43)
[ 1129.185156] wlan0: associated
[ 1129.192223] ath: regdomain 0x807c updated by CountryIE
[ 1129.192224] ath: EEPROM regdomain: 0x807c
[ 1129.192225] ath: EEPROM indicates we should expect a country code
[ 1129.192226] ath: doing EEPROM country->regdmn map search
[ 1129.192228] ath: country maps to regdmn code: 0x3a
[ 1129.192229] ath: Country alpha2 being used: CA
[ 1129.192230] ath: Regpair used: 0x3a
[ 1150.757034] wlan0: deauthenticating from 00:0c:e6:59:0c:43 by local choice (reason=3)
[ 1156.825073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1157.857584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1162.901935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1167.953160] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1172.997962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1178.045202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.789765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1189.817564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1194.875195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1199.925477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1204.975446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1212.754285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1217.804620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1222.833116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1227.874706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1232.902272] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

**dmesg | tail -20:**

Test 1:
```
[ 1150.783051] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1150.783053] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1150.783054] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1150.783056] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1150.783058] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1156.825073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1157.857584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1162.901935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1167.953160] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1172.997962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1178.045202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.789765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1189.817564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1194.875195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1199.925477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1204.975446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1212.754285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1217.804620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1222.833116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1227.874706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Test 2:
```
[ 1172.997962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1178.045202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.789765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1189.817564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1194.875195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1199.925477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1204.975446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1212.754285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1217.804620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1222.833116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1227.874706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1232.902272] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1250.308036] CPU0: Package power limit notification (total events = 8724)
[ 1250.308038] CPU1: Package power limit notification (total events = 8735)
[ 1250.308055] CPU2: Package power limit notification (total events = 8725)
[ 1250.308057] CPU3: Package power limit notification (total events = 8729)
[ 1250.310423] CPU3: Package power limit normal
[ 1250.310425] CPU1: Package power limit normal
[ 1250.310426] CPU2: Package power limit normal
[ 1250.310428] CPU0: Package power limit normal

```

nohwcrypt is still equal to 1.

I find it odd that it works at times but not at other times even if I try in the same location to eliminate it being a signal problem.

Thanks!

---

### Post by varunendra on 2012-11-20
> **mabubakr94 said:**
> ..connection for UofT would not go through, keeps asking for username and password over and over again.
..
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR=Red]on[/COLOR]**
```
Did you try the power management off script ? In your last outputs, the power management was off. It may affect connectivity, even if not the root cause of the current problem. So just turn it off by -
```
sudo iwconfig wlan0 power off
```
And retry to connect to see if it helps.

Also, there are too many IPv6 related messages which seem unusual to me (but maybe because I don't have very extensive experience with wireless networks). Try disabling IPv6 as well as setting it to 'Ignore' in Network Manager. It can be permanently disabled by adding the following to your /etc/sysctl.conf file -
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
You can easily do so by just copy-pasting the following command in a terminal -
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

If all these three settings together *(nohwcrypt=1 parameter, power management=off, and IPv6 disabled)* don't help, I must ask you to post the result of the wireless_script once again, as in [post #4]("http://ubuntuforums.org/showpost.php?p=12345428") when you experience problem in connectivity, and I may then have to consult one of the 'real' experts here.

But please confirm all of these are in effect next time you try.

Hope we get it sorted finally :)

---

### Post by mabubakr94 on 2012-11-21
Sorry about that! I forgot to disable power management before outputting iwconfig. I did turn it off after and I was still experiencing the same problems. As I saw no clear evidence that power management disabled was helping, as I got same results when I tried with it on and off, I didn't permanently disable it yet.

However, the problem still persists. The following wireless_script file was generated with the following settings:
*nohwcrypt = 1, power management = off, IPv6 ignored.*

```

*************** info trace ****************



**** uname -a ****


Linux Abubakr-Laptop 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
	Subsystem: Acer Incorporated [ALI] Device [1025:0724]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e052]
	Kernel driver in use: ath9k


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04f2:b335 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
nls_iso8859_1          12713  1 
ext2                   72880  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17457  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12529  2 
ath9k                 131308  0 
mac_hid                13205  0 
mac80211              539908  1 ath9k
wmi                    19070  1 acer_wmi
uvcvideo               76749  0 
i915                  520629  3 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
ath9k_common           14055  1 ath9k
videobuf2_vmalloc      12860  1 uvcvideo
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         46784  1 i915
psmouse                95552  0 
serio_raw              13215  0 
soundcore              15047  1 snd
lp                     17759  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
drm                   275528  4 i915,drm_kms_helper
cfg80211              206566  3 ath9k,mac80211,ath
i2c_algo_bit           13413  1 i915
parport                46345  3 parport_pc,ppdev,lp
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lpc_ich                17061  0 
microcode              22803  0 
video                  19335  2 acer_wmi,i915
mei                    40690  0 
r8169                  61650  0 


**** nm-tool ****



NetworkManager Tool

State: connecting

- Device: wlan0  [UofT] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 3 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 92 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 90 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 90 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 74 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 55 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 80 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 57 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 80 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 47 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 69 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 75 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 50 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 84 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 85 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 77 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 54 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 45 WEP
    cslab:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 44 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 27 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 27 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 60 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 70 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WEP
    cslab:           Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 29 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WEP
    UofT:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WEP
    cslab:           Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 37 WEP
    cslab:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 74 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 89 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 45 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 22 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 67 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 70 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 25 WEP
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    iqua:            Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WEP
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WEP
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    HP8AAF45:        Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    Mobile APL:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 79 WPA
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 64 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 68 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    cslab:           Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 29 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 34 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WEP
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    cslab:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60 WEP
    cslab:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 52 WEP
    UTORwin:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 32 WEP
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise


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

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


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


[   13.055065] wmi: Mapper loaded
[   13.081229] ath: EEPROM regdomain: 0x6c
[   13.081233] ath: EEPROM indicates we should expect a direct regpair map
[   13.081236] ath: Country alpha2 being used: 00
[   13.081237] ath: Regpair used: 0x6c
[   13.105932] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.107863] Registered led device: ath9k-phy0
[   13.123748] acer_wmi: Acer Laptop ACPI-WMI Extras
[   13.123762] acer_wmi: Function bitmap for Communication Button: 0x801
[   13.141090] acer_wmi: Brightness must be controlled by acpi video driver
[   14.598001] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.601008] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.358184] wlan0: authenticate with <MAC address removed>
[   22.370155] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.573495] wlan0: send auth to <MAC address removed> (try 2/3)
[   22.777254] wlan0: send auth to <MAC address removed> (try 3/3)
[   22.981007] wlan0: authentication with <MAC address removed> timed out
[   23.379869] wlan0: authenticate with <MAC address removed>
[   23.392966] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.396254] wlan0: authenticated
[   23.400487] wlan0: associate with <MAC address removed> (try 1/3)
[   23.401754] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[   23.401832] wlan0: associated
[   23.402670] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.406380] ath: regdomain 0x807c updated by CountryIE
[   23.406381] ath: EEPROM regdomain: 0x807c
[   23.406382] ath: EEPROM indicates we should expect a country code
[   23.406383] ath: doing EEPROM country->regdmn map search
[   23.406384] ath: country maps to regdmn code: 0x3a
[   23.406385] ath: Country alpha2 being used: CA
[   23.406386] ath: Regpair used: 0x3a
[   44.079944] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   61.367775] wlan0: authenticate with <MAC address removed>
[   61.375270] wlan0: direct probe to <MAC address removed> (try 1/3)
[   61.578826] wlan0: direct probe to <MAC address removed> (try 2/3)
[   61.782582] wlan0: direct probe to <MAC address removed> (try 3/3)
[   61.986333] wlan0: authentication with <MAC address removed> timed out
[   62.453945] wlan0: authenticate with <MAC address removed>
[   62.466257] wlan0: direct probe to <MAC address removed> (try 1/3)
[   62.669516] wlan0: direct probe to <MAC address removed> (try 2/3)
[   62.873297] wlan0: direct probe to <MAC address removed> (try 3/3)
[   63.077043] wlan0: authentication with <MAC address removed> timed out
[   63.486557] wlan0: authenticate with <MAC address removed>
[   63.498901] wlan0: send auth to <MAC address removed> (try 1/3)
[   63.501733] wlan0: authenticated
[   63.508521] wlan0: associate with <MAC address removed> (try 1/3)
[   63.510118] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=3)
[   63.510199] wlan0: associated
[   63.522065] ath: regdomain 0x807c updated by CountryIE
[   63.522066] ath: EEPROM regdomain: 0x807c
[   63.522068] ath: EEPROM indicates we should expect a country code
[   63.522069] ath: doing EEPROM country->regdmn map search
[   63.522071] ath: country maps to regdmn code: 0x3a
[   63.522072] ath: Country alpha2 being used: CA
[   63.522073] ath: Regpair used: 0x3a
[   83.032726] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  100.857723] wlan0: authenticate with <MAC address removed>
[  100.870351] wlan0: direct probe to <MAC address removed> (try 1/3)
[  101.071590] wlan0: direct probe to <MAC address removed> (try 2/3)
[  101.275423] wlan0: direct probe to <MAC address removed> (try 3/3)
[  101.479102] wlan0: authentication with <MAC address removed> timed out
[  101.924712] wlan0: authenticate with <MAC address removed>
[  101.937071] wlan0: direct probe to <MAC address removed> (try 1/3)
[  102.138304] wlan0: direct probe to <MAC address removed> (try 2/3)
[  102.342059] wlan0: direct probe to <MAC address removed> (try 3/3)
[  102.545817] wlan0: authentication with <MAC address removed> timed out
[  102.964347] wlan0: authenticate with <MAC address removed>
[  102.977066] wlan0: send auth to <MAC address removed> (try 1/3)
[  102.979627] wlan0: authenticated
[  102.985300] wlan0: associate with <MAC address removed> (try 1/3)
[  102.990250] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=3)
[  102.990335] wlan0: associated
[  102.994679] ath: regdomain 0x807c updated by CountryIE
[  102.994680] ath: EEPROM regdomain: 0x807c
[  102.994681] ath: EEPROM indicates we should expect a country code
[  102.994682] ath: doing EEPROM country->regdmn map search
[  102.994683] ath: country maps to regdmn code: 0x3a
[  102.994684] ath: Country alpha2 being used: CA
[  102.994685] ath: Regpair used: 0x3a
[  121.989209] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  130.489080] wlan0: authenticate with <MAC address removed>
[  130.501093] wlan0: send auth to <MAC address removed> (try 1/3)
[  130.506711] wlan0: authenticated
[  130.512367] wlan0: associate with <MAC address removed> (try 1/3)
[  130.513706] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  130.513787] wlan0: associated
[  130.522339] ath: regdomain 0x807c updated by CountryIE
[  130.522341] ath: EEPROM regdomain: 0x807c
[  130.522342] ath: EEPROM indicates we should expect a country code
[  130.522343] ath: doing EEPROM country->regdmn map search
[  130.522345] ath: country maps to regdmn code: 0x3a
[  130.522346] ath: Country alpha2 being used: CA
[  130.522347] ath: Regpair used: 0x3a
[  132.856871] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  141.726422] wlan0: authenticate with <MAC address removed>
[  141.738057] wlan0: direct probe to <MAC address removed> (try 1/3)
[  141.938767] wlan0: direct probe to <MAC address removed> (try 2/3)
[  142.142517] wlan0: direct probe to <MAC address removed> (try 3/3)
[  142.346242] wlan0: authentication with <MAC address removed> timed out
[  142.924589] wlan0: authenticate with <MAC address removed>
[  142.936235] wlan0: send auth to <MAC address removed> (try 1/3)
[  143.137279] wlan0: send auth to <MAC address removed> (try 2/3)
[  143.138198] wlan0: authenticated
[  143.141278] wlan0: associate with <MAC address removed> (try 1/3)
[  143.142513] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  143.142590] wlan0: associated
[  143.148531] ath: regdomain 0x807c updated by CountryIE
[  143.148533] ath: EEPROM regdomain: 0x807c
[  143.148535] ath: EEPROM indicates we should expect a country code
[  143.148536] ath: doing EEPROM country->regdmn map search
[  143.148537] ath: country maps to regdmn code: 0x3a
[  143.148539] ath: Country alpha2 being used: CA
[  143.148540] ath: Regpair used: 0x3a
[  183.281358] wlan0: authenticate with <MAC address removed>
[  183.284689] wlan0: send auth to <MAC address removed> (try 1/3)
[  183.289953] wlan0: authenticated
[  183.297267] wlan0: associate with <MAC address removed> (try 1/3)
[  183.298686] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  183.298768] wlan0: associated
[  292.911603] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  301.775257] wlan0: authenticate with <MAC address removed>
[  301.787178] wlan0: send auth to <MAC address removed> (try 1/3)
[  301.987281] wlan0: send auth to <MAC address removed> (try 2/3)
[  301.989988] wlan0: authenticated
[  301.995315] wlan0: associate with <MAC address removed> (try 1/3)
[  301.996962] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  301.997073] wlan0: associated
[  302.007627] ath: regdomain 0x807c updated by CountryIE
[  302.007630] ath: EEPROM regdomain: 0x807c
[  302.007632] ath: EEPROM indicates we should expect a country code
[  302.007635] ath: doing EEPROM country->regdmn map search
[  302.007638] ath: country maps to regdmn code: 0x3a
[  302.007641] ath: Country alpha2 being used: CA
[  302.007643] ath: Regpair used: 0x3a
[  317.752596] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  326.623486] wlan0: authenticate with <MAC address removed>
[  326.630363] wlan0: direct probe to <MAC address removed> (try 1/3)
[  326.833543] wlan0: direct probe to <MAC address removed> (try 2/3)
[  327.037357] wlan0: direct probe to <MAC address removed> (try 3/3)
[  327.241070] wlan0: authentication with <MAC address removed> timed out
[  327.707665] wlan0: authenticate with <MAC address removed>
[  327.723167] wlan0: direct probe to <MAC address removed> (try 1/3)
[  327.924239] wlan0: send auth to <MAC address removed> (try 2/3)
[  327.927882] wlan0: authenticated
[  327.932255] wlan0: associate with <MAC address removed> (try 1/3)
[  327.934278] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  327.934350] wlan0: associated
[  327.941712] ath: regdomain 0x807c updated by CountryIE
[  327.941715] ath: EEPROM regdomain: 0x807c
[  327.941717] ath: EEPROM indicates we should expect a country code
[  327.941719] ath: doing EEPROM country->regdmn map search
[  327.941722] ath: country maps to regdmn code: 0x3a
[  327.941724] ath: Country alpha2 being used: CA
[  327.941726] ath: Regpair used: 0x3a
[  346.717111] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  360.995638] wlan0: authenticate with <MAC address removed>
[  361.007613] wlan0: direct probe to <MAC address removed> (try 1/3)
[  361.208485] wlan0: direct probe to <MAC address removed> (try 2/3)
[  361.412252] wlan0: direct probe to <MAC address removed> (try 3/3)
[  361.616013] wlan0: authentication with <MAC address removed> timed out
[  362.099325] wlan0: authenticate with <MAC address removed>
[  362.111576] wlan0: send auth to <MAC address removed> (try 1/3)
[  362.114233] wlan0: authenticated
[  362.119428] wlan0: associate with <MAC address removed> (try 1/3)
[  362.120733] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=3)
[  362.120813] wlan0: associated
[  362.125639] ath: regdomain 0x807c updated by CountryIE
[  362.125640] ath: EEPROM regdomain: 0x807c
[  362.125641] ath: EEPROM indicates we should expect a country code
[  362.125643] ath: doing EEPROM country->regdmn map search
[  362.125644] ath: country maps to regdmn code: 0x3a
[  362.125646] ath: Country alpha2 being used: CA
[  362.125647] ath: Regpair used: 0x3a
[  382.674012] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  396.691778] wlan0: authenticate with <MAC address removed>
[  396.703536] wlan0: send auth to <MAC address removed> (try 1/3)
[  396.709950] wlan0: authenticated
[  396.713974] wlan0: associate with <MAC address removed> (try 1/3)
[  396.715529] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  396.715609] wlan0: associated
[  396.720797] ath: regdomain 0x807c updated by CountryIE
[  396.720798] ath: EEPROM regdomain: 0x807c
[  396.720799] ath: EEPROM indicates we should expect a country code
[  396.720800] ath: doing EEPROM country->regdmn map search
[  396.720801] ath: country maps to regdmn code: 0x3a
[  396.720802] ath: Country alpha2 being used: CA
[  396.720803] ath: Regpair used: 0x3a
[  582.876363] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  587.245566] wlan0: authenticate with <MAC address removed>
[  587.257627] wlan0: send auth to <MAC address removed> (try 1/3)
[  587.457891] wlan0: send auth to <MAC address removed> (try 2/3)
[  587.460768] wlan0: authenticated
[  587.465813] wlan0: associate with <MAC address removed> (try 1/3)
[  587.467183] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=1)
[  587.467291] wlan0: associated
[  587.477451] ath: regdomain 0x807c updated by CountryIE
[  587.477454] ath: EEPROM regdomain: 0x807c
[  587.477457] ath: EEPROM indicates we should expect a country code
[  587.477459] ath: doing EEPROM country->regdmn map search
[  587.477462] ath: country maps to regdmn code: 0x3a
[  587.477465] ath: Country alpha2 being used: CA
[  587.477467] ath: Regpair used: 0x3a
[  608.407292] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)


**************** done ********************


```

What's great though is that since it works sometimes, we know that Ubuntu does support the connection and has the possibility to allow me running it as main OS on my laptop. :)


Thanks!

---

### Post by varunendra on 2012-11-21
Hmm.. nothing seems wrong in there to my 'inexperienced' eyes. So before I go asking for help from someone else, one more answer please -
Have you tried saving the correct pass-phrase and encryption type in the Network Manager permanently ? It shouldn't ask you for pass-phrase then. If not, please try that this time and post back if it makes any difference or not.

---

### Post by mabubakr94 on 2012-11-21
All encryption and password settings are correct. I have checked many times but it still asks for username and password many times. Looking at the logs, it doesn't say authentication rejected, just timed out, so not sure.

---

### Post by varunendra on 2012-11-21
> **mabubakr94 said:**
> All encryption and password settings are correct....and saved in NM ?

---

### Post by mabubakr94 on 2012-11-21
Yes. When it works it works without asking for username and password so I know they are setup correctly. Only when it fails to connect will it ask for them again as the fields are already filled in.

---

### Post by varunendra on 2012-11-21
Okay then, I've asked someone to look at it when possible. Just for reference -

What are the encryption settings ? WPA & WPA2 Enterprise + TLS/LEAP/...?

Shall post back as soon as I get some help I've asked for, or maybe he'll reply you directly.

---

### Post by mabubakr94 on 2012-11-21
Hi.

**Security:** WPA & WPA2 Enterprise
**Authentication:** Protected EAP (PEAP)
Anonymous ID: ''
**CA certificate:** (none)
**PEAP version:** Automatic (Tried version 0 and 1, same results)
**Inner authentication:** MSCHAPv2

These are the settings suggested on the UofT setup page and I have configured these.

---

### Post by chili555 on 2012-11-22
First of all, please double-check the /etc/modprobe.d/ath9k.conf file. Make sure it says exactly:```
options ath9k nohwcrypt=1
```If it is any different, please correct it. 

What I strongly suspect is that we have here is a classic example of Network Manager's glaring weakness. When there are several ESSIDs with the same name and reasonable strength, as here:>  Wireless Access Points 
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 3 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    UofT:            Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
etc., etc., etc.Then we see NM roam from access point to access point never really connecting before it wants to roam again:> [   80.034563] wlan0: deauthenticating from [COLOR="Red"]00:0c:e6:48:b2:**40**[/COLOR] by local choice (reason=3)
[   90.882789] wlan0: authenticate with [COLOR="Red"]00:0c:e6:48:b2:**41**[/COLOR]
[   90.886334] wlan0: send auth to 00:0c:e6:48:b2:41 (try 1/3)
[   90.890848] wlan0: authenticated
[   90.895934] wlan0: associate with 00:0c:e6:48:b2:41 (try 1/3)
[   90.897038] wlan0: RX AssocResp from 00:0c:e6:48:b2:41 (capab=0x11 status=0 aid=1)
[   90.897113] wlan0: associated
[   90.901864] ath: regdomain 0x807c updated by CountryIE
[   90.901866] ath: EEPROM regdomain: 0x807c
[   90.901867] ath: EEPROM indicates we should expect a country code
[   90.901868] ath: doing EEPROM country->regdmn map search
[   90.901869] ath: country maps to regdmn code: 0x3a
[   90.901871] ath: Country alpha2 being used: CA
[   90.901872] ath: Regpair used: 0x3a
[  355.566941] wlan0: deauthenticating from 00:0c:e6:48:b2:41 by local choice (reason=3)
[  360.434507] wlan0: authenticate with 00:0c:e6:48:b2:40A fix that has helped in the past is to specify the MAC address of the strongest nearby access point, thereby informing NM that we want one and only one SSID named UofT. 

I suggest you do:```
nm-tool
```Make note of one of the SSIDs you wish to connect to by MAC address. Then right-click the NM icon and specify the MAC address you want. Please see attached.

We look forward to your report.

---

### Post by varunendra on 2012-11-22
Hi chili555, thanks a lot for joining-in.

Just out of curiosity -
Although I was totally unaware about that behaviour of NM and also overlooked the parts you highlighted, I was tempted to suggest the OP to switch to wicd, as I have seen many posts that suggest it is often better than NM in such weird authentication issues. Do you think it is a fact in any particular situation ? Or just coincidences? Because the posts I'm referring to were often posted by the OPs who said their problem was solved by switching to it.

I was waiting for your input before suggesting that because I found no logical explanation to that.

And..
> **chili555 said:**
> Make note of one of the SSIDs you wish to  connect to by MAC address. Then right-click the NM icon and specify the  MAC address you want.If multiple connections are stored with different MAC IDs in above manner, would NM switch automatically to the next **best** one if the person moves too far away from the current access point ? Or would he need to manually select the best one (best in his new location)?

I'm in no hurry, so please answer when you have got 'nothing better' to do :)

---

### Post by chili555 on 2012-11-22
I think there is a pretty good chance that Wicd would perform better. However, I'd try specifying the MAC in NM first. > If multiple connections are stored with different MAC IDs in above manner, would NM switch automatically to the next best one if the person moves too far away from the current access point ?Probably not and I wouldn't try. I'd try to get a setting for, for example, dorm and leave it at that. He already gets service in the lab.

He might be able to set up two or three, dorm, cafeteria, someotherplace, etc., but I don't know for sure since I have no such situation to experiment with.

What's going to show up in the NM icon is, nevertheless, what scan and nm-tool show: UofT, euroroam, etc. He'll probably need to click the NM icon, edit connections and fiddle around a bit. It is one of the few remaining weaknesses in NM. It's great for me and Mrs. Chili on her computer; there is but one SSID with a name she recognizes, not 327! She clicks and connects the first time and it works seamlessly thereafter.

I watched this thread unfold here and suspected that duplicate SSIDs were a probable issue. I also wondered how long I could hold myself back!

---

### Post by mabubakr94 on 2012-11-22
I still seem to be getting the same problem.

I'll walk you through my steps to make sure I am doing it correctly.

1. I typed *nm-tool* in the terminal and it returned a large list of connections. I looked through for all lines with ESSID equal to "UofT".
2. I found the follow with a reasonable strength, assuming 100 is max strength as I didn't see anything higher than that:

```
UofT:            Infra, 00:0C:E6:48:B2:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
```

3. I copied *00:0C:E6:48:B2:00* from above and entered it into my UofT connection in the network manager under BSSID. Additionally renamed it so I can organize as I assume I would have to make lots of these depending on location. (IPv6 is still set to ignore.)

[IMG]http://i.imgur.com/Z2nHg.png[/IMG]

4. Tried connecting multiple times but still same results. Sometimes it works, other times it does not. Only chance for it to work is after a restart and trying again. (Worked in the morning but didn't report back as I wanted to test again.  Now later in the day I'm back in the same building, just a few metres down in another room.

So manually assigning the MAC address did not have any effect. :S

Would this *wicd* you guys are talking about help?

Thanks!

Edit:

> First of all, please double-check the /etc/modprobe.d/ath9k.conf file. Make sure it says exactly:
Code:
options ath9k nohwcrypt=1

Forgot to confirm, I have checked and indeed it is correct.

---

### Post by varunendra on 2012-11-24
> **mabubakr94 said:**
> Would this *wicd* you guys are talking about help?
Not sure if Dr. chili would approve of it yet, but I'd say let's give it a shot. However, using two network managers simultaneously would almost certainly cause problems, and I won't advice to uninstall network manager unless wicd proves its worth.

So we'd only disable nm while we use wicd for a test. To install wicd -
```
sudo apt-get install wicd
```After it is downloaded and installed, we need to prevent Network Manager from loading at startup. To make it visible in "Startup Applications" dialogue box we have to edit its .desktop file in /etc/xdg/autostart/ directory -
```
gksu gedit /etc/xdg/autostart/nm-applet.desktop
```Look for the line that says - "**NoDisplay=true**".
Change the value to "**false**", so the file looks like -
```
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
**NoDisplay=[COLOR=Red]false[/COLOR]**
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```Save and close gedit. DO NOT touch any other line unless you know what you are doing. [COLOR=DarkSlateGray]*(* it is always a good practice to create a backup of system files before messing with them)*[/COLOR]

Now open Startup Applications dialogue  (Power button > Startup Applications...). You should see the NM-applet icon here with name -"Network". Just clear the check-box before it to disable it from loading at startup [COLOR=DarkSlateGray][I](you can still load it manually by pressing Alt+F2 > type nm-applet > press 'Enter'. To permanently re-enable it, if needed later, we'd only need to put a tick in the check-box again.)
[/I][/COLOR]
Now reboot, run wicd, save the required settings, try to connect and see how well it performs.
I'm not sure, but AFAIK, it needs to be started manually, and won't give you any system-tray indicator like nm-applet. If that's true *(I'd appreciate your feedback on its functioning)*, all you'd need to do is load (manually) nm-applet instead of wicd if you find it unsatisfactory. Of-course you can also delete it and all its settings, configuration files with -
```
sudo apt-get purge wicd
```
PS :
Here's something extra, although unrelated -
If you browse to **/etc/xdg/autostart** directory, you'd see many files like *nm-applet.desktop*. All of them are startup applications which don't appear in the Startup Applications dialogue-box by default. You can make them visible using the same steps as we did with *nm-applet.desktop* above.

My favourite one-liner method to make all of them visible in one step is -
sudo sed -i 's:NoDisplay=true:NoDisplay=false:' /etc/xdg/autostart/*.*
*[if you don't already know, we can always use colon (: ) or underscore ( _ ) instead of slash ( / ) as separators in sed, whatever looks better.]*

---

### Post by mabubakr94 on 2012-11-26
Hmm. I'm on Ubuntu 12.10 so I could not find the startup applications window by clicking the power button. I used Alt + F2 and typed in:

```
gnome-sessions-properties
```

It did seem to work as I was able to disable the network manager from starting up.

However, wicd did not seem to have any positive effect. It says *'awaiting authentication'* for a while but then it also seems to time out. Basically, the same result as network manager.

I was surprised this morning when the connection started working when I specified the address but once again it was random as now I am not able to connect. I think I will keep trying with network manager unless you have any other solutions.

It sucks how the school IT does not offer support for Linux.

---

### Post by varunendra on 2012-11-26
> **mabubakr94 said:**
> Hmm. I'm on Ubuntu 12.10 so I could not find the startup applications window by clicking the power button.
Just booted a 12.10 32bit iso in a VM and found that missing. However, you can still access it by typing "Startup" in Dash.

Another easier way is to just copy the nm-applet.desktop file into .config/autostart directory *(create if doesn't already exist)* in your Home, then toggle the value of line "*X-GNOME-Autostart-enabled=*" to "*true*" or "*false*" to enable/disable nm at startup.

Anyway, I remembered something from 3 years back when I was an IT executive in a college and dealt with similar problems in students' laptops. A quick search returned these -
[https://en.wikipedia.org/wiki/Wireless_access_point#Limitations](https://en.wikipedia.org/wiki/Wireless_access_point#Limitations) a snippet -
> One IEEE 802.11 AP can typically communicate with 30 client systems located within a radius of 103 m
and -
[http://compnetworking.about.com/od/wirelessfaqs/f/howmanydevices.htm](http://compnetworking.about.com/od/wirelessfaqs/f/howmanydevices.htm)
> Connecting 255 computers to a single WiFi access point, while theoretically possible, is not recommended

Now since you seem to be dual booting with windows, can you verify if you can connect to the same access-point (MAC or BSSID) in windows when it fails to connect in Ubuntu?
Obviously, I'm thinking of a possibility if the number of allowd connections or dhcp pool of an access-point gets saturated, and we are still trying to connect to it.

If this assumption has any substance and the "nm confusion with multiple APs of same name" is the only problem left, then maybe creating multiple profiles with same SSID but different BSSIDs may help by switching to other if one fails.
Although looking at the profile-name in your screenshot, I suspect if you have already tried that.

Regardless, please confirm the scenario with Windows if there's a way (or if you can find a way) to connect to specifically the same access-point which fails to connect in Ubuntu - obviously, immediately after it fails (and try back in ubuntu if it does successfuly connect in windows).

As for wicd, since it didn't help, I think you should purge it to avoid any possible conflicts -
```
sudo apt-get purge wicd
```

---

### Post by mabubakr94 on 2012-11-26
I completely wiped my windows partition but I am always connecting with my Android phone to make sure it is not the access point which has a problem. It always works on my phone.

If I understand correctly, multiple signals can cause the connections to get weird. As sometimes I have noticed that in some of my classes, being first year they are quite big (~1500 students in my largest), the connections fail when everyone boots up their laptop. However when I wait until we're midway through the lecture and less people are repeatedly trying to connect, I see more success.

As for the issue of a limited number of users allowed on a single access point, I'm not sure if that could be causing the problem. In one of my lecture halls I counted at least 6 routers in a class with around 250 students.

I will try once again with your suggestion of making multiple profiles with same SSID. Currently I only had one made for each lecture hall, I simply configured it each time by doing 'nm-tool' and changing SSID to the strongest one.

I'll let you know how it goes.

Thanks!

---

### Post by mabubakr94 on 2012-12-03
OK. It seems to be working fairly well now. Sometimes it is on and off but no worse than when on Windows 7.

Thanks for your help!

---

### Post by varunendra on 2012-12-03
> **mabubakr94 said:**
> OK. It seems to be working fairly well now. Sometimes it is on and off but no worse than when on Windows 7.

Thanks for your help!

Glad at you find it at least usable now, and sorry for leaving it in a confused state and not being able to help you more on this. But I guess that was all I could think of with my current knowledge and experience.

I very much appriciate your persistence and willingness to work through it all. I actually learned quite some new things from this thread which I'm sure would help me strengthen my skills and be more precise next time I deal with similar problems. I really owe a big thanks to you for your clear and comprehensive feedbacks and positive attitude all this while - "THANK YOU"!

I think you should mark the thread as [Solved] now **IF** you really find the connectivity and stability good enough to be called 'satisfactory', **but leave it open if** it still is an 'annoying' game of hit and miss, so we know we still need a lot of improvement to reach that level.

In any case, we all would certainly appreciate your report on what all changes you have applied and maybe a description of how it is performing now.

Thanks!

Varun

---

### Post by mabubakr94 on 2012-12-03
Hi.

I was trying to set it to solve but was unable to locate the option when I was in class. I found it now and have done so.

These are the final settings which seem to have made the wireless usable.

```
nohwcrypt = 1
power management = on (Figured turning it off had no difference.)
Using Network manager, wicd performed no better, maybe even worse.
IPv6 was initially disabled but even with it on, experienced same results. Left it on for now.

```

Chili's suggestion to manually specify MAC seemed to do the trick. Initially it showed no improvement but once again there were a lot of access points to choose between. I simply tried cycling between them and eventually it works. It is not ideal but I manually set the address each time I want to connect. However, it is not too bad as I am a CS student so I am mostly in the CS buildings which have the other connections that easily connect to Ubuntu.

Only one lecture hall does not seem to work but that had problems even on Windows 7, my guess is because of the number of people connecting in that hall. (~1500 - 2000 people)

Once again, thanks a lot for your help. Really starting to enjoy using the terminal or cmd prompt. :)

Still have some issues to fix such as not completely powering off on shutdown and card reader not working, but that will have to wait until after exams. :)

---

### Post by dapper.ic on 2013-01-07
It looks like you've got it working, but I thought I'd put this on here anyway.

I'm at the UTSC campus, but I imagine the login's the same across the board. I got it working with the same setup you described above, (WPA & WPA2 Enterprise; PEAP; PEAP Ver. Automatic; MSCHAPv2) 

Except for the Certificate. Use: /usr/share/ca-certificates/mozilla/AddTrust_External_Root.crt

Hopefully this helps.

---

### Post by mabubakr94 on 2013-01-07
> **dapper.ic said:**
> It looks like you've got it working, but I thought I'd put this on here anyway.

I'm at the UTSC campus, but I imagine the login's the same across the board. I got it working with the same setup you described above, (WPA & WPA2 Enterprise; PEAP; PEAP Ver. Automatic; MSCHAPv2) 

Except for the Certificate. Use: /usr/share/ca-certificates/mozilla/AddTrust_External_Root.crt

Hopefully this helps.

I got it working most of the time but even then it takes multiple tries. I'll try out this certificate tomorrow. Thanks!

---

### Post by dapper.ic on 2013-01-07
No prob, bob. 

Let me know if it works.

---

### Post by mabubakr94 on 2013-01-08
No luck. Still very flaky as before. I'm starting to think it might be a driver issue. My friend is also running Ubuntu and with the same settings, he can connect flawlessly. As for now their old network, UTORWin is working but that is going to be dropped in the future .

---

### Post by dapper.ic on 2013-01-08
Yeah, I always used UTORwin and actually found this thread yesterday trying to get UofT to work, before I just started fiddling around with it. I'm afraid though that this is the extent of the help I can provide. 

Good luck!

---

