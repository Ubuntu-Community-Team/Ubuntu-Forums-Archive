---
title: "Problem connecting WiFi using Intel pro wireless 3945ABG"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by anandhiroji on 2010-03-02
Problem to connect WiFi using Intel pro wireless 3945ABG

I am not able to connect to internet using my wifi my Lan works perfectly fine.
My machine is dell inspiron 1420 with Bios A10.

I am very new to Ubuntu 9.10 and this is my second day :) I am running Ubuntu from USB directly. I updated all security updates from update manager but still it is not connecting
 
Please help me so that I can also experience the Unubtu fully..

Thank you in Advance....

if i run 
dmesg | grep iwl

it display following information

ubuntu@ubuntu:~$ dmesg | grep iwl
[   35.283048] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   35.283051] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   35.283176] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   35.283191] iwl3945 0000:0c:00.0: setting latency timer to 64
[   35.355281] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   35.355285] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   35.355456] iwl3945 0000:0c:00.0: irq 31 for MSI/MSI-X
[   35.651944] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  122.878599] Modules linked in: dm_crypt binfmt_misc ppdev lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 joydev snd_pcm ecb iwl3945 dell_wmi iwlcore dell_laptop uvcvideo sdhci_pci videodev sdhci snd_seq_dummy snd_seq_oss mac80211 iptable_filter v4l1_compat dcdbas snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore led_class psmouse snd_page_alloc nvidia(P) ip_tables serio_raw cfg80211 x_tables squashfs aufs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor video output ohci1394 ieee1394 tg3 usb_storage intel_agp agpgart
[  122.879682] Modules linked in: dm_crypt binfmt_misc ppdev lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 joydev snd_pcm ecb iwl3945 dell_wmi iwlcore dell_laptop uvcvideo sdhci_pci videodev sdhci snd_seq_dummy snd_seq_oss mac80211 iptable_filter v4l1_compat dcdbas snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore led_class psmouse snd_page_alloc nvidia(P) ip_tables serio_raw cfg80211 x_tables squashfs aufs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor video output ohci1394 ieee1394 tg3 usb_storage intel_agp agpgart
[  123.805895] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[  123.837475] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[  123.906493] Registered led device: iwl-phy0::radio
[  123.906588] Registered led device: iwl-phy0::assoc
[  123.906639] Registered led device: iwl-phy0::RX
[  123.906681] Registered led device: iwl-phy0::TX
[  145.157268] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  158.459151] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  171.777850] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  182.842529] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  210.096094] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  223.414431] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  242.868937] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  256.174743] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  267.433413] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  280.740850] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  294.046948] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  312.877519] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  326.178188] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  340.100704] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  353.318275] iwl3945 0000:0c:00.0: Failed to get channel info for channel 1 [1]
[  360.084643] iwl3945 0000:0c:00.0: Failed to get channel info for channel 48 [0]
[  366.661532] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  379.973753] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  386.222258] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  392.949377] iwl3945 0000:0c:00.0: Failed to get channel info for channel 48 [0]
[  420.393780] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  433.705447] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  447.017727] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  489.224998] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  495.656731] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  502.312665] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
[  509.073907] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[  515.650016] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]

---

### Post by mark bower on 2010-03-02
Assuming you are trying to connect to a router, have you left clicked the Network Manager on the upper rt of your screen?  It shows an antenna and bars.  If not, left click it, look for the SSID (name of your router), click on it, and you should connect if no security codes in play.

mark

---

### Post by chili555 on 2010-03-02
Please do:```
sudo rmmod dell-laptop
```Does the behavior improve? If not, please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Now is it working as expected?

Based on my Googling, one person reported the same symptom:> [ 509.073907] iwl3945 0000:0c:00.0: Failed to get channel info for channel 6 [1]
[ 515.650016] iwl3945 0000:0c:00.0: Failed to get channel info for channel 36 [0]
The fix was to replace a defective router. Does yours work with other computers? Is there any improvement if you unplug the router, wait a few moments and plug it back in?

---

### Post by anandhiroji on 2010-03-04
Sorry guys I am late in replying

I have no access to my router I uses WiFi at university and at my apartment. But I am sure that there is no problem with router as many people are using it for long time and I am also connecting to it with Vista...

I can see all networks available with there strengths as a bars....

Mean while I tried to update to Ubunto 10.04 from upload manager but my USB got full and couldn't update it successfully so again I reinstalled Ubuntu 9.10 

I tried to run code given by chili 

sudo rmmod dell-laptop


and new information was displayed as

ubuntu@ubuntu:~$ sudo rmmod dell-laptop
ubuntu@ubuntu:~$ dmesg | grep iwl
[   37.159755] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   37.159758] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   37.159890] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.159906] iwl3945 0000:0c:00.0: setting latency timer to 64
[   37.239935] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   37.239939] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   37.240138] iwl3945 0000:0c:00.0: irq 31 for MSI/MSI-X
[   37.266206] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  157.797654] Modules linked in: dm_crypt binfmt_misc ppdev lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep joydev snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq arc4 snd_timer ecb snd_seq_device iptable_filter uvcvideo iwl3945 dell_wmi snd videodev ip_tables sdhci_pci psmouse iwlcore soundcore v4l1_compat sdhci ricoh_mmc x_tables dell_laptop serio_raw mac80211 snd_page_alloc nvidia(P) led_class dcdbas cfg80211 squashfs aufs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor usb_storage ohci1394 ieee1394 tg3 video output intel_agp agpgart
[  157.798762] Modules linked in: dm_crypt binfmt_misc ppdev lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep joydev snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq arc4 snd_timer ecb snd_seq_device iptable_filter uvcvideo iwl3945 dell_wmi snd videodev ip_tables sdhci_pci psmouse iwlcore soundcore v4l1_compat sdhci ricoh_mmc x_tables dell_laptop serio_raw mac80211 snd_page_alloc nvidia(P) led_class dcdbas cfg80211 squashfs aufs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor usb_storage ohci1394 ieee1394 tg3 video output intel_agp agpgart
[  157.818474] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[  157.844734] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[  157.914370] Registered led device: iwl-phy0::radio
[  157.914420] Registered led device: iwl-phy0::assoc
[  157.914463] Registered led device: iwl-phy0::RX
[  157.914515] Registered led device: iwl-phy0::TX



then I tried to connect but still it is not connecting It keep asking for Pass key..

what should i do next?

Thanks a lot

---

### Post by chili555 on 2010-03-04
Please let us see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by anandhiroji on 2010-03-05
Now it displayed two WIFi networks in my appartment one is Aliant and second Aliant1.

Following information was displayed 

ubuntu@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:22:3B:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key :on
                    ESSID:"aliant"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d2da3004c1
                    Extra: Last beacon: 1584ms ago
                    IE: Unknown: 0006616C69616E74
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:13:A3:0A:CC:71
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key :on
                    ESSID:"aliant1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e01f6128
                    Extra: Last beacon: 1584ms ago
                    IE: Unknown: 0007616C69616E7431
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C

ubuntu@ubuntu:~$ 

Thank you

---

### Post by seenthelite on 2010-03-06
I have the same wireless card 3945ABG and I find that Network Manager the default in Ubuntu does not work. So what works for me is use Synaptic Package Manager and install wicd then reboot. (When you do this Network Manager will be removed and is difficult to reinstall).

---

### Post by chili555 on 2010-03-06
> It keep asking for Pass key..A WEP key or a WPA password? Network Manager doesn't like WEP password, but loves WEP 40/128-bit HEX key.

---

### Post by fmolino on 2010-10-24
Hello everybody



I   have the same problem (no wifi) under ubuntu 10.10 on a dell xps 1330

I have tried the suggestions of chili555 unsucessfuly

Any idea? 

Francis

---

### Post by fmolino on 2010-10-24
Precision

sudo iwlist wlan0 scan

get the following answer

Interface doesn't support scanning : Network is down

(At the same time, using wifi on my AESUS eepc under ubuntu 9.04  works perfectely fine in the same room!)

---

### Post by chili555 on 2010-10-24
Please let us see:```
sudo rmmod -f dell-laptop
rfkill list all
dmesg | grep iwl
```Thanks.

---

