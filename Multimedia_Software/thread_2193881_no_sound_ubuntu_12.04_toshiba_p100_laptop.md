---
title: "no sound ubuntu 12.04 toshiba p100 laptop"
date: 2013-12-15
forum: Multimedia Software
---

### Post by scottryan80 on 2013-12-15
hi guys, i have recently been playing around with various distros and settled on ubuntu. installed on my laptop (toshiba satellite p100) every thing works perfectly except i cannot get any audio to work. i have opened alsamixerand it is saying the correct audio device but i still cannot get any sound from the laptop. can anyone provide me with a few tips please.
thanks in advance

---

### Post by codenine75a on 2013-12-15
I would try something simple and look at the speaker icon on the "task bar" and look for a little red X in the lower left hand corner.  That means it is on mute and click on it to unmute it.

---

### Post by scottryan80 on 2013-12-15
i tried that and i also checked all channels were unmuted in alsamixer using the terminal. the sound was working with xp but since clean install of ubuntu no sound. is there any way thru the terminal i can select diferent soundcards or codecs?
in alsamixer it is saying intel hd audio device and conexant which is correct, but beside this it also says waikiki?. just wondering if i could go thru and select a toshiba specific driver.
i have ubuntu running on my dell mini netbook and it was just a matter of downloading a proprietary driver to get the audio working , but with the toshiba i cannot find any.

---

### Post by scottryan80 on 2013-12-16
i have just installed ubuntu 12.04 on my toshiba p100 satellite laptop and everything works fine except for the fact i have no sound. i have checked alsa mixer in the terminal and all channels are unmuted and it has the audio device listed as HDA intel conexant cx20551 waikiki. i am not sure if this is the right audio driver. i had a similar problem when i installed ubuntu on my dell mini netbook but all i had to do was download a proprietary driver from realtek and it was sorted. i cant seem to find any proprietary drivers for the toshiba so i was wondering if there is a way to select different codecs/audio device via the terminal?
thanks

---

### Post by scottryan80 on 2013-12-16
scott@scott-Satellite-P100:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20551 (Waikiki)

---

### Post by howefield on 2013-12-16
Threads merged.

---

### Post by scottryan80 on 2013-12-16
```
scott@scott-Satellite-P100:~$ pulseaudio --dump-conf
### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
local-server-type = user
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-1.1/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 8
default-fragment-size-msec = 10
enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
deferred-volume-extra-delay-usec = 0
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000
```

---

### Post by scottryan80 on 2013-12-16
Ive spent the last 12 hours searching this forum and googling like crazy but cant find any solutions. But in the last post on this topic in this forum a user asked for these commands and outputs, then the original poster said his problem was solved but didnt explain how. so sorry for posting more but this audio problem is driving me crazy.
```

scott@scott-Satellite-P100:~$ sudo aplay -l
[sudo] password for scott: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
scott@scott-Satellite-P100:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.8.0-34-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.8.0-34-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.8.0-34-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.8.0-34-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.8.0-34-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/mid-x86/snd-soc-sst-platform.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/mid-x86/snd-soc-mfld-machine.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm5102.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-lm49453.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-sta529.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-alc5632.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm5110.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-arizona.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-isabelle.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-twl6040.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ml26124.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-da732x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-mc13783.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-da9055.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm5100.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ab8500-codec.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max9768.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm0010.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm2200.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm-adsp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-sn95031.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.8.0-34-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.8.0-34-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-cmi8328.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/galaxy/snd-azt2316.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/galaxy/snd-azt1605.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/msnd
/lib/modules/3.8.0-34-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/3.8.0-34-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.8.0-34-generic/kernel/sound/core/snd.ko
/lib/modules/3.8.0-34-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.8.0-34-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.8.0-34-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
``````

scott@scott-Satellite-P100:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```

---

### Post by scottryan80 on 2013-12-19
does anyone know if i should try to edit my dsdt file to get my audio working ?

---

### Post by scottryan80 on 2014-01-01
has anyone had this issue before with this type of soundcard?

---

### Post by scottryan80 on 2014-01-14
I solved the sound issue by downloading latest bios v4.07 and updating. using a windows preinstallation environment disc using bart PE

---

