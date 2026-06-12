---
title: "wireless not working even with drivers"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by murderd2death on 2011-09-08
(i am working with a broken arm, so please excuse any grammatical errors on my part)

i have a lenovo b570 laptop, dual booting windows 7 and ubuntu 11.04. Windows 7 is 64 bit, and runs off of 4 gbs of ram. for some reason i could only install ubuntu in 32 bit as a partition. i have run a 64 bit version inside windows without installation, but got the same issue. When ubuntu is running, regardless of whether wireless is enabled or not, it does not notice any networks. it must be plugged into a network to get any internet access. win.dows runs on wireless fine i have plugged into a network and run updates for ubuntu, and i got one for "additional drivers"

> 
broadcam STA wireless driver
tested by the ubuntu developers
liscense: proprietary

[LEFT]This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.[/LEFT]
it reads that the driver is activated and currently in use, but i still cannot connect to the internet with a wireless connection. 

please help. many regards.

---

### Post by praseodym on 2011-09-08
Hi,

please show:

```
lspci -nnk | grep -iA2 net
rfkill list
lsmod
dmesg | egrep 'b43|wl'
iwconfig
sudo iwlist scan
```
to get more infos.

---

### Post by murderd2death on 2011-09-08
> lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
wintermute@wintermute-Lenovo-B570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
wintermute@wintermute-Lenovo-B570:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451033  3 
acer_wmi               23153  0 
uvcvideo               66851  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17203  0 
videodev               75143  1 uvcvideo
wl                   2642531  0 
ideapad_laptop         13262  0 
snd                    55295  14  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  4 i915,drm_kms_helper
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
ahci                   21591  1 
libahci                25548  1 ahci
wintermute@wintermute-Lenovo-B570:~$ dmesg | egrep 'b43|wl'
[   18.053382] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.107793] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.107802] wl 0000:02:00.0: setting latency timer to 64
wintermute@wintermute-Lenovo-B570:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sudo iwlist scan
 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

  as an addendum to this information; i am not running off of my  home network at the moment, and i have just been informed that the  wireless network here has mysteriously been cut literally 3 or 4 minutes  ago.

---

### Post by murderd2death on 2011-09-08
sorry, did a search and  didnt see the sticky thread. ill take this issue there

---

### Post by wildmanne39 on 2011-09-08
Hi, why? you are already here.

You need a wired connection and then click on additional drivers and install the sta driver for your card then unplug your wired connection  and restart your computer.

It is possible to get it from the livecd also if you need too.

Also you need to do this to remove your soft block
```
rmmod -f acer-wmi
```
but this is good for only one boot so do it after you install your driver and reboot and if it works we need to make it persistent.

If you need more help post back here.
Thank you

---

### Post by praseodym on 2011-09-08
Try

```
sudo rfkill unblock all
sudo service network-manager restart
```

and check

```
rfkill list
```

---

### Post by murderd2death on 2011-09-08
> **praseodym said:**
> Try

```
sudo rfkill unblock all
sudo service network-manager restart
```and check

```
rfkill list
```
this is what i get after i put those in

```
wintermute@wintermute-Lenovo-B570:~$ sudo rfkill unblock all
wintermute@wintermute-Lenovo-B570:~$ sudo service network-manager restart
network-manager start/running, process 1786
wintermute@wintermute-Lenovo-B570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

also, wireless still wont work, should i restart computer?

---

### Post by praseodym on 2011-09-08
Unload the module **acer_wmi**:

```
sudo modprobe -rf acer_wmi
sudo rfkill unblock all
```
Check:

```
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by murderd2death on 2011-09-08
> **wildmanne39 said:**
> Hi, why? you are already here.

You need a wired connection and then click on additional drivers and install the sta driver for your card then unplug your wired connection  and restart your computer.

It is possible to get it from the livecd also if you need too.

Also you need to do this to remove your soft block
```
rmmod -f acer-wmi
```but this is good for only one boot so do it after you install your driver

```
wintermute@wintermute-Lenovo-B570:~$ rmmod -f acer-wmi
 ERROR: Removing 'acer_wmi': Operation not permitted
 
```

anything i can do from here?

>  and reboot and if it works we need to make it persistent.

If you need more help post back here.
Thank you

by persistent do you mean that im going to have to remove the softblock everytime i boot up?

---

### Post by wildmanne39 on 2011-09-08
Hi, sorry it should have been
```
sudo rmmod -f acer-wmi
```
Thank you

---

### Post by murderd2death on 2011-09-08
> **wildmanne39 said:**
> Hi, sorry it should have been
```
sudo rmmod -f acer-wmi
```Thank you
  k, when i put that n and unblock everything after i put that code in i still get no connection. and after the restart it reappears. is it essential that the wire be unplugged at the restart.

> **praseodym said:**
> Unload the module acer_wmi:

```
sudo modprobe -rf acer_wmi
sudo rfkill unblock all
```Check:


alright, so as an update i've gotten b43-fwcutter firmware-b43-installer up and going from this pages help, but now everytime i put in the last line of code to unblock all, the terminal freezes the OS. before it wasn't doing that. if i put in
```

iwconfig
rfkill list
sudo iwlist scan
```

immediately after 

```
sudo modprobe -rf acer_wmi
```

this is what i get:
```

wintermute@wintermute-Lenovo-B570:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wintermute@wintermute-Lenovo-B570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
wintermute@wintermute-Lenovo-B570:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by praseodym on 2011-09-08
What about the keys:

Fn + F5

?

---

### Post by wildmanne39 on 2011-09-08
Hi, you said > i've gotten b43-fwcutter firmware-b43-installer up and going from this pages help, but now everytime i put in the last line of code to unblock all, the terminal freezes the OS. before it wasn't doing that. if i put in
but the driver you need is the sta driver.
Thank you

---

### Post by murderd2death on 2011-09-08
> **wildmanne39 said:**
> Hi, you said 
but the driver you need is the sta driver.
Thank you

the STA driver is already installed and is actvated. from what i've read  what that is somewhat of a patch for the bcm43 driver.

---

### Post by wildmanne39 on 2011-09-08
Hi, no you can not have both it will create a conflict.
Open synaptic and remove the  b43-fwcutter firmware-b43-installer, then restart your system and see if it works if not we may have a blacklist issue.

If it does not work post the results of:
```
rfkill list
```
Thank you

---

### Post by wildmanne39 on 2011-09-08
Hi, these are the packages you need, named dkms, patch, fakeroot, and bcmwl-kernel-source. Then activate the driver.
Thank you

---

### Post by tom.tom_j on 2011-09-08
Hi murderd2death,

                          There seems to be some problem with the Kernel Update of Ubuntu 11.04 with respect to this Broadcom wireless driver :(. Just uninstall whatever extra drivers you have installed such as b43 and others. Now Deactivate the Broadcom STA wireless driver from the Additional Drivers menu. Restart your system. 

:guitar:Wifi will be working without any issues :)


Regards

---

### Post by bkratz on 2011-09-08
Here is a thread where Dr. Chili555 found several different methods of achieving connection with this device. Natively it should work with the brcm80211 driver which is probably interfering with all the other drivers being tried. Anyway, here is an interesting thread.

[http://ubuntuforums.org/showthread.php?t=1783272](http://ubuntuforums.org/showthread.php?t=1783272)

---

### Post by murderd2death on 2011-09-08
> **wildmanne39 said:**
> Hi, these are the packages you need, named dkms, patch, fakeroot, and bcmwl-kernel-source. Then activate the driver.
Thank you

alright, i'm typing this over a wireless connection right now, thanks to your instructions:D  i did have to reinput the code

```
sudo rmmod -f acer-wmi
```

is there any way i can cut acer-wmi permanently without to retype that in everytime?

if not, im perfectly content doing it. im super excited that this is actually working, this has been a problem for me for a month or so. thank you so much! :eek:

---

### Post by praseodym on 2011-09-08
Yes, blacklist the module permanently:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by wildmanne39 on 2011-09-08
Hi, I see you already have the answer, I am glad you got it working.

If I have been helpful would you consider click on my ubuntu membership application in my signature and showing your support for me.

If you need any more help please come back and would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by murderd2death on 2011-09-08
> **praseodym said:**
> Yes, blacklist the module permanently:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

this worked perfectly

---

### Post by murderd2death on 2011-09-08
> **wildmanne39 said:**
> Hi, I see you already have the answer, I am glad you got it working.

If I have been helpful would you consider click on my ubuntu membership application in my signature and showing your support for me.

If you need any more help please come back and would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

yes, i will get to writing your recommend tomorrow afternoon, youve been a great help:)

---

