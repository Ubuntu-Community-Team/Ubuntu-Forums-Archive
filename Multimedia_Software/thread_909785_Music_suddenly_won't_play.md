---
title: "Music suddenly won't play"
date: 2008-09-03
forum: Multimedia Software
---

### Post by Rixii on 2008-09-03
I've been using Ubuntu 7.10 for months now, and although I could never get my 5.1 sound working, I *have* been getting 2.1 so I've kinda just let it go. Now, today, I open up my music player (Rhythmnbox) and it won't play my music!

It gives me: "Playback Error - Could not get/set settings from/on source"

The sound works normally for the rest of my system, and my music WILL play in VLC. So, anyone have any idea what went wrong? I have tried restarting X to no avail, and I've looked through the settings

Also, if anyone happens to know how to set up the 5.1 sound for a Sound Blaster Live! emu10k1 card, please let me know. I never could figure it out, and if I'm fixing sound now, might as well start from the beginning.. (If you can only help me with my music though, I'll gladly take that.)

EDIT: When I open the GNOME ALSA Mixer, I get an error saying: "An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly." I haven't seen that before either..

---

### Post by Rixii on 2008-09-05
Can anyone help me?

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lspci
```

---

### Post by Rixii on 2008-09-05
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

---

