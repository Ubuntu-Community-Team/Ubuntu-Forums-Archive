---
title: "T22 with Edimax PCMCIA disconnects on switch to battery"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by SoftGround on 2011-06-18
I have just upgraded to 11.04 from an earlier version and most things are working better, if a little slower.  Had to remove pulse audio to get any sound.  Wifi with Edimax 54G Pcmcia card used to work fully, but now only works on mains, not on battery.

Suspected power management but iwconfig shows it is off.

Dmesg revealed that the driver had crashed in rt61pci.

```

[  452.171536] BUG: unable to handle kernel NULL pointer dereference at   (null)
[  452.171559] IP: [<e0a441df>] rt61pci_config+0x1f/0x180 [rt61pci]
[  452.171586] *pde = 17f18067 *pte = 00000000 
[  452.171598] Oops: 0000 [#1] SMP 
[  452.171607] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/PNP0C09:00/PNP0C0A:00/power_supply/BAT0/voltage_now
[  452.171618] Modules linked in: savage drm vesafb arc4 rt61pci crc_itu_t rt2x00pci rt2x00lib snd_cs46xx mac80211 gameport snd_ac97_codec ac97_bus snd_pcm thinkpad_acpi snd_seq_midi cfg80211 snd_rawmidi snd_seq_midi_event binfmt_misc ppdev snd_seq eeprom_93cx6 nsc_ircc snd_timer snd_seq_device psmouse irda pcmcia parport_pc snd yenta_socket video serio_raw nvram crc_ccitt pcmcia_rsrc soundcore pcmcia_core i2c_piix4 shpchp nls_iso8859_1 nls_cp437 vfat fat snd_page_alloc lp parport floppy e100
[  452.171718] 
[  452.171727] Pid: 917, comm: irq/11-0000:02: Not tainted 2.6.38-8-generic #42-Ubuntu IBM 2648MCU/2648MCU
[  452.171743] EIP: 0060:[<e0a441df>] EFLAGS: 00010282 CPU: 0
[  452.171754] EIP is at rt61pci_config+0x1f/0x180 [rt61pci]
[  452.171762] EAX: 00000000 EBX: d6cb7080 ECX: 00000010 EDX: d6d55f34
[  452.171770] ESI: d6d55f34 EDI: 00000010 EBP: d6d55f2c ESP: d6d55f08
[  452.171779]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  452.171787] Process irq/11-0000:02: (pid: 917, ti=d6d54000 task=d7f81940 task.ti=d6d54000)
[  452.171794] Stack:
[  452.171799]  d6cb7080 d6d609a4 d7f81bcc c183a8c0 3d9099f7 00000069 d6cb7080 17f8b000
[  452.171817]  d6d55f58 d6d55f88 e0a443b8 d6d55f58 00000000 00000000 00000000 00000000
[  452.171834]  00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  452.171851] Call Trace:
[  452.171866]  [<e0a443b8>] rt61pci_interrupt_thread+0x78/0xc8 [rt61pci]
[  452.171883]  [<c10b0762>] irq_thread+0x102/0x180
[  452.171894]  [<c10b0660>] ? irq_thread+0x0/0x180
[  452.171912]  [<c106ce04>] kthread+0x74/0x80
[  452.171922]  [<c106cd90>] ? kthread+0x0/0x80
[  452.171937]  [<c100367e>] kernel_thread_helper+0x6/0x10
[  452.171943] Code: 88 b5 60 e0 90 8d b4 26 00 00 00 00 55 89 e5 83 ec 24 89 5d f4 89 75 f8 89 7d fc 3e 8d 74 26 00 89 c3 8b 02 89 d6 89 cf 8b 40 18 <8b> 00 85 c0 75 63 8b 93 74 03 00 00 8b 83 38 02 00 00 0f b6 92 
[  452.172040] EIP: [<e0a441df>] rt61pci_config+0x1f/0x180 [rt61pci] SS:ESP 0068:d6d55f08
[  452.172055] CR2: 0000000000000000
[  452.172119] ---[ end trace 00a466d74250e1d0 ]---
[  452.172130] exiting task "irq/11-0000:02:" (917) is an active IRQ thread (irq 11)
[  455.504229] ieee80211 phy0: wlan0: No probe response from AP 00:17:3f:60:cc:4c after 500ms, disconnecting.
```

Not sure what to do next.  Will the latest driver in CVS be a drop in replacement, and will it work.

More info if you need it.

Regards.

---

### Post by SoftGround on 2011-06-19
Tried Kernel 39 but that made no difference.

Used natty included ndiswrapper with win2k drivers from Edimax website and it is now working.  Just needed to blacklist rt61pci and rt2x00pci to make sure they did not load instead.

Please note that blacklists should now go in /etc/modprobe.d/blacklist.conf
There is also a recommendation that it should include the device name (for easy maintenance) e.g. blacklist-rt61pci.conf

---

### Post by SoftGround on 2011-06-19
I have posted on the serialmonkey board about this, just for the record.

Thinkpad T22 is mostly working now, will post about that on another thread some time. i.e Install problems with Classic, removing PulseAudio, getting ALSA, Ubuntu Classic, Unity 2D issues, Canon printer/scanner drivers.

---

### Post by SoftGround on 2011-06-21
Wifi with ndiswrapper did not recover from a resume.
I needed to add to SUSPEND_MODULES in /etc/pm/confic.d/

i.e.
Edit a new file: /etc/pm/config.d/config using sudo
e.g. 
Add to it.
```
SUSPEND_MODULES="$SUSPEND_MODULES ndiswrapper"
```
Wifi restarts from scratch after a resume (it is not immediate, be patient!)

Got this from: [http://ubuntuforums.org/archive/index.php/t-1631698.html](http://ubuntuforums.org/archive/index.php/t-1631698.html)

---

