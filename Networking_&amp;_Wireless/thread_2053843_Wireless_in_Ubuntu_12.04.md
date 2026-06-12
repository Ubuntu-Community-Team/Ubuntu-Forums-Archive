---
title: "Wireless in Ubuntu 12.04"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by meetjsh on 2012-09-06
Hi Guys,
I am new to Ubuntu world. I have windows 7 and Ubuntu 12.04 installed in my Sony Vaio. 
My question is, how to connect it to wireless?

Before I have connect it via hotspot and dongle. Both time it did take much effort but it is now not showing any wireless device. I tried adding a new device. But in field where I need to give SSID, BSSID, MAC address so on, I get stuck.

Please help me.
Regards,
A

---

### Post by NikTh on 2012-09-06
Hello , 

please open a terminal (Ctrl+alt+t keys combination) and  copy-paste from here bellow commands , one line at time. 

```
lspci -nnk | grep -iA2 net
rfkill list all 
lsmod 
lsusb
iwconfig
``` 

Give the results back here , but put the results between ```
 brackets so can be readable. 

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by meetjsh on 2012-09-06
Thanks for prompt reply... These are the details which I got
 
```
[FONT=Liberation Serif]
sony@ubuntu:~$ lspci -nnk | grep -iA2 net 
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01) 
Subsystem: Foxconn International, Inc. Device [105b:e037] 
Kernel driver in use: ath9k 
-- 
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
Subsystem: Sony Corporation Device [104d:908b] 
Kernel driver in use: r8169 
sony@ubuntu:~$ ^C 
sony@ubuntu:~$ rfkill list all 
0: phy0: Wireless LAN 
Soft blocked: yes 
Hard blocked: yes 
1: hci0: Bluetooth 
Soft blocked: yes 
Hard blocked: no 
2: sony-wifi: Wireless LAN 
Soft blocked: yes 
Hard blocked: no 
3: sony-bluetooth: Bluetooth 
Soft blocked: yes 
Hard blocked: no 
sony@ubuntu:~$ lsmod 
Module Size Used by 
nls_iso8859_1 12713 1 
nls_cp437 16991 1 
vfat 17461 1 
fat 61282 1 vfat 
parport_pc 32688 0 
ppdev 17073 0 
rfcomm 46619 0 
bnep 18140 2 
lp 17759 0 
parport 46345 3 parport_pc,ppdev,lp 
joydev 17457 0 
coretemp 13400 0 
kvm 414070 0 
ghash_clmulni_intel 13180 0 
cryptd 20403 1 ghash_clmulni_intel 
nouveau 895650 2 
ttm 83595 1 nouveau 
drm_kms_helper 46784 1 nouveau 
drm 275528 4 nouveau,ttm,drm_kms_helper 
i2c_algo_bit 13413 1 nouveau 
mxm_wmi 12979 1 nouveau 
snd_hda_codec_hdmi 32007 1 
psmouse 86278 0 
microcode 22803 0 
uvcvideo 76749 0 
videobuf2_core 32851 1 uvcvideo 
sony_laptop 54039 0 
videodev 120309 2 uvcvideo,videobuf2_core 
videobuf2_vmalloc 12860 1 uvcvideo 
videobuf2_memops 13368 1 videobuf2_vmalloc 
serio_raw 13215 0 
lpc_ich 17061 0 
btusb 18334 0 
bluetooth 209199 12 rfcomm,bnep,btusb 
arc4 12529 2 
snd_hda_codec_conexant 57842 1 
snd_hda_intel 33491 5 
snd_hda_codec 134121 3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep 13602 1 snd_hda_codec 
snd_pcm 96580 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi 13324 0 
ath9k 131308 0 
snd_rawmidi 30512 1 snd_seq_midi 
mac80211 539908 1 ath9k 
snd_seq_midi_event 14899 1 snd_seq_midi 
ath9k_common 14055 1 ath9k 
snd_seq 61521 2 snd_seq_midi,snd_seq_midi_event 
ath9k_hw 395218 2 ath9k,ath9k_common 
ath 23827 3 ath9k,ath9k_common,ath9k_hw 
snd_timer 29425 2 snd_pcm,snd_seq 
snd_seq_device 14497 3 snd_seq_midi,snd_rawmidi,snd_seq 
rts_pstor 433804 0 
cfg80211 206472 3 ath9k,mac80211,ath 
snd 78734 20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
video 19335 1 nouveau 
wmi 19070 2 nouveau,mxm_wmi 
mei 40704 0 
mac_hid 13205 0 
soundcore 15047 1 snd 
snd_page_alloc 18484 2 snd_hda_intel,snd_pcm 
uas 17890 0 
usb_storage 48838 1 
r8169 61681 0 
sony@ubuntu:~$ lsub 
No command 'lsub' found, did you mean: 
Command 'lsusb' from package 'usbutils' (main) 
Command 'qsub' from package 'slurm-llnl-torque' (universe) 
Command 'qsub' from package 'gridengine-client' (universe) 
Command 'qsub' from package 'torque-client-x11' (universe) 
Command 'qsub' from package 'torque-client' (universe) 
lsub: command not found 
sony@ubuntu:~$ iwconfig 
eth0 no wireless extensions. 
[/FONT][SIZE=3][/SIZE][FONT=Liberation Serif]lo no wireless extensions. 
[/FONT][SIZE=3][/SIZE][FONT=Liberation Serif]wlan0 IEEE 802.11bgn ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=off 
Retry long limit:7 RTS thr:off Fragment thr:off 
Power Management:on 
[/FONT]
```

---

### Post by FOBoi1122 on 2012-09-06
I'm still pretty new to linux myself but I would think that you could just use the network connection manager. Does it show up on the top right corner of your menu bar? I'm guessing you tried looking at that already. Usually the wifi card will probe for nearby networks so you don't have to figure out the MAC, ESSID, etc.

Maybe also try a 
```
ifconfig wlan0 up
```
to turn on the wifi adapter.

---

### Post by NikTh on 2012-09-06
> **meetjsh said:**
> Thanks for prompt reply... These are the details which I got
 
```
[FONT=Liberation Serif]
sony@ubuntu:~$ rfkill list all 
0: phy0: Wireless LAN 
Soft blocked: yes 
Hard blocked: yes 
1: hci0: Bluetooth 
Soft blocked: yes 
Hard blocked: no 
2: sony-wifi: Wireless LAN 
Soft blocked: yes 
Hard blocked: no 
3: sony-bluetooth: Bluetooth 
Soft blocked: yes 
Hard blocked: no 
[/FONT]
```

Ok , it seems something is blocked here .

Try this command from terminal and see if WiFi resurrected

```
sudo rfkill unblock all
``` 

Thanks

---

### Post by meetjsh on 2012-09-08
i did it..but still there is no way to connect..is there need for drivers.

---

### Post by meetjsh on 2012-09-08
i also used iwconfig
```
eth0 no wireless estentions
lo no wireless extensions
wlan0.  IEEE 802.11bgn ESSID:off/any 
```
pls write me if full code is required..sory im online frm phone

---

### Post by meetjsh on 2012-09-08
i did ifconfig wlan0 up 
it shows 
```
SIOCSIFFLAGS 
```

---

### Post by NikTh on 2012-09-08
Hi , 
If you run ```
rkill list all
``` and see ***hard-blocked*** , then search for a switch . Keys combo switch (likr Fn+ ??) or search even for a switch button that enables the WiFi. 

Thanks

---

### Post by meetjsh on 2012-09-09
sory. but i did nt get it

---

### Post by NikTh on 2012-09-09
> **meetjsh said:**
> sory. but i did nt get it

Hi , 

from above results I can see that you have hard-blocked wifi. 

> ```

[FONT=Liberation Serif]sony@ubuntu:~$ rfkill list all  0: phy0: Wireless LAN  
Soft blocked: yes  [B]
Hard blocked: yes [/B] 
1: hci0: Bluetooth  
Soft blocked: yes  
Hard blocked: no  
2: sony-wifi: Wireless LAN  
Soft blocked: yes  
Hard blocked: no  
3: sony-bluetooth: Bluetooth  
Soft blocked: yes  
Hard blocked: no  [/FONT]
```[FONT=Liberation Serif]
[SIZE=3]
So I assume that the switch ON/OFF will fix the problem. [/SIZE] [SIZE=3]
Laptops usually have a switch On/Off for the wireless device (power management reasons) so you can enable or disable wifi wherever you want.
Maybe this switch is Off ? 
Usually is a Combo of Fn + some F key . In my Laptop is Fn+F5 . 
We must check this first , before we continue with other solutions. 

Thanks
[/SIZE] [/FONT]

---

### Post by meetjsh on 2012-09-10
Thanks a lot NikTh, You are the big help during the process.

Finally It is working, I just used two commands after connecting from Ethernet 

```
 sudo apt-get update 
sudo apt-get upgrade

```
though hereafter it my ubuntu screen started fluctuating and uninstalled it and re-installed it completely.

thanks a lot once again

---

