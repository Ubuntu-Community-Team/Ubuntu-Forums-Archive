---
title: "Wireless worked on ubuntu 11.04(on 11.10??)"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by nyinyizaw on 2012-03-03
[SIZE=2]Wireless does not work on ubuntu 11.11[/SIZE] . [SIZE=2]it does not even show wireless device. 
        When I was using 11.04 . I configure blacklist.conf
        [/SIZE]```
 [SIZE=3]blacklist rt2800usb [/SIZE]
```[SIZE=2] (for better connection) and perfectly worked
        at 11.11 it doesn't work 
        if i remove [/SIZE]```
 [SIZE=3]blacklist rt2800usb [/SIZE]
``` [SIZE=2]it work with deadly slow connection[/SIZE]
[SIZE=2]
        
       [/SIZE]


 [SIZE=3]More information please ask me .  thanks for helping[/SIZE]

---

### Post by praseodym on 2012-03-03
More info please:

```
lsusb
lsmod
iwconfig
rfkill list
```
What kind of computer is that?

---

### Post by nyinyizaw on 2012-03-03
[SIZE=2]Thanks for helping me  guys
[SIZE=1]sorry I am late for reply 

laptop (Hp ProBook 4416s) I am using ralink wireless rt2800 for better connection ( ralink connection disappear ) Although laptop driver is OK I cant use cause poor connection
[/SIZE]
here it is 
      [/SIZE]```

nyinyi@nyinyi-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
         
```

```

nyinyi@nyinyi-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

```

nyinyi@nyinyi-PC:~$ rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

```

[LEFT]nyinyi@nyinyi-PC:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_analog    75090  1 
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
lib80211_crypt_tkip    17240  0 
fglrx                2595537  99 
wl                   2646601  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
k10temp                12990  0 
serio_raw              12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  0 
wmi                    18744  1 hp_wmi
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 

[/LEFT]

```

---

### Post by Bucky Ball on 2012-03-03
It's 11.10, not 11.11. Have you plugged in an ethernet cable (with the USB wireless dongle plugged in), gotten online, got updates, then checked 'Additional Drivers'??? Your card may be 'automagically' detected and configured without you need to check Additional Drivers in 11.10.

---

### Post by nyinyizaw on 2012-03-03
[SIZE=2]Inn! thanks guys    I was aware for my typing error(11.10) . but my computer cant go online with ubuntu . I can go only with window . 

And Ralink not appear in additional driver
                  

[/SIZE]

---

### Post by praseodym on 2012-03-03
Since 11.10 the module rt2870sta is no more valid, use the module rt2800usb instead. Check the "blacklists":

```
grep rt2 /etc/modprobe.d/*
```

---

### Post by Bucky Ball on 2012-03-03
Try here:

[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

And go to the section a little down the page headed 'rt2800usb driver' just under where it says, 'Thanks to vitoshka@'. See how you go.

You may need to try the udev method further down the page. Just go slow and follow the instructions (copy and paste to terminal best). Good luck. ;)

---

### Post by nyinyizaw on 2012-03-03
[SIZE=2]Yes , with rt2800usb ,
 it seems working but connection was too slow[/SIZE]
[SIZE=2]What else can I do [/SIZE]

---

### Post by nyinyizaw on 2012-03-05
[SIZE=2]               Finally I go back and use old kernel version (on 11.10). Thats much better:):):):P[/SIZE]

---

