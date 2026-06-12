---
title: "No sound in ACER 4930 Laptop"
date: 2011-04-09
forum: Multimedia Software
---

### Post by jayzee on 2011-04-09
There is no sound in my acer[COLOR=Red] 4930 laptop using [COLOR=Black]the ubunttu 10.10.[/COLOR][/COLOR] but the sound was properly working in the previous version 10.04. please give me the step by step instructions. 

thanks in advance:confused::confused::oops:

---

### Post by jayzee on 2011-04-09
Help me please if any one is looking this thread

---

### Post by jayzee on 2011-04-09
i run this command and get the following output


**[SIZE=4]wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh[/SIZE]**



Link provided was [COLOR=Red]http://www.alsa-project.org/db/?f=d92ba30937f7514112e1d7bfb96e77efbeca31ac
[/COLOR] 




!!################################ !!ALSA Information Script v 0.4.60 !!################################  !!Script ran on: Sat Apr  9 06:53:24 UTC 2011   !!Linux Distribution !!------------------  Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"   !!DMI Information !!---------------  Manufacturer:      Acer       Product Name:      Aspire 4930      Product Version:   V1.15   !!Kernel Information !!------------------  Kernel release:    2.6.35-22-generic Operating System:  GNU/Linux Architecture:      i686 Processor:         unknown SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:     1.0.23 Library version:    1.0.23 Utilities version:  1.0.23   !!Loaded ALSA modules !!-------------------    !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------  --- no soundcards ---   !!PCI Soundcards installed in the system !!--------------------------------------  00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)   !!Advanced information - PCI Vendor/Device/Subsystem ID's !!--------------------------------------------------------  00:1b.0 0403: 8086:293e (rev 03) 	Subsystem: 1025:013e   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-caiaq: index=-2 snd-usb-ua101: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-usb-audio: index=-2 snd-hda-intel: model=auto snd-hda-intel: model=acer-aspire-4930g snd-hda-intel: model=acer-aspire-4930g   !!Loaded sound module options !!--------------------------   !!ALSA Device nodes !!-----------------  crw-rw----  1 root audio 116, 3 Apr  9 11:32 /dev/snd/seq crw-rw----  1 root audio 116, 2 Apr  9 11:32 /dev/snd/timer   !!Aplay/Arecord output !!------------  APLAY  aplay: device_list:235: no soundcards found...  ARECORD  arecord: device_list:235: no soundcards found...  !!Amixer output !!-------------   !!Alsactl output !!-------------  --startcollapse-- --endcollapse--   !!All Loaded Modules !!------------------  Module parport_pc ppdev binfmt_misc arc4 snd_hwdep snd_pcm snd_seq_midi iwlagn snd_rawmidi i915 snd_seq_midi_event snd_seq drm_kms_helper snd_timer snd_seq_device iwlcore mac80211 uvcvideo drm videodev v4l1_compat joydev snd intel_agp jmb38x_ms psmouse soundcore serio_raw snd_page_alloc cfg80211 i2c_algo_bit agpgart memstick video output lirc_ene0100 lirc_dev lp parport usbhid hid r8169 sdhci_pci mii sdhci led_class   !!ALSA/HDA dmesg !!------------------  [   16.846146] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000 [   16.920720] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master [   16.920726] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master (err -22) [   16.921506] snd_hda_codec: disagrees about version of symbol snd_device_new [   16.921508] snd_hda_codec: Unknown symbol snd_device_new (err -22) [   16.921661] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave [   16.921663] snd_hda_codec: Unknown symbol _snd_ctl_add_slave (err -22) [   16.921892] snd_hda_codec: disagrees about version of symbol snd_pci_quirk_lookup [   16.921895] snd_hda_codec: Unknown symbol snd_pci_quirk_lookup (err -22) [   16.922066] snd_hda_codec: disagrees about version of symbol snd_device_free [   16.922068] snd_hda_codec: Unknown symbol snd_device_free (err -22) [   16.922157] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step [   16.922159] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step (err -22) [   16.961442] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12

---

### Post by lidex on 2011-04-10
Try this to update kernel (using a Terminal="Applications->Accessories->Terminal"):
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot** and post this terminal output:
```
uname -a
```

---

