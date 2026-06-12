---
title: "WiFi randomly disconnects"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by zxca on 2011-12-03
Hi,

My connection randomly disconnects and prompts me again to input the passphrase for the wifi, I'm typing the password correctly and slowly. It does not connect until I turn off and turn on the Wireless. I'm using WPA personal and my wireless usb is RTL 8187


lsmod
> lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_codec_hdmi     31426  1 
rtl8187                56323  0 
mac80211              393459  1 rtl8187
joydev                 17393  0 
cfg80211              172392  2 rtl8187,mac80211
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
eeprom_93cx6           12653  1 rtl8187
snd_hda_codec_realtek   254125  1 
dm_multipath           22771  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                925094  3 
k10temp                12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
floppy                 60310  0 
r8169                  43104  0 
pata_atiixp            12967  0 
ahci                   21634  6 
libahci                25727  1 ahci


---

### Post by zxca on 2011-12-06
bump! no solutions? I really want to get rid of windows and make ubuntu my default os. But this issues hinders it all

---

### Post by zxca on 2011-12-07
Hello? looks like my thread is just getting ignored. 

*update*

it seems like it is frequently dropping off the connection when I'm using Transmission bittorrent client, and seldomly if not.:confused::confused::confused::confused:

---

### Post by zxca on 2011-12-07
iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RPC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 80:1F:02:0A:28:62   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


iwlist chan
> lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)



sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 80:1F:02:0A:28:62
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"RPC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003e0b401f
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0003525043
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000101103B0001031047001063041253101920061228801F020A2862102100001023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F20400011011000F576972656C65737320526F75746572100800020086
                    IE: Unknown: DD0600E04C020160


rfkill list
> 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by zxca on 2011-12-07
Bump

---

### Post by zxca on 2011-12-09
bump

---

### Post by zxca on 2011-12-10
solved. thanks for nothing:D

---

### Post by oakdog8 on 2011-12-19
Any chance you can actually share how you solved it?

---

### Post by verymadpip on 2011-12-20
Yeah, I'd appreciate the solution as I've just begun to have a similar issue.
Internal realtek device shows up in lsusb as rtl8187, the drivers match but I mainly get no internet.

Please share......

---

### Post by cdotto on 2012-01-01
The same for me:

"...it seems like it is frequently dropping off the connection when I'm  using Transmission bittorrent client, and seldomly if not"

"Yeah, I'd appreciate the solution as I've just begun to have a similar issue."

Thanks!

---

### Post by zxca on 2012-01-09
[askubuntu.com/questions/86342/wifi-randomly-disconnects-drops-out-with-an-rtl-8187]("http://askubuntu.com/questions/86342/wifi-randomly-disconnects-drops-out-with-an-rtl-8187")


@all

I just removed gnome network manager and installed WICD

---

### Post by verymadpip on 2012-01-10
I'll give it a go & report back.

From what I can gather the RTL8187 driver appears to be notoriously unreliable in linux.  My solution was to purchase a USB wireless adaptor & use that instead.

One concern I have is that if WICD doesn't do the job I'll have to reinstall Network Manager.  I've recently had a nightmare of a job trying to get it to work on a minimal install.  In fact I ended up using WICD as NM was a total washout.  I never did find out what the problem was there.

---

### Post by verymadpip on 2012-01-10
I'm sorry to say that changing the network management tool didn't help.

As I say, it appears to be the drivers & not the network management tool that is the issue.
WICD still connects me when I use the USB wireless adaptor so everyhting essentially remains as it was.

zxca; thanks for trying :)

---

### Post by verymadpip on 2012-01-10
Actually messing about with this made things worse.  WICD was unable to detect any networks after a reboot with the USB adaptor plugged in.  I've gone back to network manager & all is well.

---

### Post by verymadpip on 2012-01-19
Okay, another sitrep:

NdisWrapper with Win98 driver has fixed this issue for me (up to now).
If my success becomes not such a success I'll post an update.

---

