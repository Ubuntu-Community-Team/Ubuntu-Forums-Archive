---
title: "rt5370 debugging posts in dmesg"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by simon5555 on 2013-02-21
Hi,

I have an rt5370 usb card in an laptop where I'm running ubuntu 12.04.  I have downloaded the rt5370 driver from RTL site and installed it following instructions; the wireless is now working.  However, I get continuous messages in the system log as following (each time with a different length number):
----
===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 2888
----

Backend of dmesg output is attached.

Every so often it looses connection and from what I can gather reconnects. I attach dmesg output after such occcurrence as well.

I have trawled the web but don't seem to be able to find the answer to that.  One place mentioned that RTL drivers were by default compiled with a debugging option in place, but this appears to be in the versions for other cards - I cannot find where it can be switched off for this one. Any pointers?

Also, something must be triggering the debug output :) - can anyone shed some light on what may be causing this?

Thanks,
Simon

---

### Post by varunendra on 2013-02-21
> **simon5555 said:**
> One place mentioned that RTL drivers were by default compiled with a debugging option in place, but this appears to be in the versions for other cards - I cannot find where it can be switched off for this one. Any pointers?
A quick lookup suggests it is in os/linux/config.mk file, I'm not sure though. May help if you can provide the exact link to the driver you downloaded.

---

### Post by simon5555 on 2013-02-21
I got it from:

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

the file labeled:

RT8070/RT3070/RT3370/RT5370/RT5372 USB 03/28/2012 2.5.0.3	

Thanks

---

### Post by varunendra on 2013-02-22
> **simon5555 said:**
> I got it from:

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)
Yes, the file is there (/os/linux/config.mk file in the extracted folder).

In line 223, remove the flag "-DDBG", then compile and install again.

Also, in lines 56 and 60, change the value from 'n' to 'y' before compiling.
(HAS_WPA_SUPPLICANT=y)
(HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y)

Let us know how it goes.

---

### Post by simon5555 on 2013-02-22
Thanks - I thought that it might be.  If I remove this flag, then I get an error compiling the driver:

[SNIP]
/home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c: In function ‘RTMP_STA_IoctlHandle’:
/home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:7286:4: error: implicit declaration of function ‘RTMPIoctlMAC’ [-Werror=implicit-function-declaration]
/home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:7290:4: error: implicit declaration of function ‘RTMPIoctlE2PROM’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o] Error 1
make[1]: *** [_module_/home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic-pae'
make: *** [LINUX] Error 2

Thanks

---

### Post by varunendra on 2013-02-22
Hmm.. experimenting with the driver..
[s](how did you compile by the way, I can't compile it at all!)

Can you post the modinfo of the driver?
```
modinfo rt2870sta
```
(assuming it is indeed rt2870sta that is built from this package)[/s]

**EDIT:**
Nevermind, compiled like a breeze on a live session of 12.04, and turned out to be rt5370sta (although description says RT2870).
Also, couldn't find what I was expecting in modinfo output (parameter for setting debugging mode).

Experimenting further..

---

### Post by varunendra on 2013-02-23
Nah, couldn't find anything relevant except that it builds fine (with some warnings) with all the "**-DDFS_DEBUG**" flags removed from the config.mk file.

You may try building and installing again with that flag removed. Although it doesn't seem relevant to me, yet wouldn't hurt trying.

Here's an old bug-report regarding the issue where comment #12 suggests almost the same thing we already tried : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807)

Just for the record (if not for any further hint), I'd like to see -
```
modinfo rt5370sta
lspci -nnk | grep -iA2 net
lsmod
```

**EDIT:**
Forgot this one -
```
iwpriv
```
please post its output as well.

Thanks!

---

### Post by simon5555 on 2013-02-25
Hi,

Thanks. The outputs are as follows:

```
simon@simon-ES1105N:~$ modinfo rt5370sta
filename:       /lib/modules/3.2.0-38-generic pae/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     B5F68EDB8F10C7E19E04080
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-38-generic-pae SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```

--------
```
simon@simon-ES1105N:~$ lspci -nnk | grep -iA2 net
[NONE] - this is a usb card btw

```
-------------
```
simon@simon-ES1105N:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  1 
snd_hda_codec_hdmi     31775  1 
joydev                 17393  0 
snd_hda_codec_realtek   174313  1 
rt5370sta             730296  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                86520  0 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17830  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  12 
btusb                  17948  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             158479  23 bnep,rfcomm,btusb
parport_pc             32114  0 
cedarview_gfx         381372  4 
ppdev                  12849  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
drm                   196391  6 cedarview_gfx,ttm,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_algo_bit           13199  1 cedarview_gfx
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
video                  19115  1 cedarview_gfx
wmi                    18744  0 

```
----------
```
simon@simon-ES1105N:~$ iwpriv
lo        no private ioctls.

ra0       Available private ioctls :
          set              (8BE2) : set 1024 char  & get   0      
          connStatus       (0004) : set 1024 char  & get 2047 char 
          driverVer        (0005) : set 1024 char  & get 2047 char 
          bainfo           (0006) : set 1024 char  & get 2047 char 
          descinfo         (0007) : set 1024 char  & get 2047 char 
          radio_off        (000A) : set 1024 char  & get 2047 char 
          radio_on         (000B) : set 1024 char  & get 2047 char 
          show             (0015) : set 1024 char  & get 2047 char 
          adhocEntry       (0016) : set 1024 char  & get 2047 char 
          bbp              (8BE3) : set 2047 char  & get 2047 char 
          mac              (8BE5) : set 1024 char  & get 1024 char 
          rf               (8BF3) : set 2047 char  & get 2047 char 
          e2p              (8BE7) : set 1024 char  & get 1024 char 
          stat             (8BE9) : set   0       & get 2047 char 
          get_site_survey  (8BED) : set   0       & get 1024 char

```

---

### Post by simon5555 on 2013-02-25
Managed to compile it with the -DDFS_DEBUG flag removed (but -DDBG still in place as it would not compile otherwise).

dmesg still produces the following output:
```
....
[   13.956698] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   14.220968] RTMP_TimerListAdd: add timer obj f85b2b70!
[   14.220982] RTMP_TimerListAdd: add timer obj f85b2bb8!
[   14.220990] RTMP_TimerListAdd: add timer obj f85b2c00!
[   14.220997] RTMP_TimerListAdd: add timer obj f85b2b28!
[   14.221007] RTMP_TimerListAdd: add timer obj f85b2a50!
[   14.221014] RTMP_TimerListAdd: add timer obj f85b2a98!
[   14.221021] RTMP_TimerListAdd: add timer obj f857d628!
[   14.221027] RTMP_TimerListAdd: add timer obj f856cef0!
[   14.221034] RTMP_TimerListAdd: add timer obj f856cf40!
[   14.221041] RTMP_TimerListAdd: add timer obj f857d714!
[   14.221050] RTMP_TimerListAdd: add timer obj f857d598!
[   14.221061] RTMP_TimerListAdd: add timer obj f857d6c8!
[   14.222631] -->RTUSBVenderReset
[   14.222849] <--RTUSBVenderReset
[   14.365105] init: alsa-restore main process (1000) terminated with status 19
[   14.425382] init: gdm main process (1017) killed by TERM signal
[   14.701760] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   14.702064] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.702634] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.703506] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.868721] Key1Str is Invalid key length(0) or Type(0)
[   14.868759] Key2Str is Invalid key length(0) or Type(0)
[   14.868796] Key3Str is Invalid key length(0) or Type(0)
[   14.868833] Key4Str is Invalid key length(0) or Type(0)
[   14.869399] 1. Phy Mode = 5
[   14.869403] 2. Phy Mode = 5
[   14.869409] NVM is Efuse and its size =2d[2d0-2fc] 
[   14.920678] phy mode> Error! The chip does not support 5G band 15!
[   14.920957] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   14.930933] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   14.972839] 3. Phy Mode = 9
[   14.975385] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   14.975391] \x1b[mAsicSetRxAnt, switch to main antenna
[   15.020724] MCS Set = ff 00 00 00 01
[   15.031298] <==== rt28xx_init, Status=0
[   15.033087] 0x1300 = 00064300
[   15.054354] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[   15.317553] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   15.576670] RTMP_TimerListAdd: add timer obj f85b2b70!
[   15.576679] RTMP_TimerListAdd: add timer obj f85b2bb8!
[   15.576685] RTMP_TimerListAdd: add timer obj f85b2c00!
[   15.576690] RTMP_TimerListAdd: add timer obj f85b2b28!
[   15.576697] RTMP_TimerListAdd: add timer obj f85b2a50!
[   15.576702] RTMP_TimerListAdd: add timer obj f85b2a98!
[   15.576707] RTMP_TimerListAdd: add timer obj f857d628!
[   15.576712] RTMP_TimerListAdd: add timer obj f856cef0!
[   15.576717] RTMP_TimerListAdd: add timer obj f856cf40!
[   15.576722] RTMP_TimerListAdd: add timer obj f857d714!
[   15.576728] RTMP_TimerListAdd: add timer obj f857d598!
[   15.576735] RTMP_TimerListAdd: add timer obj f857d6c8!
[   15.578180] -->RTUSBVenderReset
[   15.578321] <--RTUSBVenderReset
[   16.062399] Key1Str is Invalid key length(0) or Type(0)
[   16.062464] Key2Str is Invalid key length(0) or Type(0)
[   16.062529] Key3Str is Invalid key length(0) or Type(0)
[   16.062593] Key4Str is Invalid key length(0) or Type(0)
[   16.063582] 1. Phy Mode = 5
[   16.063591] 2. Phy Mode = 5
[   16.063598] NVM is Efuse and its size =2d[2d0-2fc] 
[   16.108946] phy mode> Error! The chip does not support 5G band 15!
[   16.109195] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   16.112940] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   16.134062] 3. Phy Mode = 9
[   16.136647] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   16.136650] \x1b[mAsicSetRxAnt, switch to main antenna
[   16.177028] MCS Set = ff 00 00 00 01
[   16.187711] <==== rt28xx_init, Status=0
[   16.189256] 0x1300 = 00064300
[   16.230475] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   16.231204] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   18.369902] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1459
[   20.613853] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2298
[   20.623112] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=8)
[   20.765574] RTMP_TimerListAdd: add timer obj f85e19e0!
[   20.848200] Rcv Wcid(1) AddBAReq
[   20.848220] Start Seq = 00000000
[   20.848231] RTMP_TimerListAdd: add timer obj f85e45f4!
[   20.879523] RTMP_TimerListAdd: add timer obj f85e1a38!
[   26.548696] init: plymouth-stop pre-start process (1664) terminated with status 1
[   30.867689] ra0: no IPv6 routers present
[   38.884508] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 2405
[   46.385036] Indicate_Legacy_Packet():flush reordering_timeout_mpdus! RxWI->Flags=128, pRxWI.TID=0, RxD->AMPDU=0!
[   46.385055] b, flush one!
[   51.293585] Rcv Wcid(1) AddBAReq
[   51.293593] Start Seq = 00000000
[   51.293613] RTMP_TimerListAdd: add timer obj f85e4664!
[   79.019629] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 2405
[  139.239537] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 2596

```

---

### Post by simon5555 on 2013-02-26
Fiddled with it a bit.  Switching to wicd instead of network-manager seems to get rid of "===>rt_ioctl_giwscan. 17(17) BSS returned, data->length =.." messages in dmesg.

Still, the driver seems to start up with quite a few messages indicating that it struggles at first.  This is the dmesg output (thanks for code tags btw, didn't realise could use them:)):

```

[   14.620860] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   14.950192] RTMP_TimerListAdd: add timer obj f9408b70!
[   14.950204] RTMP_TimerListAdd: add timer obj f9408bb8!
[   14.950212] RTMP_TimerListAdd: add timer obj f9408c00!
[   14.950219] RTMP_TimerListAdd: add timer obj f9408b28!
[   14.950228] RTMP_TimerListAdd: add timer obj f9408a50!
[   14.950234] RTMP_TimerListAdd: add timer obj f9408a98!
[   14.950241] RTMP_TimerListAdd: add timer obj f93d3628!
[   14.950248] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   14.950254] RTMP_TimerListAdd: add timer obj f93c2f40!
[   14.950261] RTMP_TimerListAdd: add timer obj f93d3714!
[   14.950269] RTMP_TimerListAdd: add timer obj f93d3598!
[   14.950278] RTMP_TimerListAdd: add timer obj f93d36c8!
[   14.952965] -->RTUSBVenderReset
[   14.953087] <--RTUSBVenderReset
[   15.476579] Key1Str is Invalid key length(0) or Type(0)
[   15.476618] Key2Str is Invalid key length(0) or Type(0)
[   15.476654] Key3Str is Invalid key length(0) or Type(0)
[   15.476691] Key4Str is Invalid key length(0) or Type(0)
[   15.477264] 1. Phy Mode = 5
[   15.477268] 2. Phy Mode = 5
[   15.477274] NVM is Efuse and its size =2d[2d0-2fc] 
[   15.523670] phy mode> Error! The chip does not support 5G band 15!
[   15.523902] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   15.527913] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   15.550165] 3. Phy Mode = 9
[   15.552646] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   15.552650] \x1b[mAsicSetRxAnt, switch to main antenna
[   15.598364] MCS Set = ff 00 00 00 01
[   15.611585] <==== rt28xx_init, Status=0
[   15.613152] 0x1300 = 00064300
[   15.874616] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1748
[   20.478087] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 3033
[   20.852721] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[   21.130771] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   21.391681] RTMP_TimerListAdd: add timer obj f9408b70!
[   21.391690] RTMP_TimerListAdd: add timer obj f9408bb8!
[   21.391696] RTMP_TimerListAdd: add timer obj f9408c00!
[   21.391701] RTMP_TimerListAdd: add timer obj f9408b28!
[   21.391708] RTMP_TimerListAdd: add timer obj f9408a50!
[   21.391713] RTMP_TimerListAdd: add timer obj f9408a98!
[   21.391718] RTMP_TimerListAdd: add timer obj f93d3628!
[   21.391723] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   21.391728] RTMP_TimerListAdd: add timer obj f93c2f40!
[   21.391733] RTMP_TimerListAdd: add timer obj f93d3714!
[   21.391739] RTMP_TimerListAdd: add timer obj f93d3598!
[   21.391746] RTMP_TimerListAdd: add timer obj f93d36c8!
[   21.393327] -->RTUSBVenderReset
[   21.393443] <--RTUSBVenderReset
[   21.891132] Key1Str is Invalid key length(0) or Type(0)
[   21.891171] Key2Str is Invalid key length(0) or Type(0)
[   21.891207] Key3Str is Invalid key length(0) or Type(0)
[   21.891244] Key4Str is Invalid key length(0) or Type(0)
[   21.891803] 1. Phy Mode = 5
[   21.891807] 2. Phy Mode = 5
[   21.891812] NVM is Efuse and its size =2d[2d0-2fc] 
[   21.938323] phy mode> Error! The chip does not support 5G band 15!
[   21.938569] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   21.942289] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   21.964046] 3. Phy Mode = 9
[   21.966665] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   21.966673] \x1b[mAsicSetRxAnt, switch to main antenna
[   22.007767] MCS Set = ff 00 00 00 01
[   22.018442] <==== rt28xx_init, Status=0
[   22.019975] 0x1300 = 00064300
[   22.569208] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   22.828941] RTMP_TimerListAdd: add timer obj f9408b70!
[   22.828951] RTMP_TimerListAdd: add timer obj f9408bb8!
[   22.828956] RTMP_TimerListAdd: add timer obj f9408c00!
[   22.828962] RTMP_TimerListAdd: add timer obj f9408b28!
[   22.828969] RTMP_TimerListAdd: add timer obj f9408a50!
[   22.828974] RTMP_TimerListAdd: add timer obj f9408a98!
[   22.828979] RTMP_TimerListAdd: add timer obj f93d3628!
[   22.828984] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   22.828989] RTMP_TimerListAdd: add timer obj f93c2f40!
[   22.828994] RTMP_TimerListAdd: add timer obj f93d3714!
[   22.829000] RTMP_TimerListAdd: add timer obj f93d3598!
[   22.829007] RTMP_TimerListAdd: add timer obj f93d36c8!
[   22.830486] -->RTUSBVenderReset
[   22.830630] <--RTUSBVenderReset
[   23.319205] Key1Str is Invalid key length(0) or Type(0)
[   23.319244] Key2Str is Invalid key length(0) or Type(0)
[   23.319280] Key3Str is Invalid key length(0) or Type(0)
[   23.319317] Key4Str is Invalid key length(0) or Type(0)
[   23.319877] 1. Phy Mode = 5
[   23.319881] 2. Phy Mode = 5
[   23.319887] NVM is Efuse and its size =2d[2d0-2fc] 
[   23.371998] phy mode> Error! The chip does not support 5G band 15!
[   23.372291] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   23.376096] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   23.397475] 3. Phy Mode = 9
[   23.399976] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   23.399985] \x1b[mAsicSetRxAnt, switch to main antenna
[   23.441202] MCS Set = ff 00 00 00 01
[   23.451892] <==== rt28xx_init, Status=0
[   23.453408] 0x1300 = 00064300
[   25.167584] init: plymouth-stop pre-start process (1726) terminated with status 1
[   25.582652] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   25.583274] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   25.603820] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=8)
[   27.839942] ===>rt_ioctl_giwscan. 25(25) BSS returned, data->length = 3422
[   27.840502] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=8)
[   30.473996] ===>rt_ioctl_giwscan. 27(27) BSS returned, data->length = 3626
[   30.600937] RTMP_TimerListAdd: add timer obj f94379e0!
[   30.840555] Rcv Wcid(1) AddBAReq
[   30.840565] Start Seq = 00000000
[   30.840576] RTMP_TimerListAdd: add timer obj f943a5f4!
[   30.967344] RTMP_TimerListAdd: add timer obj f9437a38!
[   33.569280] ra0: no IPv6 routers present
[   54.578766] Rcv Wcid(1) AddBAReq
[   54.578775] Start Seq = 00000000
[   54.578783] RTMP_TimerListAdd: add timer obj f943a664!

```

Any suggestions?

---

### Post by varunendra on 2013-02-26
Nope!

In fact switching to wicd can get rid of the message (or at least can reduce the intensity) is a new discovery in itself for me, and I owe you a big thanks for sharing it.

I tried to examine the source code for the driver but was too complex for my non-professional brain. I think I have already reached the limit of my knowledge, although I love pushing it :)

I'd definitely post when and if I can find something worth trying, but for now I'm out of ideas.

I'd appreciate your updates on it though.

---

### Post by simon5555 on 2013-03-01
While I was playing with it I had to start it up from a liveCD and checked the network.  Apparently all was quiet in the log:

```

[   37.862046] cfg80211: World regulatory domain updated:
[   37.862056] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   37.862064] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   37.862070] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   37.862076] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   37.862082] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   37.862088] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.003200] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
[   38.161917] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   38.161929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.161936] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   38.161942] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.161948] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   38.161954] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.161960] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   38.161967] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.161973] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   38.161979] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.161985] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   38.161992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162007] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   38.162014] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162020] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   38.162026] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162032] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   38.162038] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162044] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   38.162050] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162057] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   38.162063] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.162070] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   38.162076] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   38.162083] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   38.162089] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   38.162096] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   38.162102] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   38.208870] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   38.209765] Registered led device: rt2800usb-phy0::radio
[   38.209858] Registered led device: rt2800usb-phy0::assoc
[   38.209941] Registered led device: rt2800usb-phy0::quality
[   38.210065] usbcore: registered new interface driver rt2800usb
[   38.824474] init: alsa-restore main process (1751) terminated with status 99
[   39.477502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.478416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.153627] wlan0: authenticate with bc:76:70:05:1a:98
[   79.192971] wlan0: send auth to bc:76:70:05:1a:98 (try 1/3)
[   79.195739] wlan0: authenticated
[   79.219711] wlan0: associate with bc:76:70:05:1a:98 (try 1/3)
[   79.228942] wlan0: RX AssocResp from bc:76:70:05:1a:98 (capab=0x411 status=0 aid=4)
[   79.237186] wlan0: associated
[   79.237781] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

I am postng this from under the liveCD start up.  This is running with a different driver, of course, and probably simply has all debugging switched off :).  The wireless connection is not solid though - sometimes it connects with 70% signal strength and sometimes 100%, occasionally may drop the connection and then reconnects.  I attach a few informational outputs for your reference.  Not quite sure why iwpriv output is all but empty and and  iwconfig signal strength shows 70/70.
```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

```
------
```

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               22572  0 
arc4                   12474  2 
rt2800usb              22487  0 
rt2800lib              57759  1 rt2800usb
crc_ccitt              12628  1 rt2800lib
snd_hda_codec_hdmi     31778  1 
joydev                 17394  0 
snd_hda_codec_realtek    64876  1 
rt2x00usb              20100  1 rt2800usb
rt2x00lib              49084  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_intel          33029  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              475488  3 rt2800lib,rt2x00usb,rt2x00lib
snd_hwdep              13277  1 snd_hda_codec
cfg80211              181041  2 rt2x00lib,mac80211
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
dm_multipath           22755  0 
snd_rawmidi            25426  1 snd_seq_midi
scsi_dh                14205  1 dm_multipath
coretemp               13362  0 
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18396  0 
psmouse                91022  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
lpc_ich                16993  0 
serio_raw              13032  0 
btusb                  17952  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13078  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
parport_pc             32115  0 
bnep                   17791  2 
ppdev                  12850  0 
rfcomm                 38104  12 
lp                     17456  0 
bluetooth             189585  24 btusb,bnep,rfcomm
parport                40931  3 parport_pc,ppdev,lp
squashfs               36096  1 
overlayfs              27551  1 
nls_iso8859_1          12618  1 
dm_raid45              76509  0 
xor                    26091  1 dm_raid45
dm_mirror              21862  0 
dm_region_hash         16101  1 dm_mirror
dm_log                 18194  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 749989  0 
zlib_deflate           26623  1 btrfs
libcrc32c              12544  1 btrfs
wmi                    18745  0 
gma500_gfx            198234  2 
drm_kms_helper         47459  1 gma500_gfx
drm                   240232  3 gma500_gfx,drm_kms_helper
i2c_algo_bit           13317  1 gma500_gfx
video                  19070  1 gma500_gfx
usb_storage            39720  1 

```
-----
```

ubuntu@ubuntu:~$ modinfo rt2800usb
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D718536FBFA7ECEE9BC1525
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```
-------
```

ubuntu@ubuntu:~$ iwpriv
wlan0     no private ioctls.

lo        no private ioctls.

```
------
```

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:132   Missed beacon:0

lo        no wireless extensions.

```

---

### Post by varunendra on 2013-03-02
I got a bit too busy since last post, couldn't get time for forums.

Anyway, what if you try the live session driver with nohwcrypt parameter -
```
sudo modprobe -v rt2800usb nohwcrypt=y
```

As an additional measure, please also make sure to turn the power management off -
```
sudo iwconfig wlan0 power off
```
Does it get any more stable?


Btw, from man iwpriv-
> iwpriv - configure optionals (private) parameters of a wireless network
interface
..which sometimes also contains an on/off switch for debugging. I was looking for the same (hopelessly though) in modinfo as well. But in our case, it was no luck :(

---

### Post by simon5555 on 2013-03-04
Hi,

No notable impact/result.  rt2870usb isn't stable though - took a sequence of iwconfig with the following results (note the Bit rate):
```

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=121.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:46   Missed beacon:0

lo        no wireless extensions.

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=108 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:49   Missed beacon:0

lo        no wireless extensions.

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:49   Missed beacon:0

lo        no wireless extensions.

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:49   Missed beacon:0

lo        no wireless extensions.

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:51   Missed beacon:0

lo        no wireless extensions.

ubuntu@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MTS_2775724"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:64   Missed beacon:0

lo        no wireless extensions.


```

At the same time everything is quiet in dmesg, even ater connect/disconnect cycle:
```

[   40.887247] cfg80211: Calling CRDA to update world regulatory domain
[   41.196418] microcode: CPU1 sig=0x30661, pf=0x8, revision=0x10c
[   41.216210] microcode: CPU2 sig=0x30661, pf=0x8, revision=0x10c
[   41.225747] microcode: CPU3 sig=0x30661, pf=0x8, revision=0x10c
[   41.244478] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   41.341468] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   41.406282] init: failsafe main process (1545) killed by TERM signal
[   41.468223] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   41.471044] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   41.472232] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   41.542399] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   41.545261] cfg80211: World regulatory domain updated:
[   41.545283] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   41.545292] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.545299] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.545305] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.545312] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.545318] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.589839] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
[   41.595248] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   41.749754] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   41.749767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749775] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   41.749781] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749787] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   41.749793] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749799] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   41.749805] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749811] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   41.749818] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749823] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   41.749829] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749835] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   41.749842] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749848] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   41.749855] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749861] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   41.749867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749874] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   41.749881] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749888] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   41.749894] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.749901] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   41.749908] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.749915] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   41.749922] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.749929] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   41.749937] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.796400] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   41.797314] Registered led device: rt2800usb-phy0::radio
[   41.797402] Registered led device: rt2800usb-phy0::assoc
[   41.797486] Registered led device: rt2800usb-phy0::quality
[   41.798738] usbcore: registered new interface driver rt2800usb
[   42.448547] init: alsa-restore main process (1746) terminated with status 99
[   43.024355] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.035539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  110.111357] wlan0: authenticate with bc:76:70:05:1a:98
[  110.154441] wlan0: send auth to bc:76:70:05:1a:98 (try 1/3)
[  110.158710] wlan0: authenticated
[  110.181036] wlan0: associate with bc:76:70:05:1a:98 (try 1/3)
[  110.190184] wlan0: RX AssocResp from bc:76:70:05:1a:98 (capab=0x411 status=0 aid=3)
[  110.198261] wlan0: associated
[  110.198844] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  511.579729] wlan0: deauthenticating from bc:76:70:05:1a:98 by local choice (reason=3)
[  511.628843] cfg80211: All devices are disconnected, going to restore regulatory settings
[  511.628854] cfg80211: Restoring regulatory settings
[  511.628863] cfg80211: Calling CRDA to update world regulatory domain
[  511.652611] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  511.652621] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652626] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  511.652631] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652635] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  511.652640] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652645] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  511.652650] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652654] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  511.652659] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652663] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  511.652668] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652673] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  511.652677] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652682] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  511.652686] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652691] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  511.652696] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652700] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  511.652705] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652709] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  511.652714] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652719] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  511.652723] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  511.652728] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  511.652733] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  511.652737] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  511.652742] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  511.652748] cfg80211: World regulatory domain updated:
[  511.652751] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  511.652756] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652761] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  511.652766] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  511.652771] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  511.652775] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  527.185369] wlan0: authenticate with bc:76:70:05:1a:98
[  527.228368] wlan0: send auth to bc:76:70:05:1a:98 (try 1/3)
[  527.229868] wlan0: authenticated
[  527.256198] wlan0: associate with bc:76:70:05:1a:98 (try 1/3)
[  527.267575] wlan0: RX AssocResp from bc:76:70:05:1a:98 (capab=0x411 status=0 aid=3)
[  527.275774] wlan0: associated
[  594.723994] wlan0: deauthenticating from bc:76:70:05:1a:98 by local choice (reason=3)
[  594.771824] cfg80211: All devices are disconnected, going to restore regulatory settings
[  594.771848] cfg80211: Restoring regulatory settings
[  594.771870] cfg80211: Calling CRDA to update world regulatory domain
[  594.797171] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  594.797180] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797186] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  594.797191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797195] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  594.797200] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797205] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  594.797210] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797214] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  594.797219] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797223] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  594.797228] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797232] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  594.797237] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797242] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  594.797247] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797251] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  594.797256] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797260] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  594.797265] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797270] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  594.797274] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797279] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  594.797284] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  594.797288] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  594.797293] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  594.797298] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  594.797302] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  594.797309] cfg80211: World regulatory domain updated:
[  594.797312] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  594.797317] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797322] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  594.797327] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  594.797331] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  594.797336] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  631.306558] wlan0: authenticate with bc:76:70:05:1a:98
[  631.356170] wlan0: send auth to bc:76:70:05:1a:98 (try 1/3)
[  631.357741] wlan0: authenticated
[  631.382726] wlan0: associate with bc:76:70:05:1a:98 (try 1/3)
[  631.391968] wlan0: RX AssocResp from bc:76:70:05:1a:98 (capab=0x411 status=0 aid=3)
[  631.400897] wlan0: associated

```

---

### Post by varunendra on 2013-03-04
Even though you may fix the rate with "sudo iwconfig rate xx" or "sudo iwconfig rate xx auto", it isn't worth trying if the connection is not stable at any of the rates.

By the way, are you using n-channel? Disabling it in router often does miracles.

---

### Post by simon5555 on 2013-03-04
To be totally frank, I am not sure how to disable the n-channel on the router or how to check whether it is on:).  I have a Huawei HG532c router.

---

### Post by varunendra on 2013-03-04
> **simon5555 said:**
> To be totally frank, I am not sure how to disable the n-channel on the router or how to check whether it is on:).  I have a Huawei HG532c router.

The fact that you are sometimes connected at a speed higher than 54Mb/s is itself a proof that n-channel is enabled in the router and is being used sometimes by the driver.

Refer to page 12, section 3.1.3, WLAN Rates in your router's manual here : [http://www.huaweidevice.com.eg/Product-Description/360download.php?filename=pdf/HG532c.pdf](http://www.huaweidevice.com.eg/Product-Description/360download.php?filename=pdf/HG532c.pdf)

However, I couldn't find screenshots or step-by-step instructions for its web management console. But there must be an option to choose/enable/disable the supported channels.

Be aware that doing so will limit the speed to 54Mb/s, so if it doesn't help stability, you may wish to enable it again. Although with Linux drivers it most often helps.

---

### Post by simon5555 on 2013-03-05
Thanks, I found where to switch b/g/n on the router and yes slowing it down seems to have some effect.  What seem to have had an even greater effect was setting the channel to high number instead of auto (I use 11).  Surprisingly (for me as I do not know what is actually helping here) dmesg has been very quiet and speed us at 135! Here is the tailend of dmesg:
```

 [   12.543363] rtusb init rt2870 --->[   12.543825] 
[   12.543830] 
[   12.543832] === pAd = f93c1000, size = 519032 ===
[   12.543835] 
[   12.544743] <-- RTMPAllocTxRxRingMemory, Status=0
[   12.545074] <-- RTMPAllocAdapterBlock, Status=0
[   12.548646] Overlay GTT address is 7c0000
[   12.562822] usbcore: registered new interface driver rt2870
[   12.756985] type=1400 audit(1362479315.802:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=737 comm="apparmor_parser"
[   12.764022] type=1400 audit(1362479315.810:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=737 comm="apparmor_parser"
[   12.764930] type=1400 audit(1362479315.810:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=737 comm="apparmor_parser"
[   12.998711] init: failsafe main process (750) killed by TERM signal
[   13.143646] init: network-manager main process (817) terminated with status 127
[   13.143738] init: network-manager main process ended, respawning
[   13.147986] fbcon: psbfb (fb0) is primary device
[   13.269297] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   13.285972] type=1400 audit(1362479316.330:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=889 comm="apparmor_parser"
[   13.287658] type=1400 audit(1362479316.334:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889 comm="apparmor_parser"
[   13.288574] type=1400 audit(1362479316.334:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
[   13.292720] type=1400 audit(1362479316.338:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=888 comm="apparmor_parser"
[   13.294552] type=1400 audit(1362479316.342:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=892 comm="apparmor_parser"
[   13.473634] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[   13.480357] Console: switching to colour frame buffer device 170x48
[   13.495297] fb0: psbfb frame buffer device
[   13.495306] drm: registered panic notifier
[   13.495431] Cedartrail: apply sample cache workaround
[   13.495718] Device ID: 2
[   13.495750] [drm] Initialized pvrsrvkm 8.1.0 2009-03-10 for 0000:00:02.0 on minor 0
[   13.495907] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.496046] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   13.496119] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.571643] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   13.572572] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   13.573528] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   13.574854] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   13.959515] init: gdm main process (1023) killed by TERM signal
[   14.403938] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   14.725543] RTMP_TimerListAdd: add timer obj f9408b70!
[   14.725557] RTMP_TimerListAdd: add timer obj f9408bb8!
[   14.725565] RTMP_TimerListAdd: add timer obj f9408c00!
[   14.725574] RTMP_TimerListAdd: add timer obj f9408b28!
[   14.725583] RTMP_TimerListAdd: add timer obj f9408a50!
[   14.725591] RTMP_TimerListAdd: add timer obj f9408a98!
[   14.725599] RTMP_TimerListAdd: add timer obj f93d3628!
[   14.725606] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   14.725613] RTMP_TimerListAdd: add timer obj f93c2f40!
[   14.725620] RTMP_TimerListAdd: add timer obj f93d3714!
[   14.725629] RTMP_TimerListAdd: add timer obj f93d3598!
[   14.725639] RTMP_TimerListAdd: add timer obj f93d36c8!
[   14.727193] -->RTUSBVenderReset
[   14.727316] <--RTUSBVenderReset
[   15.243250] Key1Str is Invalid key length(0) or Type(0)
[   15.243288] Key2Str is Invalid key length(0) or Type(0)
[   15.243325] Key3Str is Invalid key length(0) or Type(0)
[   15.243374] Key4Str is Invalid key length(0) or Type(0)
[   15.243941] 1. Phy Mode = 5
[   15.243945] 2. Phy Mode = 5
[   15.243950] NVM is Efuse and its size =2d[2d0-2fc] 
[   15.292146] phy mode> Error! The chip does not support 5G band 15!
[   15.292379] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   15.296152] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   15.317766] 3. Phy Mode = 9
[   15.320282] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   15.320285] \x1b[mAsicSetRxAnt, switch to main antenna
[   15.361384] MCS Set = ff 00 00 00 01
[   15.372058] <==== rt28xx_init, Status=0
[   15.373580] 0x1300 = 00064300
[   15.633369] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1135
[   20.466703] ===>rt_ioctl_giwscan. 27(27) BSS returned, data->length = 3674
[   21.156687] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   21.416782] RTMP_TimerListAdd: add timer obj f9408b70!
[   21.416792] RTMP_TimerListAdd: add timer obj f9408bb8!
[   21.416798] RTMP_TimerListAdd: add timer obj f9408c00!
[   21.416803] RTMP_TimerListAdd: add timer obj f9408b28!
[   21.416810] RTMP_TimerListAdd: add timer obj f9408a50!
[   21.416815] RTMP_TimerListAdd: add timer obj f9408a98!
[   21.416820] RTMP_TimerListAdd: add timer obj f93d3628!
[   21.416825] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   21.416830] RTMP_TimerListAdd: add timer obj f93c2f40!
[   21.416835] RTMP_TimerListAdd: add timer obj f93d3714!
[   21.416841] RTMP_TimerListAdd: add timer obj f93d3598!
[   21.416849] RTMP_TimerListAdd: add timer obj f93d36c8!
[   21.418362] -->RTUSBVenderReset
[   21.418459] <--RTUSBVenderReset
[   21.896443] Key1Str is Invalid key length(0) or Type(0)
[   21.896481] Key2Str is Invalid key length(0) or Type(0)
[   21.896518] Key3Str is Invalid key length(0) or Type(0)
[   21.896554] Key4Str is Invalid key length(0) or Type(0)
[   21.897128] 1. Phy Mode = 5
[   21.897132] 2. Phy Mode = 5
[   21.897138] NVM is Efuse and its size =2d[2d0-2fc] 
[   21.943486] phy mode> Error! The chip does not support 5G band 15!
[   21.943801] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   21.947614] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   21.968848] 3. Phy Mode = 9
[   21.971462] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   21.971471] \x1b[mAsicSetRxAnt, switch to main antenna
[   22.012425] MCS Set = ff 00 00 00 01
[   22.023136] <==== rt28xx_init, Status=0
[   22.024680] 0x1300 = 00064300
[   22.627092] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   22.886122] RTMP_TimerListAdd: add timer obj f9408b70!
[   22.886131] RTMP_TimerListAdd: add timer obj f9408bb8!
[   22.886137] RTMP_TimerListAdd: add timer obj f9408c00!
[   22.886142] RTMP_TimerListAdd: add timer obj f9408b28!
[   22.886149] RTMP_TimerListAdd: add timer obj f9408a50!
[   22.886154] RTMP_TimerListAdd: add timer obj f9408a98!
[   22.886159] RTMP_TimerListAdd: add timer obj f93d3628!
[   22.886164] RTMP_TimerListAdd: add timer obj f93c2ef0!
[   22.886169] RTMP_TimerListAdd: add timer obj f93c2f40!
[   22.886174] RTMP_TimerListAdd: add timer obj f93d3714!
[   22.886180] RTMP_TimerListAdd: add timer obj f93d3598!
[   22.886188] RTMP_TimerListAdd: add timer obj f93d36c8!
[   22.887997] -->RTUSBVenderReset
[   22.888170] <--RTUSBVenderReset
[   23.379283] Key1Str is Invalid key length(0) or Type(0)
[   23.379322] Key2Str is Invalid key length(0) or Type(0)
[   23.379358] Key3Str is Invalid key length(0) or Type(0)
[   23.379395] Key4Str is Invalid key length(0) or Type(0)
[   23.379970] 1. Phy Mode = 5
[   23.379974] 2. Phy Mode = 5
[   23.379980] NVM is Efuse and its size =2d[2d0-2fc] 
[   23.426392] phy mode> Error! The chip does not support 5G band 15!
[   23.426702] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   23.431002] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   23.452118] 3. Phy Mode = 9
[   23.454743] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   23.454753] \x1b[mAsicSetRxAnt, switch to main antenna
[   23.495725] MCS Set = ff 00 00 00 01
[   23.506398] <==== rt28xx_init, Status=0
[   23.508059] 0x1300 = 00064300
[   25.004665] init: plymouth-stop pre-start process (1656) terminated with status 1
[   25.663156] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   25.664398] /home/simon/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[   25.672928] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 2609
[   25.673758] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=11)
[   25.688165] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=11)
[   28.240889] ===>rt_ioctl_giwscan. 25(25) BSS returned, data->length = 3613
[   28.328388] RTMP_TimerListAdd: add timer obj f94379e0!
[   28.880578] Rcv Wcid(1) AddBAReq
[   28.880586] Start Seq = 00000000
[   28.880594] RTMP_TimerListAdd: add timer obj f943a5f4!
[   28.978444] RTMP_TimerListAdd: add timer obj f9437a38!
[   33.558869] ra0: no IPv6 routers present
[   52.444964] Rcv Wcid(1) AddBAReq
[   52.444971] Start Seq = 00000000
[   52.444979] RTMP_TimerListAdd: add timer obj f943a664!
[  387.526532] DeQueueRunning[0]= TRUE!
[  532.862493] RTMP_TimerListAdd: add timer obj f9437a90!
[  723.289247] ACPI: EC: GPE storm detected, transactions will use polling mode
[ 1165.594752] DeQueueRunning[0]= TRUE!
[ 1978.723624] DeQueueRunning[0]= TRUE!

```

and iwconfig is:

```

simon@simon-ES1105N:~$ iwconfig
lo        no wireless extensions.


ra0       Ralink STA  ESSID:"MTS_2775724"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-39 dBm  Noise level:-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I will observe it further and report.  Every so often "DeQueueRunning[0]= TRUE!" comes through and I also want to investigate this too :).

---

### Post by varunendra on 2013-03-05
That's great!
..and a really useful info. Thanks a lot for all the testing and the feedback. You are certainly adding new things to my knowledge.

I don't know either what may be helping here, can only guess which I wouldn't at this point. As a post in the bug report page mentioned, the debug messages were only indicators of some rather intangible issue with connectivity. As such, I think it is safe to assume that fixing the channel to a number not commonly used (thus having less traffic) could have helped.

In any case, it is certainly good to know that there can be fixes that are better than disabling n-channel and compromising with slower channels.
Shall keep an eye on your progress, and thanks again for the valuable feedback!

---

### Post by simon5555 on 2013-03-11
Did some more testing and switching between wicd and network-manager.  Bottom line is that the combination of wicd + high channels gives virtually no "[COLOR=#000000][FONT=Ubuntu Mono]===>rt_ioctl_giwscan. 25(25) BSS returned, data->length ="[FONT=arial] messages in dmesg.  Using nm produces them, albeit somewhat fewer with higher channel than with lower. [/FONT] 
[FONT=arial]
Ended up running both wicd and nm since i need to use vpn every so often and setting it up seems to be far more involved with wicd than with nm:(.[/FONT]
[/FONT][/COLOR]

---

### Post by kurt18947 on 2013-03-11
simon5555, perhaps I didn't read carefully but did you try just plugging your adapter in?  I just purchased a 'generic' rt5370 device and it is 'plug 'n' play' on 12.04, 12.10 & 13.04.  No downloads or compiling necessary.

---

### Post by simon5555 on 2013-03-15
[COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]kurt18947

Thanks.  The card is actually already built into the laptop and it does seem to work with the standard drivers.  However the connection is unstable (it disconnects and reconnects every so often) and the signal strength is reduced (even next to the router its c80% whereas with the new driver it is at 100% almost anywhere in the flat).  This is why I have been looking at switching to the new drivers. [/COLOR]

---

### Post by kurt18947 on 2013-03-15
> **simon5555 said:**
> [COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]kurt18947

Thanks.  The card is actually already built into the laptop and it does seem to work with the standard drivers.  However the connection is unstable (it disconnects and reconnects every so often) and the signal strength is reduced (even next to the router its c80% whereas with the new driver it is at 100% almost anywhere in the flat).  This is why I have been looking at switching to the new drivers. [/COLOR]

Ah, you're using RT2800PCI (I think that's the designation), my device uses RT2800USB.  I wonder if you're being affected by a hardware encryption bug. Sometimes unstable connections are helped by disabling hardware encryption and using software encryption instead.  You could experiment by trying this:

Make sure you doing this from an account with sudo privileges.  Open a terminal and enter the following:

```
gksu gedit /etc/modprobe.d/rt2800pci.conf

```

That should give you a new empty screen. Copy this into the blank editor:

```
options rt2800pci nohwcrypt=1

```

Save and reboot. I've also seen that line as "nohwcrypt=y" once so I'm not certain which is correct, I'd
probably go with "nohwcrypt=1".  I don't believe there is any risk to this and if it doesn't help, you can simply delete the file.

---

### Post by varunendra on 2013-03-15
> **kurt18947 said:**
> Ah, you're using RT2800PCI (I think that's the designation), my device uses RT2800USB.
Hi kurt,
Even though the device is built-in, it can be on a USB bus, which is the case here -
> **simon5555 said:**
> ```
simon@simon-ES1105N:~$ lspci -nnk | grep -iA2 net
[NONE] - this is a usb card btw
```
Hence it is same as an external usb adapter, natively supported by the rt2800usb driver.

Also -
> **kurt18947 said:**
> I wonder if you're being affected by a hardware encryption bug. Sometimes unstable connections are helped by disabling hardware encryption and using software encryption instead.
True. But unfortunately, simon has already tried that -
> **varunendra said:**
> Anyway, what if you try the live session driver with nohwcrypt parameter -
```
sudo modprobe -v rt2800usb nohwcrypt=y
```

As an additional measure, please also make sure to turn the power management off -
```
sudo iwconfig wlan0 power off
```
Does it get any more stable?
..with no significant improvement -
> **simon5555 said:**
> No notable impact/result.  rt2870usb isn't stable though....
.... again -
> **simon5555 said:**
> I am postng this from under the liveCD start up.  This is running with a different driver, of course........ The wireless connection is not solid though - sometimes it connects with 70% signal strength and sometimes 100%, occasionally may drop the connection and then reconnects.


But I like your curiosity, and so I think you deserve an explanation to whatever doubts you have -
> **kurt18947 said:**
> I've also seen that line as "nohwcrypt=y" once so I'm not certain which is correct, I'd
probably go with "nohwcrypt=1". 
1/0 are integer values and Y/N are Boolean values to logical true/false respectively. Although so far I have always seen '1' work where 'Y' is expected, but I prefer to go with what is expected by the driver.

To see what the driver expects, simply use modinfo command with the driver. For example -

```
ubuntu@ubuntu:~$ **modinfo rt2800usb**
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
....
....
....
....
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
**parm:         nohwcrypt:Disable hardware encryption. [COLOR="#FF0000"](bool)[/COLOR]**  
```
Note that the only parameter available for the rt2800usb driver is 'nohwcrypt', and it expects a (bool) value, means Y or N (small y and n are also valid).
But like I said, if you use '1' instead of 'Y', it gets accepted too.

Now if you run modinfo ath9k, it lists the same parameter with (int) value-
> modinfo ath9k
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
....
**parm:           nohwcrypt: Disable hardware encryption [COLOR="#FF0000"](int)[/COLOR]**

Means only integer 1 or 0 are acceptable values. If you try **sudo modprobe -v ath9k nohwcrypt=[COLOR="#FF0000"]y[/COLOR]**, it gives error -
> FATAL: Error inserting ath9k (/lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): **[COLOR="#FF0000"]Invalid argument[/COLOR]**

So in my experience so far, (int) 1 or 0 values have always been acceptable even where (bool) was expected, but the vice-versa is not true.

One more thing -
> **kurt18947 said:**
> I don't believe there is any risk to this and if it doesn't help, you can simply delete the file.
Well, as we saw in the above example, there IS a minor risk - the driver simply does not get loaded if a parameter is wrong. Either there should be no parameter (defaults will be loaded), or it should be correct.

Hope you didn't fall asleep while reading this ;)

---

### Post by kurt18947 on 2013-03-15
Thank you for that, Varun.  Very instructive.

---

### Post by varunendra on 2013-03-15
You're welcome !
As long as you are willing to learn, there are instructors here who can explain much better in much less words. :)

---

### Post by simon5555 on 2013-03-15
Hi,

Varun is right, it is a built in card on usb:
```

simon@simon-ES1105N:~$ lsusb
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I think I may have nailed the debug output issue.  They seem to have forgotten to put DBG ifdef/endif the right way around, i.e. debug switches in [path]/sta/sta_cfg.c.  The solution seems to be to make the following adjustments in [path]/sta/sta_cfg.c:
- move "#endif" statement from line 4694 to line 4537;
- insert "#ifdef DBG" just before the "RTMPIoctlMAC(pAd, pRequest);" call on line 7286 and "#endif" immediately after;
- insert "#ifdef DBG" just before the "RTMPIoctlE2PROM(pAd, pRequest);" call on line 7291 and "#endif" immediately after;

After that it compiles, albeit giving some warnings, installs and dmesg is quiet even running under network-manager :-). 

```

[   11.906852] rtusb init rt2870 --->
[   11.913400] usbcore: registered new interface driver rt2870
[   11.918914] microcode: CPU0 sig=0x30661, pf=0x8, revision=0x10c
[   11.985155] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   11.985536] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.985855] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.153385] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.156614] type=1400 audit(1363370347.131:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=667 comm="apparmor_parser"
[   12.157726] type=1400 audit(1363370347.131:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
[   12.158318] type=1400 audit(1363370347.131:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
[   12.458002] microcode: CPU1 sig=0x30661, pf=0x8, revision=0x10c
[   12.463906] microcode: CPU2 sig=0x30661, pf=0x8, revision=0x10c
[   12.470025] microcode: CPU3 sig=0x30661, pf=0x8, revision=0x10c
[   12.476091] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.483964] coretemp coretemp.0: Unable to read TjMax from CPU 0
[   12.483999] coretemp coretemp.0: Using relative temperature scale!
[   12.484044] coretemp coretemp.0: Unable to read TjMax from CPU 2
[   12.484071] coretemp coretemp.0: Using relative temperature scale!
[   12.612337] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   12.665228] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   13.184719] init: failsafe main process (797) killed by TERM signal
[   13.295511] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.295523] Bluetooth: BNEP filters: protocol multicast
[   13.303352] Bluetooth: RFCOMM TTY layer initialized
[   13.303371] Bluetooth: RFCOMM socket layer initialized
[   13.303378] Bluetooth: RFCOMM ver 1.11
[   13.462337] ppdev: user-space parallel port driver
[   13.520287] type=1400 audit(1363370348.495:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=882 comm="apparmor_parser"
[   13.527417] type=1400 audit(1363370348.503:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=882 comm="apparmor_parser"
[   13.562065] type=1400 audit(1363370348.539:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=889 comm="apparmor_parser"
[   13.567814] type=1400 audit(1363370348.543:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=890 comm="apparmor_parser"
[   13.569413] type=1400 audit(1363370348.543:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=890 comm="apparmor_parser"
[   13.570546] type=1400 audit(1363370348.547:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=890 comm="apparmor_parser"
[   13.582080] type=1400 audit(1363370348.559:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=891 comm="apparmor_parser"
[   14.981011] 0x1300 = 00064300
[   15.194176] init: plymouth-stop pre-start process (1188) terminated with status 1
[   16.130899] 0x1300 = 00064300
[   18.068952] Adding 2083836k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2083836k SS

```

```

simon@simon-ES1105N:~$ iwconfig
ra0       Ralink STA  ESSID:"MTS_2775724"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-44 dBm  Noise level:-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.

```

Cheers, Simon

---

### Post by varunendra on 2013-03-15
> **simon5555 said:**
> 
I think I may have nailed the debug output issue.  They seem to have forgotten to put DBG ifdef/endif the right way around, i.e. debug switches in [path]/sta/sta_cfg.c.  The solution seems to be to make the following adjustments in [path]/sta/sta_cfg.c:
- move "#endif" statement from line 4694 to line 4537;
- insert "#ifdef DBG" just before the "RTMPIoctlMAC(pAd, pRequest);" call on line 7286 and "#endif" immediately after;
- insert "#ifdef DBG" just before the "RTMPIoctlE2PROM(pAd, pRequest);" call on line 7291 and "#endif" immediately after;

After that it compiles, albeit giving some warnings, installs and dmesg is quiet even running under network-manager :-). 

Please keep it on testbed for a while, and post back about connectivity and stability. If all good, I think it may be the *Golden Post of the month* ! :D

---

### Post by simon5555 on 2013-03-18
Tested it for a few days with the newly compiled driver and have had no problems with wifi stability/connectivity/signal strength.  dmesg is also dead quiet :-).  Of course there is a simpler way of amending the code by simply removing "#ifdef DBG" on line 4095 and "endif /* DBG */" on line 4693. 
 
So, the eventual procedure to install rt5370 driver with debug messages switched off is:

1. download driver archive 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2 ([COLOR=#000000]RT8070/RT3070/RT3370/RT5370/RT5372 USB 03/28/2012 2.5.0.3 from[/COLOR] [http://www.mediatek.com/_en/07_downl...ows.php?sn=501]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501"))

2. unpack it where ever you saved it to and go into the folder:
```

tar -xvf 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2
cd 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
```

3. amend os/linux/config.mk:
HAS_WPA_SUPPLICANT=y instead of HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y instead of HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
WFLAGS += -DCONFIG_STA_SUPPORT instead of WFLAGS += -DCONFIG_STA_SUPPORT -DDBG

4. amend sta/sta-cfg.c:
remove "#ifdef DBG" on line 4095
remove "endif /* DBG */" on line 4693

5. if required (i.e. if compilation gives off errors) run

```

sudo apt-get install build-essential linux-headers-generic

```
6. compile it and install

```

sudo make
sudo make install
modprobe rt5370sta

```

7. blacklist old drivers by inserting at the end of /etc/modprobe.d/blacklist.conf:
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb

8. reboot

and the wifi should be there with no debugging messages in dmesg:).

---

### Post by varunendra on 2013-03-18
Grrreat!! Bookmarked for sure!

Thanks a lot for your time and contribution. Wish I knew a way to award medals to individual posts :D.
But I do know to rate threads (not sure if normal users can see it), and going to rate this one as "Excellent" - credit all yours :)

---

### Post by simon5555 on 2013-03-31
Have been playing with the driver a bit more and came across this: [https://build.opensuse.org/package/view_file?expand=1&file=rt5370sta-2.5.0.3-convert-devicename-to-wlanX.patch&package=rt5370sta&project=driver%3Awireless](https://build.opensuse.org/package/view_file?expand=1&file=rt5370sta-2.5.0.3-convert-devicename-to-wlanX.patch&package=rt5370sta&project=driver%3Awireless)

Turns out changing ra0 to wlan0 is somewhat simple:):
```

simon@simon-ES1105N:~$ iwconfig
wlan0     Ralink STA  ESSID:"MTS_2775724"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: BC:76:70:05:1A:98   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.



```

---

