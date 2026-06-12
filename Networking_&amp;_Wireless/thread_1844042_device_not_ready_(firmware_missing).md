---
title: "device not ready (firmware missing)"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by FreakOfNature on 2011-09-14
[LEFT][SIZE=2]I just recently bought a usb wireless adapter advertized to work with linux. The [/SIZE][SIZE=2]Asus USB-N13. When I plug it in it says "device not ready (firmware missing)" In the disc that comes with it is a folder that says linux drivers, but there isn't any kind if installer I can find, just a bunch of files. I'm a brand new user of ubuntu, what do I do?

edit: Also, it works just fine with a wired connection.
[/SIZE] [/LEFT]

---

### Post by FreakOfNature on 2011-09-17
bump (hopefully they are allowed)

---

### Post by praseodym on 2011-09-17
Please show the terminal outputs of:

```
lsusb
lsmod
iwconfig
```

---

### Post by varunendra on 2011-09-17
> **praseodym said:**
> Please show the terminal outputs of:

```
lsusb
lsmod
iwconfig
```
this^
Plus, the list of files in the "linux drivers" folder. Usually it is a three step process to install such drivers, which goes like - ./configure > make > make install.

---

### Post by FreakOfNature on 2012-02-13
Sorry I took so long! Here's what it gave me.
[FONT=Liberation Serif, Times New Roman, serif][SIZE=2]lsusb:[/SIZE][/FONT]
```
 
[FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 003 Device 005: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 003 Device 004: ID 047d:102d Kensington Pilot Optical[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 002 Device 002: ID 03f0:1604 Hewlett-Packard DeskJet 940c[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
```
  
[FONT=Liberation Serif, Times New Roman, serif][SIZE=2]lsmod:[/SIZE][/FONT]
```
 
[FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Module                  Size  Used by[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]rt2870sta             410104  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]arc4                   12473  2 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_intel8x0           33213  2 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_ac97_codec        105614  1 snd_intel8x0[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]ac97_bus               12642  1 snd_ac97_codec[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]rt2800usb              17907  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]rt2800lib              43824  1 rt2800usb[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]crc_ccitt              12595  2 rt2870sta,rt2800lib[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]rt2x00usb              19693  1 rt2800usb[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]i915                  451033  2 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_seq_midi           13132  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_rawmidi            25269  1 snd_seq_midi[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_seq_midi_event     14475  1 snd_seq_midi[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]binfmt_misc            13213  1 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_timer              28659  2 snd_pcm,snd_seq[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]ppdev                  12849  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]drm_kms_helper         40745  1 i915[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]cfg80211              156212  2 rt2x00lib,mac80211[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]dcdbas                 14054  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]drm                   184164  2 i915,drm_kms_helper[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]usbhid                 41704  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]hid                    77084  1 usbhid[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]usblp                  17827  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]soundcore              12600  1 snd[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]parport_pc             32111  1 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]i2c_algo_bit           13184  1 i915[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]snd_page_alloc         14073  2 snd_intel8x0,snd_pcm[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]shpchp                 32345  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]video                  18951  1 i915[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]lp                     13349  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]parport                36746  3 ppdev,parport_pc,lp[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]b44                    35301  0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]ssb                    45942  1 b44[/SIZE][/FONT]
```
    [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]iwconfig:[/SIZE][/FONT]
```
 
[FONT=Liberation Serif, Times New Roman, serif][SIZE=2]lo        no wireless extensions.[/SIZE][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]eth0      no wireless extensions.[/SIZE][/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]wlan0     IEEE 802.11bgn  ESSID:off/any  [/SIZE][/FONT] 
           [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/SIZE][/FONT] 
           [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Retry  long limit:7   RTS thr:off   Fragment thr:off[/SIZE][/FONT]
           [FONT=Liberation Serif, Times New Roman, serif][SIZE=2]Power Management:on[/SIZE][/FONT]
```

---

### Post by praseodym on 2012-02-13
There are two drivers loaded:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rt2870sta rt2800usb
sudo modprobe -v rt2870sta
```
Replug the stick.

---

### Post by FreakOfNature on 2012-02-16
Sorry, I don't know exactly what you mean for me to do. I put in that code right? By replug the stick, do you mean it should be out for that process or do I literally take it out and replug it in when it finishes?

---

### Post by varunendra on 2012-02-16
> **FreakOfNature said:**
> Sorry, I don't know exactly what you mean for me to do. I put in that code right? By replug the stick, do you mean it should be out for that process or do I literally take it out and replug it in when it finishes?
Just run (copy-paste to avoid errors) those commands in terminal, then pull out the USB stick > wait a few seconds/min. > replug it to get detected.

It actually doesn't matter whether the stick is plugged in or not while running those commands. What the commands will do is to remove one of the drivers and prevent it from loading again when you plug-in the stick next time. This would allow the correct driver to get loaded properly and avoid conflicts with the other one.

I'd leave it to *praseodym* now since he is the expert. I'd rather sit aside and just watch it getting solved :).

---

