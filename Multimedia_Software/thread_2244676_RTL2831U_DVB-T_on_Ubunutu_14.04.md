---
title: "RTL2831U DVB-T on Ubunutu 14.04"
date: 2014-09-18
forum: Multimedia Software
---

### Post by JimmyJames89 on 2014-09-18
Following this tutorial [http://crysol.org/es/node/1082](http://crysol.org/es/node/1082)

get this error:

```
james@James-PC:~/rtl2831-r2$ sudo make install
make -C /home/james/rtl2831-r2/v4l install
make[1]: Entering directory `/home/james/rtl2831-r2/v4l'
-e 
Removing obsolete files from /lib/modules/3.3.0-35-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/3.3.0-35-generic/kernel/drivers/media/dvb/frontends:

-e 
Removing obsolete files from /lib/modules/3.3.0-35-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/3.3.0-35-generic/kernel/drivers/media/video:

Installing kernel modules under /lib/modules/3.3.0-35-generic/kernel/drivers/media/:
/sbin/depmod -a 3.3.0-35-generic 
depmod: ERROR: could not open directory /lib/modules/3.3.0-35-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/james/rtl2831-r2/v4l'
make: *** [install] Error 2
james@James-PC:~/rtl2831-r2$ 


```

Have tried testing with w_scan, dvb scan - doesn't yield any results.

Something is telling me I'm going to have to reinstall 12.04 ubuntu, the compatibility seems to be present in that distro. 

If anyone can shine any light on what I can do to get this thing to run in xine of kaffeine or something! 

James

---

### Post by JimmyJames89 on 2014-09-18
lsusb:

```
Bus 001 Device 002: ID 0bda:2831 Realtek Semiconductor Corp. RTL2831U DVB-T
```

lsmod:

```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
dm_crypt               23177  0 
mxl5005s               62347  1 
arc4                   12608  2 
dvb_usb_rtl28xxu       30421  0 
rtl2830                18804  2 dvb_usb_rtl28xxu
rtl2832                19784  1 dvb_usb_rtl28xxu
dvb_usb_v2             36025  1 dvb_usb_rtl28xxu
dvb_core              125880  3 rtl2830,rtl2832,dvb_usb_v2
rc_core                27389  3 dvb_usb_rtl28xxu,dvb_usb_v2
i2c_mux                12896  1 rtl2832
zd1211rw               63742  0 
mac80211              630653  1 zd1211rw
cfg80211              484040  2 mac80211,zd1211rw
snd_hda_codec_analog    15049  1 
gpio_ich               13476  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_intel,snd_hda_codec_analog
kvm                   451511  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  16 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  1 
mei_me                 18627  0 
mac_hid                13205  0 
mei                    82276  1 mei_me
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
e1000e                254433  0 
psmouse               106678  0 
usb_storage            62209  1 
ptp                    18933  1 e1000e
i915                  783805  3 
floppy                 69418  0 
video                  19476  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
pps_core               19382  1 ptp
drm                   303102  4 i915,drm_kms_helper
pata_acpi              13038  0 
```

---

### Post by Agio on 2015-02-14
Hi,

I'm having the same problem with kernel 3.2.0-23-generic. Did you have any luck compiling the module or getting the card to work?.

thanks!

---

