---
title: "Error in Compiling Compat-wireless 2.6"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by Randize on 2011-08-25
I'm very new to linux, so my understanding about it may be little. I'm using Ubuntu 64bit, was trying to update my Alpha awus036nha with atheros chipset AR9217,I believe it's using ath9k_htc.

So I followed the step in here [http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)
which led me to down the two patch and compat-wireless, I applied the patches. But I got an error about linux/pm_qos.h cannot be found while I was executing the sudo make command.

Anyone had the same problem before? What am I missing here?

---

### Post by nm_geo on 2011-08-25
I did the following for a USB adapter that needed the ath9k_htc

Downloaded the driver installer
    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
    Execute the .deb packet

    Had already connected the WiFi adapter

    Needed the htc_9271.fw (firmware)
    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)
Click on 1.3/
    Moved it to /lib/firmware

Since you are a noobie .. maybe you need this 
cd to where you saved the file could be Downloads or Desktop

```
cd Desktop
``````
sudo mv htc_9271.fw /lib/firmware
```

---

### Post by Randize on 2011-08-26
How do I check if the driver has been installed correctly? Because I did try your method, nm_geo, much appreciated. But my problem still persist.

```
Module                  Size  Used by
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
vesafb                 13761  1 
parport_pc             36959  0 
ppdev                  17113  0 
arc4                   12529  2 
binfmt_misc            17565  1 
ath9k_htc              61400  0 
mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
ath9k_hw              323077  2 ath9k_htc,ath9k_common
nvidia              10709116  40 
ath                    23773  2 ath9k_htc,ath9k_hw
cfg80211              178528  3 ath9k_htc,mac80211,ath
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
option                 25285  2 
usb_wwan               20407  1 option
usbserial              42908  7 option,usb_wwan
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            27903  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53845  1 i7core_edac
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
ahci                   25951  3 
r8169                  48022  0 
usb_storage            53538  0 
uas                    17996  0 
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci
pata_jmicron           12747  0 
floppy                 74120  0 

``````
Interface    Chipset        Driver

wlan0        AR9001/9002/9271    usb - [phy0]

```Because these are the same as before as I recall. My main reason to change the driver is because my card could not inject packet efficiently. Another thing is, my driver limits my txpower at 20.

```
22:08:44  Trying broadcast probe requests...
22:08:46  No Answer...
22:08:46  Found 2 APs
```I'm not sure if 'No Answer' is a normal sign, I'm only able to inject 1 AP at the moment, so I assume this has to do with my driver.

```
randize@randize-EX58-UD3R:~$ sudo iwconfig mon0 txpower 30
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device mon0 ; Invalid argument.
randize@randize-EX58-UD3R:~$ sudo iwconfig wlan0 txpower 30
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
randize@randize-EX58-UD3R:~$ sudo iwconfig wlan0 txpower 20
randize@randize-EX58-UD3R:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
randize@randize-EX58-UD3R:~$ 

```And this is the txpower limitation I'm getting, anything higher than 20 will give me the error. My awus036nha is suppose to give 30dBm at max. Referring to here [http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NHA&Category=0](http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NHA&Category=0)

---

### Post by Randize on 2011-08-26
I just knew that my driver is still using the old firmware.
```

randize@randize-EX58-UD3R:~$ dmesg | grep ath9k
[   11.173296] usb 1-1: ath9k_htc: Transferred FW: **ar9271.fw**, size: 51312
[   11.438573] usb 1-1: ath9k_htc: HTC initialized with 33 credits
[   12.061066] Registered led device: ath9k-phy0::radio
[   12.061083] Registered led device: ath9k-phy0::assoc
[   12.061103] Registered led device: ath9k-phy0::tx
[   12.061116] Registered led device: ath9k-phy0::rx
[   12.061118] usb 1-1: ath9k_htc: USB layer initialized
[   12.061139] usbcore: registered new interface driver ath9k_hif_usb

```

Any way to load up the htc_9271.fw guys?

---

### Post by nm_geo on 2011-08-27
Let's make sure it is in the /lib/firmware

```
cd /lib/firmware
``````
ls | grep htc_9271.fw  
```That was a good catch on your side by the way.
I just looked at mine and I have both firmwares in my /lib/firmware.

do this please with adapter plugged in 

```
lsusb
```

---

### Post by Randize on 2011-08-27
I've got those two too.
```

randize@randize-EX58-UD3R:/lib/firmware$ ls | grep htc*
htc_9271.fw
randize@randize-EX58-UD3R:/lib/firmware$ ls | grep ar9271*
ar9271.fw
randize@randize-EX58-UD3R:/lib/firmware$ 
```

Here's my lsusb.
```
Bus 008 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by nm_geo on 2011-08-27
Ok let's verify 

```
cd /lib/firmware
```

```
ls | grep htc_7010.fw
```

That firmware is also listed in the modinfo for the ath9k_htc..
I do not know why..

So do the following

```
sudo modinfo ath9k_htc

```

My last alias listed fits your USB number.

alias:          usb:v[COLOR=Red]0CF3[/COLOR]p[COLOR=Red]9271[/COLOR]d*dc*dsc*dp*ic*isc*ip*

I guess we could move the offending firmware out of  /lib/firmware
That might force the correct firmware to run...??

---

### Post by nm_geo on 2011-08-27
Here is a link that might help ..

[http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc)

I am using a much newer kernel so my mapping is probably different

```
cat /etc/lsb-release; uname -a
```DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux Latitude-D620 3.0.0-0300rc2-generic #201106081532 SMP Wed Jun 8 16:21:54 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by Randize on 2011-08-27
Here's my modinfo for ath9k_htc. I didn't have the newer firmware for ar7010, so I download it in /lib/firmware
```
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ar9271.fw
firmware:       ar7010_1_1.fw
firmware:       ar7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     8F244C9A8C97C1B3B163005
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
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
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       2.6.38-11-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)

```Just to verify.
```
randize@randize-EX58-UD3R:/lib/firmware$ ls | grep htc_
htc_7010.fw
htc_9271.fw
```I also tried to move the old firmware, ar9271.fw, ar7010.fw and ar7010_1_1.fw altogether but my dmesg and modinfo still shows me the old firmware. Hmm.. Still no idea how to load it up. I'll give you my kernel version.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux randize-EX58-UD3R 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by nm_geo on 2011-08-27
Notice in your modinfo the firmware is called out..

> firmware:       ar9271.fw
 firmware:       ar7010_1_1.fw
 firmware:       ar7010.fw

If you want to get your geek on as chili555 would say we can upgrade the kernel. To a much newer one.  Since you are rather new to Ubuntu you probably don't have lots of important tweaks and changes.  I like to run on the cutting edge with kernels to get the benefit of all the new stuff, but it does not help when I am trying to help a new user with the standard install and the original kernel.

Here is a link to installing the 3.0 kernel in Natty if you want to try that route. If you decide to do it be sure you get the 64 bit kernel and headers.

[http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html](http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html)

everyone needs the all.deb
But if you have 64 bit installed you need the two that end in _amd64.deb
Be sure to install them in order as mentioned on the link.

When you reboot look for the 3.0 kernel to boot into. Then we might have to go through the ath9k_htc install and adding firmware again..

---

### Post by Randize on 2011-08-29
Alright I'm on a newer kernel now with slight problem, my nVidia driver is not compatible with the kernel version now, I can still use Ubuntu but without unity. Not a big problem, cause my mission is to get my driver right.
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux randize-EX58-UD3R 3.0.0-0300-generic #201107220917 SMP Fri Jul 22 09:20:45 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```I think I'm running with the new firmware now.
```
[   11.339591] usb 1-1: ath9k_htc: **Transferred FW: htc_9271.fw**, size: 51272
[   11.574392] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[   11.766384] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.3
[   11.952999] Registered led device: ath9k_htc-phy0
[   11.953003] usb 1-1: ath9k_htc: USB layer initialized
[   11.953028] usbcore: registered new interface driver ath9k_htc

``````
filename:       /lib/modules/3.0.0-0300-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[B]firmware:       htc_9271.fw
firmware:       htc_7010.fw[/B]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     E38FCD3060996964BF650AD
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
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
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       3.0.0-0300-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)

```Even the information in airmon is slightly different now.
```
Interface    Chipset        Driver

wlan0        Atheros AR9271    ath9k - [phy0]
```However I'm still sad that I could not get it to inject properly and the txpower limitation is still there. The old driver could inject packets to one of my AP, the newer firmware doesn't allow me to inject packets in any AP at all.

What could I be missing?

---

