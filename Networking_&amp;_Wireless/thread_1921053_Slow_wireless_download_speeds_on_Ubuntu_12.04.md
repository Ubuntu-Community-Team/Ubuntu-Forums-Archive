---
title: "Slow wireless download speeds on Ubuntu 12.04"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by Our on 2012-02-06
So I made the move from Windows 7 to Ubuntu 12.04 today but the Internet speed is nearly a quarter of what I was previously getting on Windows. All the Hardware is still the same as before. I am quite baffled about why it is like this.

I have tried Googling my issue but nothing seemed to work.  Below is my current INTERNET speed.

[[IMG]http://www.speedtest.net/result/1754827630.png[/IMG]]("http://www.speedtest.net")

Before the switch over I had 28-34Mb/s download... My upload was the same as it is now. 

Here is some basic information... if you need anything else please let me know.

iwconfig

```
malvora@Moda:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:114  Invalid misc:1659   Missed beacon:0

eth0      no wireless extensions.
```lspci -nnk | grep -iA2 net

```
malvora@Moda:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7672]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7672]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: ASUSTeK Computer Inc. Device [1043:130f]
    Kernel driver in use: rt2800pci
```lsmod

```
malvora@Moda:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
nls_iso8859_1          12713  1 
isofs                  40257  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  1 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
uas                    18027  0 
usb_storage            49199  1 
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_realtek   223759  1 
arc4                   12529  2 
nouveau               774452  3 
rt2800pci              18715  0 
snd_hda_intel          33773  5 
rt2800lib              58925  1 rt2800pci
ttm                    76949  1 nouveau
drm_kms_helper         42489  1 nouveau
drm                   241834  5 nouveau,ttm,drm_kms_helper
snd_hda_codec         127723  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              51205  3 rt2800pci,rt2800lib,rt2x00pci
i2c_algo_bit           13423  1 nouveau
mac80211              502720  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
mei                    41616  0 
psmouse                87603  0 
joydev                 17693  0 
eeprom_93cx6           12725  1 rt2800pci
mxm_wmi                12979  1 nouveau
serio_raw              13211  0 
snd_hwdep              13668  1 snd_hda_codec
wmi                    19256  1 mxm_wmi
video                  19411  1 nouveau
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
lp                     17799  0 
shpchp                 37277  0 
parport                46562  3 parport_pc,ppdev,lp
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62098  0 
```If I need to enter more information please tell me...


Thanks,
Ouroboros

---

### Post by sanderj on 2012-02-06
Why do you use 12.04, which is still in Alpha state?

When you use 11.10, what speed do you get? You could just use a live-boot to check it out.

---

### Post by Our on 2012-02-06
The same exact problem was had on 11.10.

---

### Post by Our on 2012-02-06
More info that might help...

hwinfo --wlan

```
malvora@Moda:~$ hwinfo --wlan
> hal.1: read hal dataprocess 2346: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: PCI 500.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: xxxxxxxxxxxxxx
  Parent ID: xxxxxxxxxxxxxx
  SysFS ID: /devices/pci0000:00/0000:00:1c.3/0000:05:00.0
  SysFS BusID: 0000:05:00.0
  Hardware Class: network
  Model: "RaLink RT2860"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x0781 "RT2860"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x130f 
  Driver: "rt2800pci"
  Driver Modules: "rt2800pci"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xfa400000-0xfa40ffff (rw,non-prefetchable)
  IRQ: 19 (no events)
  HW Address: e0:69:95:22:f9:32
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00"
  Driver Info #0:
    Driver Status: rt2800pci is active
    Driver Activation Cmd: "modprobe rt2800pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)

```


"RaLink RT2860" that is what hwinfo says the wifi card  is. And the drivers are rt2800. Could that be the problem and if so how can I fix it?

---

### Post by sanderj on 2012-02-06
I would google "RaLink RT2860 ubuntu 11.10"

---

### Post by Our on 2012-02-06
>_< as if i did not try that...

---

### Post by Our on 2012-02-09
I do not know how or why but my connection magically went back to the way it used to be. I was just playing Minecraft then BAM! 30mbps! Thank you Gods of Ubuntu!

---

### Post by yuki2012 on 2012-02-10
Yes,it's really really slow:mad:

---

### Post by Our on 2012-02-11
And now it is back to being slow... GAH!

---

### Post by Our on 2012-02-16
Bump!

---

### Post by TheMidnightWings on 2012-03-04
I am/was having the same problem with the Alpha, and now with the Beta 1 release. I think it's a problem with the new Kernel being still unstable itself, making the Internet slow. I hope they resolve it considering I spend most of my time on the Internet and writing on Linux, with slow Internet it defeats the point. Anyway. Two things I did sped it up BIG TIME. First, go to this page and set-up OpenDNS for Ubuntu [https://store.opendns.com/setup/operatingsystem/ubuntu]("https://store.opendns.com/setup/operatingsystem/ubuntu") 
The tutorial is a bit dated, but it still applies since the Interface of the network manager hasn't changed. 
Next go into the network manager again and set it to ignore IVP6, this helped a lot as well. Hope that helps you speed it up somewhat! And I really hope the issue is resolved soon...

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by neumann7 on 2012-06-03
In case it helps others,

I recently upgraded to 12.04 from 11.10 on a Dell Vostro 3350 with Intel Centrino Wireless-N 1030.  I experienced similar buggy wireless with limited signal strength.  As I had done with 11.10, I set power management to "off." This helped, as it had in 11.10, but wireless was still buggy and exhibited much worse performance than other older machines that only had wireless g cards.  

I did some digging and found this forum, but was disappointed to find that the commands

```
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
```had no effect on my machine.  

The problem was that I didn't realize that the kernel module on my machine is now **iwlwifi** and not **iwlagn**. I ran the same commands as above with **iwlagn** replaced by **iwlwifi**, and it disabled wireless n as expected and the wireless performance improved dramatically.  So my advice is to check the kernel module name, and if it's **iwlwifi**, then run

```
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

---

### Post by SisterNotes on 2012-06-19
Thank you!! The steps in comment #12 (after correcting the file name for "wifi" saved my new 12.04 installation. Hurray!

Thank you!

---

### Post by sky80 on 2012-08-23
Thank you guys so much!! I was almost about to give up on ubuntu and go back to MS.. 

cheers fellas!

---

