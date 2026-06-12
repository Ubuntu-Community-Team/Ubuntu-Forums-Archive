---
title: "Touchpad SYNA3602 not working - Kernel 5.8"
date: 2020-11-24
forum: MINT
---

### Post by hage-benoit on 2020-11-24
Hello. 

My touchpad SYNA3602 is not working. No pointer control, no button. 

Here are the info:

inxi -Fxz
```
System:
  Kernel: 5.8.0-29-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Cinnamon 4.6.7 Distro: Linux Mint 20 Ulyana 
  base: Ubuntu 20.04 focal 
Machine:
  Type: Laptop System: CHUWI Innovation And (ShenZhen) product: AeroBook Pro 
  v: N/A serial: <filter> 
  Mobo: CHUWI Innovation And (ShenZhen) model: AeroBook Pro serial: <filter> 
  UEFI: American Megatrends v: ZW-BI-133-X133KR110-KF60B-015-G7 
  date: 07/11/2020 
Battery:
  ID-1: BAT0 charge: 34.2 Wh condition: 38.0/N/A Wh 
  model: Intel SR 1 SR Real Battery status: Discharging 
CPU:
  Topology: Dual Core model: Intel Core m3-8100Y bits: 64 type: MT MCP 
  arch: Amber Lake rev: 9 L2 cache: 4096 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 12799 
  Speed: 600 MHz min/max: 400/3400 MHz Core speeds (MHz): 1: 600 2: 600 
  3: 600 4: 600 
Graphics:
  Device-1: Intel UHD Graphics 615 driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 615 (AML-KBL) v: 4.6 Mesa 20.0.8 
  direct render: Yes 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.8.0-29-generic 
Network:
  Device-1: Intel Wireless 7265 driver: iwlwifi v: kernel port: f040 
  bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 21.52 GiB (9.0%) 
  ID-1: /dev/sda vendor: Morebeck model: N100 256GB size: 238.47 GiB 
Partition:
  ID-1: / size: 115.01 GiB used: 21.44 GiB (18.6%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 4.66 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 40.5 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 207 Uptime: 22m Memory: 7.65 GiB used: 2.84 GiB (37.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
]
```


xinput

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=12    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Keyboard Mouse Consumer Control    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera: USB Camera                  id=10    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=11    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse System Control    id=14    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=15    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=16    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse Consumer Control    id=18    [slave  keyboard (3)]
]

```


ls /sys/bus/i2c/devices/ | grep i2c

```

i2c-0
i2c-1
i2c-2
i2c-3
i2c-4
i2c-5
i2c-6
i2c-7
i2c-8
i2c-SYNA3602:00

```


journalctl | grep i2c

```
Nov 20 13:03:08 Aerobook kernel: i2c /dev entries driver
Nov 20 13:03:08 Aerobook kernel: i2c_hid i2c-SYNA3602:00: i2c-SYNA3602:00 supply vdd not found, using dummy regulator
Nov 20 13:03:08 Aerobook kernel: i2c_hid i2c-SYNA3602:00: i2c-SYNA3602:00 supply vddl not found, using dummy regulator
Nov 20 13:03:08 Aerobook kernel: i2c_hid i2c-SYNA3602:00: weird size of HID descriptor (5)
Nov 20 13:22:30 Aerobook kernel: i2c /dev entries driver
Nov 20 13:22:30 Aerobook kernel: i2c i2c-0: 2/2 memory slots populated (from DMI)
Nov 20 13:22:30 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 20 13:22:30 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 Mouse as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input6
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input7
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input8
Nov 20 13:22:30 Aerobook kernel: hid-generic 0018:0911:5288.0001: input,hidraw0: I2C HID v1.00 Mouse [SYNA3602:00 0911:5288] on i2c-SYNA3602:00
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 Mouse as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input16
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input17
Nov 20 13:22:30 Aerobook kernel: input: SYNA3602:00 0911:5288 UNKNOWN as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-SYNA3602:00/0018:0911:5288.0001/input/input18
Nov 20 13:22:30 Aerobook kernel: hid-multitouch 0018:0911:5288.0001: input,hidraw0: I2C HID v1.00 Mouse [SYNA3602:00 0911:5288] on i2c-SYNA3602:00
Nov 20 16:35:52 Aerobook kernel: i2c /dev entries driver
Nov 20 16:35:52 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 20 16:35:52 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 20 16:35:52 Aerobook kernel: i2c i2c-1: 2/2 memory slots populated (from DMI)
Nov 20 16:35:52 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb usbhid hid_generic i915 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i2c_algo_bit aesni_intel drm_kms_helper crypto_simd syscopyarea sysfillrect i2c_i801 cryptd sysimgblt fb_sys_fops glue_helper i2c_smbus cec rc_core sdhci_pci cqhci ahci drm sdhci libahci xhci_pci xhci_pci_renesas intel_lpss_pci intel_lpss idma64 virt_dma wmi i2c_hid hid pinctrl_sunrisepoint video pinctrl_intel
Nov 20 16:42:01 Aerobook kernel: i2c /dev entries driver
Nov 20 16:42:01 Aerobook kernel: i2c i2c-0: 2/2 memory slots populated (from DMI)
Nov 20 16:42:01 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 20 16:42:01 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 20 16:42:01 Aerobook kernel: i2c_hid i2c-SYNA3602:00: weird size of HID descriptor (2)
Nov 20 16:42:01 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb hid_generic usbhid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect crct10dif_pclmul sysimgblt crc32_pclmul fb_sys_fops cec ghash_clmulni_intel rc_core aesni_intel drm i2c_i801 crypto_simd xhci_pci xhci_pci_renesas intel_lpss_pci sdhci_pci intel_lpss cqhci idma64 i2c_smbus sdhci virt_dma cryptd glue_helper ahci i2c_hid libahci wmi hid pinctrl_sunrisepoint video pinctrl_intel
Nov 20 16:43:29 Aerobook kernel: i2c /dev entries driver
Nov 20 16:43:29 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 20 16:43:29 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 20 16:43:29 Aerobook kernel: i2c i2c-1: 2/2 memory slots populated (from DMI)
Nov 20 16:43:29 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb usbhid hid_generic i915 i2c_algo_bit drm_kms_helper syscopyarea crct10dif_pclmul sysfillrect crc32_pclmul sysimgblt ghash_clmulni_intel fb_sys_fops aesni_intel i2c_i801 cec rc_core crypto_simd cryptd glue_helper drm i2c_smbus ahci xhci_pci xhci_pci_renesas intel_lpss_pci intel_lpss sdhci_pci i2c_hid idma64 cqhci virt_dma libahci sdhci wmi hid video pinctrl_sunrisepoint pinctrl_intel
Nov 21 01:34:19 Aerobook kernel: i2c /dev entries driver
Nov 21 01:34:19 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 21 01:34:19 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 21 01:34:19 Aerobook kernel: i2c i2c-1: 2/2 memory slots populated (from DMI)
Nov 21 01:34:19 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb usbhid hid_generic i915 i2c_algo_bit drm_kms_helper syscopyarea crct10dif_pclmul crc32_pclmul sysfillrect sysimgblt fb_sys_fops cec i2c_i801 ghash_clmulni_intel i2c_smbus aesni_intel sdhci_pci rc_core cqhci xhci_pci ahci drm libahci sdhci intel_lpss_pci intel_lpss idma64 crypto_simd virt_dma xhci_pci_renesas wmi cryptd i2c_hid glue_helper hid video pinctrl_sunrisepoint pinctrl_intel
Nov 22 11:15:35 Aerobook kernel: i2c /dev entries driver
Nov 22 11:15:35 Aerobook kernel: i2c i2c-0: 2/2 memory slots populated (from DMI)
Nov 22 11:15:35 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 22 11:15:35 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 22 11:38:49 Aerobook kernel: i2c /dev entries driver
Nov 22 11:38:49 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 22 11:38:49 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 22 11:38:49 Aerobook kernel: i2c_hid i2c-SYNA3602:00: weird size of HID descriptor (2)
Nov 22 11:38:49 Aerobook kernel: i2c i2c-1: 2/2 memory slots populated (from DMI)
Nov 22 17:59:42 Aerobook kernel: i2c /dev entries driver
Nov 22 17:59:42 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 22 17:59:42 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 22 17:59:42 Aerobook kernel: i2c i2c-0: 2/2 memory slots populated (from DMI)
Nov 22 17:59:42 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb usbhid hid_generic i915 i2c_algo_bit i2c_hid drm_kms_helper syscopyarea crct10dif_pclmul sysfillrect crc32_pclmul sysimgblt fb_sys_fops ghash_clmulni_intel aesni_intel sdhci_pci cqhci crypto_simd i2c_i801 i2c_smbus cec sdhci cryptd glue_helper intel_lpss_pci rc_core intel_lpss ahci idma64 libahci virt_dma drm xhci_pci xhci_pci_renesas hid wmi video pinctrl_sunrisepoint pinctrl_intel
Nov 22 18:03:45 Aerobook kernel: i2c /dev entries driver
Nov 22 18:03:45 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 22 18:03:45 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 22 18:03:45 Aerobook kernel: i2c_hid i2c-SYNA3602:00: weird size of HID descriptor (2)
Nov 22 18:03:45 Aerobook kernel: i2c i2c-1: 2/2 memory slots populated (from DMI)
Nov 22 18:03:45 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb hid_generic usbhid i915 i2c_algo_bit crct10dif_pclmul drm_kms_helper crc32_pclmul syscopyarea sysfillrect sysimgblt ghash_clmulni_intel fb_sys_fops cec rc_core xhci_pci aesni_intel sdhci_pci cqhci i2c_i801 i2c_smbus drm crypto_simd sdhci ahci i2c_hid libahci xhci_pci_renesas intel_lpss_pci cryptd glue_helper intel_lpss idma64 virt_dma wmi hid pinctrl_sunrisepoint video pinctrl_intel
Nov 22 20:18:36 Aerobook kernel: i2c /dev entries driver
Nov 22 20:18:36 Aerobook kernel: i2c i2c-0: 2/2 memory slots populated (from DMI)
Nov 22 20:18:36 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vdd not found, using dummy regulator
Nov 22 20:18:36 Aerobook kernel: i2c_hid i2c-SYNA3602:00: supply vddl not found, using dummy regulator
Nov 22 20:18:36 Aerobook kernel: i2c_hid i2c-SYNA3602:00: weird size of HID descriptor (2)
Nov 22 20:18:36 Aerobook kernel: Modules linked in: rtsx_usb_sdmmc rtsx_usb hid_generic usbhid crct10dif_pclmul crc32_pclmul i915 ghash_clmulni_intel i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops cec rc_core aesni_intel drm crypto_simd cryptd glue_helper i2c_hid hid i2c_i801 xhci_pci i2c_smbus sdhci_pci ahci cqhci libahci intel_lpss_pci xhci_pci_renesas intel_lpss idma64 sdhci virt_dma wmi pinctrl_sunrisepoint video pinctrl_intel

```


So far I've found this website: [https://forum.manjaro.org/t/syna3602-touchpad-not-working-at-all/3108/11](https://forum.manjaro.org/t/syna3602-touchpad-not-working-at-all/3108/11) , but the similarities of the bug stops when I have to enter these two commands: they don't do anything. 

```

sudo rmmod i2c_hid sudo modprobe i2c_hid

```

I've report the bug on bugzilla: 
[https://bugzilla.kernel.org/show_bug.cgi?id=210311](https://bugzilla.kernel.org/show_bug.cgi?id=210311) , but if anyone 
manage to get the touchpad working, I would be very intrested on that 
solution. 

Many thanks in advance.[URL="https://forum.manjaro.org/t/syna3602-touchpad-not-working-at-all/3108/11"]

[/URL]

---

### Post by coffeecat on 2020-11-24
*Thread moved to **Linux Mint** sub-forum*

---

### Post by hage-benoit on 2020-11-27
Bump?

---

