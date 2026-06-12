---
title: "TP LINK TL-WN727N question"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by feardotcom on 2013-07-19
So the usb adapter works out of the box, for the most part. It says the reception is horrible, 1 bar. It seems to drop connection randomly. ( i was pulling fills from my nas and it would constantly drop and i would have to go back and pull those files again.)

So my question is if i went through the hassle of installing the RT5372 drivers would it even fix the issue and would i have to recompile the drivers after every kernel update?

---

### Post by praseodym on 2013-07-19
Please check:
```
uname -a
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by feardotcom on 2013-07-19
```
chris@chris-pc:~$ uname -a
Linux chris-pc 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
chris@chris-pc:~$ lsusb
Bus 002 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 003 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chris@chris-pc:~$ lsmod
Module                  Size  Used by
usb_storage            57204  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
arc4                   12615  2 
nvidia               9410995  48 
rt2800usb              26854  0 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
snd_hda_codec_hdmi     36913  4 
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
sp5100_tco             13735  0 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  7 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
snd                    68876  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
wmi                    19070  0 
i2c_piix4              13266  0 
edac_core              62003  0 
microcode              22881  0 
serio_raw              13215  0 
edac_mce_amd           23114  0 
k10temp                13126  0 
mac_hid                13205  0 
ppdev                  17073  0 
parport_pc             28152  1 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
r8169                  67446  0 
crc_itu_t              12707  1 firewire_core
pata_acpi              13038  0 
ahci                   25731  3 
libahci                31364  1 ahci
pata_atiixp            13242  0 
chris@chris-pc:~$ iwconfig
tun0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NAS1_2GEXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 2C:B0:5D:3A:2D:09   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:818  Invalid misc:234   Missed beacon:0

chris@chris-pc:~$ sudo iwlist scan
[sudo] password for chris: 
tun0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

```

It looks like it already has the 5370 driver?

---

### Post by praseodym on 2013-07-20
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```
You can try to install the driver with dkms according to this:
[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#Installation-ueber-DKMS](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#Installation-ueber-DKMS)

---

### Post by feardotcom on 2013-08-02
That didn't really seem to help. Now i'm having the problem of it randomly disconnecting and then it wont see my wifi signal. I have to unplug the adapter and plug it back in.

---

### Post by praseodym on 2013-08-03
Please show:
```

iwlist chan
sudo iwlist scan
route -n
ifconfig -a
cat /etc/resolv.conf
```
Try pure WPA2-AES encryption, a fixed channel, not to hide the network and to change the bandwidth to 20 MHz instead of 20/40 MHz

---

### Post by feardotcom on 2013-08-03
i did not see an option for wpa2-aes. I didn't see an option to change the bandwidth. But i have my router set to 20, not 40. 

Could my VPN be a problem? Sometimes when i disconnect the vpn the adapter will connect. Coincidence maybe? I have it set up the way they said to. It's by Private Internet Access.

---

### Post by praseodym on 2013-08-04
Did you tick "connect automatically" in your VPN settings?

---

### Post by feardotcom on 2013-08-04
Yes, i wanted to make sure i didn't forget to connect to my vpn.

---

### Post by praseodym on 2013-08-08
Try to compile this driver, Variant A:

[http://forum.ubuntuusers.de/topic/c300ru-usb-rt2860-kein-ieee-802-11n/#post-2831641](http://forum.ubuntuusers.de/topic/c300ru-usb-rt2860-kein-ieee-802-11n/#post-2831641)

---

