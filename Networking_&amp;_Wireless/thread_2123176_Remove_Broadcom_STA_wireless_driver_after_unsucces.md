---
title: "Remove Broadcom STA wireless driver after unsuccessful installation"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by ywatson on 2013-03-07
Hi,

Until now, elementaryOS Luna Beta 1 (based on Ubuntu 12.04) worked perfectly on my computer (also installing of applications). However, when I tried to install the Broadcom STA wireless driver using Additional Drivers I got a black screen with the following text (which I found in both /var/log/syslog.log and /var/log/kern.log):

```


from /var/log/syslog.log:

Mar  4 10:59:20 home-elementary kernel: [43499.888547] Modules linked in: wl(P+) cfg80211 lib80211 joydev hp_wmi snd_hda_codec_si3054 sparse_keymap snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket pcmcia_rsrc pcmcia_core psmouse serio_raw snd soundcore snd_page_alloc rfcomm bnep parport_pc bluetooth ppdev mac_hid lp parport i915 firewire_ohci firewire_core crc_itu_t drm_kms_helper drm i2c_algo_bit wmi video [last unloaded: cfg80211]
Mar  4 10:59:20 home-elementary kernel: [43499.889049] 
Mar  4 10:59:20 home-elementary kernel: [43499.889067] Pid: 6208, comm: modprobe Tainted: P           O 3.2.0-38-generic-pae #61-Ubuntu Hewlett-Packard HP Compaq nx7400 (EY304ET#ABH)/30A2
Mar  4 10:59:20 home-elementary kernel: [43499.889192] EIP: 0060:[<e0f8c4b8>] EFLAGS: 00210246 CPU: 0
Mar  4 10:59:20 home-elementary kernel: [43499.889289] EIP is at wdev_priv.part.7+0x3/0x5 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.889334] EAX: 00000000 EBX: dccdbc80 ECX: dccdbc80 EDX: dbca7c90
Mar  4 10:59:20 home-elementary kernel: [43499.889390] ESI: dbca7c90 EDI: dbca7c0c EBP: db02bcec ESP: db02bcec
Mar  4 10:59:20 home-elementary kernel: [43499.889446]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar  4 10:59:20 home-elementary kernel: [43499.889496] Process modprobe (pid: 6208, ti=db02a000 task=dc67f230 task.ti=db02a000)
Mar  4 10:59:20 home-elementary kernel: [43499.889567] Stack:
Mar  4 10:59:20 home-elementary kernel: [43499.889588]  db02bd00 e0f8b944 dccdbc80 dbca7c90 dbca7c0c db02bd14 e0f8459f dbca7c00
Mar  4 10:59:20 home-elementary kernel: [43499.889671]  ded70800 dccdb800 db02bdc0 e0f84f68 c105abb5 00000000 ffffff06 00000000
Mar  4 10:59:20 home-elementary kernel: [43499.889754]  c196af93 db02bd7d db02bdb0 00200246 db02bd6e c1746134 0000a9eb 000d8e32
Mar  4 10:59:20 home-elementary kernel: [43499.889839] Call Trace:
Mar  4 10:59:20 home-elementary kernel: [43499.889904]  [<e0f8b944>] wl_cfg80211_detach+0xc4/0xd0 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.889993]  [<e0f8459f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890082]  [<e0f84f68>] wl_free+0x58/0x250 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890129]  [<c105abb5>] ? console_trylock+0x15/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890204]  [<e0ea4e92>] ? wlc_attach+0xf6c/0xfda [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890291]  [<e0f8c42b>] wl_pci_probe+0x51c/0x53c [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890344]  [<c15a81ed>] ? _raw_spin_lock_irqsave+0x2d/0x40
Mar  4 10:59:20 home-elementary kernel: [43499.890402]  [<c138e1f5>] ? pm_runtime_enable+0x45/0x70
Mar  4 10:59:20 home-elementary kernel: [43499.890454]  [<c12d2627>] local_pci_probe+0x47/0xb0
Mar  4 10:59:20 home-elementary kernel: [43499.890499]  [<c12d3b28>] pci_device_probe+0x68/0x90
Mar  4 10:59:20 home-elementary kernel: [43499.890549]  [<c11a8c57>] ? sysfs_create_link+0x17/0x20
Mar  4 10:59:20 home-elementary kernel: [43499.890599]  [<c1385fbd>] really_probe+0x4d/0x150
Mar  4 10:59:20 home-elementary kernel: [43499.890643]  [<c138f629>] ? pm_runtime_barrier+0x49/0xb0
Mar  4 10:59:20 home-elementary kernel: [43499.890694]  [<c13861fa>] driver_probe_device+0x3a/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890742]  [<c13862b1>] __driver_attach+0x91/0xa0
Mar  4 10:59:20 home-elementary kernel: [43499.890787]  [<c1386220>] ? driver_probe_device+0x60/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890838]  [<c1385339>] bus_for_each_dev+0x49/0x70
Mar  4 10:59:20 home-elementary kernel: [43499.890888]  [<c1385df1>] driver_attach+0x21/0x30
Mar  4 10:59:20 home-elementary kernel: [43499.890931]  [<c1386220>] ? driver_probe_device+0x60/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890981]  [<c1385acf>] bus_add_driver+0x17f/0x260
Mar  4 10:59:20 home-elementary kernel: [43499.891030]  [<c12d3b50>] ? pci_device_probe+0x90/0x90
Mar  4 10:59:20 home-elementary kernel: [43499.891080]  [<c1386786>] driver_register+0x66/0x110
Mar  4 10:59:20 home-elementary kernel: [43499.891129]  [<c12d38d2>] __pci_register_driver+0x42/0xc0
Mar  4 10:59:20 home-elementary kernel: [43499.891199]  [<e01be017>] wl_module_init+0x17/0x1000 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.891250]  [<c1003035>] do_one_initcall+0x35/0x170
Mar  4 10:59:20 home-elementary kernel: [43499.891301]  [<e01be000>] ? 0xe01bdfff
Mar  4 10:59:20 home-elementary kernel: [43499.891340]  [<c109623c>] sys_init_module+0xac/0x210
Mar  4 10:59:20 home-elementary kernel: [43499.892020]  [<c11434b3>] ? sys_close+0x73/0xc0
Mar  4 10:59:20 home-elementary kernel: [43499.892020]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  4 10:59:20 home-elementary kernel: [43499.892020] Code: d0 e8 0d bc 61 e0 89 f0 e8 76 8a ff ff 89 d8 e8 4f 50 34 e0 31 d2 89 f8 e8 c6 97 3f e0 58 5b 5e 5f 5d c3 55 89 e5 0f 0b 55 89 e5 <0f> 0b 55 89 e5 3e 8d 74 26 00 0f 0b 55 89 e5 3e 8d 74 26 00 0f 
Mar  4 10:59:20 home-elementary kernel: [43499.892020] EIP: [<e0f8c4b8>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:db02bcec


from /var/log/kern.log:

Mar  4 10:59:20 home-elementary kernel: [43499.888547] Modules linked in: wl(P+) cfg80211 lib80211 joydev hp_wmi snd_hda_codec_si3054 sparse_keymap snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket pcmcia_rsrc pcmcia_core psmouse serio_raw snd soundcore snd_page_alloc rfcomm bnep parport_pc bluetooth ppdev mac_hid lp parport i915 firewire_ohci firewire_core crc_itu_t drm_kms_helper drm i2c_algo_bit wmi video [last unloaded: cfg80211]
Mar  4 10:59:20 home-elementary kernel: [43499.889049] 
Mar  4 10:59:20 home-elementary kernel: [43499.889067] Pid: 6208, comm: modprobe Tainted: P           O 3.2.0-38-generic-pae #61-Ubuntu Hewlett-Packard HP Compaq nx7400 (EY304ET#ABH)/30A2
Mar  4 10:59:20 home-elementary kernel: [43499.889192] EIP: 0060:[<e0f8c4b8>] EFLAGS: 00210246 CPU: 0
Mar  4 10:59:20 home-elementary kernel: [43499.889289] EIP is at wdev_priv.part.7+0x3/0x5 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.889334] EAX: 00000000 EBX: dccdbc80 ECX: dccdbc80 EDX: dbca7c90
Mar  4 10:59:20 home-elementary kernel: [43499.889390] ESI: dbca7c90 EDI: dbca7c0c EBP: db02bcec ESP: db02bcec
Mar  4 10:59:20 home-elementary kernel: [43499.889446]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar  4 10:59:20 home-elementary kernel: [43499.889496] Process modprobe (pid: 6208, ti=db02a000 task=dc67f230 task.ti=db02a000)
Mar  4 10:59:20 home-elementary kernel: [43499.889567] Stack:
Mar  4 10:59:20 home-elementary kernel: [43499.889588]  db02bd00 e0f8b944 dccdbc80 dbca7c90 dbca7c0c db02bd14 e0f8459f dbca7c00
Mar  4 10:59:20 home-elementary kernel: [43499.889671]  ded70800 dccdb800 db02bdc0 e0f84f68 c105abb5 00000000 ffffff06 00000000
Mar  4 10:59:20 home-elementary kernel: [43499.889754]  c196af93 db02bd7d db02bdb0 00200246 db02bd6e c1746134 0000a9eb 000d8e32
Mar  4 10:59:20 home-elementary kernel: [43499.889839] Call Trace:
Mar  4 10:59:20 home-elementary kernel: [43499.889904]  [<e0f8b944>] wl_cfg80211_detach+0xc4/0xd0 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.889993]  [<e0f8459f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890082]  [<e0f84f68>] wl_free+0x58/0x250 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890129]  [<c105abb5>] ? console_trylock+0x15/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890204]  [<e0ea4e92>] ? wlc_attach+0xf6c/0xfda [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890291]  [<e0f8c42b>] wl_pci_probe+0x51c/0x53c [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.890344]  [<c15a81ed>] ? _raw_spin_lock_irqsave+0x2d/0x40
Mar  4 10:59:20 home-elementary kernel: [43499.890402]  [<c138e1f5>] ? pm_runtime_enable+0x45/0x70
Mar  4 10:59:20 home-elementary kernel: [43499.890454]  [<c12d2627>] local_pci_probe+0x47/0xb0
Mar  4 10:59:20 home-elementary kernel: [43499.890499]  [<c12d3b28>] pci_device_probe+0x68/0x90
Mar  4 10:59:20 home-elementary kernel: [43499.890549]  [<c11a8c57>] ? sysfs_create_link+0x17/0x20
Mar  4 10:59:20 home-elementary kernel: [43499.890599]  [<c1385fbd>] really_probe+0x4d/0x150
Mar  4 10:59:20 home-elementary kernel: [43499.890643]  [<c138f629>] ? pm_runtime_barrier+0x49/0xb0
Mar  4 10:59:20 home-elementary kernel: [43499.890694]  [<c13861fa>] driver_probe_device+0x3a/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890742]  [<c13862b1>] __driver_attach+0x91/0xa0
Mar  4 10:59:20 home-elementary kernel: [43499.890787]  [<c1386220>] ? driver_probe_device+0x60/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890838]  [<c1385339>] bus_for_each_dev+0x49/0x70
Mar  4 10:59:20 home-elementary kernel: [43499.890888]  [<c1385df1>] driver_attach+0x21/0x30
Mar  4 10:59:20 home-elementary kernel: [43499.890931]  [<c1386220>] ? driver_probe_device+0x60/0x60
Mar  4 10:59:20 home-elementary kernel: [43499.890981]  [<c1385acf>] bus_add_driver+0x17f/0x260
Mar  4 10:59:20 home-elementary kernel: [43499.891030]  [<c12d3b50>] ? pci_device_probe+0x90/0x90
Mar  4 10:59:20 home-elementary kernel: [43499.891080]  [<c1386786>] driver_register+0x66/0x110
Mar  4 10:59:20 home-elementary kernel: [43499.891129]  [<c12d38d2>] __pci_register_driver+0x42/0xc0
Mar  4 10:59:20 home-elementary kernel: [43499.891199]  [<e01be017>] wl_module_init+0x17/0x1000 [wl]
Mar  4 10:59:20 home-elementary kernel: [43499.891250]  [<c1003035>] do_one_initcall+0x35/0x170
Mar  4 10:59:20 home-elementary kernel: [43499.891301]  [<e01be000>] ? 0xe01bdfff
Mar  4 10:59:20 home-elementary kernel: [43499.891340]  [<c109623c>] sys_init_module+0xac/0x210
Mar  4 10:59:20 home-elementary kernel: [43499.892020]  [<c11434b3>] ? sys_close+0x73/0xc0
Mar  4 10:59:20 home-elementary kernel: [43499.892020]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  4 10:59:20 home-elementary kernel: [43499.892020] Code: d0 e8 0d bc 61 e0 89 f0 e8 76 8a ff ff 89 d8 e8 4f 50 34 e0 31 d2 89 f8 e8 c6 97 3f e0 58 5b 5e 5f 5d c3 55 89 e5 0f 0b 55 89 e5 <0f> 0b 55 89 e5 3e 8d 74 26 00 0f 0b 55 89 e5 3e 8d 74 26 00 0f 
Mar  4 10:59:20 home-elementary kernel: [43499.892020] EIP: [<e0f8c4b8>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:db02bcec


```

And now everytime I try to install something from the Software Center, it eventually gives the same black screen. I found the driver in the Software Center and tried to remove it, but it gave the same screen once again. I would like to know how I could remove the driver or restore the system to before the attempt of installing it. Being able to use my wireless card isn't that important, I would rather have an otherwise perfectly working system and not having to lose a lot of work for a clean install. (And once I know how to get rid of it I could always try again some other time.)

Thanks!

---

### Post by chili555 on 2013-03-07
I suspect there is a deeper problem here and I suspect you'll post back and say it isn't fixed, but to answer plainly the question you asked:```
sudo apt-get remove --purge bcmwl-kernel-source
```We await your results!

---

### Post by kc1di on 2013-03-07
you can try this go to a terminal and type the following
> sudo apt-get purge broadcom-sta

---

### Post by chili555 on 2013-03-07
> **kc1di said:**
> you can try this go to a terminal and type the followingThere is no such package.

---

### Post by ywatson on 2013-03-07
Thanks for the prompt responses.

This is the message I got after executing 'sudo apt-get remove --purge bcmwl-kernel-source':

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

And after running 'sudo dpkg --configure -a' it first went on to do a lot of things but before it finished I got the black screen again and needed to restart.

I get the feeling however that I can still interact with the OS while seeing the black screen (also previous times), it still makes certain sounds and when I hit the power key and then Space or Enter it shuts down the computer.

---

### Post by chili555 on 2013-03-07
If you have the black screen and a blinking cursor like the attached, then, yes you can. Just repeat your commands:```
sudo dpkg --configure -a
sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by ywatson on 2013-03-07
Unfortunately there is no cursor, no command line to which I can type something as input. Only the text from my first post filling a black screen. I'm seeing no reaction to whatever key I hit, however it feels like there is a reaction from the (graphical) OS 'behind' the black screen as it were, making familiar OS (not hardware) beeping sounds for 'invalid keypress' etc.

---

### Post by chili555 on 2013-03-07
I suggest you reboot. In the first few seconds of the boot process, press Shift to get to the GRUB menu. Select Recovery Mode. I believe, although I currently have no 12.04 installation to check, you will either go directly or have the option to go to a root prompt. Try your commands again, however since you are already root, you won't need 'sudo.' Please see attached.

---

### Post by ywatson on 2013-03-08
Did as you suggested. However 'dpkg --configure -a' gave the following message:

```

dpkg: error: unable to access dpkg status area: Read-only file system

```

And the remove command gave the same message as before. I don't know if it makes any difference, but at the top of the menu the title also says: "Recovery Menu (filesystem state: read-only)".

Might it help the initial problem if I choose "dpkg  Repair broken packages"?

---

### Post by chili555 on 2013-03-08
> **ywatson said:**
> 
Might it help the initial problem if I choose "dpkg  Repair broken packages"?Absolutely, please do.

---

### Post by ywatson on 2013-03-08
After trying the repair packages option in recovery mode, it looks like it recognized there was something wrong with bcmwl-kernel-source, as it tried to start uninstalling it. There was a lot of text, but eventually it hang at:

```

[  121.959337] cfg80211:  (5735000 kHz - 5835000 kHz @ 40000 kHz), (300 mBi, 2000 mBm)

```

I needed to reboot, as nothing seemed to happen or respond (i.e. I could type, but the process was not finished and it didn't do anything for more than half an hour).

Also, it didn't uninstall bcmwl-kernel-source (or it reinstalled it) and I'm still having the same problem.

---

### Post by chili555 on 2013-03-08
> [  121.959337] cfg80211:  (5735000 kHz - 5835000 kHz @ 40000 kHz), (300 mBi, 2000 mBm)That's one of the messages that appears when the wireless card and driver meet and start determining what channels it can use. I didn't think cfg80211 was a dependency of wl. Is there another wireless device present? A USB perhaps? If so, remove it for now.

I suggest trying to get wl to absolutely not try to load and freeze up by renaming it:```
modinfo wl
```...will tell you the specific module being loaded; for example:> chili@Think410:~$ modinfo wl
filename:       [COLOR="#FF0000"]/lib/modules/3.5.0-25-generic/updates/dkms/wl.ko[/COLOR]
license:        MIXED/Proprietary
srcversion:     1C6A0B8B0000A8D58131D83
<snip>
Your location will probably be different, but use the exact location to rename the file:```
sudo mv /lib/modules/3.5.0-25-generic/updates/dkms/wl.ko  /lib/modules/3.5.0-25-generic/updates/dkms/wl.bak 
```Now go back to the repair packages option in recovery mode and see if you can succeed.

---

### Post by ywatson on 2013-03-08
Did as you said, however, it still hangs at the same point. This time I actually saw it say that the uninstallation was completed. After that it said something like: 

```

Loading new bcmwl-[some version number] DKMS files...

```

...and then again all the frequencies, eventually freezing at one of them.

Also, after that it had recreated the wl.ko file in the module folder.

---

### Post by chili555 on 2013-03-08
Frankly, I have no further suggestions. I recommend you consider a fresh install.

---

### Post by ywatson on 2013-03-10
I think I'll reinstall then.

Thank you for the excellent support though!

---

