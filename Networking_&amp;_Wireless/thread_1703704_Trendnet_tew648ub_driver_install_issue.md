---
title: "Trendnet tew648ub driver install issue"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by frenziedfemale on 2011-03-09
I am trying to get my wireless USB adapter to work. I have downloaded what I think is the correct driver RTL8712 and began the process of making and installing. I completed the **tar** command and then the **make** command and was happily moving on to the **sudo make install** portion ... I got the following error...

[B]Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.[/B]

I am lost now. If you can help, (hopefully with very good instructions that I may follow!;)), I would be so very happy!

I have the windows drivers available as well if that would be easier, but I have no clue how I would make that work with ubuntu.  

Using Ubuntu 10.10 Maverick Kernel 2.6.35-27-generic   if that helps.

---

### Post by chili555 on 2011-03-09
Please try:```
sudo su
make clean
make
make install
exit
```Note and post any errors.

Could we see:```
lsusb
```Maybe there is an easier way.

---

### Post by frenziedfemale on 2011-03-14
Sorry it took so long for me to get back here but I am now ready to tackle this.

lsusb gives the following results:

  	 	 	 	p { margin-bottom: 0.21cm; }  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter  
 Bus 002 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I am trying you suggested entries now and will post results in a few minutes!

---

### Post by frenziedfemale on 2011-03-14
No joy 

I can get the light on the usb adapter to flash, it recognizes wireless networks that are available, but will not connect. Repeatedly asks for the password. I can connect using my son's Belkin adapter. I guess maybe the Trendnet is just a no-go? I have searched and tried a few suggestions that are out there but still having the same results.

---

### Post by chili555 on 2011-03-14
Let's see if there are any informative kernel messages:```
lsmod
dmesg | grep -e 8712 -e 818
```Thanks.

---

### Post by frenziedfemale on 2011-03-14
ok ! I have no idea what any of this is but I'm guessing you do! 


 lsmod
Module                  Size  Used by
michael_mic             1744  0 
lib80211_crypt_tkip     7736  0 
wl                   1959533  0 
lib80211                5058  2 lib80211_crypt_tkip,wl
arc4                    1165  0 
rt73usb                22506  0 
crc_itu_t               1383  1 rt73usb
rt2x00usb               9779  1 rt73usb
rt2x00lib              27307  2 rt73usb,rt2x00usb
mac80211              231959  2 rt2x00usb,rt2x00lib
cfg80211              144694  2 rt2x00lib,mac80211
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
joydev                  8767  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
radeon                829255  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
r8192s_usb            287340  0 
drm_kms_helper         30200  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168060  5 radeon,ttm,drm_kms_helper
acer_wmi               13929  0 
uvcvideo               55847  0 
eeprom_93cx6            1345  1 r8192s_usb
led_class               2633  2 rt2x00lib,acer_wmi
videodev               43098  1 uvcvideo
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 radeon
video                  18712  0 
soundcore                880  1 snd
shpchp                 29886  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
k10temp                 2607  0 
i2c_piix4               8635  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
usb_storage            40204  0 
libahci                21728  1 ahci
pata_atiixp             3288  0 
atl1c                  29949  0 
myname@myname-Aspire:~$ dmesg | grep -e 8712 -e 818

 dmesg | grep -e 8712 -e 818
[    0.153017] hpet0: 3 comparators, 32-bit 14.318180 MHz counter

(missed that last part on my first try)

---

### Post by chili555 on 2011-03-14
Well, the module you tried to compile, 8712u is not loaded. However, you have a whole pile of other drivers!> smod
Module Size Used by
michael_mic 1744 0
lib80211_crypt_tkip 7736 0
[COLOR="Red"]wl[/COLOR] 1959533 0
lib80211 5058 2 lib80211_crypt_tkip,wl
arc4 1165 0
[COLOR="Red"]rt73usb[/COLOR] 22506 0
crc_itu_t 1383 1 rt73usb
rt2x00usb 9779 1 rt73usb
rt2x00lib 27307 2 rt73usb,rt2x00usb
mac80211 231959 2 rt2x00usb,rt2x00lib
cfg80211 144694 2 rt2x00lib,mac80211
--- snip ---
[COLOR="Red"]r8192s_usb[/COLOR] 287340 0
--- snip ---
eeprom_93cx6 1345 1 r8192s_usb
led_class 2633 2 rt2x00lib,acer_wmi
--- snip ---
atl1c 29949 0 wl is appropriate for a newer Broadcom card. Do you have one? rt73usb and dependencies might be for your Belkin.

There is often a problem with firmware for the r8192s_usb which is correct for your device. Please post:```
dmesg | grep 819
cat /etc/modules
```When trying to connect with wireless, any ethernet cables should be detached.

---

