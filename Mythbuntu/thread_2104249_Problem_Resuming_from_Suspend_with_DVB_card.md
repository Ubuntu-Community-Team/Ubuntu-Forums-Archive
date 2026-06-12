---
title: "Problem Resuming from Suspend with DVB card"
date: 2013-01-12
forum: Mythbuntu
---

### Post by os2 on 2013-01-12
I'm running MythBU 12.04.

I have a problem resuming my system from Suspend mode when the DVB card is plugged into the USB port.

What is the latest/best solution to this available now to solve this problem?

On another Linux system I would run modprobe -r and rmmod -f to switch the device off and put the script into /etc/pm/sleed.d. Except on MythBU I can't seem to get a handle on the device through modprobe -r or rmmod.

What is the latest/best solution now?

Thanks

---

### Post by Toz on 2013-01-12
What is the name of the module? **lsmod** might help identify it.

Once identified, create a file called **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="<module>"
```
...replace <module> with the actual name of the module.

On suspend, pm-utils will then automatically unload that module and reload on resume.

Log file is found at: /var/log/pm-suspend.log

---

### Post by os2 on 2013-01-12
I put this in /etc/pm/sleep.d/modules as you suggested:

> SUSPEND_MODULES="tm6000_dvb"
SUSPEND_MODULES="tm6000_alsa"
SUSPEND_MODULES="tm6000"

The module/tuner is tm6000.

It doesn't work I'm afraid..

---

### Post by Toz on 2013-01-12
It should read:
```
SUSPEND_MODULES="tm6000_dvb tm6000_alsa tm6000"
```
Also review the log file (/var/log/pm-suspend.log) to see if it says anything about it.

---

### Post by os2 on 2013-01-12
It still didn't work because tm6000_alsa was reported to still being in use. 

> 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module tm6000_dvb...Done.
[COLOR=Red]Unloading kernel module tm6000_alsa...FATAL: Module tm6000_alsa is in use.[/COLOR]
/usr/lib/pm-utils/sleep.d/75modules: 89: /usr/lib/pm-utils/sleep.d/75modules: log: not found
Failed.
[COLOR=Red]Unloading kernel module tm6000...FATAL: Module tm6000_alsa is in use.[/COLOR]
/usr/lib/pm-utils/sleep.d/75modules: 89: /usr/lib/pm-utils/sleep.d/75modules: log: not found
Failed.


How can I unhook this tm6000_alsa module? I was able to do it in Ubuntu 12.10 with rmmod -f. This is MU 12.04.


Here is the module list from PM-suspend.log:

> 
UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
lirc_dev               19166  0 
tpm_infineon           17536  0 
snd_hda_codec_analog    97987  1 
pata_pcmcia            17074  1 
zl10353                17835  0 
dvb_core              105885  0 
[COLOR=Red]tm6000_alsa            13581  1 [/COLOR]
rc_hauppauge           12532  0 
tuner_xc2028           31226  1 
tuner                  27415  1 
arc4                   12529  2 
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_pcm                97275  3 tm6000_alsa,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
pcmcia                 49353  1 pata_pcmcia
[COLOR=Red]tm6000                 71578  1 tm6000_alsa[/COLOR]
v4l2_common            21560  2 tuner,tm6000
videodev              134125  3 tuner,tm6000,v4l2_common
media                  21344  1 videodev
videobuf_vmalloc       13589  1 tm6000
iwl4965               127946  0 
[COLOR=Red]videobuf_core          26022  2 tm6000,videobuf_vmalloc[/COLOR]
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
[COLOR=Red]rc_core                26273  3 rc_hauppauge,tm6000[/COLOR]
iwl_legacy             83098  1 iwl4965
mac80211              506862  2 iwl4965,iwl_legacy
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
snd_timer              29990  2 snd_pcm,snd_seq
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                97485  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
snd                    79041  18 [COLOR=Red]snd_hda_codec_analog,tm6000_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/COLOR]
cfg80211              205774  3 iwl4965,iwl_legacy,mac80211
irda                  201324  0 
btusb                  18332  0 
bluetooth             180153  1 btusb
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
crc_ccitt              12707  1 irda
parport_pc             32866  1 
i915                  477545  2 
tpm_tis                18804  0 
drm_kms_helper         46978  1 i915
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
mei                    41616  0 
drm                   241971  3 i915,drm_kms_helper
input_polldev          13896  1 lis3lv02d
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
uas                    18180  0 
usb_storage            49198  0 
firewire_ohci          41000  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                156715  0 


---

### Post by Toz on 2013-01-12
Try changing the order:
```
SUSPEND_MODULES="tm6000_dvb tm6000 tm6000_alsa"
```

Also, this is not right:
> /usr/lib/pm-utils/sleep.d/75modules: 89: /usr/lib/pm-utils/sleep.d/75modules: log: not found
Failed. 

Can you post back the contents of /usr/lib/pm-utils/sleep.d/75modules and /etc/pm/config.d/modules?

---

### Post by os2 on 2013-01-12
> **Toz said:**
> Try changing the order:
```
SUSPEND_MODULES="tm6000_dvb tm6000 tm6000_alsa"
```Also, this is not right:


Can you post back the contents of /usr/lib/pm-utils/sleep.d/75modules and /etc/pm/config.d/modules?


I'll give it a go but I don't think it will work. Usually I unload tm6000 last as it's the actual tuner module from the software firmware. The reason for this is other modules are dependent on tm6000, such as tm6000_dvb or tm6000_alsa.

This is /usr/lib/pm-utils/sleep.d/75modules:

> #!/bin/sh
# Unload requested modules.

. "${PM_FUNCTIONS}"

suspend_modules()
{
    [ -z "$SUSPEND_MODULES" ] && return $NA
    for x in $SUSPEND_MODULES ; do
            printf "Unloading kernel module %s..." "$x"
        modunload $x && echo Done. || echo Failed.
    done
    return 0
}

resume_modules()
{
    modreload
    echo "Reloaded unloaded modules."
}

case "$1" in
    hibernate|suspend)
        suspend_modules
        ;;
    thaw|resume)
        resume_modules
        ;;
    *) exit $NA
        ;;
esac


---

### Post by Toz on 2013-01-12
> On another Linux system I would run modprobe -r and rmmod -f to switch the device off and put the script into /etc/pm/sleed.d. Except on MythBU I can't seem to get a handle on the device through modprobe -r or rmmod.

This may be relevant. From **man rmmod**:
```
-f --force
                 This option can be extremely  dangerous:  it  has  no  effect
                 unless CONFIG_MODULE_FORCE_UNLOAD was set when the kernel was
                 compiled.  With this option, you can remove modules which are
                 being  used, or which are not designed to be removed, or have
                 been marked as unsafe (see lsmod(8)).

```

So lets check if CONFIG_MODULE_FORCE_UNLOAD is set in the kernel:
```

cat /boot/config-$(uname -r) | grep CONFIG_MODULE_FORCE_UNLOAD
# CONFIG_MODULE_FORCE_UNLOAD is not set
```
...is not set on my kernel (3.5.0-21).

You may need a custom kernel build.

---

### Post by os2 on 2013-01-12
Having changed the order of the modules in /etc/pm/config.d/modules it still has not worked.

This is PM-suspend.log:

> 
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
[COLOR=Lime]Unloading kernel module tm6000_dvb...Done.[/COLOR]
[COLOR=Red]Unloading kernel module tm6000...FATAL: Module tm6000_alsa is in use.[/COLOR]
/usr/lib/pm-utils/sleep.d/75modules: 89: /usr/lib/pm-utils/sleep.d/75modules: log: not found
Failed.
[COLOR=Red]Unloading kernel module tm6000_alsa...FATAL: Module tm6000_alsa is in use.[/COLOR]
/usr/lib/pm-utils/sleep.d/75modules: 89: /usr/lib/pm-utils/sleep.d/75modules: log: not found
Failed.


I can unload tm6000_dvb by hand with rmmod -f tm6000_dvb. But not tm6000_alsa.
How can I find out the dependencies on tm6000_alsa?

---

### Post by Toz on 2013-01-12
> How can I find out the dependencies on tm6000_alsa?
```
$ modinfo tm6000_alsa
filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/media/video/tm6000/tm6000-alsa.ko
license:        GPL
author:         Mauro Carvalho Chehab <mchehab@redhat.com>
description:    ALSA driver module for tm5600/tm6000/tm6010 based TV cards
srcversion:     4DE7ED5B92156EAEE8BC195
[COLOR="Red"]depends:        snd-pcm,tm6000,snd[/COLOR]
intree:         Y
vermagic:       3.5.0-21-generic SMP mod_unload modversions 
parm:           enable:Enable tm6000x soundcard. default enabled. (array of bool)
parm:           index:Index value for tm6000x capture interface(s). (array of int)
parm:           debug:enable debug messages (int)

```

---

### Post by os2 on 2013-01-12
> 
So lets check if CONFIG_MODULE_FORCE_UNLOAD is set in the kernel:
```

cat /boot/config-$(uname -r) | grep CONFIG_MODULE_FORCE_UNLOAD
# CONFIG_MODULE_FORCE_UNLOAD is not set
```...is not set on my kernel (3.5.0-21).

You may need a custom kernel build.

It's not set on mine either kernel 3.2.0-35.

> CONFIG_MODULE_FORCE_UNLOAD is not set

Kernel 3.4+ allows me to use the -f option in rmmod, and often with a complete lock-up if the tuner-device is busy.

---

### Post by os2 on 2013-01-12
> **Toz said:**
> ```
$ modinfo tm6000_alsa
filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/media/video/tm6000/tm6000-alsa.ko
license:        GPL
author:         Mauro Carvalho Chehab <mchehab@redhat.com>
description:    ALSA driver module for tm5600/tm6000/tm6010 based TV cards
srcversion:     4DE7ED5B92156EAEE8BC195
[COLOR=Red]depends:        snd-pcm,tm6000,snd[/COLOR]
intree:         Y
vermagic:       3.5.0-21-generic SMP mod_unload modversions 
parm:           enable:Enable tm6000x soundcard. default enabled. (array of bool)
parm:           index:Index value for tm6000x capture interface(s). (array of int)
parm:           debug:enable debug messages (int)

```

I'm unable to disable snd-pcm and snd modules by hand either.

I'm going to try and update the kernel to at least 3.4 and see if it works.

---

