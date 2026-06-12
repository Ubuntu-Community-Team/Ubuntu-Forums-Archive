---
title: "Toshiba NB520 wireless enable/disable"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by nicks27 on 2011-07-15
The Fn+F8 keystroke won't enable/disable wireless on my Toshiba NB520 (running Xubuntu 11.04 desktop). Other Fn+FX keystrokes (display contrast, audio volume up/down/mute) are working ok.

The only way I have found to disable it is to blacklist the **ath9k** kernel module. This appears to disable the on-board wireless (although the LED indicator stays on so I'm not convinced). I use an external removable USB wireless adapter to avoid rebooting every time I need to enable/disable wireless.

The machine's BIOS is updated to the latest v1.90. There is only one setting to enable/disable all networking including wired, nothing to specifically enable/disable on-board wireless (but in any case this would require rebooting each time which is inconvenient).

Following the information at [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver) , attempting to load the **toshiba_acpi** kernel module results in an error:
```
~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.38-10-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device

```

Attempting to load the **omnibook** kernel module adds a /proc/omnibook but it is empty. (the machine's startup screen shows a "Phoenix" logo in the bottom-left, which presumably means it's a Phoenix BIOS rather than a Toshiba BIOS).

So my questions are:
1) Has blacklisting the **ath9k** kernel module fully disabled the wireless hardware (despite the LED remaining on)?
2) Is it a bug that the **toshiba_acpi** and **omnibook** kernel modules don't work with this hardware?
 3) Can normal Fn+F8 enabling/disabling (or some other solution not requiring a reboot) be achieved, and how?

Thanks.

---

### Post by chili555 on 2011-07-15
> Has blacklisting the ath9k kernel module fully disabled the wireless hardware (despite the LED remaining on)?If you mean, has it turned the wireless radio off, then no.> Is it a bug that the toshiba_acpi and omnibook kernel modules don't work with this hardware?I don't know yet. We shall investigate more.> Can normal Fn+F8 enabling/disabling (or some other solution not requiring a reboot) be achieved, and how?Probably; again, we need to investigate more. 

Why do you want to disable the wireless, simply because you don't want or need it full time and to save battery power? If we could find another way, would you use the Atheros internal? Please open a terminal and run and post:```
lsmod
rfkill list all
```We shall look for the flaw that doesn't operate the Fn+F8 keys.

---

### Post by nicks27 on 2011-07-20
Thanks for those answers.
In answer to your question, it's a combination of saving battery power and being able to otherwise use the machine in places like hospitals where wireless isn't allowed. I would use the Atheros internal if I could easily (i.e. without rebooting) enable/disable it as needed. 

Here are the results from the two commands you asked me to run:

```

$ **lsmod**
Module                  Size  Used by
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  3 bnep
parport_pc             32111  0 
ppdev                  12849  0 
btusb                  18160  1 
bluetooth              65493  8 sco,bnep,l2cap,btusb
joydev                 17322  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  450934  2 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
snd                    55295  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
drm                   180037  3 i915,drm_kms_helper
soundcore              12600  1 snd
sparse_keymap          13666  0 
lp                     13349  0 
toshiba_bluetooth      12711  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  6 
libahci                25548  1 ahci
r8169                  42534  0 

$ **rfkill list all**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by chili555 on 2011-07-20
The module *omnibook* has several parameters we can try:> $ modinfo omnibook
filename:       /lib/modules/2.6.38-10-generic/kernel/ubuntu/omnibook/omnibook.ko
license:        GPL
description:    Kernel interface for HP OmniBook, HP Pavilion, Toshiba Satellite and Compal ACL00 laptops
version:        2.20090707-trunk
author:         Soós Péter, Mathieu Bérard
srcversion:     302E1ECA1E6B00F304E6876
depends:        
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           throttle:Use 0 to disable, 1 to enable CPU throttling control (int)
parm:           wifi:Use 0 to disable, 1 to enable Wifi adapter control (int)
parm:           touchpad:Use 0 to disable, 1 to enable touchpad handling (int)
parm:           temperature:Use 0 to disable, 1 to enable thermal status and policy support (int)
parm:           key_polling:Use 0 to disable, 1 to enable key polling (int)
parm:           muteled:Use 0 to disable, 1 to enable 'Audo Mute' LED control (int)
parm:           lcd:Use 0 to disable, 1 to enable to LCD brightness support (int)
parm:           dmi:Use 0 to disable, 1 to enable DMI informations display support (int)
parm:           hotkeys:Use 0 to disable, 1 to enable hotkeys handling (int)
parm:           fan_policy:Use 0 to disable, 1 to enable fan control policy support (int)
parm:           fan:Use 0 to disable, 1 to enable fan status monitor and control (int)
parm:           dump:Use 0 to disable, 1 to enable embedded controller register dump support (int)
parm:           dock:Use 0 to disable, 1 to enable docking station support (int)
parm:           display:Use 0 to disable, 1 to enable display status handling (int)
parm:           cooling:Use 0 to disable, 1 to enable CPU cooling method control (int)
parm:           bluetooth:Use 0 to disable, 1 to enable bluetooth adapter control (int)
parm:           blank:Use 0 to disable, 1 to enable lcd console blanking (int)
parm:           battery:Use 0 to disable, 1 to enable battery status monitoring (int)
parm:           ac:Use 0 to disable, 1 to enable AC adapter status monitoring (int)
parm:           ectype:Type of embedded controller firmware
parm:           userset:Use 0 to disable, 1 to enable users to set parameters (int)
Let's try one:```
sudo modprobe mnibook hotkeys=1
```Now does Fn+F8 work? When you manipulate the key combination, is there any recognition here?```
sudo tail -f /var/log/syslog
```Close tail syslog with Ctrl+c. If this works, we can write a short file and make it permanent.

---

### Post by nicks27 on 2011-07-22
OK, I tried  [FONT=Courier New]sudo modprobe omnibook hotkeys=1[/FONT]   and I got a black & white screen with system messages. I recovered back to the desktop with ALT+CTRL+F7 and tried the Fn+F8 combination but it gave no response. Here's the relevant section of /var/log/syslog :

```

Jul 22 21:17:15 kinito kernel: [ 2066.505604] omnibook: Driver version 2.20090707-trunk.
Jul 22 21:17:15 kinito kernel: [ 2066.505745] omnibook: Unknown model.
Jul 22 21:17:15 kinito kernel: [ 2066.506886] BUG: unable to handle kernel paging request at 00008800
Jul 22 21:17:15 kinito kernel: [ 2066.507200] IP: [<00008800>] 0x8800
Jul 22 21:17:15 kinito kernel: [ 2066.507388] *pde = 2bc9a067 *pte = 00000000 
Jul 22 21:17:15 kinito kernel: [ 2066.507600] Oops: 0000 [#1] SMP 
Jul 22 21:17:15 kinito kernel: [ 2066.507763] last sysfs file: /sys/devices/platform/omnibook/uevent
Jul 22 21:17:15 kinito kernel: [ 2066.508015] Modules linked in: omnibook(+) arc4 rtl8187 mac80211 cfg80211 eeprom_93cx6 sco bnep l2cap parport_pc ppdev btusb bluetooth joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi i915 snd_seq_midi_event snd_seq drm_kms_helper snd_timer drm uvcvideo snd_seq_device snd i2c_algo_bit videodev video sparse_keymap soundcore toshiba_bluetooth psmouse snd_page_alloc serio_raw lp parport usb_storage uas ahci libahci r8169
Jul 22 21:17:15 kinito kernel: [ 2066.510027] 
Jul 22 21:17:15 kinito kernel: [ 2066.510087] Pid: 1966, comm: modprobe Not tainted 2.6.38-10-generic #46-Ubuntu TOSHIBA TOSHIBA NB520/PBU00
Jul 22 21:17:15 kinito kernel: [ 2066.510242] EIP: 0060:[<00008800>] EFLAGS: 00210206 CPU: 0
Jul 22 21:17:15 kinito kernel: [ 2066.510242] EIP is at 0x8800
Jul 22 21:17:15 kinito kernel: [ 2066.510242] EAX: 00000000 EBX: f86e2784 ECX: 00000000 EDX: 00008800
Jul 22 21:17:15 kinito kernel: [ 2066.510242] ESI: 00000000 EDI: ffffffea EBP: dd04fe30 ESP: dd04fe14
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul 22 21:17:15 kinito kernel: [ 2066.510242] Process modprobe (pid: 1966, ti=dd04e000 task=f4cfa5e0 task.ti=dd04e000)
Jul 22 21:17:15 kinito kernel: [ 2066.510242] Stack:
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  f915e0de 00000034 00000040 000080d0 00000104 00000005 13b13b2a dd04fe4c
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  f915e277 c11850c7 00000001 ebe84e08 f86e2014 f86e2014 dd04fe54 c1335631
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  dd04fe78 c133440d ebe84e64 00000000 dd04fe78 c133c67b ebe84e08 ffffffed
Jul 22 21:17:15 kinito kernel: [ 2066.510242] Call Trace:
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<f915e0de>] ? omnibook_init+0xa0/0x178 [omnibook]
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<f915e277>] omnibook_probe+0xc1/0x122 [omnibook]
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c11850c7>] ? sysfs_create_link+0x17/0x20
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1335631>] platform_drv_probe+0x11/0x20
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c133440d>] really_probe+0x4d/0x150
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c133c67b>] ? pm_runtime_barrier+0x4b/0xb0
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c13346ac>] driver_probe_device+0x3c/0x60
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c13347a9>] __device_attach+0x49/0x60
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1334760>] ? __device_attach+0x0/0x60
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c133353f>] bus_for_each_drv+0x4f/0x70
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c13345ca>] device_attach+0x7a/0x90
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1334760>] ? __device_attach+0x0/0x60
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1333d85>] bus_probe_device+0x25/0x40
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1331f4c>] device_add+0x28c/0x380
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c127d033>] ? kvasprintf+0x43/0x60
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1273504>] ? kobject_set_name_vargs+0x64/0x70
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1335ea7>] platform_device_add+0xe7/0x1a0
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1336094>] ? platform_device_alloc+0x54/0x70
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<f915e3e1>] omnibook_module_init+0xdd/0xfe [omnibook]
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1001255>] do_one_initcall+0x35/0x170
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<f915e304>] ? omnibook_module_init+0x0/0xfe [omnibook]
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1088afb>] sys_init_module+0xdb/0x230
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c1125aa5>] ? sys_close+0x75/0xd0
Jul 22 21:17:15 kinito kernel: [ 2066.510242]  [<c150a194>] syscall_call+0x7/0xb
Jul 22 21:17:15 kinito kernel: [ 2066.510242] Code:  Bad EIP value.
Jul 22 21:17:15 kinito kernel: [ 2066.510242] EIP: [<00008800>] 0x8800 SS:ESP 0068:dd04fe14
Jul 22 21:17:15 kinito kernel: [ 2066.510242] CR2: 0000000000008800
Jul 22 21:17:15 kinito kernel: [ 2066.633400] ---[ end trace b59a719cf5660ef6 ]---
Jul 22 21:17:30 kinito acpid: client 978[0:0] has disconnected
Jul 22 21:17:30 kinito acpid: client connected from 978[0:0]
Jul 22 21:17:30 kinito acpid: 1 client rule loaded
Jul 22 21:17:30 kinito kernel: [ 2081.058856] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

```

---

### Post by chili555 on 2011-07-22
Great. A kernel oops. 

I really don't have another idea. I wish I could be of greater assistance.

---

### Post by nicks27 on 2011-07-23
I don't know if it helps, but the following information might be more meaningful to you than it is to me, and perhaps indicate where to go next. I un-blacklisted the [FONT=Courier New]**ath9k**[/FONT] kernel module before generating these:

The output from the command  **[FONT=Courier New]rkill list all[/FONT]**  (with **[FONT=Courier New]ath9k[/FONT]** un-blacklisted) is:
 ```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```and running  [FONT=Courier New]**sudo rfkill block all**[/FONT]  only soft-blocks each of the two devices (would hard blocking disable the hardware/radio and if so how could this be done?).

The kernel messages from running  **[FONT=Courier New]sudo modprobe omnibook[/FONT]**  are:
```

[ 1141.340941] omnibook: Driver version 2.20090707-trunk.
[ 1141.341092] omnibook: Unknown model.
[ 1141.344261] BUG: unable to handle kernel paging request at 00008800
[ 1141.348024] IP: [<00008800>] 0x8800
[ 1141.348024] *pde = 00000000 
[ 1141.348024] Oops: 0000 [#1] SMP 
[ 1141.348024] last sysfs file: /sys/devices/platform/omnibook/uevent
[ 1141.348024] Modules linked in: omnibook(+) sco bnep l2cap parport_pc ppdev btusb bluetooth snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi arc4 joydev snd_rawmidi snd_seq_midi_event ath9k snd_seq mac80211 snd_timer snd_seq_device ath9k_common uvcvideo i915 ath9k_hw snd ath drm_kms_helper soundcore videodev drm snd_page_alloc cfg80211 psmouse serio_raw sparse_keymap lp i2c_algo_bit video toshiba_bluetooth parport usbhid hid usb_storage uas ahci libahci r8169
[ 1141.348024] 
[ 1141.348024] Pid: 1755, comm: modprobe Not tainted 2.6.38-10-generic #46-Ubuntu TOSHIBA TOSHIBA NB520/PBU00
[ 1141.348024] EIP: 0060:[<00008800>] EFLAGS: 00010206 CPU: 1
[ 1141.348024] EIP is at 0x8800
[ 1141.348024] EAX: 00000000 EBX: f9287784 ECX: 00000000 EDX: 00008800
[ 1141.348024] ESI: 00000000 EDI: ffffffea EBP: e71e5e30 ESP: e71e5e14
[ 1141.348024]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 1141.348024] Process modprobe (pid: 1755, ti=e71e4000 task=f451a5e0 task.ti=e71e4000)
[ 1141.348024] Stack:
[ 1141.348024]  f928d0de 00000034 00000040 000080d0 00000104 00000005 13b13b2a e71e5e4c
[ 1141.348024]  f928d277 c11850c7 00000001 ed1c4e08 f9287014 f9287014 e71e5e54 c1335631
[ 1141.348024]  e71e5e78 c133440d ed1c4e64 00000000 e71e5e78 c133c67b ed1c4e08 ffffffed
[ 1141.348024] Call Trace:
[ 1141.348024]  [<f928d0de>] ? omnibook_init+0xa0/0x178 [omnibook]
[ 1141.348024]  [<f928d277>] omnibook_probe+0xc1/0x122 [omnibook]
[ 1141.348024]  [<c11850c7>] ? sysfs_create_link+0x17/0x20
[ 1141.348024]  [<c1335631>] platform_drv_probe+0x11/0x20
[ 1141.348024]  [<c133440d>] really_probe+0x4d/0x150
[ 1141.348024]  [<c133c67b>] ? pm_runtime_barrier+0x4b/0xb0
[ 1141.348024]  [<c13346ac>] driver_probe_device+0x3c/0x60
[ 1141.348024]  [<c13347a9>] __device_attach+0x49/0x60
[ 1141.348024]  [<c1334760>] ? __device_attach+0x0/0x60
[ 1141.348024]  [<c133353f>] bus_for_each_drv+0x4f/0x70
[ 1141.348024]  [<c13345ca>] device_attach+0x7a/0x90
[ 1141.348024]  [<c1334760>] ? __device_attach+0x0/0x60
[ 1141.348024]  [<c1333d85>] bus_probe_device+0x25/0x40
[ 1141.348024]  [<c1331f4c>] device_add+0x28c/0x380
[ 1141.348024]  [<c127d033>] ? kvasprintf+0x43/0x60
[ 1141.348024]  [<c1273504>] ? kobject_set_name_vargs+0x64/0x70
[ 1141.348024]  [<c1335ea7>] platform_device_add+0xe7/0x1a0
[ 1141.348024]  [<c1336094>] ? platform_device_alloc+0x54/0x70
[ 1141.348024]  [<f928d3e1>] omnibook_module_init+0xdd/0xfe [omnibook]
[ 1141.348024]  [<c1001255>] do_one_initcall+0x35/0x170
[ 1141.348024]  [<f928d304>] ? omnibook_module_init+0x0/0xfe [omnibook]
[ 1141.348024]  [<c1088afb>] sys_init_module+0xdb/0x230
[ 1141.348024]  [<c1125aa5>] ? sys_close+0x75/0xd0
[ 1141.348024]  [<c150a194>] syscall_call+0x7/0xb
[ 1141.348024] Code:  Bad EIP value.
[ 1141.348024] EIP: [<00008800>] 0x8800 SS:ESP 0068:e71e5e14
[ 1141.348024] CR2: 0000000000008800
[ 1141.523551] ---[ end trace ea3b4e6453bba4d1 ]---
Jul 23 09:46:43 kinito kernel: [ 1268.835046] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

```The kernel messages from running  **[FONT=Courier New]grep ath9k /var/log/kern.log[/FONT]**  are:
```

[   13.828457] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.828480] ath9k 0000:07:00.0: setting latency timer to 64
[   14.689600] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.691501] Registered led device: ath9k-phy0::radio
[   14.691583] Registered led device: ath9k-phy0::assoc
[   14.691760] Registered led device: ath9k-phy0::tx
[   14.691930] Registered led device: ath9k-phy0::rx

```The output from the command  **[FONT=Courier New]sudo find /proc /sys -name *ath9k*[/FONT]**  is:
```

/proc/irq/17/ath9k
/sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/leds/ath9k-phy0::radio
/sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/leds/ath9k-phy0::assoc
/sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/leds/ath9k-phy0::tx
/sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/leds/ath9k-phy0::rx
/sys/bus/pci/drivers/ath9k
/sys/class/leds/ath9k-phy0::radio
/sys/class/leds/ath9k-phy0::assoc
/sys/class/leds/ath9k-phy0::tx
/sys/class/leds/ath9k-phy0::rx
/sys/kernel/debug/ieee80211/phy0/ath9k
/sys/module/cfg80211/holders/ath9k
/sys/module/ath/holders/ath9k_hw
/sys/module/ath/holders/ath9k
/sys/module/ath9k_hw
/sys/module/ath9k_hw/holders/ath9k_common
/sys/module/ath9k_hw/holders/ath9k
/sys/module/ath9k_common
/sys/module/ath9k_common/holders/ath9k
/sys/module/mac80211/holders/ath9k
/sys/module/ath9k
/sys/module/ath9k/drivers/pci:ath9k

```

---

### Post by chili555 on 2011-07-23
> (would hard blocking disable the hardware/radio and if so how could this be done?).Well, that's the whole point, isn't it? Ideally, Fn+F8 would do it but apparently does nothing. > The kernel messages from running sudo modprobe omnibook are:
Code:

[ 1141.340941] omnibook: Driver version 2.20090707-trunk.
[ 1141.341092] omnibook: Unknown model.
[ 1141.344261] [COLOR="Red"]BUG: unable to handle kernel paging request[/COLOR] at 00008800
[ 1141.348024] IP: [<00008800>] 0x8800
[ 1141.348024] *pde = 00000000 
[ 1141.348024] [COLOR="Red"]Oops:[/COLOR] 0000 [#1] SMP 
[ 1141.348024] [COLOR="Red"]last sysfs file: /sys/devices/platform/**omnibook**[/COLOR]/ueventI think that's the equivalent of, "I don't want a Ford truck piston in my BMW so I'm going to blow up now. BOOM!"

Generally, laptops have a -wmi or a -laptopmode driver that translates keys that are specific to a particular laptop into action the kernel understands; in your case, "Turn on the wireless, please." I can see nothing in your lsmod that does that aside from sparse-keymap. Of course, the operative word is "sparse." Sparse, as in not enough.

If you search this forum for hp-wmi, acer-wmi and dell-laptop, you will be plenty of examples of these modules that load and mismanage the wireless key, leading to crazy solutions like *removing* the module in order to get the wireless to work.

We have looked for alternatives, toshiba-acpi and omnibook and neither work. The clue, as we see in hindsight, is that neither load on boot and do the job we expect. I am not sure there is much else you can do. You could look for a bug and file a comment: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

You could simply be happy with what you have. As long as the ath9k driver is blacklisted, power to the radio is reduced but not stopped. When you want to use the wireless, load it and when you want to stop, unload it:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
```Last, you could skip a few caffe lattes and drop the $5 in a jar and save for a newer laptop.

---

### Post by nicks27 on 2011-07-24
OK, thanks for your explanatory remarks and trying to find a solution.

For now I'll just have to leave the ath9k module blacklisted, avoid using the machine in wifi-restricted areas, and carry my power adaptor around. I've filed a bug report and I'll post here if/when a solution is found.

(As for the lattes, I've already skipped more than a few to buy this machine after my old laptop had a motherboard failure).

Thanks,

---

### Post by tux_i on 2011-08-17
hello nicks27.

have you try this [http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=snapshot;h=aadeb3ee7c029252fedf8d7420664e92d922d3ae;sf=tgz](http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=snapshot;h=aadeb3ee7c029252fedf8d7420664e92d922d3ae;sf=tgz)

from [http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=summary](http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=summary)

it's the last version of omnibook driver . i check that from this forum
[http://www.avidandrew.com/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu](http://www.avidandrew.com/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu)
we have phoenix bios

---

