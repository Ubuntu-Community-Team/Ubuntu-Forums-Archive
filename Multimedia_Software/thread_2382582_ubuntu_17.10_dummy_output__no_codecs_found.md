---
title: "ubuntu 17.10: dummy output / no codecs found"
date: 2018-01-15
forum: Multimedia Software
---

### Post by skraynev on 2018-01-15
Hi all.
 I recently upgraded from 16.04 to 17.10 and figured out, that I lost audio.
I can use USB headphones (it works well), but when I try to use front/back side jack I can't hear anything.
Moreover in audio settings I see only **Dummy Output** device.

Note, that previously (in 16.04) all outputs worked without any issues.

When I do: ```
sudo alsa force-reload
``` 
It constantly returns: ```
snd_hda_intel 0000:00:1f.3: no codecs found!
```

More information is available below:

```
upload=true&script=true&cardinfo=!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Mon Jan 15 13:58:14 UTC 2018




!!Linux Distribution
!!------------------


Ubuntu 17.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 17.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 17.10" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=artful




!!DMI Information
!!---------------


Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      B150M-DS3H
Product Version:   Default string
Firmware Version:  F20
Board Vendor:      Gigabyte Technology Co., Ltd.
Board Name:        B150M-DS3H-CF




!!ACPI Device Status Information
!!---------------


/sys/bus/acpi/devices/ACPI000C:00/status      15
/sys/bus/acpi/devices/INT33A1:00/status      15
/sys/bus/acpi/devices/INT340E:00/status      15
/sys/bus/acpi/devices/INT3F0D:00/status      15
/sys/bus/acpi/devices/LNXPOWER:00/status      1
/sys/bus/acpi/devices/LNXPOWER:01/status      1
/sys/bus/acpi/devices/LNXPOWER:02/status      1
/sys/bus/acpi/devices/LNXPOWER:03/status      1
/sys/bus/acpi/devices/LNXPOWER:04/status      1
/sys/bus/acpi/devices/LNXPOWER:05/status      1
/sys/bus/acpi/devices/LNXPOWER:06/status      1
/sys/bus/acpi/devices/LNXPOWER:07/status      1
/sys/bus/acpi/devices/LNXPOWER:08/status      1
/sys/bus/acpi/devices/LNXPOWER:09/status      1
/sys/bus/acpi/devices/LNXPOWER:0a/status      1
/sys/bus/acpi/devices/LNXPOWER:0b/status      1
/sys/bus/acpi/devices/LNXPOWER:0c/status      1
/sys/bus/acpi/devices/LNXPOWER:0d/status      1
/sys/bus/acpi/devices/LNXPOWER:0e/status      1
/sys/bus/acpi/devices/LNXPOWER:0f/status      1
/sys/bus/acpi/devices/LNXPOWER:10/status      1
/sys/bus/acpi/devices/LNXPOWER:11/status      1
/sys/bus/acpi/devices/LNXPOWER:12/status      1
/sys/bus/acpi/devices/LNXPOWER:13/status      1
/sys/bus/acpi/devices/LNXPOWER:14/status      1
/sys/bus/acpi/devices/LNXPOWER:15/status      1
/sys/bus/acpi/devices/LNXPOWER:16/status      1
/sys/bus/acpi/devices/PNP0103:00/status      15
/sys/bus/acpi/devices/PNP0400:00/status      15
/sys/bus/acpi/devices/PNP0501:00/status      15
/sys/bus/acpi/devices/PNP0C02:02/status      15
/sys/bus/acpi/devices/PNP0C02:04/status      3
/sys/bus/acpi/devices/PNP0C02:06/status      3
/sys/bus/acpi/devices/PNP0C04:00/status      31
/sys/bus/acpi/devices/PNP0C0C:00/status      15
/sys/bus/acpi/devices/PNP0C0E:00/status      11
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9
/sys/bus/acpi/devices/device:69/status      15
/sys/bus/acpi/devices/device:75/status      11




!!Kernel Information
!!------------------


Kernel release:    4.13.0-29-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k4.13.0-29-generic
Library version:    1.1.3
Utilities version:  1.1.3




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No




!!Soundcards recognised by ALSA
!!-----------------------------


--- no soundcards ---




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1f.3 0403: 8086:a170 (rev 31)
    Subsystem: 1458:a182




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=0




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  1 Jan 15 16:54 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 15 16:54 /dev/snd/timer




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:270: no soundcards found...


ARECORD


arecord: device_list:270: no soundcards found...


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
ipt_MASQUERADE
nf_nat_masquerade_ipv4
xfrm_user
xfrm_algo
iptable_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_nat_ipv4
xt_addrtype
iptable_filter
xt_conntrack
nf_nat
nf_conntrack
libcrc32c
br_netfilter
bridge
stp
llc
bnep
aufs
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
snd_seq_midi
snd_seq_midi_event
joydev
input_leds
snd_rawmidi
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
kvm
snd_seq
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
pcbc
snd_seq_device
snd_timer
aesni_intel
aes_x86_64
crypto_simd
glue_helper
cryptd
snd
intel_cstate
intel_rapl_perf
soundcore
shpchp
mei_me
mei
hci_uart
btbcm
serdev
btqca
btintel
bluetooth
ecdh_generic
acpi_als
mac_hid
intel_lpss_acpi
intel_lpss
kfifo_buf
industrialio
tpm_infineon
acpi_pad
cuse
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
hid_generic
usbhid
i915
i2c_algo_bit
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
r8169
fb_sys_fops
mii
drm
ahci
libahci
wmi
video
pinctrl_sunrisepoint
pinctrl_intel
i2c_hid
hid




!!ALSA/HDA dmesg
!!--------------


[    2.536736] intel_rapl: Found RAPL domain dram
[    2.590430] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    2.706932] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[    2.708013] snd_hda_intel 0000:00:1f.3: no codecs found!
[    2.713901] WARN_ON(crtc->config->scaler_state.scaler_id < 0)
--
[    2.713957] WARNING: CPU: 0 PID: 314 at /build/linux-UasLRx/linux-4.13.0/drivers/gpu/drm/i915/intel_display.c:4755 skylake_pfit_enable+0xe6/0xf0 [i915]
[    2.713957] Modules linked in: snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event joydev input_leds snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_seq irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd snd intel_cstate intel_rapl_perf soundcore shpchp mei_me mei hci_uart btbcm serdev btqca btintel bluetooth ecdh_generic acpi_als mac_hid intel_lpss_acpi intel_lpss kfifo_buf industrialio tpm_infineon acpi_pad cuse parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt r8169 fb_sys_fops mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel
[    2.713986]  i2c_hid hid
--
[    2.746263] WARNING: CPU: 0 PID: 314 at /build/linux-UasLRx/linux-4.13.0/drivers/gpu/drm/i915/intel_display.c:12277 intel_atomic_commit_tail+0xdb1/0xf90 [i915]
[    2.746263] Modules linked in: snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event joydev input_leds snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_seq irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd snd intel_cstate intel_rapl_perf soundcore shpchp mei_me mei hci_uart btbcm serdev btqca btintel bluetooth ecdh_generic acpi_als mac_hid intel_lpss_acpi intel_lpss kfifo_buf industrialio tpm_infineon acpi_pad cuse parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt r8169 fb_sys_fops mii drm ahci libahci wmi video pinctrl_sunrisepoint pinctrl_intel
[    2.746291]  i2c_hid hid



```

Could you please help me to fix this annoying issue.

---

### Post by VMC on 2018-01-15
What does ```
alsamixer
``` show? Any muted devices?

---

### Post by Yellow Pasque on 2018-01-15
```
snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
snd_hda_intel 0000:00:1f.3: no codecs found!
```

I have seen this trick work for that issue:
Go into the BIOS/EFI, and disable the "Audio Controller" (under "Chipset" menu). Save the changes and reboot. Then, go back into BIOS and set Audio Controller back to Enabled. Save and reboot.

Side note: I would consider updating the BIOS, because it includes security fixes.

> **VMC said:**
> What does alsamixer show? Any muted devices?

You can see the alsamixer values in the OP's alsa information. There is nothing there (it's blank) because the codec was not even found/probed. In other words, the problem is at a deeper level than mixer settings.

---

### Post by skraynev on 2018-01-16
> **Temüjin said:**
> 
I have seen this trick work for that issue:
Go into the BIOS/EFI, and disable the "Audio Controller" (under "Chipset" menu). Save the changes and reboot. Then, go back into BIOS and set Audio Controller back to Enabled. Save and reboot.

Side note: I would consider updating the BIOS, because it includes security fixes.



Thank you for the advise. Unfortunately simple disable/enable option "Audio Controller" did not help me. I tried it several times, but the issue is still there.

Regarding updating BIOS, I will do it later and post result here.

---

### Post by skraynev on 2018-01-17
> **Temüjin said:**
> 
Side note: I would consider updating the BIOS, because it includes security fixes.


Finally, BIOS update helped me. Now all devices connected via jack work fine.
Thank you very much for the help!

---

