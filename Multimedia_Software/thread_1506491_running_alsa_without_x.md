---
title: "running alsa without x"
date: 2010-06-10
forum: Multimedia Software
---

### Post by curantil on 2010-06-10
I have a small box running without keyboard and screen. The audio  is connected to my hifi as music player.
I run xmms2 on it so I can control the music from other pc's. But I noticed I need to be logged in X on that box before alsa seems to be loaded which is a problem as I need to reconnect a keyboard to it everytime the box is rebooted.

Is there a way to load alsa without needing to log in? I have been looking for it but I don't seem to be able to find a way to do it.

---

### Post by Yellow Pasque on 2010-06-10
ALSA will be loaded automatically, but you may need to start pulseaudio manually (as Ubuntu is usually configured to start the pulse X11 daemon when you log in to GNOME).
```
pulseaudio --start
```

---

### Post by curantil on 2010-06-10
Ah, that seems to help somewhat. I can run xmms2 with the pulse-plugin now. 
There is still no sound though. I presume the volume may be 0, but when I try to start alsamixer it says: ```
cannot open mixer: No suchfile or directory
```


Alsa doesn't seem to work completly. When I try to load the alsa plugin in xmms2 it gives the message:
```
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback
```

Any ideas? Thanks

---

### Post by Yellow Pasque on 2010-06-10
You can use pacmd to control pulseaudio on the command line:
```
pacmd
set-sink-mute 0,false
```

---

### Post by curantil on 2010-06-11
Setting the mute to false does not fix the audio. Setting the volume to 100 neither.
But I noticed this in my dmesg:
```
[168513.212943] HDA Intel 0000:00:0f.0: PCI INT A disabled
[168513.442410] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[168513.442494] HDA Intel 0000:00:0f.0: setting latency timer to 64
[168513.504149] hda_codec: ALC662 rev1: BIOS auto-probing.
[168513.505318] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:0f.0/input/input5
[228767.229905] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[233311.522143] pulseaudio[8272]: segfault at 426b90 ip 00426b90 sp bfb7af0c error 4 in module-intended-roles.so[45d000+3000]
```
I could not reproduce it to see exactly when that happens though.

---

### Post by curantil on 2010-06-11
Aha! I have rebooted, and now the sound works!

Maybe some module was not loaded correctly or in my trying I did something that screwed something up. But after the reboot I can use xmms2 with the alsa module, and the alsamixer also works. (PCM was set to 0, so maybe that was the reason I could not hear anything before with pulse)

Anyway. Thanks a lot!

---

