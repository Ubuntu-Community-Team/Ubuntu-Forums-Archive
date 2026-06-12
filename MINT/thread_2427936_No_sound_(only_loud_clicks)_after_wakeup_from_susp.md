---
title: "No sound (only loud clicks) after wakeup from suspend"
date: 2019-09-27
forum: MINT
---

### Post by sakralbar on 2019-09-27
Hello!

I have linux mint 19.2 (based on ubuntu 18.04). After exiting sleep mode (suspend), the sound stops working. I hear loud clicks in the speakers. In Pavucontrol, [I see that the system is playing a sound]("https://downloader.disk.yandex.ru/preview/d5280ea0f835374e28b6ef8d45527fad9ab6b250b0a32b0d65295128253b48b5/5d8e46af/Y9yQUl146zYwixu9r-a7aNZTMchzuFEcam34r7uQRcX7pQLnKW5FFR1EE-e3YyD0N29kMDFY11qVTb1tyMZ8Tw%3D%3D?uid=0&filename=2019-09-27_08-23_1.png&disposition=inline&hash=&limit=0&content_type=image%2Fpng&owner_uid=0&tknv=v2&size=1920x941"), but I can not hear it.
Switching output devices does nothing. System kernel updates too.

Only after several "sudo alsa force-reload" or "pulseaudio -k" the sound starts to work (for example, in the browser). But system sounds do not work.
Otherwise, the sound appears after a reboot, sometimes only after two reboots.

```

lspci -nnk | grep -A2 Audio
05:00.1 Audio device [0403]: NVIDIA Corporation GP108 High Definition Audio Controller [10de:0fb8] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd GP108 High Definition Audio Controller [1458:375c]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
06:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e3]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:a182]
    Kernel driver in use: snd_hda_intel

```

alsa-base.conf
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Added by me
options snd-hda-intel power_save=0 power_save_controller=N
#options snd-hda-intel model=auto
#options snd-hda-intel probe_mask=1
```

My computer contains an AB350M-DS3H-V2 motherboard and an AMD Ryzen 3 3200G processor. Kernel 4.15.0-64-generic.

What can I do to make the sound work again after the standby mode?

---

### Post by Irihapeti on 2019-09-27
*Thread moved to **MINT** subforum.*

---

