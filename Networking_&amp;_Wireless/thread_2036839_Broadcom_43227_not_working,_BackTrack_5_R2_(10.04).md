---
title: "Broadcom 43227 not working, BackTrack 5 R2 (10.04)"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by xblueorbx on 2012-08-03
I have tried searching these forums as well as Google and nothing seems to be helping, so I decided to get some help from you guys. My BCM43227 is simply not working... I tried installing ndiswrapper to install the Windows drivers and although it says that it installed the device, it's still not working.

"lspci | grep Network":
```

08:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n

```lsmod:
```

Module                  Size  Used by
radeon                813181  2 
ttm                    68384  1 radeon
drm_kms_helper         40041  1 radeon
drm                   225891  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13156  1 radeon
dm_crypt               22668  0 
joydev                 17457  0 
snd_hda_codec_hdmi     31994  1 
snd_hda_codec_realtek   222503  1 
snd_seq_midi           13324  0 
snd_rawmidi            29179  1 snd_seq_midi
snd_hda_intel          33175  3 
snd_hda_codec         110336  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14436  1 snd_seq_midi
snd_seq                60549  2 snd_seq_midi,snd_seq_midi_event
snd_hwdep              13554  1 snd_hda_codec
snd_pcm                92879  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
acer_wmi               27846  0 
shpchp                 37130  0 
snd_timer              28838  2 snd_seq,snd_pcm
snd_seq_device         14129  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     17789  0 
parport                44368  1 lp
edac_core              51499  0 
edac_mce_amd           22882  0 
snd                    64384  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
soundcore              12598  1 snd
sp5100_tco             13697  0 
k10temp                13119  0 
i2c_piix4              13167  0 
uvcvideo               67221  0 
snd_page_alloc         18101  2 snd_hda_intel,snd_pcm
videodev               93508  1 uvcvideo
v4l2_compat_ioctl32    20896  1 videodev
psmouse                72820  0 
sparse_keymap          13526  1 acer_wmi
serio_raw              13211  0 
dm_mirror              21906  0 
dm_region_hash         19667  1 dm_mirror
dm_log                 18215  2 dm_mirror,dm_region_hash
aufs                  183689  0 
tg3                   147905  0 
video                  18858  0 
wmi                    18697  1 acer_wmi

```Please let me know if I can be of any more help.

Thank you in advance!

---

### Post by praseodym on 2012-08-03
Hi,

you need the Broadcom-STA-driver for this device. Remove Ndiswrapper completely.

---

### Post by xblueorbx on 2012-08-03
> **praseodym said:**
> Hi,

you need the Broadcom-STA-driver for this device. Remove Ndiswrapper completely.

Downloaded from Broadcom's website and I get the following error when I use "make":
```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /usr/src/hybrid_wl/built-in.o
  CC [M]  /usr/src/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /usr/src/hybrid_wl/src/wl/sys/wl_linux.o
/usr/src/hybrid_wl/src/wl/sys/wl_linux.c:388: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initializer
/usr/src/hybrid_wl/src/wl/sys/wl_linux.c:388: warning: initialization from incompatible pointer type
make[2]: *** [/usr/src/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/usr/src/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-source-3.2.6'
make: *** [all] Error 2

```Also, already tried this with no luck:
```

apt-get install bcmwl-kernel-source

OUTPUT:

Error! Bad return status for module build on kernel: 3.2.6 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by praseodym on 2012-08-03
You need a patched driver for kernel 3.x, see here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS)

Choose the appropriate one of "gepatchte Version für Kernel 3.x"

Check before:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Vorbereitungen](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Vorbereitungen)

the packages you need to compile and the drivers, that shall be blacklisted

---

### Post by vipulkumar7 on 2012-08-03
I think you need to ask in backtrck forums  :)

---

### Post by xblueorbx on 2012-08-03
> **vipulkumar7 said:**
> I think you need to ask in backtrck forums  :)

Considering that BackTrack is a recompiled version of Ubuntu 10.04, I believe I am posting in the right forums. Enlighten me if you know a little something I don't. 

Praseodym, I'll try that when I get a chance and will report back. Thanks for the help so far.

---

### Post by xblueorbx on 2012-08-03
> **praseodym said:**
> You need a patched driver for kernel 3.x, see here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS)

Choose the appropriate one of "gepatchte Version für Kernel 3.x"

Check before:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Vorbereitungen](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Vorbereitungen)

the packages you need to compile and the drivers, that shall be blacklisted

I tried to follow those instructions after translating the pages but kept getting errors with the linux-headers-generic, I ended up crossing this page [(LINK)]("http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/") when I did a Google search on the error I was getting while trying to compile my drivers.

I downloaded the patch, patched the file, and configured the connection, works perfectly now! Thank you for all your help! Without it I would have never found that page.

---

### Post by fkeri on 2012-12-06
> **xblueorbx said:**
> I tried to follow those instructions after translating the pages but kept getting errors with the linux-headers-generic, I ended up crossing this page [(LINK)]("http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/") when I did a Google search on the error I was getting while trying to compile my drivers.

I downloaded the patch, patched the file, and configured the connection, works perfectly now! Thank you for all your help! Without it I would have never found that page.

Okay, I managed to do this. Big thank you. The wifi indicator LED is on, and I can see some wireless networks in Wicd Network Manager after setting the wireless interface to eth1. Now it can 'see' networks, but how do I make it to 'listen' and inject packages. I am curious to know how to enable the functions embedded in Backtrack R3, because they are not working with this driver.

---

