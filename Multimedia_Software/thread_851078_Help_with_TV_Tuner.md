---
title: "Help with TV Tuner"
date: 2008-07-06
forum: Multimedia Software
---

### Post by quantumstitch on 2008-07-06
Hi All,
I have just switched to Ubuntu 8.04 from Fedora Core. I always had a problem with my old TV tuner card in Fedora. It works great now. However, I have to swap the speaker cable from the sound card jack to the tv card jack to listen to TV. Also, the sound from the tv card just streams out, without xawtv or tvtime running. Is there a way to fix this so that the audio from the tv jack is input to the sound card and only output when a xawtv or tvtime is running? The sound is on-board, btw. Thanks,
-stitch

---

### Post by Jose Catre-Vandis on 2008-07-06
Without knowing what tv card you have I am just guessing and making suggestions:

1. Run a small jack lead from your tv card to your line in?

or

2. Check to see if your tv card has a digital audio output connector on it (actually on the card) and that your motherboard has a connector too. Then use a cable, like the ones for connecting up CD-Roms. I do this with my card to get sound.

also sounds like something is starting up in order for sound to be coming from the tv card without you running an application. Try checking with top or system monitor to see what might be running, or have a play with alsamixer/pulse mixer.

---

### Post by quantumstitch on 2008-07-06
THanks for the help. I think a little more info may help...

Only the on-board sound card shows up in alsa. Obviously manipulating any of these does nothing to the tuner card.

The card is an old All-In-Wonder card (circa 2000). Ubuntu identifies it as having the bt878 chip. It has coax cable in, composite in, and a simple audio jack out. I don't think it supports digital audio. It might have an output on the board in the case, but I haven't checked.

From lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
01:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```



-stitch

---

### Post by fishbulb1022 on 2008-12-27
If the audio is streaming while tvtime is not running, its because its not auto muting the line ine when you close the program. I saw that several other people were having problems (as well as myself) so I posted a fix [http://ubuntuforums.org/showthread.php?p=6445498#post6445498]("http://ubuntuforums.org/showthread.php?p=6445498#post6445498")

Hope this works for you.

---

