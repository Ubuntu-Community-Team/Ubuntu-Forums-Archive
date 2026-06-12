---
title: "Ubuntu 12.04 can not find wifistation ub04 driver"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by Lorenci on 2012-06-22
Ubuntu 12.04 can not find wifistation ub04 driver please help me, i  need to install driver of wifi in ubuntu 12.04 :D Can anyone help me?

---

### Post by wildmanne39 on 2012-06-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Lorenci on 2012-06-22
Ok,i followed your steps and  and it appears

lenci@lenci:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux lenci 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
lenci@lenci:~$ lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169
lenci@lenci:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 005: ID 0cf3:b002 Atheros Communications, Inc. Ubiquiti WiFiStation 802.11n [Atheros AR9271]
Bus 002 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 002 Device 004: ID 09da:8090 A4 Tech Co., Ltd X-718BK Oscar Optical Gaming Mouse
lenci@lenci:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lenci@lenci:~$ rfkill list all
lenci@lenci:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40257  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nouveau               774571  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 nouveau
eeepc_wmi              13109  0 
mxm_wmi                12979  1 nouveau
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20762  1 rt73usb
rt2x00lib              55301  2 rt73usb,rt2x00usb
psmouse                87603  0 
wmi                    19256  2 mxm_wmi,asus_wmi
joydev                 17693  0 
lp                     17799  0 
soundcore              15091  1 snd
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
mac_hid                13253  0 
mac80211              506816  2 rt2x00usb,rt2x00lib
video                  19596  1 nouveau
usbhid                 47199  0 
serio_raw              13211  0 
hid                    99559  1 usbhid
cfg80211              205544  2 rt2x00lib,mac80211
usb_storage            49198  0 
r8169                  62099  0 
pata_via               13701  0

---

### Post by wildmanne39 on 2012-06-22
Hi, the device is not listed in 12.04 but the driver is present we can try this:
```
sudo modprobe -r rt73usb
```
Unplug the adapter.
```
echo 'install ath9k_htc modprobe --ignore-install ath9k_htc ; /bin/echo "0cf3 b002" > /sys/bus/usb/drivers/ath9k_htc/new_id' | sudo tee /etc/modprobe.d/ath9k_htc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Thanks

---

### Post by Lorenci on 2012-06-22
It works but just in  Wirelees -g usb dongle dosen't work in wifistation UB04 look the picture.. 

Works with this usb wirelees  >>> [IMG]http://www.google.com/imgres?q=Wireless+-g+usb+dongle+cnet&um=1&hl=en&biw=1215&bih=936&noj=1&tbm=isch&tbnid=KON23RjHJytg0M:&imgrefurl=http://www.impc.co.nz/products/iw_13074.html&docid=w60Q8t82slS_PM&itg=1&imgurl=http://www.impc.co.nz/Uploads/Items/99139/ori_13074.jpg&w=741&h=526&ei=SfHkT5XdO5DvsgaHkqDICQ&zoom=1&iact=hc&vpx=142&vpy=234&dur=291&hovh=160&hovw=225&tx=159&ty=82&sig=112559293629511817055&page=1&tbnh=153&tbnw=215&start=0&ndsp=20&ved=1t:429,r:0,s:0,i:77[/IMG] [http://goo.gl/mB9yR](http://goo.gl/mB9yR)

Dosen't work with this usb wirelees  >> [IMG]http://www.google.com/imgres?q=Wifistation+ub+04&um=1&hl=en&biw=1215&bih=936&noj=1&tbm=isch&tbnid=NVVAFxCdpDrA5M:&imgrefurl=http://www.4netonline.com/on/index.php%3Fmanufacturer_id%3D19%26target%3Dmanufacturers&docid=51x8zlvOONP5jM&imgurl=http://www.4netonline.com/on/images/product_images/thumbnail_UB04_WifiStation.jpg&w=200&h=200&ei=mvHkT8bJGYLYsgbisYSjCQ&zoom=1&iact=hc&vpx=147&vpy=166&dur=167&hovh=160&hovw=160&tx=95&ty=70&sig=112559293629511817055&page=1&tbnh=133&tbnw=133&start=0&ndsp=33&ved=1t:429,r:0,s:0,i:74[/IMG] [http://goo.gl/L6Jlw](http://goo.gl/L6Jlw)

Has any solutions?

---

### Post by wildmanne39 on 2012-06-22
Hi, did you do all the codes in my last post?

Were there any error's?

Please post:
```
modinfo ath9k_htc
```

Thanks

---

### Post by Lorenci on 2012-06-22
Look.

lenci@lenci:~$ modinfo ath9k_htc
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9B885B82530A1FF8F15C062
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
lenci@lenci:~$

---

### Post by wildmanne39 on 2012-06-22
Hi, that did not work, I will have to do some more research it may take a while this is a new issue for me.
Thanks

---

### Post by Lorenci on 2012-06-22
Ok,Thank you,i will wait...And appreciate your work.

---

### Post by wildmanne39 on 2012-06-22
Hi, reboot you computer with the adapter plugged in that we are working on and the other one disconnected and see if it see's it after the reboot.
Thanks

---

### Post by Lorenci on 2012-06-22
I reboot my computer with the adapter plugged in and nothing changed..Everything was as before 

Driver not working.

---

### Post by wildmanne39 on 2012-06-22
Hi, I am going to ask the expert my friend if he can have a look, he is much better at adding devices then I am.
Thanks

---

### Post by Lorenci on 2012-06-22
Ok I'm waiting

---

### Post by chili555 on 2012-06-22
Please try:```
sudo rm /etc/modprobe.d/ath9k_htc.conf
echo 'install ath9k_htc modprobe --ignore-install ath9k_htc ; /bin/echo "0cf3 b002" > /sys/bus/usb/drivers/ath9k_htc/new_id' | sudo tee /etc/modprobe.d/ath9k_htc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
dmesg | grep ath9k
iwconfig
```The difference is a space and not a colon: *echo 'install ath9k_htc modprobe --ignore-install ath9k_htc ; /bin/echo "0cf3**[COLOR="Red"]:[/COLOR]**b002" > /sys/bus/usb/drivers/ath9k_htc/new_id' | sudo tee /etc/modprobe.d/ath9k_htc.conf*

---

### Post by Lorenci on 2012-06-22
Thank you : 
[wildmanne39]("http://ubuntuforums.org/member.php?u=508533")
Thank you 
[URL="http://ubuntuforums.org/member.php?u=35909"]chili555                      It works now i can use my Wifisatation :D Thank you. 
[/URL]

---

### Post by chili555 on 2012-06-22
My buddy Wild Man hopes you will use thread tools at the top to mark Solved. Quite a few searchers will appreciate it.

---

### Post by Lorenci on 2012-06-22
I Made.Anything else?

---

### Post by wildmanne39 on 2012-06-22
Hi, nope that is it, glad it is working, now you know how one little thing in code can make a difference.

That is why chili is the expert and I am the student.
Enjoy

---

### Post by Lorenci on 2012-06-22
Yea i know Anyway.Thnx again. when I have any other problem will be contacted I think that this would not be wrong

---

### Post by Don Charisma on 2012-10-26
Hi There,

I'm using the Wifistation EXT which has the following lsusb :-

```
ubuntu@ubuntu-VirtualBox:~$ lsusb
Bus 001 Device 003: ID 0cf3:b003 Atheros Communications, Inc. Ubiquiti WiFiStationEXT 802.11n [Atheros AR9271]
```

I've tried changing the commands used to get Wifistation working on 12.04 :

```
sudo rm /etc/modprobe.d/ath9k_htc.conf
echo 'install ath9k_htc modprobe --ignore-install ath9k_htc ; /bin/echo "0cf3 b003" > /sys/bus/usb/drivers/ath9k_htc/new_id' | sudo tee /etc/modprobe.d/ath9k_htc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
dmesg | grep ath9k
iwconfig

```

But I still can't get any wlan on iwconfig. 

I'm using 12.10, on virtualbox (host win 7 x64) [http://sourceforge.net/projects/virtualboximage/files/Ubuntu%20Linux/12.10/ubuntu-12.10-desktop-i386.7z](http://sourceforge.net/projects/virtualboximage/files/Ubuntu%20Linux/12.10/ubuntu-12.10-desktop-i386.7z)

Anybody can help ?

Kind regards

---

### Post by chili555 on 2012-10-26
> **Don Charisma said:**
> Hi There,

But I still can't get any wlan on iwconfig. 

I'm using 12.10, on virtualbox (host win 7 x64) [http://sourceforge.net/projects/virtualboximage/files/Ubuntu%20Linux/12.10/ubuntu-12.10-desktop-i386.7z](http://sourceforge.net/projects/virtualboximage/files/Ubuntu%20Linux/12.10/ubuntu-12.10-desktop-i386.7z)

Anybody can help ?

Kind regardsAnd you probably never will. Networking in Virtual Box uses NAT or bridged networking and not the wireless device directly. 

[https://forums.virtualbox.org/viewtopic.php?f=1&t=50728](https://forums.virtualbox.org/viewtopic.php?f=1&t=50728)

---

### Post by Don Charisma on 2012-10-27
Thanks for the reply, but I disagree ... Virtualbox is able to connect USB devices, and I've had other USB wifi network adapters working before with Linux ...

Anybody else have any ideas ?

Kind regards

---

