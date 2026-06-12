---
title: "Getting ALSA to work with my Intel HD Audio"
date: 2009-03-24
forum: Multimedia Software
---

### Post by mamlouk on 2009-03-24
I bought an Acer Aspire 6920G laptop last year, and installed Ubuntu 8.10 as soon as it was released. Back then, the only way to get my sound card to run was to blacklist ALSA, and run OSS.

I followed a link that was posted on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), and it got my sound card running on OSS.

Now ALSA has added functionality to Intel HD Audio, and I want to revert back to ALSA before 9.04 is released, or else I'll reformat or something.

```
mamlouk@mamlouk-laptop:~$ uname -r
2.6.27-14-generic
```
```
mamlouk@mamlouk-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```
I tried back-tracing (as far as I remember since the page was changed), and cleared my blacklist file.
```
mamlouk@mamlouk-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# Added by me
blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb-midi
```
The last few lines in the end were added by myself in an attempt to blacklist OSS.

I tried installing the newest ALSA drivers (1.0.19) as per the instructions on [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) and on [http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/](http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/).

When I attempt to modprobe after the installation, I get ```
mamlouk@mamlouk-laptop:~$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.27-14-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
My dmesg holds a number of lines similar to:```
-- SNIP --
[ 4325.551666] snd: Unknown symbol unregister_sound_special
[ 4325.552077] snd: Unknown symbol register_sound_special_device
[ 4325.553106] snd: Unknown symbol sound_class
[ 4325.554793] snd_timer: Unknown symbol snd_info_register
[ 4325.554936] snd_timer: Unknown symbol snd_info_create_module_entry
[ 4325.555068] snd_timer: Unknown symbol snd_info_free_entry
[ 4325.555290] snd_timer: Unknown symbol snd_verbose_printk
[ 4325.555440] snd_timer: Unknown symbol snd_iprintf
[ 4325.555610] snd_timer: Unknown symbol snd_ecards_limit
[ 4325.555775] snd_timer: Unknown symbol snd_oss_info_register
[ 4325.555888] snd_timer: Unknown symbol snd_unregister_device
[ 4325.556096] snd_timer: Unknown symbol snd_device_new
[ 4325.556351] snd_timer: Unknown symbol snd_register_device_for_dev
[ 4325.586088] snd: Unknown symbol unregister_sound_special
[ 4325.586483] snd: Unknown symbol register_sound_special_device
[ 4325.587522] snd: Unknown symbol sound_class
[ 4325.589954] snd_timer: Unknown symbol snd_info_register
[ 4325.590099] snd_timer: Unknown symbol snd_info_create_module_entry
[ 4325.590225] snd_timer: Unknown symbol snd_info_free_entry
[ 4325.590440] snd_timer: Unknown symbol snd_verbose_printk
[ 4325.590581] snd_timer: Unknown symbol snd_iprintf
[ 4325.590741] snd_timer: Unknown symbol snd_ecards_limit
[ 4325.590901] snd_timer: Unknown symbol snd_oss_info_register
[ 4325.591010] snd_timer: Unknown symbol snd_unregister_device
[ 4325.591137] snd_timer: Unknown symbol snd_device_new
[ 4325.591374] snd_timer: Unknown symbol snd_register_device_for_dev
[ 4325.596243] snd_pcm: Unknown symbol snd_info_register
[ 4325.596387] snd_pcm: Unknown symbol snd_info_create_module_entry
[ 4325.596588] snd_pcm: Unknown symbol snd_timer_notify
[ 4325.596729] snd_pcm: Unknown symbol snd_timer_interrupt
[ 4325.596838] snd_pcm: Unknown symbol snd_info_free_entry
[ 4325.596947] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[ 4325.597083] snd_pcm: Unknown symbol snd_info_get_str
[ 4325.600247] snd_pcm: Unknown symbol snd_verbose_printk
[ 4325.600475] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[ 4325.600585] snd_pcm: Unknown symbol snd_card_file_add
[ 4325.600754] snd_pcm: Unknown symbol snd_iprintf
[ 4325.600923] snd_pcm: Unknown symbol snd_major
[ 4325.601228] snd_pcm: Unknown symbol snd_unregister_device
[ 4325.601350] snd_pcm: Unknown symbol snd_timer_new
[ 4325.601459] snd_pcm: Unknown symbol snd_device_new
[ 4325.601650] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[ 4325.601886] snd_pcm: Unknown symbol snd_lookup_minor_data
[ 4325.602034] snd_pcm: Unknown symbol snd_info_create_card_entry
[ 4325.602144] snd_pcm: Unknown symbol snd_power_wait
[ 4325.602269] snd_pcm: Unknown symbol snd_device_free
[ 4325.602455] snd_pcm: Unknown symbol snd_card_file_remove
[ 4325.602564] snd_pcm: Unknown symbol snd_register_device_for_dev
[ 4325.602781] snd_pcm: Unknown symbol snd_device_register
[ 4325.602897] snd_pcm: Unknown symbol snd_info_get_line
[ 4325.611000] snd_hwdep: Unknown symbol snd_info_register
[ 4325.611144] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 4325.611254] snd_hwdep: Unknown symbol snd_info_free_entry
[ 4325.611384] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 4325.611508] snd_hwdep: Unknown symbol snd_verbose_printk
[ 4325.611624] snd_hwdep: Unknown symbol snd_register_oss_device
[ 4325.611742] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 4325.611854] snd_hwdep: Unknown symbol snd_card_file_add
[ 4325.611987] snd_hwdep: Unknown symbol snd_iprintf
[ 4325.612127] snd_hwdep: Unknown symbol snd_major
[ 4325.612304] snd_hwdep: Unknown symbol snd_unregister_device
[ 4325.612422] snd_hwdep: Unknown symbol snd_device_new
[ 4325.612536] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 4325.612674] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 4325.612793] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 4325.612910] snd_hwdep: Unknown symbol snd_card_file_remove
[ 4325.613019] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 4325.621613] snd_hda_codec: Unknown symbol snd_ctl_add
[ 4325.621786] snd_hda_codec: Unknown symbol snd_card_proc_new
[ 4325.621903] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[ 4325.622073] snd_hda_codec: Unknown symbol snd_ctl_remove
[ 4325.622182] snd_hda_codec: Unknown symbol snd_ctl_find_id
[ 4325.622291] snd_hda_codec: Unknown symbol snd_verbose_printk
[ 4325.622441] snd_hda_codec: Unknown symbol snd_ctl_new1
[ 4325.622600] snd_hda_codec: Unknown symbol snd_component_add
[ 4325.622715] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[ 4325.622858] snd_hda_codec: Unknown symbol snd_iprintf
[ 4325.622981] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 4325.623213] snd_hda_codec: Unknown symbol snd_hwdep_new
[ 4325.623461] snd_hda_codec: Unknown symbol snd_device_new
[ 4325.623609] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[ 4325.623840] snd_hda_codec: Unknown symbol snd_pci_quirk_lookup
[ 4325.624062] snd_hda_codec: Unknown symbol snd_device_free
[ 4325.624171] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[ 4325.624351] snd_hda_codec: Unknown symbol snd_pcm_format_width
[ 4325.633362] snd_hda_intel: Unknown symbol snd_pcm_new
[ 4325.633477] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 4325.633595] snd_hda_intel: Unknown symbol snd_card_register
[ 4325.633704] snd_hda_intel: Unknown symbol snd_card_free
[ 4325.633813] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 4325.633957] snd_hda_intel: Unknown symbol snd_hda_bus_new
[ 4325.634236] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[ 4325.634345] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[ 4325.634492] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 4325.634602] snd_hda_intel: Unknown symbol snd_hda_codec_new
[ 4325.634884] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[ 4325.635039] snd_hda_intel: Unknown symbol snd_hda_power_up
[ 4325.635151] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[ 4325.635279] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 4325.635424] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 4325.635543] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 4325.635693] snd_hda_intel: Unknown symbol snd_hda_power_down
[ 4325.635804] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[ 4325.635924] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 4325.636105] snd_hda_intel: Unknown symbol snd_hda_suspend
[ 4325.636248] snd_hda_intel: Unknown symbol snd_device_new
[ 4325.636357] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[ 4325.636512] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 4325.636626] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 4325.636736] snd_hda_intel: Unknown symbol snd_hda_resume
[ 4325.636845] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 4325.636991] snd_hda_intel: Unknown symbol snd_hda_build_controls
[ 4325.637278] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 4325.637513] snd_hda_intel: Unknown symbol snd_card_create
[ 4325.637622] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 4325.637731] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```
And even ```
mamlouk@mamlouk-laptop:~$ ls /proc/a*
ac_adapter  dsdt                 fadt  power_resource  thermal_zone
battery     embedded_controller  fan   processor       video
button      event                info  sleep           wakeup

``` There is no /proc/asound.
Can anyone give me some pointers to what I did wrong?

---

### Post by mamlouk on 2009-03-27
Shameless bump, any ideas?

---

### Post by politas on 2009-07-05
I'm getting the exact same symptoms, just in the last couple of days.

[QUOTE="dmesg"][ 3808.971439] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[ 3808.971811] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 3808.971819] snd_hda_intel: Unknown symbol snd_ctl_add
[ 3808.972163] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 3808.972169] snd_hda_intel: Unknown symbol snd_pcm_new
[ 3808.972420] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 3808.972427] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 3808.972647] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 3808.972653] snd_hda_intel: Unknown symbol snd_card_register
[ 3808.972854] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 3808.972860] snd_hda_intel: Unknown symbol snd_card_free
[ 3808.973053] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 3808.973061] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 3808.973263] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[ 3808.973270] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 3808.973909] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[ 3808.973914] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 3808.974104] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[ 3808.974111] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[ 3808.975977] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[ 3808.975984] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 3808.976476] snd_hda_intel: disagrees about version of symbol snd_component_add
[ 3808.976483] snd_hda_intel: Unknown symbol snd_component_add
[ 3808.976697] snd_hda_intel: disagrees about version of symbol snd_ctl_make_virtual_master
[ 3808.976704] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[ 3808.976992] snd_hda_intel: Unknown symbol snd_card_new
[ 3808.977405] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 3808.977412] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 3808.977613] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 3808.977620] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 3808.977880] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 3808.977886] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 3808.978095] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 3808.978102] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 3808.978399] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 3808.978405] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 3808.978641] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 3808.978647] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 3808.978983] snd_hda_intel: disagrees about version of symbol snd_device_new
[ 3808.978990] snd_hda_intel: Unknown symbol snd_device_new
[ 3808.979179] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[ 3808.979186] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[ 3808.979493] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 3808.979499] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 3808.979789] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 3808.979796] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 3808.979984] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 3808.979991] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 3808.980546] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[ 3808.980552] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 3808.981050] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 3808.981056] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 3808.981243] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 3808.981250] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step[/quote]

[quote="~$ cat /proc/asound/cards"]--- no soundcards ---[/quote]

[quote="sudo modprobe snd-hda-intel"]FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/quote]

[quote="uname -r"]2.6.27-14-generic[/quote]

[quote="aplay -l"]aplay: device_list:223: no soundcards found...[/quote]

Sound was working fine on Thursday, before I allowed a "critical" kernel upgrade.

---

### Post by wwuster on 2009-07-05
I just rebooted after a couple of weeks of updates and I also have no sound. I have an Intel motherboard.

How do you find what's wrong?

William

---

### Post by fleasbaby on 2009-07-05
Not sure if this helps, but this link sorted my issues out on my HP laptop:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Only took a simple update of the alsa file.

---

### Post by idoitprone on 2012-05-22
[http://ubuntuforums.org/showthread.php?t=1382744](http://ubuntuforums.org/showthread.php?t=1382744)

maybe these commands?
```

[LIST]
[*]sudo apt-get install module-assistant
[*]sudo m-a update
[*]sudo m-a prepare
[*]sudo m-a a-i alsa
[/LIST]

```

---

