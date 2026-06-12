---
title: "wireless issues, problems with ndiswrapper"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by tahafisaka6 on 2012-01-18
I have a gateway lt1004u netbook and just installed 11.10.  So far everything seems to be working ok except for my wireless adapter.  I have the link to enable wireless but when I do this it does not get checked.  I tried searching for support and think I need to install the ndiswrapper.  I first tried in terminal and get a message to insert the installed disk into /media/cd-rom.  I do not have a cd-rom on this machine.  I installed from a usb stick.  I then opened the ubunto software center and found the ndiswrapper install in there and tried that way and also received a message pop up requesting to insert the install disk into the cd-rom.

Also I have seen a few things stating to go to systems/administration and I have yet to figure out where this is.

---

### Post by praseodym on 2012-01-18
Hi,

please open a terminal with CTRL+ALT+T and enter the following commands one by one (you may use c/p):

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by tahafisaka6 on 2012-01-18
Thank you for the quick response.

I tried the steps but does not seem to have changed anything,  here are the output results.:


justine@Minie:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k
justine@Minie:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
justine@Minie:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
arc4                   12473  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
ath5k                 145100  0 
snd_hda_codec_realtek   254125  1 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                73673  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
cfg80211              172392  3 ath5k,ath,mac80211
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
i915                  505159  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
wmi                    18744  1 acer_wmi
drm                   192194  4 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
r8169                  43104  0 
justine@Minie:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
justine@Minie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
justine@Minie:~$ sudo iwlist scan
[sudo] password for justine: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by wildmanne39 on 2012-01-19
Hi, I thought I would help out since praseodym is off line.

Please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
it also shows that the hardware switch is off, please check the switch, if it does not have one then a key or combination of keys will turn it on.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
Thanks for the response.  I was wondering about that already myself.  There is a switch at the front which turns it off and on usually, but the light is not doing anything at all when sliding the switch.  Here is the resluts from the last cmd:

justine@Minie:~$ echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for justine: 
blacklist acer_wmi
justine@Minie:~$

---

### Post by wildmanne39 on 2012-01-19
Hi, run ```
rfkill list all
```again and we will see if the blocks are gone, and if you have not done so reboot with wired connection unplugged.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
the switch does toggle on and off within windows xp.

---

### Post by wildmanne39 on 2012-01-19
Hi, that is good make sure it is on before you switch to ubuntu.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
justine@Minie:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
justine@Minie:~$

---

### Post by wildmanne39 on 2012-01-19
Hi, show the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by tahafisaka6 on 2012-01-19
do you know why the ndiswrapper will not me install?  and/or what am I supposed to do when it is asking me to insert the install disk for 11.10 i386?

---

### Post by wildmanne39 on 2012-01-19
Hi, you do not need ndiswrapper your driver is all ready installed.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
justine@Minie:~$ cat /etc/modprobe.d/blacklist.conf
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
blacklist acer_wmi
justine@Minie:~$ 



also, the switch is on in windows xp, i shut down windows xp then boot into ubuntu

---

### Post by wildmanne39 on 2012-01-19
Hi, I have to go off line for tonight, I well check on you tomorrow.

---

### Post by tahafisaka6 on 2012-01-19
ok,  thank you very much for your time, it is greatly appreciated.

---

### Post by wildmanne39 on 2012-01-19
Hi, try this:
```
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k
```
make sure your wired connection is disconnected and do not restart.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
that fixed the problem.  so should this fix it from now on, or is there something that I need to remember in case it starts acting up again.?

---

### Post by wildmanne39 on 2012-01-19
Hi, if you have any more problems with it we will write a short script for those commands to be ran at boot.
Thanks

---

### Post by tahafisaka6 on 2012-01-19
ok, so I rebooted, and everything came back up working, i plugged in ethernet, turned off wireless, turned back on everything seems to be working perfect now.   Thank you very very much for your support.

---

### Post by wildmanne39 on 2012-01-19
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

